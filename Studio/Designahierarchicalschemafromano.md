# Design a hierarchical schema from a normalized Polyglot model

When most of the physical targets are hierarchical, it is advised to denormalize a Polyglot prior to deriving into physical target models.&nbsp; In some cases, it makes more sense to keep the Polyglot model normalized.&nbsp; In yet other cases, you may want to have both normalized and denormalized structures in the Polyglot model.

&nbsp;

In this article we cover the case when it is preferable to keep a highly normalized Polyglot model.&nbsp; Then instead of deriving from the Polyglot model into the physical model, this example goes over using external references.

&nbsp;

If the only physical target is an OpenAPI definition on top of a relational database, fully denormalizing the Polyglot model is usually unnecessary.&nbsp; The Polyglot model can remain strictly normalized, and the hierarchical shape of the API response can be built in the OpenAPI model itself, by reusing the normalized structure via external references.

&nbsp;

This page shows how to do that with the current features of Hackolade Studio, without relying on Polyglot model derivation.

&nbsp;

Note: you can create external references from OpenAPI components either to a Polyglot Model or directly to a physical model.&nbsp; The principles below apply in both cases.

&nbsp;

***Order management illustration***

We use a simple order management model, fully normalized in a Polyglot Model:

&nbsp;

![Normalized Polyglot model order management](<lib/Normalized Polyglot model order management.png>)

&nbsp;

&nbsp;

The API we want to design exposes:

GET /orders/{orderId}

The response shape should be hierarchical, not relational:

Order\
&nbsp;├─ orderId\
&nbsp;├─ date\
&nbsp;├─ status\
&nbsp;├─ customer        &nbsp; ← embedded customer object\
&nbsp;   &nbsp; ├─ customerIdentifier\
&nbsp;   &nbsp; ├─ lastName\
&nbsp;   &nbsp; ├─ firstName\
&nbsp;   &nbsp; └─ email\
&nbsp;└─ orderLines\[\]    &nbsp; ← array of order lines\
&nbsp;   &nbsp; ├─ quantity\
&nbsp;   &nbsp; ├─ soldUnitPrice\
&nbsp;   &nbsp; ├─ productId\
&nbsp;   &nbsp; └─ productName

The key point: we want this hierarchical OpenAPI schema while keeping the Polyglot Model normalized and unchanged.

&nbsp;

## Referencing entities vs referencing attributes

External references in Hackolade let you reuse the structure of an existing model:

* when you reuse an entity or attribute via external reference, its internal structure is immutable in the referring model: you cannot add or remove attribute inside that referenced object.
* if you need to add, remove, or simplify attributes, you must reference individual attributes, not the whole entity.

&nbsp;

This leads to the following rule of thumb:

* Use an entity-level external reference when you reuse the entity as-is.
* Use attribute-level external references when you want to:

  * omit some attributes,
  * add new attributes.

&nbsp;

The rest of this page applies this rule to our Order example.

&nbsp;

&nbsp;

## Example: design GET order API

### Create the response schema: Order component

In the OpenAPI model, create a component schema representing the API response, for example Order.

* Go to the "Components" lower tab
* Add a component "Order" of type "Object" under "schemas"

![Normalized Polyglot create API response schema](<lib/Normalized Polyglot create API response schem.png>)​

&nbsp;

​

We want to reuse some attributes from the normalized Order entity, omit the foreign key Customer identifier, add a nested customer object and an orderLines array.

&nbsp;

Because we are not reusing the Order entity as-is, we cannot reference the whole entity. Instead, we will reference only the fields we need.

* Via the contextual menu on the Order component, choose Add attribute \> Reference \> External...

​

![Normalized Polyglot API response external ref](<lib/Normalized Polyglot API response external ref.png>)

​

* Locate the model where the references are present.
* You can multi-select several attributes in the Polyglot Model to create multiple external references in one operation. In our example, we select:

  * &#51; Order attributes (identifier, date and status) but not the Customer identifier, because the customer will be represented as a nested object.
  * the customer entity that we want to resuse as-is (identifier, last name, first name, email), so an entity-level reference is appropriate.

​

![Normalized Polyglot external ref select attri](<lib/Normalized Polyglot external ref select attri.png>)

​

Result so far in the API schema:

​

![Normalized Polyglot external ref API schema](<lib/Normalized Polyglot external ref API schema.png>)

​

Next, we add the list of order lines to the Order schema.

* Add an orderLines attribute of type "array", which contains items of type "object"

​

![Normalized Polyglot external ref order lines](<lib/Normalized Polyglot external ref order lines.png>)

​

Inside each object in the orderLines array, we want to reuse quantity and sold unit price from the Order line entity, and the identifier and name from the Product entity.&nbsp; Again, because we are modifying the structure compared to the normalized entity, we cannot reference the whole Order line entity or the whole Product entity.&nbsp;

&nbsp;

Instead, we will reference only the attributes we need, similarly to what we did for Order:

* Via the contextual menu on the array item object, choose Add attribute \> Reference \> External...
* Locate the model where the references are present.
* You can multi-select several attributes in the Polyglot Model to create multiple external references in one operation. In our example, we select:

​

![Normalized Polyglot ext ref order lines attri](<lib/Normalized Polyglot ext ref order lines attri.png>)

​

Resulting Order schema:

​

![Normalized Polyglot ext ref order lines schema](<lib/Normalized Polyglot ext ref order lines schem.png>)

​

The above illustrates a second reason to use field-level references: controlling the level of detail exposed by a given API.

&nbsp;

### Use Order component in response

In the API model:

* create your resource, request and response

​

![Normalized Polyglot order component response](<lib/Normalized Polyglot order component response.png>)

​

* make the schema referencing the Order component

​

![Normalized Polyglot order comp create ext ref](<lib/Normalized Polyglot order comp create ext ref.png>)

​

As a result, a hierarchical OpenAPI response on top of a normalized Polyglot (or physical) model without denormalizing the source model.

&nbsp;

![Normalized Polyglot OpenAPI denormaliz schema](<lib/Normalized Polyglot OpenAPI denormaliz schema.png>)​

&nbsp;

​

## Summary of patterns and recommendations

The main patterns are:

1. Keep the Polyglot Model normalized
- &nbsp;

  - do not denormalize entities just because the API response is hierarchical.
  - let the OpenAPI model express the hierarchy.

2. Use external references wherever possible
- &nbsp;

  - they ensure the API schemas stay aligned with the underlying model.
  - changes in the Polyglot or physical model can be propagated to the API with minimal effort.

3. Choose the right granularity for external references
- &nbsp;

  - entity-level reference: Use when the API should expose an entity as-is, with all its attributes and structure unchanged
  - attribute-level reference: Use when the API needs:

    - to add nested objects (e.g. embedding customer and orderLines into Order),
    - to hide some attributes (e.g. omitting Product Description),
    - to compose a new view that mixes attributes from different entities (eg. mixing Order line and Product attributes inside one single array item)

4. Remember that referenced objects are immutable
- &nbsp;

  - once you reference an entity or attribute externally, you cannot change its internal structure in the OpenAPI model.
  - to customize the structure, always drop down to referencing individual attributes.

&nbsp;

&nbsp;

