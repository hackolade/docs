# Machine-to-machine connection to Collibra

This page is relevant for machine-to-machine OAuth to a Collibra instance using a service account. It does not apply for Hackolade Studio [client connection to a Collibra instance using an identified user via OAuth](OAuthsetupwithEntraID.md).

&nbsp;

Use this Machine-to-machine OAuth for Collibra Data Dictionary to create and test a connection in Hackolade Studio, then run publishing to Collibra via the Command Line Interface, possibly on a dedicated server, and possibly in Docker. Connecting from the Studio application is not supported for this auth type.

&nbsp;

## Connect the CLI to Collibra with client credentials

### 1. Prerequisite in Collibra: register a new application

1\. In Collibra, go to OAuth settings and register a new application [Collibra OAuth documentation](https://productresources.collibra.com/docs/collibra/latest/Content/Settings/OAuth/co_oauth-settings.htm)

&nbsp;

2\. Choose application type Integration (not Platform)

&nbsp;

![Collibra M2M Register application](<lib/Collibra M2M Register application.png>)

&nbsp;

3\. Retain the Client ID and Client Secret, they will be needed in next step in Studio.

&nbsp;

### 2. Create a Collibra connection in Studio UI

1. Access the Data Dictionary Connections in Hackolade Studio Desktop.
   1. Create a new model (pick the target you need, e.g. MongoDB).
   2. Open Main Menu > Tools > Forward-Engineer > Governance Platforms > Collibra…
2. Click Add
3. Fill in in Connection tab:
   1. Name: e.g. My Collibra client credentials connection
   2. Path: your Collibra base URL (e.g. [https://your-instance.collibra.com](https://your-instance.collibra.com/))
4. Fill in in Authentication tab:
   1. Authentication: OAuth
   2. Identity provider: Collibra client credentials (Command Line Interface only)
   3. Client ID and Client Secret: obtained at step 1 from Collibra OAuth settings
5. Click Test connection: should succeed.
6. Click Save.

&nbsp;

A yellow warning explains this connection is CLI only.

&nbsp;

![Collibra M2M Create CLI connection](<lib/Collibra M2M Create CLI connection.png>)

&nbsp;

### 3. Use the connection in CLI

#### Option A: saved connection name

Export is optional if the connection is saved in the same Hackolade profile the CLI uses.

&nbsp;

#### Option B: export file

1\. In Studio ID, select the connection in the list.\
2\. Click Export and save the JSON/BIN file.\
3\. Then run CLI from a terminal (see [Command Line Interface documentation](<https://hackolade.com/help/CommandLineInterface.html#forwEngDataDictionary>).)

&nbsp;

**Publishing example:**

&nbsp;

```bash
hackolade forwengdatadictionary \
 --connectname="My Collibra client credentials connection" \
 --model="/path/to/model.json" \
 --targetresource=your_collibra_domain_name
```

&nbsp;

**Reverse-engineer example:**

&nbsp;

```bash
hackolade revengdatadictionary \
 --target=MONGODB \
 --connectname="My Collibra client credentials connection" \
 --datadictionaryresource=your_collibra_domain_name \
 --model="/absolute/path/to/output-model.json"
```

&nbsp;

Use --connectfile instead of --connectname when using an exported JSON file.

&nbsp;

## Additional notes

While the GUI can be used to create a CLI connection in Hackolade Studio to be reused by the CLI, it is not possible to use a machine-to-machine OAuth mechanism from the GUI.

&nbsp;

CLI-only connections show a “CLI only” badge in the list.

&nbsp;

![Collibra M2M CLI only badge](<lib/Collibra M2M CLI only badge.png>)

&nbsp;

Connect or double-click shows a warning and stops.

&nbsp;

![Collibra M2M CLI only dialog](<lib/Collibra M2M CLI only dialog.png>)
