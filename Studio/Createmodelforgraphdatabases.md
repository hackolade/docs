# Create model for graph databases

In the previous tutorial, we reviewed how to generate documentation and pictures for your data model.&nbsp; By the end of this tutorial, you will master the creation of data models for property graph databases.

&nbsp;

You may also [view this tutorial](<https://youtu.be/C0NoEbDMNm4> "target=\"\_blank\"") on YouTube.&nbsp; Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-11-create-a-model-for-graph-databases> "target=\"\_blank\"").

&nbsp;

**Note:** this tutorial is specific to property graph databases such as Neo4j, Cosmos DB with Gremlin API, JanusGraph, Neptune with Gremlin API, Tinkerpop, etc.

&nbsp;

Property graph databases are a special family of NoSQL databases, with a unique ability to reveal relationships in data that users did not necessarily knew existed.&nbsp; This is as opposed to so-called "relational" databases, which merely enforce referential integrity for foreign keys representing pre-defined relationships between normalized entities.

&nbsp;

The sweet spot for graph databases covers use cases such as fraud detection, recommendation engines, friends of friends, etc.&nbsp; Terminology is also different than more traditional databases, where an entity is called a vertex (plural: vertices) or node, and a relationship is often called an edge.&nbsp; Not only vertices have attributes, but edges can have attributes as well.&nbsp; Finally, graph data is generally represented with circles and arcs between them.

&nbsp;

Still on terminology, an entity (of a data model) representing a node is called a "node label" or "vertex label", whereas the representation in a data model of edges is called an "edge label" or a "relationship type".

&nbsp;

Data modeling for graph databases must of course follow similar principles.&nbsp; This is why we introduced a special Graph Diagram in plugins for property graph database targets:

![Tutorial - Graph diagram](<lib/Tutorial%20-%20Graph%20diagram.png>)

&nbsp;

While the above is a much more user-friendly view of a graph data model, we nevertheless keep an Entity-Relationship view.&nbsp; Note that the ERD is adapted to accommodate attributes (aka properties) for relationships:

![Image](<lib/Tutorial%20-%20Graph%20ERD.png>)

&nbsp;

The creation of data model for graph databases using this ERD is similar to what was covered in previous tutorials. &nbsp;

&nbsp;

## Graph diagram

Let's see with an example how to create a data model for a property graph database.&nbsp; You first create a new model, having chosen a graph database such as Neo4j.&nbsp; You create a container for the database, then right-click in it and choose Add Node Label.

![Image](<lib/Tutorial%20Graph%20Add%20Node%20Label.png>)

&nbsp;

&nbsp;

A shape will be added to the diagram, to which you can assign a name, for example Person:

![Image](<lib/Graph%20node%20label.png>)

&nbsp;

The different controls appearing inside the circle when you hover over the shape are described in details in [this page](<Graphshapes.md>).

&nbsp;

You can follow the same process to create a second node label, or you can click on the control to add an edge label&nbsp; (top right control in the circle) then click elsewhere in the container, which will add both an additional node label, plus the edge label between the 2.&nbsp; After naming the different objects, you get something like this:

![Tutorial - Graph 2 nodes 1 edge](<lib/Tutorial%20-%20Graph%202%20nodes%201%20edge.png>)

&nbsp;

It is now time to create some properties to the node labels and edge label:

![Image](<lib/Tutorial%20-%20Graph%202%20nodes%201%20edge%20with%20attribut.png>)

&nbsp;

You should note a couple of toolbar buttons to control the layout:

\- the toggle of force-directed layout with its cursor to control the distance between node labels

\- the display options controlling the orientation of the edge label names, as well as whether attribute boxes should appear or not

![Tutorial - Graph display options](<lib/Tutorial%20-%20Graph%20display%20options.png>)

&nbsp;

Note also that you may pin individual node labels so as to anchor the force-directed layout.&nbsp; You can also display attribute boxes individually.

&nbsp;

Many more controls are described in [this page](<Graphshapes.md>) to help you with a powerful and flexible data modeling of your graph databases. &nbsp;

&nbsp;

The ability of the application to forward-engineer schemas depends on the capabilities of the target technology.&nbsp; For example JanusGraph is based on schema declaration.&nbsp; In the case of others, we do "forward-engineering by example" and apply data to the database instance.

&nbsp;

&nbsp;

In this tutorial, we reviewed how to create data models for property graph databases.&nbsp; In the next tutorial, we will cover how to create a model for REST APIs using Swagger or OpenAPI specification.

