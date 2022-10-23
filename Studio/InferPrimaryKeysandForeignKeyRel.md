# Infer Primary Keys and Foreign Key Relationships

With v6.3.0, a new feature was introduced for RDBMS and related targets.&nbsp; There can be several reasons why you don't originally have Primary Keys and/or Foreign Keys in your model:

\- you have a data model loaded from a source that did not provide them;&nbsp;

\- you reverse-engineered from a Big Data Analytics platform that don't support these constraints;

\- you decided not to enforce PK and/or FK constraints for performance reasons

&nbsp;

We provide this feature in the Tools menu so you can invoke it at any time.&nbsp; It generates candidate PKs and PKs to be added to your model. The algorithm works on the metadata of the entities and attributes without looking at the actual data. &nbsp;

&nbsp;

The feature is based on the published paper [Foreign Key Constraint Identification in Relational Databases](<Foreign%20Key%20Constraint%20Identification%20in%20Relational%20Databases> "target=\"\_blank\"") by Jan Motl and Pavel Kordík.&nbsp; The approach is fast and scalable, it is target agnostic, and it is not affected by data quality.

&nbsp;

## Methodology

The identification of PKs is a relatively easy task, and it further helps identify FKs, since FK constraints typically reference PKs. In both PK and FK identification stages, a probability that an attribute is part of a constraint is predicted, then the probability is passed to an optimizer to deliver a binary prediction.

&nbsp;

### Primary keys

Primary keys are identified by:

1. attribute ordinal position in the table (PKs are commonly at the beginning)
1. data type (e.g. integers or char are preferred over doubles or text)
1. presence of a keyword like "id" in the attribute name
1. similarity of the attribute name with the entity name, using Jaro-Winkler string distance
1. nullability of the attribute (Not null attributes are more likely to be a PK)
1. attribute width in bytes (PKs are commonly short)

&nbsp;

Once these features are collected, they are passed to logistic regression to estimate the probability that the attribute is in a primary key.&nbsp; Since each entity can have at most a single PK (or a composite PK), the attribute with the highest probability in the entity is declared to be the primary key of the entity.

&nbsp;

Since each entity should contain a PK, a single most likely PK is identified for each entity in the model.&nbsp; If the single most likely PK attribute in an entity is a doppelgänger, then all its doppelgängers in the entity are declared to be part of the PK as well, creating a composite key.

&nbsp;

### Foreign key relationships

Foreign keys are identified by:

1. known PKs (FK should reference a PK)
1. data types (FK should reference a PK of a compatible data type)
1. data type properties (e.g. data type sizes should agree)
1. similarity of the FK name with the PK name (should be high)
1. similarity of the FK name with the PK entity name (should be high)
1. similarity of the FK name with the FK entity name (should be low)
1. attribute width of the FK should be similar to the PK width
1. minimum and maximum values of the FK is in the range of the PK
1. minimum and maximum values of the FK cover a significant range of the PK values

&nbsp;

Once again, probabilities are estimated with logistic regression. And the most likely FK constraints are returned (a compound FK is returned if the PK is compound).

The FK optimization is formulated as an integer linear optimization problem on a directed graph.&nbsp; A unity constraint enforces that a FK can reference only a single PK.&nbsp; A completeness constraint ensures that compound FKs are syntactically correct.&nbsp; A doppelgänger constraint says that if attributes are doppelgängers to each other, then either all or neither attribute from the doppelgänger set reference the (same) PK attribute.

&nbsp;

## Limitations

This function is provided on a "best effort" basis.&nbsp; The success of the operation depends on many factors, including the relevance of entity and attribute names, their consistency, the accuracy of data types, etc.&nbsp; There are currently specific areas where the functions is known to have some limitations:

&nbsp;

### Composite primary keys

The identification of composite PKs should work just fine, as long as attributes are [dopplegängers](<https://en.wikipedia.org/wiki/Doppelgänger> "target=\"\_blank\""), i.e. their names are similar within the same entity, for example atom\_id1 and atom\_id2. &nbsp;

&nbsp;

### Recursive foreign key relationships

Currently, the string distance between the attribute names is such that we cannot always reliably identify recursive FK relationships, i.e; when the parent and child entities are in fact the same entity and the foreign key refers back to the same entity.&nbsp; The presence of a prefix "Parent" helps to reveal, for example, a foreign key from child ParentOrganizationKey to the parent OrganizationKey.

&nbsp;

Otherwise, if you know that a recursive FK relationship exists in an entity, you may attempt to run the function on that entity without selecting any other entities for that run.

