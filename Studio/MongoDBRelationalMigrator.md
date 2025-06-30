# MongoDB Relational Migrator

MongoDB developed a handy tool to accelerate customer migrations from legacy relational systems to MongoDB. The MongoDB Relational Migrator is a sort of ETL that takes a source relational DDL, then through a process of denormalization, generates a target MongoDB schema based on denormalization performed by the user (or suggested by the application), then takes the mapping and applies it to data moved from the RDBMS instance to a MongoDB instance.&nbsp; You may consult additional [commercial information](<https://www.mongodb.com/products/relational-migrator> "target=\"\_blank\"") and [documentation](<https://www.mongodb.com/docs/relational-migrator/> "target=\"\_blank\"") on the MongoDB website.

&nbsp;

The dernomalization part of the Relational Migrator is inspired by our [own feature](<SuggestdenormalizationofaSQLsche.md>) on the subject, developed back in 2016...

&nbsp;

Based on a close collaboration with MongoDB, users can, since v6.11.8, easily import (a.k.a. reverse-engineer) one of the outputs of the MongoDB Relational Migrator.&nbsp; The steps to follow are really simple... &nbsp;

## Export relmig file from the MongoDB Relational Migrator

Before you export, you first should go through the steps of creating the [Mapping and Modelling Rules](<https://www.mongodb.com/docs/relational-migrator/mapping-rules/mapping-rules/> "target=\"\_blank\"") in the Relational Migrator, as well as go through the [Schema Recommendations](<https://www.mongodb.com/docs/relational-migrator/mapping-rules/new-rules-suggested-mappings/> "target=\"\_blank\"").&nbsp; Once you are satisfied with your target MongoDB model, you want to export it so it can be imported into a Hackolade Studio model.

&nbsp;

This export can be performed either from the opening screen by clicking on the ellipsis menu for a given project and choosing Export:

![Relational Migrator - export from opening scr](<lib/Relational Migrator - export from opening scr.png>)

&nbsp;

&nbsp;

or from inside a project, by clicking the top 3 dots menu and choosing Export:

![Relational Migrator - export from project](<lib/Relational Migrator - export from project.png>)

&nbsp;

Next, the Relational Migrator displays this dialog.&nbsp; Click Export:

![Relational Migrator - export dialog](<lib/Relational Migrator - export dialog.png>)

&nbsp;

&nbsp;

A file with the .relmig extension is generated and saved in the default Downloads folder of your browser.

&nbsp;

## Reverse-engineer relmig file into Hackolade Studio

In Hackolade Studio, select an existing MongoDB data model, or create a new one.&nbsp; The model must be for the MongoDB target.

&nbsp;

Select the menu Tools \> Reverse-Engineer \> MongoDB Relational Migrator file...

&nbsp;

![Relational Migrator - reverse-engineering menu](<lib/Relational Migrator- reverse-engineering menu.png>)

&nbsp;

&nbsp;

Click the folder icon from the following dialog, and use your OS file picker to choose the .relmig file previously downloaded, then click OK:

![Relational Migrator - file picker](<lib/Relational Migrator - file picker.png>)

&nbsp;

The model will promptly be created in Hackolade Studio where it can be enriched:

![Relational Migrator - imported data model](<lib/Relational Migrator - imported data model.png>)

&nbsp;

You may apply further evolutions by leveraging to rich feature set of the application:

&nbsp;

