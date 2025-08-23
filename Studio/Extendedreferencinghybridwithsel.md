# Extended referencing hybrid with selective duplication

# Extended referencing: hybrid with selective duplication

In some scenarios, both entities involved in the relationship are considered important enough to exist independently, yet optimizing access patterns justifies duplicating certain attributes between them.

This approach follows the well-established **Extended Reference Pattern**, widely used in document modeling practices.

&nbsp;

## Repository of examples

The sample models used in the examples below can be found in [this repository](<https://github.com/hackolade/demo-models-read-only/tree/main/Pragmatic%20data%20modeling> "target=\"\_blank\"").&nbsp; They can be opened in the browser with the following links, provided proper license:

\- [1-Polyglot.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/1-Polyglot.hck.json\&b=main> "target=\"\_blank\"")

\- [4a-Extended referencing to normalization before modeler intervention-Oracle.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/4a-Extended%20referencing%20to%20normalization%20before%20modeler%20intervention-Oracle.hck.json\&b=main> "target=\"\_blank\"")

\- [4b-Extended referencing to normalization after modeler intervention-Oracle.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/4b-Extended%20referencing%20to%20normalization%20after%20modeler%20intervention-Oracle.hck.json\&b=main> "target=\"\_blank\"")

&nbsp;

Note also the naming convention applied to transform business names in the Polyglot model with Pascal case and spaces, into technical names int he physical models with lowercase and underscores)

&nbsp;

## **Example of customer and product reviews with duplicated attributes**

In this example:

* The Customer entity contains:

  * Core customer attributes
  * A Reviews array, where each review includes:

    * The Product identifier as a foreign key
    * The Product name duplicated for convenience
    * The Rating

* The Product entity contains:

  * Product details
  * A Reviews array, where each review includes:

    * The Rating
    * A nested Customer object containing:

      * The Customer identifier as a foreign key
      * The Pseudo duplicated for convenience

&nbsp;

This structure allows efficient access to relevant information from both sides:

* From the Customer document, you can see all written reviews with the product name directly accessible
* From the Product document, you can access reviews and key customer information without additional lookups

&nbsp;

The attributes chosen for duplication depend entirely on the business context and access patterns.

&nbsp;

![Pragmatic modeling - Polyglot Extended ref](<lib/Pragmatic modeling - Polyglot Extended ref.png>)

&nbsp;

&nbsp;

### **Foreign key vs. foreign master relationships**

In Hackolade Studio, the visual representation of relationships distinguishes between:

* **Foreign key relationships** (solid lines): These point directly to the primary key of another entity, representing classic foreign key behavior.
* **Foreign master relationships** (dotted lines): These indicate attributes that are duplicated from another entity but do not correspond to the primary key. Typically, they represent stable, descriptive fields selectively copied to improve performance or support application needs.

&nbsp;

This visual distinction helps clarify which attributes are true relational keys, and which are duplicated for convenience within the extended reference pattern.

### Derivation with normalization

When deriving this Polyglot Logical Model to a relational physical model with normalization, the following structure is generated:

&nbsp;

![Pragmatic modeling - derive with normalization](<lib/Pragmatic modeling - derive with normalizatio.png>)

&nbsp;

* A customer table containing customer details
* A product table containing product details
* Two separate reviews tables:

  * One reflecting the Reviews array embedded in the Product entity
  * One reflecting the Reviews array embedded in the Customer entity

* A customer1 table containing customer attributes duplicated within the product context

&nbsp;

This behavior is expected given the structure of the Polyglot Logical Model and the selective duplication implemented using the extended reference pattern.

&nbsp;

However, after derivation, some adjustments are required by the data modeler to align the physical model with relational best practices:

* Keep only a single consolidated reviews table, acting as a true join table between product and customer.
* Remove the redundant reviews and customer1 tables generated during the derivation process.
* Ensure the final reviews table contains the necessary foreign keys.

&nbsp;

![Pragmatic modeling -derive with normaliiz adjusted](<lib/Pragmatic modeling -derive with normaliiz adj.png>)

&nbsp;

This step reflects the trade-off inherent to Polyglot Logical Modeling:

* The logical model prioritizes technology agnosticism and flexibility
* Minor adaptations are expected when translating to specific targets like relational databases

&nbsp;

The data modeler plays a key role in refining the derived physical model to ensure both structural integrity and optimal performance.

&nbsp;

## **Example of customer and order with duplicated attributes**

In this example:

* The Customer entity contains:

  * Core customer information
  * An array of orders, with selected order details (ordered date and status) duplicated directly inside the customer entity

* The Order entity exists independently, containing:

  * Full order details
  * Selected customer details (lastname and firstname) duplicated directly inside the order entity

&nbsp;

![Pragmatic modeling - duplicated attributes](<lib/Pragmatic modeling - duplicated attributes.png>)

&nbsp;

This structure ensures that frequently accessed or relevant attributes are immediately available within each entity, improving performance and simplifying common queries, while preserving the full source of truth within the related entity.

&nbsp;

The choice of which attributes to duplicate depends on the access patterns and business requirements.

\
Typically, duplicated attributes are stable or immutable, but this is not a strict rule.

&nbsp;

### Derivation with normalization

When deriving this structure to a relational physical model, the following is generated:

* A customer table containing core customer details
* An order table containing order details, including foreign keys to customer and duplicated customer attributes
* A customer1 table generated from the nested duplication within the Order entity
* An orders table generated from the nested array within the Customer entity

&nbsp;

![Pragmatic modeling - one-to-many normalization](<lib/Pragmatic modeling - one-to-many normalizatio.png>)

&nbsp;

This behavior is expected given the structure of the Polyglot Logical Model and the selective duplication implemented using the extended reference pattern.

&nbsp;

However, after derivation, some adjustments are required by the data modeler to align the physical model with relational best practices:

* Remove the redundant customer1 and orders tables
* Maintain a single normalized order table with foreign keys referencing customer

&nbsp;

![Pragmatic modeling - 1-to-many normal adjust](<lib/Pragmatic modeling - 1-to-many normal adjust.png>)

&nbsp;

This illustrates:

* The flexibility of Polyglot Logical Modeling for mixed paradigms
* The importance of the modeler's expertise in refining derived physical models
* The trade-offs involved when applying extended referencing in one-to-many scenarios

