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
* relationships that carry attributes are automatically materialized as an associative table. The associative structure contains the relationship attributes and two Foreign Key relationships toward the originally linked entities.&nbsp; Such transformation is mandatory for these targets: since Foreign Key-based platforms do not support attributes directly on relationships, generating an [associative entity](<https://en.wikipedia.org/wiki/Associative\_entity> "target=\"\_blank\"") (a.k.a junctions tables, join tables, bridge tables, link tables, intersection tables, mapping tables, crosswalk, or many-to-many resolver) is the only way to preserve the relationship attributes without information loss.

&nbsp;

## Targets with Edges (graph databases)

For graph-only targets, all relationships become edges.

* all Polyglot relationships are derived as edges, regardless of how they were modeled.
* linked entities become source and target nodes.
* direction follows the graph convention (out-node → in-node), using the order of linked entities.

&nbsp;

## Polyglot to Polyglot

When deriving a Polyglot model into another Polyglot model, relationships carrying attributes are, by default, materialized as associative entities.

This reflects the typical modeling progression from a conceptual structure toward a more explicit logical model.&nbsp; A relationship that carries attributes (for example, *Order-Product* with *quantity*) becomes an associative entity with two Foreign Key relationships to the originally linked entities.

An option during the derive operation allows you to disable this behavior.&nbsp; If the option is unchecked, relationships carrying attributes remain unchanged and are preserved as relationships with attributes in the derived Polyglot model.&nbsp; The option is enabled by default.

&nbsp;

## Not derived information

Some relationship properties are conceptual or logical only and are not propagated to physical models, regardless of the target:

* verbs,
* roles,
* constraint type (identifying vs non-identifying).

&nbsp;

These properties enrich understanding in Polyglot but do not currently map to physical constructs.

&nbsp;

