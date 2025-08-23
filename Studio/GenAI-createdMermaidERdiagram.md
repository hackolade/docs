# GenAI-created Mermaid ER diagram

As the first step of our [AI roadmap](<DatamodelingandtheAIlifecycle.md>), it is now possible, starting with v8.3.2, to import (reverse-engineer) a model in Mermaid ER diagram code.&nbsp; This features allows to instantly generate models, polyglot or physical, then edit and enrich them, plus integrate suggestions from GenAI.&nbsp; By integrating AI-generated diagrams with Hackolade Studio’s intuitive modeling, teams can efficiently develop and refine their data models, enhancing collaboration and accelerating the development cycle.

&nbsp;

## Mermaid&nbsp;

[Mermaid](<https://www.mermaidchart.com/> "target=\"\_blank\"") is a JavaScript-based diagramming and charting tool that uses Markdown-inspired text definitions, and a renderer to create and modify complex diagrams. Among many other types of diagrams, Mermaid supports [ER diagrams](<https://mermaid.js.org/syntax/entityRelationshipDiagram.html> "target=\"\_blank\"").&nbsp; Users have the possibility to use the tool for ER diagrams with basic functionality.&nbsp; Its [playground](<https://www.mermaidchart.com/play#pako:eNptj00Kg0AMha8SZu8F3NYui2DbnSCpE4aAkylxXKl3V5lS7c\_bhHxJ3iOjaYMlkxvSgtEp-lpg1el-vZWXcwVj6jf1UVkcCHr6geSRu53K4B-kgO6waTESKDleTzBykGYjaT6nUlbF38iglrRh-2WW8O5yTPZhkPhh\_n5pmrIsjK-wHJ4dttTXYuYFcGBQ9A> "target=\"\_blank\"") also allows to create simple diagrams, although far from the professional level and capabilities of Hackolade Studio.

&nbsp;

Mermaid is a&nbsp; popular tool, meaning that there are many existing ER diagrams that users would like to easily convert into Hackolade Studio models. Also, Mermaid has a very convenient AI interface, including their [Mermaid Chart GPT plugin](<https://docs.mermaidchart.com/plugins/mermaid-chart-gpt> "target=\"\_blank\"") to ChatGPT..&nbsp;

&nbsp;

Note that, among other things, Mermaid does NOT support: [NOT NULL constraints](<https://github.com/mermaid-js/mermaid/issues/4429> "target=\"\_blank\""), string length or numeric precision and scale, complex data types (except the root level of an array with no further details), generation of DDLs or physical schemas.&nbsp; It nevertheless remains a handy way to prompt GenAI LLMs, then import the output into Hackolade Studio.

&nbsp;

## Prompt

ChatGPT and other generative AI models find it easier to generate ER diagrams in Mermaid code compared to SQL DDL or traditional modeling standards because Mermaid uses a simple, human-readable syntax that closely aligns with natural language. Its declarative and visual style allows AI to map conceptual relationships directly into diagram code without needing strict adherence to data types, constraints, or database-specific rules. Unlike DDLs, which requires precision and contextual knowledge of database engines, Mermaid is more forgiving and doesn’t require runtime validation. This makes it an ideal format for GenAI to produce quickly and accurately from natural prompts.

&nbsp;

You may create prompts using entire business requirements, and fine-tune the prompt until the result suits your needs.&nbsp; For the purpose of this documentation page, here is a super simple prompt example:

> Generate an ERD in Mermaid code for an e-commerce application, full with tables, columns, data types, relationships.&nbsp; Place table comments just above each table, and column comments inline.

&nbsp;

With some LLMs, it might be required to specify:&nbsp;

Provide syntactically correct code so it can be accepted by [https://www.mermaidchart.com/](<https://www.mermaidchart.com/>)

&nbsp;

You may also ask the LLM to&nbsp;

> Only use the information provided

&nbsp;or to&nbsp;

> Also suggest additional data that should be included.

&nbsp;

**Note:** the results vary greatly depending on the LLM and the prompt. &nbsp;

&nbsp;

&nbsp;

Here is a simple example response from ChatGPT for the above prompt:

&nbsp;

> erDiagram\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Users Table\
&nbsp; &nbsp; %% Stores registered customers and admin users\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; USERS {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; string username "Unique username"\
&nbsp; &nbsp; &nbsp; &nbsp; string email "User email address"\
&nbsp; &nbsp; &nbsp; &nbsp; string password\_hash "Encrypted password"\
&nbsp; &nbsp; &nbsp; &nbsp; string role "customer/admin"\
&nbsp; &nbsp; &nbsp; &nbsp; datetime created\_at "Account creation date"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Products Table\
&nbsp; &nbsp; %% Stores items for sale\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; PRODUCTS {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; string name "Product name"\
&nbsp; &nbsp; &nbsp; &nbsp; string description "Product description"\
&nbsp; &nbsp; &nbsp; &nbsp; decimal price "Price of the product"\
&nbsp; &nbsp; &nbsp; &nbsp; int stock\_quantity "Available stock"\
&nbsp; &nbsp; &nbsp; &nbsp; datetime created\_at "Date added"\
&nbsp; &nbsp; &nbsp; &nbsp; int category\_id FK "FK to product category"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Categories Table\
&nbsp; &nbsp; %% Groups of similar products\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; CATEGORIES {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; string name "Category name"\
&nbsp; &nbsp; &nbsp; &nbsp; string description "Optional details"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Orders Table\
&nbsp; &nbsp; %% Each customer order\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; ORDERS {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; int user\_id FK "FK to USERS"\
&nbsp; &nbsp; &nbsp; &nbsp; datetime order\_date "Date of order"\
&nbsp; &nbsp; &nbsp; &nbsp; string status "pending/shipped/delivered"\
&nbsp; &nbsp; &nbsp; &nbsp; decimal total\_amount "Calculated order total"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Order Items Table\
&nbsp; &nbsp; %% Line items per order\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; ORDER\_ITEMS {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; int order\_id FK "FK to ORDERS"\
&nbsp; &nbsp; &nbsp; &nbsp; int product\_id FK "FK to PRODUCTS"\
&nbsp; &nbsp; &nbsp; &nbsp; int quantity "Quantity ordered"\
&nbsp; &nbsp; &nbsp; &nbsp; decimal unit\_price "Snapshot of product price"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Addresses Table\
&nbsp; &nbsp; %% Shipping or billing addresses\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; ADDRESSES {\
&nbsp; &nbsp; &nbsp; &nbsp; int id PK "Primary key"\
&nbsp; &nbsp; &nbsp; &nbsp; int user\_id FK "FK to USERS"\
&nbsp; &nbsp; &nbsp; &nbsp; string address\_line1 "Street address"\
&nbsp; &nbsp; &nbsp; &nbsp; string address\_line2 "Apartment/Suite/etc."\
&nbsp; &nbsp; &nbsp; &nbsp; string city "City"\
&nbsp; &nbsp; &nbsp; &nbsp; string state "State or region"\
&nbsp; &nbsp; &nbsp; &nbsp; string postal\_code "Zip or postal code"\
&nbsp; &nbsp; &nbsp; &nbsp; string country "Country"\
&nbsp; &nbsp; &nbsp; &nbsp; string type "billing/shipping"\
&nbsp; &nbsp; }\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; %% Relationships\
&nbsp; &nbsp; %% ----------------------------\
&nbsp; &nbsp; USERS \|\|--o{ ORDERS : "places"\
&nbsp; &nbsp; USERS \|\|--o{ ADDRESSES : "has"\
&nbsp; &nbsp; PRODUCTS \|\|--o{ ORDER\_ITEMS : "included in"\
&nbsp; &nbsp; ORDERS \|\|--o{ ORDER\_ITEMS : "contains"\
&nbsp; &nbsp; ORDERS }o--\|\| USERS : "belongs to"\
&nbsp; &nbsp; ORDER\_ITEMS }o--\|\| PRODUCTS : "refers to"\
&nbsp; &nbsp; PRODUCTS }o--\|\| CATEGORIES : "belongs to"\
&nbsp;

&nbsp;

**Important:** Mermaid supports many different kinds of diagrams.&nbsp; Hackolade Studio currently only supports the import of ER diagram code of Mermaid.&nbsp; The code must start with the first line&nbsp;

> erDiagram

&nbsp;and follow the [specification](<https://mermaid.js.org/syntax/entityRelationshipDiagram.html> "target=\"\_blank\""), and must be syntactically compliant for us to parse the code.

&nbsp;

A more complex prompt based on requirements could be:

> I am tasked with designing a Human Resources training database system for employees.\
Each employee is uniquely identified by their Employee Reference Number. Employees belong to specific departments, and each department is managed by an employee, and each department has an Assistant Manager.\
The system will store information about various training courses, including the attendance and grades of employees for each course.\
Generate an Entity-Relationship Diagram (ERD) in Mermaid code, including the tables, columns, data types, relationships. Place table comments just above each table, and column comments inline.

&nbsp;

## Prompt template

To avoid too much iterative prompting, you may want to combine your requirements with a template such as the one below, replacing the options with your specific instructions.

&nbsp;

> You are a senior data modeler with 20 years of experience.\
\
Task: Generate a complete Mermaid ER diagram for \[system, domain to model\] \
(e.g., an e-commerce application, a hospital management system, a ride-sharing platform).\
\
Modeling context:\
\- Level of data modeling: \[conceptual \| logical \| physical\]\
\- For \[Targeted technology, platform\] (e.g., technology-agnostic, RDBMS, document store, key-value stores, search engines, graph databases...)\
\
Rules for this diagram:\
&#49;. Mermaid syntax compliance\
&nbsp;&nbsp; a. Follow the official spec: https://mermaid.js.org/syntax/entityRelationshipDiagram.html\
&nbsp;&nbsp; b. First line must be \`erDiagram\`.\
&nbsp;&nbsp; c. Must compile without errors on https://www.mermaidchart.com/\
\
&#50;. Comments\
&nbsp;&nbsp; a. Use \`%%\` comment lines above each entity to describe its purpose.\
&nbsp;&nbsp; b. Use quoted inline comments after each column to describe its purpose.\
\
&#51;. Entities\
&nbsp;&nbsp; a. Must include \[list required entities\] (or generate them based on the domain).\
\
&#52;. Attributes\
&nbsp;&nbsp; a. All attributes must have a data type for logical and physical models. Types must be single tokens (no commas or parentheses) to be compatible with Mermaid syntax.\
&nbsp;&nbsp; b. Add constraints when applicable. Mermaid supports PK (Primary Key), FK (Foreign Key), and UK (Unique Key) markers after the attribute name. The key markers (PK, FK, UK) are optional but, if present, must be written exactly as shown, separated by commas, with no extra words. All other constraints (not null, default, check...) must be inside the comment.\
\
&#53;. Relationships\
&nbsp;&nbsp; a. Define relationships with appropriate cardinality, including 0-to-many using Mermaid ER syntax.\
&nbsp;&nbsp; b. If this is a physical model with many-to-many relationships, provide junction tables to fully normalize the model.\
&nbsp;&nbsp; c. Ensure relationships make sense for the chosen modeling level and paradigm.\
\
&#54;. Naming conventions\
&nbsp;&nbsp; a. Use \[naming style\] (e.g., snake\_case, PascalCase).\
\
Output format: Provide a Mermaid code block that is ready to paste directly into a Mermaid-compatible renderer.

&nbsp;

Sometimes the generated Mermaid code cannot be reverse-engineered because the syntax is not fully valid, which can happen with AI-generated output.&nbsp; If necessary, continue the conversation with the LLM using an iterative prompting approach.

&nbsp;

1. Copy the exact parsing error message you received:
1. Provide this error message and ask the LLM to fix the code based on that error.

&nbsp;

Gen AI will adjust the output to address the parsing issue and progressively improve the code until it meets Mermaid’s syntax requirements.

&nbsp;

## Reverse-engineer in Hackolade Studio

There are 2 ways to import Mermaid ER diagram code into Hackolade Studio: by reading Mermaid files with .mmd extensions, or by reading the clipboard into which you would have copied the Mermaid code from the GenAI provider's response to your prompt.

&nbsp;

Depending on the target technology of your model, the import process will convert the data types into the closest corresponding type for the target.&nbsp; Naming conventions, if enabled, are applied.

&nbsp;

With either method, the above Mermaid code will result in this Hackolade Studio diagram:

![Mermaid ER e-commerce from ChatGPT](<lib/Mermaid ER e-commerce from ChatGPT.png>)

&nbsp;

### From Mermaid files

Go to Tools \> Reverse-Engineer \> Mermaid ER Diagrams... and select one or more Mermaid files with the extension .mmd

&nbsp;

![Mermaid RE from file](<lib/Mermaid RE from file.png>)

&nbsp;

### From your Clipboard

Our Open From dialog, which already allows to [open models from](<OpenmodelfromGitrepo.md>) either your local computer or from any of the Git repo providers you might have configured, is where we have allowed to read your clipboard (the temporary storage in your computer's memory.).&nbsp; When you prompt your GPT and ask to create output in Mermaid ER diagram code, you may click the Copy button which populates your clipboard.&nbsp; When you access the Open From dialog and choose the Clipboard tab on the left, we automatically read the latest entry in your clipboard.&nbsp; If you change the content of the clipboard, you can update the content of the dialog by clicking the Refresh button.

&nbsp;

![Open From Mermaid ER diagram code](<lib/Open From Mermaid ER diagram code.png>)

&nbsp;

&nbsp;

When you click on the Open button, the Mermaid ER diagram code is parsed and is added to the currently opened model.&nbsp; Depending on the selected target, the data types are mapped according to the closest available data type for that target.&nbsp; If no model is already opened, you are prompted to choose the target.

&nbsp;

&nbsp;

### From remote repository

Similarly, it is possible, if you have a [repository connection](<Connecttoarepositoryhub.md>) to a repo provider, to select one or more files with Mermaid ER diagram code.

&nbsp;

&nbsp;

### With the Command-Line Interface

With the argument --source=mermaid in the command [revEngDiagram](<https://hackolade.com/help/CommandLineInterface.html#revEngDiagram> "target=\"\_blank\"") of the CLI, you may automate the import of files with Mermaid ER diagram code.

&nbsp;

