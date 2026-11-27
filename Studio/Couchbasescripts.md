---
description: Hackolade Studio generates Couchbase scripts and JavaScript Ottoman ODM schema files from your Couchbase data model.
seoTitle: Generate Couchbase N1QL and Ottoman schemas
image: lib/Forward-Engineering - Couchbase Ottoman Schem.png
---
# Couchbase scripts

For those in a technology stack using JavaScript, and are using the [Ottoman ODM](<http://ottomanjs.com/> "target=\"_blank\""), Hackolade also provides the option to export a JavaScript Ottoman schema file for the collection definition via the menu option Tools > Forward-Engineering > Ottoman Schema or Couchbase script

![Forward-Engineering - Ottoman Schema file](<lib/Forward-Engineering - Ottoman Schema file.png>)

The same information can also be viewed in the Ottoman Schema tab:\
![Forward-Engineering - Couchbase Ottoman Schem](<lib/Forward-Engineering - Couchbase Ottoman Schem.png>)

We provide a sort of "forward-engineering by example", with an automatic JSON data sample generation. The script also includes the creation of indexes, and it can be applied to the database instance, provided that appropriate credentials are granted to the user. If the specified bucket does not exist, we attempt to create it.

![Couchbase forward-engineering script](<lib/Couchbase forward-engineering script.png>)

The following credentials are required:

- if the bucket exists, the user should have at least:

* [Query Manage Index](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#query-manage-index> "target=\"_blank\"") - to insert indexes.
* [Query Insert](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#query-insert> "target=\"_blank\"") - to Insert documents.

If a bucket doesn't exist, the user needs either [Full Admin](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#full-admin> "target=\"_blank\"") or [Cluster Admin](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#cluster-admin> "target=\"_blank\"") to be able to create the bucket.

## Custom script hooks for Couchbase with scopes and collections

For a data model of the **Couchbase w/ collections** target (see [Couchbase with scopes and collections](Couchbasewithscopesandcollection.md)), you can insert your own N1QL statements or comments in the generated Couchbase script. They work like the [custom script hooks for SQL targets](<https://hackolade.com/help/Target-specific.html#Custom%20script%20hooks>), with hook points of their own. A common need is a pause after each CREATE SCOPE and each CREATE COLLECTION statement: Couchbase creates scopes and collections asynchronously, so a statement that uses a new collection right after its creation can fail.

Hackolade Studio replaces the variables described below, inserts the rest of your content as you wrote it, and does not change the generated statements. With the hooks defined in the data model, the [Command-Line Interface](CommandLineInterface.md) produces the same script as the application.

> [!NOTE]
> Custom script hooks, when created, are stored in the data model file.  They apply only for that specific data model.  If you want a custom script hook to appear in multiple data models, it needs to be repeated.  Or stored in a model that serves as a template for new ones.

### Hook points

You can insert custom content at these positions of a Couchbase script:

- Before all statements
- After all statements
- Before each CREATE SCOPE statement
- Before a specific CREATE SCOPE statement
- After each CREATE SCOPE statement
- After a specific CREATE SCOPE statement
- Before each CREATE COLLECTION statement
- Before a specific CREATE COLLECTION statement
- After each CREATE COLLECTION statement
- After a specific CREATE COLLECTION statement

There is currently no hook point around CREATE INDEX statements. The indexes of a collection are created after the "After CREATE COLLECTION" hooks of that collection, so a pause placed there also runs before the creation of its indexes.

### Where to define the hooks

You define the hooks in the **Custom scripts** property of the Properties Pane of a data model, at three levels:

- **Model level**: Before all statements, After all statements, and before and after each CREATE SCOPE and each CREATE COLLECTION of the data model. Hackolade Studio generates one script per scope, so the Before all statements and After all statements hooks are placed at the start and at the end of the script of each scope.
- **Scope level**: before and after the CREATE SCOPE statement of this scope, and before and after each CREATE COLLECTION statement of the collections in this scope.
- **Collection level**: before and after the CREATE COLLECTION statement of this collection.

You can also define hooks for all your Couchbase data models at the target level. In **Tools > Options > Forward-Engineering**, in the Script generation section, select the **Couchbase w/ collections** target, then select a file for each hook point you need. Hackolade Studio reads the content of these files when it generates the script. Target-level hooks are not available in the browser version of Hackolade Studio.

Hooks are cumulative, in the same order as for [SQL targets](<https://hackolade.com/help/Target-specific.html#Level%20priority%20and%20execution%20order>). Before hooks run from the target level down to the collection level; after hooks run from the collection level back up to the target level. For example, with hooks at every level, the script of the `sales` scope contains this sequence around the creation of the `order` collection:

```text
target-level Before each CREATE COLLECTION
model-level Before each CREATE COLLECTION
scope-level Before each CREATE COLLECTION
collection-level Before CREATE COLLECTION
CREATE COLLECTION default:`retail`.`sales`.`order` IF NOT EXISTS;
collection-level After CREATE COLLECTION
scope-level After each CREATE COLLECTION
model-level After each CREATE COLLECTION
target-level After each CREATE COLLECTION
CREATE INDEX statements of the order collection
```

### Variables

Three variables are available in Couchbase hooks. The Custom scripts dialog lists them in its footer, and you can copy them from there:

- `${bucketName}`: the name of the bucket of the scope
- `${scopeName}`: the name of the current scope
- `${collectionName}`: the name of the current collection

Hackolade Studio replaces each variable with the name in backticks, as in the generated statements: `${bucketName}.${scopeName}.${collectionName}` becomes `` `retail`.`sales`.`order` ``. Do not add backticks around the variables yourself. The namespace is not part of the variables, so write `default:` before them when your statement needs it.

Around a CREATE SCOPE statement, `${bucketName}` and `${scopeName}` have a value, and `${collectionName}` is empty. Around a CREATE COLLECTION statement, the three variables have a value. In Before all statements and After all statements, `${bucketName}` and `${scopeName}` have the value of the scope of the script; `${collectionName}` has a value only when the script creates a single collection. As for SQL targets, a variable used outside of its scope is replaced with an empty value.

### Example: pause after each scope and collection creation

N1QL has no pause statement, and teams usually run the generated script with their own deployment tool. In this example, the team's deployment tool reads a `-- WAIT` comment as an instruction to wait until the object exists. The team adds this comment at model level, in **After each CREATE SCOPE**:

```sql
-- WAIT default:${bucketName}.${scopeName}
```

and in **After each CREATE COLLECTION**:

```sql
-- WAIT default:${bucketName}.${scopeName}.${collectionName}
```

The script of the `sales` scope then contains:

```sql
CREATE SCOPE default:`retail`.`sales` IF NOT EXISTS;

-- WAIT default:`retail`.`sales`

CREATE COLLECTION default:`retail`.`sales`.`customer` IF NOT EXISTS;

-- WAIT default:`retail`.`sales`.`customer`

CREATE COLLECTION default:`retail`.`sales`.`order` IF NOT EXISTS;

-- WAIT default:`retail`.`sales`.`order`
```

Replace the `-- WAIT` marker with the command or the convention of your own deployment tool.

### Hooks and sample data

> [!WARNING]
> When the generated script includes sample data (the **Include sample data** option), a custom script can make the insertion of the sample data fail, depending on what it contains. For example, a hook that drops a collection or changes its settings can break the UPSERT statements that follow. Check the full script before you apply it.

In the application, Hackolade Studio shows the sample data in a separate Sample data tab, without hooks. In a single script file, the UPSERT statements of the sample data come after the hooks of the last collection, and before the After all statements hooks.
