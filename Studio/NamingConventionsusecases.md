# Naming Conventions use cases

In Hackolade Studio, every modeling object has two name fields: a mandatory Name and an optional Technical Name. This does not represent “business vs technical” by default — it simply means that if only the Name is defined, that value is used everywhere (in diagrams and in generated artifacts). A true separation only exists when a Technical Name is explicitly provided: the Name then plays the role of the business-friendly label, while the Technical Name is used for physical generation and implementation.

&nbsp;

When using [Naming Conventions](Namingconventions.md), which allows to automatically generate technical names from the business name, it is often useful to experiment at a small scale to understand the behavior and possibilities, prior to deploying at a larger scale.

&nbsp;

The enabling of Naming Conventions is not mandatory, and can be done for some targets and not others, if that's what you wish. It is performed in the menu Tools > Options > Naming Conventions for each target. There are 3 possible options for each target: disabled, Business-to-Technical, or Technical-to-Business.

&nbsp;

Typically there are no reasons to enable Technical-to-Business. The functionally makes most sense when enabled for Business-to-Technical. It does exist however for ad-hoc manipulations, as illustrated below.

&nbsp;

> [!NOTE]
> Even if Naming Conventions are disabled in Tools > Options, it is possible to couple names of any individual object, as described [here](<https://hackolade.com/help/Namingconventions.html#Properties%20Pane>). Similarly, even if Naming Conventions are enabled in Tools > Options, it is possible to decouple names of any individual object.

&nbsp;

When reading this page of use cases, it is assumed that you have reviewed the [documentation page](Namingconventions.md), and maybe even viewed the [video](<https://community.hackolade.com/slides/slide/naming-conventions-33> "target=\"_blank\"").

&nbsp;

For naming conventions to work best, it is strongly suggested to make the rules of business-to-technical and technical-to-business symmetrical. Some features are not. For example, the removal of vowels or specific characters during business-to-technical transformation cannot be reconstructed during technical-to-business transformation. It is preferable to leverage an abbreviations file.

&nbsp;

## Use Case # 1: apply Naming Conventions to an existing data model

Whenever you make a change to the Naming Conventions screen in Tools > Options, the application displays a dialog to apply the changes to model open at the time of the change. You may choose to apply the changes to only the names already coupled in the open model. Or to the entire modeL.

&nbsp;

![Naming Conventions - apply changes dialog](<lib/Naming Conventions - apply changes dialog.png>)

&nbsp;

> [!IMPORTANT]
> Only the model open at the time of the change is concerned by these changes. If you want to apply the naming conventions to other model, you must proceed as follows...

&nbsp;

1\) open the model for which you want the set Naming conventions to be applied\
2\) go to Tool > Options > Naming Conventions\
3\) scroll down to the bottom of the dialog and click the button "Apply options to current model"\
4\) choose whether you want the conventions to be applied only to the already coupled names, or to the entire model\
5\) click the Apply button.

&nbsp;

If for example your model had no coupling of names previously, and your naming conventions are now set for this target to coupling of Business-to-Technical names, then if you choose to apply to the entire model, then all the names of all the objects will have their technical names derived from their business names according to the set rules.

&nbsp;

You can see below in case # 3 why it may be very important to only apply rules to previously coupled names, instead of to the entire model.

&nbsp;

## Use Case # 2: clear all technical names in a data model

> [!WARNING]
> This function allows to clear data. Be careful to not lose any valuable data that you might have wanted to retain.

&nbsp;

When you disable the coupling in Tools > Options > Naming Conventions, the application displays, similarly to case # 1 above, a dialog. But in this case a checkbox allows, if checked, to clear the technical names.

&nbsp;

![Naming Conventions - apply changes with clear](<lib/Naming Conventions - apply changes with clear.png>)\
Again, it is possible to have this performed for only names previously coupled, or to the entire model.

&nbsp;

## Use Case # 3: handle evolution of abbreviations and/or transformation rules

This is a very real use case! Many companies have had databases in production for a long time, meaning that technical names are in place. Let's say that you now want to make naming conventions evolve, or to change some abbreviations, or simply to create naming conventions when none were in place before. It would be hard to impose a change of physical table names or column names. In this case, you want to keep existing technical names, but you want any future object to follow the (updated) naming conventions.

&nbsp;

Let's say that you have a model that was created with old naming conventions. You want to retain the physical/technical names as they are going forward, but you also want new objects to be created with the new rules or the abbreviations. You need to follow these steps:

&nbsp;

1\) decouple all the existing names

- go to Tools > Options > Naming Conventions
- disable name coupling by choosing No in the dropdown list "Enable name coupling"
- click Apply
- choose "To the entire model" -- DO NOT check the Clear checkbox
- Click Apply

&nbsp;

2\) re-enable Business-to-Technical name coupling with the new rules.\
3\) when presented with the dialog to apply the naming conventions configuration, click Cancel so no changes are applied. All future objects created in the model will be created with coupling, using the conventions rules.

&nbsp;

Make sure to perform this operation for each model of the same target to which the rules would apply.

&nbsp;

## Use case # 4: generate business names from technical names during reverse-engineering

Prior to reverse-engineering from your database instance or from DDLs, you would want to assemble an abbreviations file. Abbreviations files in Hackolade Studio work both directions: in Business-to-Technical coupling, by taking full words or expressions listed in the first column of the CSV, and abbreviating them according to what's in the second column of the CSV in the corresponding line. It also works during reverse-engineering, by parsing technical names separated by underscores or camelCases, finding the abbreviation in the second column, and translating into a business name using the first column of the CSV in the corresponding line. Even if your coupling is set to Business-to-Technical, the application knows to convert technical names to business names during reverse-engineering.

&nbsp;

When performing a reverse-engineering operation from a technical source (DDL, JSON, schema file, database instance, or any system-driven structure), the incoming names are naturally technical names. At this point, 2 situations are possible:

1. you want to keep a single name. The technical name should simply become your Name. In that case, the procedure below does not apply.
2. you want to distinguish business names from technical names. You want the incoming technical names to generate business-friendly names, while preserving (or later regenerating) clean technical names using naming conventions.

&nbsp;

This workflow is relevant when:

- you want clean business names that differ from the technical identifiers found in the source,
- you want to initialize a Polyglot model from a technical artifact and immediately separate business vs. technical terminology,
- or you simply want dual naming (business + technical) in any target model.

&nbsp;

This process applies equally to any target model — Polyglot or any technology-specific model. The workflow is identical regardless of where the reverse-engineered structure ends up.

&nbsp;

You need to follow these steps:\
1\) activate naming conventions Technical-to-Business\
2\) run the reverse-engineering operation. You are prompted with a dialog, and must choose to Technical names\
![Reverse-engineering technical names](<lib/Reverse-engineering technical names.png>)\
For each modeling object (container, entity, attribute, etc.), the system:

- creates the technical name as parsed from the source.
- generates the business name using your technical-to-business naming convention rules.
- activates Technical-to-Business coupling so that both names remain aligned until you decide otherwise.

&nbsp;

3\) decouple modeling by going to Tools > Options > Naming Conventions

- disable coupling
- apply to all coupled objects (do NOT clear technical names)

&nbsp;

4\) re-activate Business-to-Technical coupling by going to Tools > Options > Naming Conventions

- enable coupling Business-to-Technical
- apply to the entire model
