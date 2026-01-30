# Choosing a naming strategy

In general, if a Polyglot model has no technical names, and you have Naming Conventions enabled, special attention is required (on the front of technical names) when deriving a target model from a Polyglot model:

&nbsp;

![Naming Conventions derived technical names](<lib/Naming Conventions derived technical names.png>)

&nbsp;

&nbsp;

&nbsp;

One particular scenario requires special attention: when technical names are defined in the Polyglot source model, and at the same time naming conventions are enabled in the target model.

&nbsp;

This situation creates a potential conflict, as two naming strategies are now competing for control over the technical name in the target model:

* technical names coming from the source (parent) Polyglot model, and
* technical names generated from the business name, according to the target’s active naming conventions

&nbsp;

Hackolade Studio prompts the user to choose which source should be considered authoritative.

&nbsp;

**Important note:**&nbsp; while in many cases, the derive operation is into a physical technology target, it is also possible to derive into another Polyglot model.&nbsp; The generic term "derived" used in the examples below can be either a physical model or another polyglot model.&nbsp; In the latter case, of course the Naming Conventions are the same for both the parent Polyglot model and the derived Polyglot model.&nbsp; The response below remain important however, as it determines the name coupling in the derived model.

&nbsp;

## State your choice during the derive operation

At the moment of derivation, if naming conventions are enabled in the target model, the user must choose between two options.

&nbsp;

![Polyglot naming conventions choice dialog](<lib/Polyglot naming conventions choice dialog.png>)

&nbsp;

### Option 1: Apply the naming conventions of the derived target

When Naming Conventions have been enabled in Tools \> Options for the target of the model.

&nbsp;

In this option, the technical names in the derived model are generated based on the source Polyglot business names, then derived using the active naming convention.&nbsp; Meaning that technical names, if any, in the parent Polyglot model are ignored during derivation.

&nbsp;

This is suitable if your organization prefers to centralize naming rules per target technology, and doesn’t want to use the Polyglot technical names, if any. &nbsp;

&nbsp;

You may have technical names in a parent Polyglot model, whether uncoupled from the business names...&nbsp;

![Polyglot technical names uncoupled](<lib/Polyglot technical names uncoupled.png>)

&nbsp;

&nbsp;

or coupled with naming conventions rules. &nbsp;

&nbsp;

![Polyglot technical names coupled](<lib/Polyglot technical names coupled.png>)

&nbsp;

In either case, the target technical names are coupled to the business name derived from Polyglot.

&nbsp;

### Option 2: Keep the Polyglot parent's technical names

When Naming Conventions have been enabled in Tools \> Options for the target of the model.&nbsp; But with this choice, you prefer to keep the technical names defined in the Polyglot and have them derived into the target.&nbsp; Meaning that the naming conventions of the target are not applied for these objects.

&nbsp;

This option is appropriate when technical names have been carefully defined in Polyglot and should be reused across multiple target technologies, whether uncoupled from the business names.

&nbsp;

![Keep Polyglot technical names uncoupled](<lib/Keep Polyglot technical names uncoupled.png>)

&nbsp;

&nbsp;

or coupled with naming conventions rules. &nbsp;

&nbsp;

![Keep Polyglot technical names coupled](<lib/Keep Polyglot technical names coupled.png>)

In either case, the target technical names are derived from the Polyglot technical names.

&nbsp;

## Important considerations

This choice is applied to all modeling objects that are derived from the parent Polyglot model used in this derive operation.&nbsp; A different choice can be made when deriving from another Polyglot model.&nbsp; Additionally, the same Polyglot model can be derived into distinct derived models, each with its own choice.

&nbsp;

This choice is currently irreversible: to change it, you would need to derive again from into a new target model.

&nbsp;

## Why this question when no technical names are defined in the Polyglot?

The dialog appears even if the Polyglot model currently has no technical names, for an important reason: Hackolade Studio must anticipate the possibility that technical names may be added to the Polyglot model at a later time.

&nbsp;

Since each derivation establishes a fixed relationship between a Polyglot model and its derived model(s), it is crucial to decide upfront which source should govern technical names:

* either the Polyglot model, if technical names will be maintained centrally,
* or the target model, via naming conventions.

&nbsp;

This choice is made once per derivation, and will apply to all current and future derived objects for that Polyglot-to-target pair -- ensuring consistency over time, even if technical names are introduced later.

