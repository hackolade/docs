# Logical to Physical with Polyglot Relationships

Polyglot relationships are [defined at a conceptual and logical level](<ConceptualtoLogicalwithPolyglotr.md>), independently of any physical technology.&nbsp; When you derive a physical model from a Polyglot model, each relationship is translated into a construct supported by that target.

&nbsp;

During derivation, relationships are translated in the most appropriate way for each target, based on:

* what the target supports,
* and what you expressed in the Polyglot model.

&nbsp;

## Targets with Foreign Key / Foreign Master

This includes relational databases, NoSQL databases with the exclusion of graph database (see below), and all targets that support relationships, even if not enforced:

* relationships already defined as Foreign Key / Foreign Master are derived as-is.
* many-to-many relationships without relationship attributes may result in an associative table for relational targets (configurable, enabled by default).
* relationships that carry attributes are not directly supported by these targets. They are converted into a Foreign Key-based relationship, without Foreign Key constraint defined.

&nbsp;

**Note:** materializing relationships carrying attributes as associative tables containing these attributes is planned but not supported yet.

&nbsp;

## Targets with Edges (graph databases)

For graph-only targets, all relationships become edges.

* all Polyglot relationships are derived as edges, regardless of how they were modeled.
* linked entities become source and target nodes.
* direction follows the graph convention (out-node → in-node), using the order of linked entities.

&nbsp;

## Polyglot to Polyglot

When deriving a Polyglot model into another Polyglot model, nothing changes.

&nbsp;

All relationships are preserved as-is, including their structure, their properties, and their modeling intent.

&nbsp;

## Not derived information

Some relationship properties are conceptual or logical only and are not propagated to physical models, regardless of the target:

* verbs,
* roles,
* constraint type (identifying vs non-identifying).

&nbsp;

These properties enrich understanding in Polyglot but do not currently map to physical constructs.

&nbsp;

