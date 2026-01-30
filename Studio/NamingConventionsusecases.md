# Naming Conventions use cases

In Hackolade Studio, every modeling object has two name fields: a mandatory Name and an optional Technical Name.&nbsp; This does not represent “business vs technical” by default — it simply means that if only the Name is defined, that value is used everywhere (in diagrams and in generated artifacts).&nbsp; A true separation only exists when a Technical Name is explicitly provided: the Name then plays the role of the business-friendly label, while the Technical Name is used for physical generation and implementation.

&nbsp;

When using [Naming Conventions](<Namingconventions.md>), which allows to automatically generate technical names from the business name, it is often useful to experiment at a small scale to understand the behavior and possibilities, prior to deploying at a larger scale. &nbsp;

&nbsp;

The enabling of Naming Conventions is not mandatory, and can be done for some targets and not others, if that's what you wish.&nbsp; It is performed in the menu Tools \> Options \> Naming Conventions for each target.&nbsp; There are 3 possible options for each target: disabled, Business-to-Technical, or Technical-to-Business.

&nbsp;

Typically there are no reasons to enable Technical-to-Business.&nbsp; The functionally makes most sense when enabled for Business-to-Technical.&nbsp; It does exist however for ad-hoc manipulations, as illustrated below.

&nbsp;

**Note:** even if Naming Conventions are disabled in Tools \> Options, it is possible to couple names of any individual object, as described [here](<https://hackolade.com/help/Namingconventions.html#Properties%20Pane>).&nbsp; Similarly, even if Naming Conventions are enabled in Tools \> Options, it is possible to decouple names of any individual object.

&nbsp;

When reading this page of use cases, it is assumed that you have reviewed the [documentation page](<Namingconventions.md>), and maybe even viewed the [video](<https://community.hackolade.com/slides/slide/naming-conventions-33> "target=\"\_blank\"").

&nbsp;

For naming conventions to work best, it is strongly suggested to make the rules of business-to-technical and technical-to-business symmetrical.&nbsp; Some features are not.&nbsp; For example, the removal of vowels or specific characters during business-to-technical transformation cannot be reconstructed during technical-to-business transformation.&nbsp; It is preferable to leverage an abbreviations file.

&nbsp;

&nbsp;

## Use Case # 1: apply Naming Conventions to an existing data model

Whenever you make a change to the Naming Conventions screen in Tools \> Options, the application displays a dialog to apply the changes to model open at the time of the change. You may choose to apply the changes to only the names already coupled in the open model.&nbsp; Or to the entire modeL. &nbsp;

&nbsp;

![Naming Conventions - apply changes dialog](<lib/Naming Conventions - apply changes dialog.png>)

&nbsp;

**Important note:** only the model open at the time of the change is concerned by these changes.&nbsp; If you want to apply the naming conventions to other model, you must proceed as follows...

&nbsp;

&#49;) open the model for which you want the set Naming conventions to be applied

&#50;) go to Tool \> Options \> Naming Conventions

&#51;) scroll down to the bottom of the dialog and click the button "Apply options to current model"

&#52;) choose whether you want the conventions to be applied only to the already coupled names, or to the entire model

&#53;) click the Apply button.

&nbsp;

If for example your model had no coupling of names previously, and your naming conventions are now set for this target to coupling of Business-to-Technical names, then if you choose to apply to the entire model, then all the names of all the objects will have their technical names derived from their business names according to the set rules. &nbsp;

&nbsp;

You can see below in case # 3 why it may be very important to only apply rules to previously coupled names, instead of to the entire model.

&nbsp;

## Use Case # 2: clear all technical names in a data model

**Warning:** this function allows to clear data.&nbsp; Be careful to not lose any valuable data that you might have wanted to retain.

&nbsp;

When you disable the coupling in Tools \> Options \> Naming Conventions, the application displays, similarly to case # 1 above, a dialog.&nbsp; But in this case a checkbox allows, if checked, to clear the technical names.

&nbsp;

![Naming Conventions - apply changes with clear](<lib/Naming Conventions - apply changes with clear.png>)

Again, it is possible to have this performed for only names previously coupled, or to the entire model. &nbsp;

&nbsp;

&nbsp;

## Use Case # 3: handle evolution of abbreviations and/or transformation rules

This is a very real use case\!&nbsp; Many companies have had databases in production for a long time, meaning that technical names are in place.&nbsp; Let's say that you now want to make naming conventions evolve, or to change some abbreviations, or simply to create naming conventions when none were in place before.&nbsp; It would be hard to impose a change of physical table names or column names.&nbsp; In this case, you want to keep existing technical names, but you want any future object to follow the (updated) naming conventions.

&nbsp;

Let's say that you have a model that was created with old naming conventions.&nbsp; You want to retain the physical/technical names as they are going forward, but you also want new objects to be created with the new rules or the abbreviations.&nbsp; You need to follow these steps:

&nbsp;

&#49;) decouple all the existing names&nbsp;

\- go to Tools \> Options \> Naming Conventions

\- disable name coupling by choosing No in the dropdown list "Enable name coupling"

\- click Apply

\- choose "To the entire model" -- DO NOT check the Clear checkbox

\- Click Apply

&#50;) re-enable Business-to-Technical name coupling with the new rules. &nbsp;

&#51;) when presented with the dialog to apply the naming conventions configuration, click Cancel so no changes are applied.&nbsp; All future objects created in the model will be created with coupling, using the conventions rules.

&nbsp;

Make sure to perform this operation for each model of the same target to which the rules would apply.

&nbsp;

## Use case # 4: generate business names from technical names during reverse-engineering

Prior to reverse-engineering from your database instance or from DDLs, you would want to assemble an abbreviations file.&nbsp; Abbreviations files in Hackolade Studio work both directions: in Business-to-Technical coupling, by taking full words or expressions listed in the first column of the CSV, and abbreviating them according to what's in the second column of the CSV in the corresponding line.&nbsp; It also works during reverse-engineering, by parsing technical names separated by underscores or camelCases, finding the abbreviation in the second column, and translating into a business name using the first column of the CSV in the corresponding line.&nbsp; Even if your coupling is set to Business-to-Technical, the application knows to convert technical names to business names during reverse-engineering.

&nbsp;

When performing a reverse-engineering operation from a technical source (DDL, JSON, schema file, database instance, or any system-driven structure), the incoming names are naturally technical names. At this point, 2 situations are possible:

1. you want to keep a single name. The technical name should simply become your Name. In that case, the procedure below does not apply.
1. you want to distinguish business names from technical names.&nbsp; You want the incoming technical names to generate business-friendly names, while preserving (or later regenerating) clean technical names using naming conventions.

&nbsp;

This workflow is relevant when:

* you want clean business names that differ from the technical identifiers found in the source,
* you want to initialize a Polyglot model from a technical artifact and immediately separate business vs. technical terminology,
* or you simply want dual naming (business + technical) in any target model.

&nbsp;

This process applies equally to any target model — Polyglot or any technology-specific model. The workflow is identical regardless of where the reverse-engineered structure ends up.

&nbsp;

You need to follow these steps:

&#49;) activate naming conventions Technical-to-Business

&#50;) run the reverse-engineering operation.&nbsp; You are prompted with a dialog, and must choose to Technical names\
![Reverse-engineering technical names](<lib/Reverse-engineering technical names.png>)\
&nbsp; For each modeling object (container, entity, attribute, etc.), the system:

* &nbsp;
  * creates the technical name as parsed from the source.
  * generates the business name using your technical-to-business naming convention rules.
  * activates Technical-to-Business coupling so that both names remain aligned until you decide otherwise.

&#51;) decouple modeling by going to Tools \> Options \> Naming Conventions

* &nbsp;
  * disable coupling
  * apply to all coupled objects (do NOT clear technical names)

&#52;) re-activate Business-to-Technical coupling by going to Tools \> Options \> Naming Conventions

* &nbsp;
  * enable coupling Business-to-Technical
  * apply to the entire model

&nbsp;

