# GenAI-created Mermaid ER diagram

As the first step of our [AI roadmap](DatamodelingandtheAIlifecycle.md), it is now possible, starting with v8.3.2, to import (reverse-engineer) a model in Mermaid ER diagram code. This features allows to instantly generate models, polyglot or physical, then edit and enrich them, plus integrate suggestions from GenAI. By integrating AI-generated diagrams with Hackolade Studio’s intuitive modeling, teams can efficiently develop and refine their data models, enhancing collaboration and accelerating the development cycle.

&nbsp;

## Mermaid

[Mermaid](<https://www.mermaidchart.com/> "target=\"_blank\"") is a JavaScript-based diagramming and charting tool that uses Markdown-inspired text definitions, and a renderer to create and modify complex diagrams. Among many other types of diagrams, Mermaid supports [ER diagrams](<https://mermaid.js.org/syntax/entityRelationshipDiagram.html> "target=\"_blank\""). Users have the possibility to use the tool for ER diagrams with basic functionality. Its [playground](<https://www.mermaidchart.com/play#pako:eNptj00Kg0AMha8SZu8F3NYui2DbnSCpE4aAkylxXKl3V5lS7c_bhHxJ3iOjaYMlkxvSgtEp-lpg1el-vZWXcwVj6jf1UVkcCHr6geSRu53K4B-kgO6waTESKDleTzBykGYjaT6nUlbF38iglrRh-2WW8O5yTPZhkPhh_n5pmrIsjK-wHJ4dttTXYuYFcGBQ9A> "target=\"_blank\"") also allows to create simple diagrams, although far from the professional level and capabilities of Hackolade Studio.

&nbsp;

Mermaid is a popular tool, meaning that there are many existing ER diagrams that users would like to easily convert into Hackolade Studio models. Also, Mermaid has a very convenient AI interface, including their [Mermaid Chart GPT plugin](<https://docs.mermaidchart.com/plugins/mermaid-chart-gpt> "target=\"_blank\"") to ChatGPT..

&nbsp;

Note that, among other things, Mermaid does NOT support: [NOT NULL constraints](<https://github.com/mermaid-js/mermaid/issues/4429> "target=\"_blank\""), string length or numeric precision and scale, complex data types (except the root level of an array with no further details), generation of DDLs or physical schemas. It nevertheless remains a handy way to prompt GenAI LLMs, then import the output into Hackolade Studio.

&nbsp;

## Prompt

ChatGPT and other generative AI models find it easier to generate ER diagrams in Mermaid code compared to SQL DDL or traditional modeling standards because Mermaid uses a simple, human-readable syntax that closely aligns with natural language. Its declarative and visual style allows AI to map conceptual relationships directly into diagram code without needing strict adherence to data types, constraints, or database-specific rules. Unlike DDLs, which requires precision and contextual knowledge of database engines, Mermaid is more forgiving and doesn’t require runtime validation. This makes it an ideal format for GenAI to produce quickly and accurately from natural prompts.

&nbsp;

You may create prompts using entire business requirements, and fine-tune the prompt until the result suits your needs. For the purpose of this documentation page, here is a super simple prompt example:

&nbsp;

```text
Generate an ERD in Mermaid code for an e-commerce application, full with tables, columns, data types, relationships.  Place table comments just above each table, and column comments inline.
```

&nbsp;

With some LLMs, it might be required to specify:\
`Provide syntactically correct code so it can be accepted by `[`https://www.mermaidchart.com/`](https://www.mermaidchart.com/)

&nbsp;

You may also ask the LLM to

&nbsp;

```text
Only use the information provided
```

&nbsp;

or to

&nbsp;

```text
Also suggest additional data that should be included.
```

&nbsp;

> [!NOTE]
> The results vary greatly depending on the LLM and the prompt.

&nbsp;

Here is a simple example response from ChatGPT for the above prompt:

&nbsp;

```text
erDiagram
    %% ----------------------------
    %% Users Table
    %% Stores registered customers and admin users
    %% ----------------------------
    USERS {
        int id PK "Primary key"
        string username "Unique username"
        string email "User email address"
        string password_hash "Encrypted password"
        string role "customer/admin"
        datetime created_at "Account creation date"
    }
    %% ----------------------------
    %% Products Table
    %% Stores items for sale
    %% ----------------------------
    PRODUCTS {
        int id PK "Primary key"
        string name "Product name"
        string description "Product description"
        decimal price "Price of the product"
        int stock_quantity "Available stock"
        datetime created_at "Date added"
        int category_id FK "FK to product category"
    }
    %% ----------------------------
    %% Categories Table
    %% Groups of similar products
    %% ----------------------------
    CATEGORIES {
        int id PK "Primary key"
        string name "Category name"
        string description "Optional details"
    }
    %% ----------------------------
    %% Orders Table
    %% Each customer order
    %% ----------------------------
    ORDERS {
        int id PK "Primary key"
        int user_id FK "FK to USERS"
        datetime order_date "Date of order"
        string status "pending/shipped/delivered"
        decimal total_amount "Calculated order total"
    }
    %% ----------------------------
    %% Order Items Table
    %% Line items per order
    %% ----------------------------
    ORDER_ITEMS {
        int id PK "Primary key"
        int order_id FK "FK to ORDERS"
        int product_id FK "FK to PRODUCTS"
        int quantity "Quantity ordered"
        decimal unit_price "Snapshot of product price"
    }
    %% ----------------------------
    %% Addresses Table
    %% Shipping or billing addresses
    %% ----------------------------
    ADDRESSES {
        int id PK "Primary key"
        int user_id FK "FK to USERS"
        string address_line1 "Street address"
        string address_line2 "Apartment/Suite/etc."
        string city "City"
        string state "State or region"
        string postal_code "Zip or postal code"
        string country "Country"
        string type "billing/shipping"
    }
    %% ----------------------------
    %% Relationships
    %% ----------------------------
    USERS ||--o{ ORDERS : "places"
    USERS ||--o{ ADDRESSES : "has"
    PRODUCTS ||--o{ ORDER_ITEMS : "included in"
    ORDERS ||--o{ ORDER_ITEMS : "contains"
    ORDERS }o--|| USERS : "belongs to"
    ORDER_ITEMS }o--|| PRODUCTS : "refers to"
    PRODUCTS }o--|| CATEGORIES : "belongs to"
```

&nbsp;

> [!IMPORTANT]
> Mermaid supports many different kinds of diagrams. Hackolade Studio currently only supports the import of ER diagram code of Mermaid. The code must start with the first line

&nbsp;

```text
erDiagram
```

&nbsp;

and follow the [specification](<https://mermaid.js.org/syntax/entityRelationshipDiagram.html> "target=\"_blank\""), and must be syntactically compliant for us to parse the code.

&nbsp;

A more complex prompt based on requirements could be:

&nbsp;

```text
I am tasked with designing a Human Resources training database system for employees.
Each employee is uniquely identified by their Employee Reference Number. Employees belong to specific departments, and each department is managed by an employee, and each department has an Assistant Manager.
The system will store information about various training courses, including the attendance and grades of employees for each course.
Generate an Entity-Relationship Diagram (ERD) in Mermaid code, including the tables, columns, data types, relationships. Place table comments just above each table, and column comments inline.
```

&nbsp;

## Prompt template

To avoid too much iterative prompting, you may want to combine your requirements with a template such as the one below, replacing the options with your specific instructions.

&nbsp;

```text
You are a senior data modeler with 20 years of experience.
Task: Generate a complete Mermaid ER diagram for [system, domain to model]
(e.g., an e-commerce application, a hospital management system, a ride-sharing platform).

Modeling context:
- Level of data modeling: [conceptual | logical | physical]
- For [Targeted technology, platform] (e.g., technology-agnostic, RDBMS, document store, key-value stores, search engines, graph databases...)

Rules for this diagram:
1. Mermaid syntax compliance
   a. Follow the official spec: https://mermaid.js.org/syntax/entityRelationshipDiagram.html
   b. First line must be `erDiagram`.
   c. Must compile without errors on https://www.mermaidchart.com/

2. Comments
   a. Use `%%` comment lines above each entity to describe its purpose.
   b. Use quoted inline comments after each column to describe its purpose.

3. Entities
   a. Must include [list required entities] (or generate them based on the domain).

4. Attributes
   a. All attributes must have a data type for logical and physical models. Types must be single tokens (no commas or parentheses) to be compatible with Mermaid syntax.
```

&nbsp;

*`b. `Add constraints when applicable. Mermaid supports PK (Primary Key), FK (Foreign Key), and UK (Unique Key) markers after the attribute name. The key markers (PK, FK, UK) are optional but, if present, must be written exactly as shown, separated by commas, with no extra words. All other constraints (not null, default, check...) must be inside the comment`.`*

&nbsp;

```text
5. Relationships
   a. Define relationships with appropriate cardinality, including 0-to-many using Mermaid ER syntax.
   b. If this is a physical model with many-to-many relationships, provide junction tables to fully normalize the model.
   c. Ensure relationships make sense for the chosen modeling level and paradigm.

6. Naming conventions
   a. Use [naming style] (e.g., snake_case, PascalCase).

Output format: Provide a Mermaid code block that is ready to paste directly into a Mermaid-compatible renderer.
```

&nbsp;

Sometimes the generated Mermaid code cannot be reverse-engineered because the syntax is not fully valid, which can happen with AI-generated output. If necessary, continue the conversation with the LLM using an iterative prompting approach.

1. Copy the exact parsing error message you received:
2. Provide this error message and ask the LLM to fix the code based on that error.

&nbsp;

Gen AI will adjust the output to address the parsing issue and progressively improve the code until it meets Mermaid’s syntax requirements.

&nbsp;

## Reverse-engineer in Hackolade Studio

There are 2 ways to import Mermaid ER diagram code into Hackolade Studio: by reading Mermaid files with .mmd extensions, or by reading the clipboard into which you would have copied the Mermaid code from the GenAI provider's response to your prompt.

&nbsp;

Depending on the target technology of your model, the import process will convert the data types into the closest corresponding type for the target. Naming conventions, if enabled, are applied.

&nbsp;

With either method, the above Mermaid code will result in this Hackolade Studio diagram:\
![Mermaid ER e-commerce from ChatGPT](<lib/Mermaid ER e-commerce from ChatGPT.png>)

&nbsp;

### From Mermaid files

Go to Tools > Reverse-Engineer > Mermaid ER Diagrams... and select one or more Mermaid files with the extension .mmd

&nbsp;

![Mermaid RE from file](<lib/Mermaid RE from file.png>)

&nbsp;

### From your Clipboard

Our Open From dialog, which already allows to [open models from](OpenmodelfromGitrepo.md) either your local computer or from any of the Git repo providers you might have configured, is where we have allowed to read your clipboard (the temporary storage in your computer's memory.). When you prompt your GPT and ask to create output in Mermaid ER diagram code, you may click the Copy button which populates your clipboard. When you access the Open From dialog and choose the Clipboard tab on the left, we automatically read the latest entry in your clipboard. If you change the content of the clipboard, you can update the content of the dialog by clicking the Refresh button.

&nbsp;

![Open From Mermaid ER diagram code](<lib/Open From Mermaid ER diagram code.png>)

&nbsp;

When you click on the Open button, the Mermaid ER diagram code is parsed and is added to the currently opened model. Depending on the selected target, the data types are mapped according to the closest available data type for that target. If no model is already opened, you are prompted to choose the target.

&nbsp;

### From remote repository

Similarly, it is possible, if you have a [repository connection](Connecttoarepositoryhub.md) to a repo provider, to select one or more files with Mermaid ER diagram code.

&nbsp;

### With the Command-Line Interface

With the argument --source=mermaid in the command [revEngDiagram](<https://hackolade.com/help/CommandLineInterface.html#revEngDiagram>) of the CLI, you may automate the import of files with Mermaid ER diagram code.
