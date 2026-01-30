# Handling of technical names during Impact Analysis

The previous page detailed your choices when originally deriving a model from Polyglot.&nbsp; Then both the parent Polyglot and the derived models are likely to continue to evolve over time.&nbsp; This page outlines different cases and how they are handled when refreshing references, how they are handled in the Impact Analysis screen, and the resulting impact in the derived model.

&nbsp;

## Reminder

Let's ensure a common understanding of some of the terms used below:

* **enabling naming conventions:** this action takes place in Tools \> Options \> [Naming Conventions](<Namingconventions.md>) by selecting the value in the dropdown "Enable name coupling", typically with Business-to-Technical.&nbsp; This action is applied by technology target.&nbsp; It is applied to the currently open model, as well as to all other models opened going forward, for the selected target technology.&nbsp; It is generally applied to all objects in the model: container, entities, views, and attributes.
* **coupling individual business and technical names:** while enabling and disabling naming conventions is generally applied to the entire open model and for upcoming object additions, it is also possible to determine the coupling status of business and technical names for each individual object.&nbsp; As a result, it is possible that, while naming conventions are enabled for all future object creations, some other objects in the same model have their business and technical names decoupled.&nbsp; And vice-versa.&nbsp; See more details in [this page](<NamingConventionsusecases.md>).
* **deviation:** in a model derived from Polyglot, it is possible to deviate from the Polyglot model.&nbsp; For example, in a derived entity, you may want to delete some unneeded attributes, and/or add new attributes.&nbsp; Similarly, you may, for any object, change some (but not all) properties.&nbsp; The model file keeps track of these deviations so that, when refreshing references you don't lose the changes that you carefully made to the derived model.&nbsp; In the context of Naming Conventions in this page, you will see in Case 3 below that a deviation is automatically created when technical names exist in Polyglot, but in the derived model, the technical name is coupled with the business name of the derived model, thereby ignoring the technical name of the Polyglot model.&nbsp; If the coupling rules are the same, the result might be no different, but a deviation is created nonetheless.

&nbsp;

## Case 1: no technical names in Polyglot model

If you prefer to centralize naming rules per target technology, and don’t want to maintain technical names in Polyglot, then your Polyglot model does not define any technical names for its modeling objects (entities, attributes, etc.). Only business names are provided in Polyglot.&nbsp; Note that this case represents the situation that existed prior to v8.6.0 which introduced technical names in Polyglot.

&nbsp;

### What happens during impact analysis?

When the target model is derived, and changes are later made in the parent Polyglot model, the following actions occur during impact analysis:

* if the business name was modified in the parent Polyglot, then the business name in the target model is updated, as long as the business name had not been manually changed in the target (i.e., not deviated).
* if no naming convention is active in the target of the derived model, then the technical name remains unchanged .

&nbsp;

![No technical names in polyglot model](<lib/No technical names in polyglot model.png>)

&nbsp;

* if naming conventions are applied in the target of the derived model, then the technical name is recalculated, based on the updated business name in the parent Polyglot model..

&nbsp;

![Coupling no technical names in polyglot model](<lib/Coupling no technical names in polyglot model.png>)

&nbsp;

&nbsp;

## Case 2: technical names are defined in Polyglot and derived into target

In this scenario, the technical names have been carefully defined in the Polyglot model, to be reused across multiple target technologies. During derivation, the user initially chose to preserve those Polyglot names in the derived model.

&nbsp;

Technical names in the parent Polyglot model may exist but are uncoupled from the business names:

&nbsp;

![Technical names in Polyglot and derived](<lib/Technical names in Polyglot and derived.png>)

&nbsp;

or they may result from business-to-technical name coupling:

![Coupling Technical names in Polyglot and derived](<lib/Coupling Technical names in Polyglot and deri.png>)

&nbsp;

### What happens during impact analysis?

When changes are made in the Polyglot model, the following behavior applies during [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis> "target=\"\_blank\"") when updating references:

* the business name in the derived model is updated to reflect any changes made in the Polyglot model — unless that business name had been manually changed (deviated) in the derived model.
* the technical name in the derived model is also updated based on the Polyglot value — again, only if that technical name had not been manually changed in the derived model..

&nbsp;

Technical names in the parent Polyglot model may exist but are uncoupled from the business names:

&nbsp;

![Impact Technical in Polyglot and derived](<lib/Impact Technical in Polyglot and derived.png>)

&nbsp;

&nbsp;

or they may result from business-to-technical name coupling:

&nbsp;

![Impact coupling Technical name in Polyglot and derived](<lib/Impact coupling Tech in Polyglot and derived.png>)

&nbsp;

&nbsp;

In other words, both names (business and technical) remain derived from the parent Polyglot model and are not coupled to each other in the derived model, as long as no deviation occurs.

&nbsp;

This approach is ideal when you want to manage naming at the Polyglot level and ensure consistency across multiple derived models.

&nbsp;

**Note:** whether technical names in the Polyglot were entered manually or generated via name coupling, there is no impact on behavior in this case. From the perspective of the derived model, what matters is the presence (or absence) of technical names in the Polyglot - not how they were obtained.

&nbsp;

This distinction may be useful to advanced users wondering whether Polyglot-side naming conventions influence downstream synchronization behavior: they do not.

&nbsp;

## Case 3: technical names exist in Polyglot, but target applies its own naming conventions

In this scenario, the Polyglot model contains technical names. However, during derivation, you explicitly chose not to reuse those values, and instead opted to apply the naming conventions specific to the target model.

&nbsp;

![Polyglot naming conventions choice dialog](<lib/Polyglot naming conventions choice dialog.png>)

&nbsp;

This scenario is useful when technical names exist in Polyglot for reuse in most target models, but a specific target has technology‑ or organization‑specific naming rules that take precedence (e.g., enforced DB naming policy in one environment).

&nbsp;

### Deviations in impact analysis

As technical names were defined in the Polyglot and the choice by the user lead to ignoring them in favor of the naming conventions of the target, a deviation is created for each object. This means that the target’s technical names no longer reflect the values from the Polyglot.&nbsp; In the [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis> "target=\"\_blank\"") when updating references, these deviations appear in turquoise, just like any other property where the target value has been intentionally modified or overridden.

&nbsp;

As with any deviated property in a derived object, this property is no longer synchronized with the Polyglot.&nbsp; Any future change to the technical name in the Polyglot is ignored, across all subsequent impact analysis operations. In other words, this technical name is now fully managed by the target model and behaves as if it were independent from the Polyglot source.

&nbsp;

Technical names in the parent Polyglot model may exist but are uncoupled from the business names:

&nbsp;

![Technical names in Polyglot with target naming conventions](<lib/Tech in Polyglot with target conventions.png>)

&nbsp;

or they may result from business-to-technical name coupling:

&nbsp;

![Coupling technical names in Polyglot with target naming conventions](<lib/Coupling tech in Polyglot with target conv.png>)

&nbsp;

### What happens during impact analysis?

When changes are later made in the Polyglot model, the following rules apply during [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis> "target=\"\_blank\"") when updating references:

* business name in the target is updated based on changes made in the Polyglot, as long as the business name has not been manually modified (deviated) in the target.
* technical name in the target is not updated from Polyglot, since the user chose to ignore Polyglot technical names for this derivation.
* instead, the technical name continues to be calculated by the target’s naming conventions rules for coupling, based on the business name update (if coupling is active), or remains unchanged if there is no coupling.
* a deviation indicator is shown for the technical name during impact analysis, because the target value differs from the Polyglot value (which exists, but was deliberately ignored).

&nbsp;

Technical names in the parent Polyglot model may exist but are uncoupled from the business names:

&nbsp;

![Impact technical names in Polyglot with target naming conventions](<lib/Impact tech in Polyglot with target conv.png>)

&nbsp;

or they may result from business-to-technical name coupling:

![Impact coupling technical names in Polyglot with target naming conventions](<lib/Impact coupling tech in Polyglot with target.png>)

&nbsp;

&nbsp;

**Note:** whether technical names in the Polyglot were entered manually or generated via name coupling, there is no impact on behavior in this case. From the perspective of the derived model, what matters is the presence (or absence) of technical names in the Polyglot - not how they were obtained.

&nbsp;

This distinction may be useful to advanced users wondering whether Polyglot-side naming conventions influence downstream synchronization behavior: they do not.

&nbsp;

