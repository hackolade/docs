# GraphQL

[GraphQL](<http://www.graphql.org/>) is a query language for APIs and a runtime for fulfilling those queries with existing data..&nbsp; It is an API standard that provides a more efficient, powerful and flexible alternative to REST. GraphQL was developed and [open-sourced by Facebook](<https://legacy.reactjs.org/blog/2015/02/20/introducing-relay-and-graphql.html>) in 2015 and is now maintained by a large community of companies and individuals from all over the world.

&nbsp;

At its core, GraphQL enables *declarative data fetching* where a client can specify exactly what data it needs from an API. Instead of multiple endpoints that return fixed data structures, a GraphQL server only exposes a single endpoint and responds with precisely the data a client asked for.&nbsp; Another advantage lies in the fact that you can evolve your APIs without versioning, because you can add newer fields and types, or deprecate aging fields without impacting existing queries.

&nbsp;

[GraphQL](<https://github.com/graphql/graphql-spec> "target=\"\_blank\"") provides a concise way to define a [GraphQL schema](<https://www.prisma.io/blog/graphql-server-basics-the-schema-ac5e2950214e> "target=\"\_blank\"") with a well-structured syntax that is officially part of the GraphQL specification.&nbsp; It uses its own language for defining schemas, known as the [GraphQL Schema Definition Language (SDL)](<https://www.prisma.io/blog/graphql-sdl-schema-definition-language-6755bcb9ce51> "target=\"\_blank\""). SDL is both intuitive and easy to use while remaining highly powerful and expressive. Schema definitions are sometimes also called IDL (Interface Definition Language) or SDL (Schema Definition Language).

&nbsp;

To perform model-first design of a GraphQL API with Hackolade Studio, you must first download the GraphQL [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; This plugin is strictly compliant with the GraphQL specification. &nbsp;

&nbsp;

Creating APIs is not easy\! And creating a GraphQL SDL (Schema Designing Language) in a design-first approach can be tedious at best, and often error-prone and frustrating...&nbsp; Hackolade takes a **graphical** and **schema-centric** approach so you can focus on the content of queries and responses. The application also assists with all the metadata to produce validated GraphQL SDL files.&nbsp; You can also reverse-engineer existing GraphQL SDL to produce a graphical representation of your APIs.

A notable differentiator versus all the existing tools in the GraphQL ecosystem is the Hackolade patent-pending nested representation in an entity-relationships diagram of relatinships between types.&nbsp; Our drastically different visualization approach is anchored in the fact that both queries and responses are done using JSON with nested objects, regardless of whether the data source is relational or not.&nbsp; All current tools representing GraphQL schemas stick to a flat and relational visualization, for example

![GraphQL existing tools visualization](<lib/GraphQL existing tools visualization.png>)

While this visualization may be structured with some corrrelation to the SDL syntax and the relational structures. &nbsp; But there are several issues with his visualization:

\- it seems acceptable for super simple models, but it quickly become hard to read with larger models.&nbsp; In other words, it does not scale.

\- it is hard for users to relate the payload being exchanged in the API to the schema SDL

\- if the source is NoSQL, the denormalized data source is normalized to fit the SDL syntax

Instead, Hackolade Studio shows the above model in this way, where one single entity box represents the structure of a single end point:

![GraphQL Hackolade Studio nested visualization](<lib/GraphQL Hackolade Studio nested visualization.png>)

It is easy to see how a diagram becomes naturally more scalable and user-friendly to read and interpret.

&nbsp;

Hackolade Studio was specially adapted to support the API design for GraphQL, including all the necessary metadata for the API, the type definitions, as well as the root types with their arguments for queries, mutations, and subscriptions.&nbsp; The application closely follows the terminology of the specification.&nbsp; The graphical tool puts the focus on what really matters in an API: the schema of the information being exchanged between systems.&nbsp; At the same time, it provides assistance to modelers and does not require mastery of the GraphQL SDL syntax.&nbsp; It generates validated SDL files that are syntactically correct and compatible with the specification thereby greatly improving productivity, consistency, and quality. &nbsp;

&nbsp;

The diagram below shows the structure of a [StarWars schema](<https://github.com/graphql/graphql-spec?tab=readme-ov-file#type-system> "target=\"\_blank\"") used to illustrate the [GraphQL specification](<https://github.com/graphql/graphql-spec?tab=readme-ov-file#graphql> "target=\"\_blank\""):

![GraphQL workspace](<lib/GraphQL workspace.png>)

&nbsp;

&nbsp;

and the resulting SDL, syntactically correct and automatically generated by the tool:

![GraphQL SDL generation](<lib/GraphQL SDL generation.png>)

&nbsp;

## GraphQL SDL specification summary

Every GraphQL server has two core parts that determine how it works: a **schema** and **resolve functions**.

&nbsp;

The schema serves as a blueprint for the data that can be retrieved through the GraphQL server. It specifies the queries that clients are allowed to make, the types of data available, and the relationships between those types.

While the schema defines query permissions and type relationships, it does not include the source of the data for each type. This responsibility falls on server resolve functions. Since resolve functions go beyond the scope of a data modeling tool, we won’t cover them here.

Here are some principles of a GraphQL schema:

&nbsp;

**&#49;. Types:** the schema specifies the different types of data that can be requested.

**&#50;. Fields:** each type includes a set of fields that define the specific pieces of data available. These fields can be various data types, such as strings, integers, or other complex objects.

**&#51;. Arguments:** fields can take arguments, allowing for more precise data retrieval. For example, an orderBy argument can determine the sorting order of returned posts.

**&#52;. Queries:** the schema establishes the entry points for fetching data through queries, which are used to retrieve information from a GraphQL server.

**&#53;. Mutations:** it also defines mutations, which are operations that modify data on the server, such as creating, updating, or deleting records.

**&#54;. Resolvers:** the schema includes resolver functions responsible for fetching data for each field. When a GraphQL query runs, the corresponding resolver is triggered to retrieve the required information.

&nbsp;

The syntax for writing schemas is called [Schema Definition Language](<https://www.prisma.io/blog/graphql-sdl-schema-definition-language-6755bcb9ce51> "target=\"\_blank\"") (SDL).&nbsp; Here is an example of how we can use the SDL to define a simple type called Person:

> type Person {\
&nbsp; &nbsp; name: String\!\
&nbsp; &nbsp; age: Int\!\
}

&nbsp;

This type has two *fields*, they’re called name and age and are respectively of type String and Int. The exclamation mark ("\!")following the type means that this field is *required*.

&nbsp;

It’s also possible to express relationships between types. In the example of a *blogging* application, a Person could be associated with a Post:

> type Post {\
&nbsp; &nbsp; title: String\!\
&nbsp; &nbsp; author: Person\!\
}

&nbsp;

Conversely, the other end of the relationship needs to be placed on the Person type

> type Person {\
&nbsp; &nbsp; name: String\!\
&nbsp; &nbsp; age: Int\!\
&nbsp; &nbsp; posts: \[Post\!\]\!\
}

&nbsp;

Note that there is a *one-to-many*-relationship between Person and Post since the posts field on Person is actually an *array* (or *list*) of posts, represented by square brackets ("\[...\]")

&nbsp;

### Operations

The Query type in a GraphQL schema is similar to the "operations" (i.e., requests) defined in an OpenAPI (formerly known as Swagger) specification.&nbsp; They are entry points for queries, mutations, and subscriptions.

&nbsp;

In an OpenAPI specification, an "operation" represents a request that can be made to a server, along with the parameters and response that are expected for the request. An operation is typically defined as a combination of a HTTP method (e.g., GET, POST, PUT, etc.) and a path (e.g., "/users").

&nbsp;

In a GraphQL schema, the Query type serves a similar purpose, but it is defined in a more flexible and expressive way. Instead of using HTTP methods and paths to define operations, a GraphQL schema uses fields and arguments to define the data that can be queried.

&nbsp;

### Fetching data with queries

When working with REST APIs, data is loaded from specific endpoints. Each endpoint has a clearly defined structure of the information that it returns. This means that the data requirements of a client are effectively *encoded* in the URL that it connects to.

&nbsp;

The approach taken in GraphQL is radically different. Instead of having multiple endpoints that return fixed data structures, GraphQL APIs typically only expose *a single endpoint*. This works because the structure of the data that’s returned is not fixed. Instead, it’s completely flexible and lets the client decide what data is actually needed.

&nbsp;

That means that the client needs to send more *information* to the server to express its data needs - this information is called a *query*.

&nbsp;

One of the major advantages of GraphQL is that it allows for naturally querying *nested* information. For example, if you wanted to load all the posts that a Person has written, you could simply follow the structure of your types to request this information:

> {\
&nbsp; &nbsp; allPersons {\
&nbsp; &nbsp; &nbsp; &nbsp; name\
&nbsp; &nbsp; &nbsp; &nbsp; age\
&nbsp; &nbsp; &nbsp; &nbsp; posts {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; title\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }\
}

&nbsp;

**GraphQL** allows a client to specify exactly what data it needs from the API.&nbsp; In the example above, a user can adapt the query to only return the relevant information.&nbsp; If the field age in the example above is not relevan tfor this query, then the query could be adjusted so that the field age is not included in the response:

> {\
&nbsp; &nbsp; allPersons {\
&nbsp; &nbsp; &nbsp; &nbsp; name\
&nbsp; &nbsp; &nbsp; &nbsp; posts {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; title\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }\
}

##### **Queries with Arguments**

In GraphQL, each *field* can have zero or more arguments if that’s specified in the *schema*. For example, the allPersons field could have a last parameter to only return up to a specific number of persons. Here’s what a corresponding query would look like:

> {\
&nbsp; &nbsp; allPersons(last: 2) {\
&nbsp; &nbsp; &nbsp; &nbsp; name\
&nbsp; &nbsp; }\
}

&nbsp;

The allPersons field in this query is called the *root field* of the query. Everything that follows the root field, is called the *payload* of the query.

&nbsp;

Here are some examples of common arguments that are used in a "Query" type:

&nbsp;

* id: A unique identifier for a specific object.
* limit: The maximum number of results to return.
* offset: The number of results to skip before returning results.
* sort: The field or fields to sort the results by.
* order: The order in which to sort the results (e.g. ascending or descending).
* filter: A set of conditions to filter the results by.
* find: Used to search for specific data based on specific criteria, typically a user input.

&nbsp;

There can be others like: where, distinct\_on, order\_by, etc.

> mutation {\
&nbsp; &nbsp; createPerson(name: "Bob", age: 36) {\
&nbsp; &nbsp; &nbsp; &nbsp; name\
&nbsp; &nbsp; &nbsp; &nbsp; age\
&nbsp; &nbsp; }\
}

&nbsp;

Notice that the mutation also has a *root field* - in this case it’s called createPerson.

&nbsp;

It is possible to also query information when sending mutations, which can be a very powerful tool to retrieve new information from the server in a single roundtrip\!

&nbsp;

### Realtime Updates with Subscriptions

Another important requirement for many applications today is to have a *realtime* connection to the server in order to get immediately informed about important events. For this use case, GraphQL offers the concept of *subscriptions*.

&nbsp;

When a client *subscribes* to an event, it will initiate and hold a steady connection to the server. Whenever that particular event then actually happens, the server pushes the corresponding data to the client. Unlike queries and mutations that follow a typical “*request-response*-cycle”, subscriptions represent a *stream* of data sent over to the client.

&nbsp;

Subscriptions are declared in SDLs as a root type in the schema alongside the query and mutation types. Here is an example of how subscriptions can be declared in a GraphQL schema:

> type Subscription {\
&nbsp; &nbsp; newMessage: Message\
}

&nbsp;

In this example, the Subscription type has a field called newMessage that returns a Message type. This means that the client can subscribe to notifications for new messages by using this field in a subscription query.

&nbsp;

Subscription fields can also accept arguments in the same way that query and mutation fields do. For example:

> type Subscription {\
&nbsp; &nbsp; newMessage(roomId: ID\!): Message\
}

&nbsp;

In this example, the newMessage field accepts a required argument called roomId. This allows the client to specify which room for which they want to subscribe to notifications.

&nbsp;

Subscriptions can also use the @ directives to specify conditions that must be met before the subscription is triggered. For example:

> type Subscription {\
&nbsp; &nbsp; newMessage(roomId: ID\!): Message @auth\
}

&nbsp;

In this example, the @auth directive specifies that the client must be authenticated in order to subscribe to notifications for new messages in the specified room.

&nbsp;

### Structure of an SDL

&nbsp;

Here is a list of keywords used in the GraphQL SDL to define a GraphQL schema:

&nbsp;

* **Schema:** defines the root types of a GraphQL API, which serve as entry points. These include Query, Mutation, and Subscription.
* **Type:** specifies an object type in the schema, representing a collection of fields that can be queried together.
* **Interface:** declares a set of fields that multiple object types can implement, ensuring consistency across different types.
* **Union:** represents a union type, allowing a field to return multiple possible object types without sharing common fields.
* **Scalar:** defines a custom scalar type beyond the built-in types like String, Int, Float, Boolean, and ID.
* **Enum:** creates an enumeration type, which is a predefined set of named values that a field can return.
* **Input:** describes an input object type used for passing structured arguments in mutations.
* **Extend:** expands an existing type or interface by adding new fields or functionality.
* **Directive:** defines a custom directive to modify schema behavior. Directives can be applied to fields, arguments, and other schema elements, with the server passing them to the client for interpretation.

&nbsp;

## Build a GraphQL SDL with Hackolade Studio

A GraphQL model in Hackolade Studio can be built in different ways:

\- forward-engineering a Hackolade Studio model of any target, using the function for model-driven API generation (TBA)

\- deriving from a Polyglot model (TBA)

\- reverse-engineering an artifact like DDL or JSON-Schema (TBA)

\- reverse-engineer from an Excel template (TBA)

\- building the model from a blank page.

&nbsp;

We focus here on this last option, as it provides a good understanding for how the plugin operates. &nbsp;

&nbsp;

### Type definitions

The core of any GraphQL implementation is a definition of the object types it can return, structured within the GraphQL type system and outlined in the GraphQL schema.&nbsp; Let's build together a GraphQL model in Hackolade Studio, based on a [StarWars example](<https://github.com/graphql/graphql-spec?tab=readme-ov-file#type-system> "target=\"\_blank\"").&nbsp; We start with so-called "non-root types".

Non-root types in GraphQL are types that define the structure of data but are not directly used as entry points for queries, mutations, or subscriptions.

Root types, on the other hand, serve as the entry points of a GraphQL API and include Query, Mutation, and Subscription, which define how clients interact with the schema.&nbsp; We describe in the next section how to build root type operations or entry points.

Type definitions are created in the corresponding lower tab of the central pane

![GraphQL central pane tabs](<lib/GraphQL central pane tabs.png>)

&nbsp;

THe different types that you can define are proposed in a tree view:

![GraphQL Type Definitions](<lib/GraphQL Type Definitions.png>)

&nbsp;

To build your types, you may use the Actions menu, the toolbar icons, or the contextual menu either in the Object Browser on the left or in the Central Pane.&nbsp; In this example, we use the contextual menu which filters options to show only the appropriate one(s) for the type you're creating or enhancing.

Let's create the first type:

&nbsp;

![GraphQL Create Objects Type](<lib/GraphQL Create Objects Type.png>)

&nbsp;

&nbsp;

&nbsp;

The type Human is an object type, and that object contains a field with the label name which has a data type Sting:

![GraphQL Type - Add field](<lib/GraphQL Type - Add field.png>)

&nbsp;

We can easily add an ID field and a homePlanet field:

![GraphQL object type example](<lib/GraphQL object type example.png>)

&nbsp;

In the next step, we need to define a reusable Enum, then reference it in the Human object type:

![GraphQL create enum type](<lib/GraphQL create enum type.png>)

&nbsp;

To create a reference to the newly created Enum is easy.&nbsp; But before we do that, there is a subtlety here.&nbsp; A Human can appear in more than one episode.&nbsp; So it is necessary here to first create a list, the represent the 1-to-n relationship between Human and Episodes:

![GraphQL create list field for multiple items](<lib/GraphQL create list field for multiple items.png>)

&nbsp;

Then replace the list item by a reference to the previously defined Episode Enum:&nbsp;

![GraphQL reference previously created type](<lib/GraphQL reference previously created type.png>)

&nbsp;

&nbsp;

and it results in this structure:

![GraphQL obect structure with reference](<lib/GraphQL obect structure with reference.png>)

&nbsp;

Most importantly, you can see that Hackolade Studio automatically generates the syntactically correct SDL in the GraphQL Schema lower tab of the central pane:

![GraphQL SDL](<lib/GraphQL SDL.png>)

&nbsp;

In the above process, we simply added new fields to the Human object.&nbsp; That's fine.&nbsp; But in some cases, you may want to leverage a reusable structure.&nbsp; We're already doing that by referencing the Enum Episode.&nbsp; And referencing can be used in many circumstances.

*Referencing* any non-root type means using that type as a subobject in your own type definition, but without the possibility of making deviations.

But there is another possibility, which *implements an interface*.&nbsp; Implementing an interface means defining an object type that adheres to the interface by including all its required fields, ensuring consistency across multiple object types.&nbsp; It also allows you to query these types using the interface as a common denominator.

In the StarWars example, we want to create a Droid type which shares the first 4 fields with the type Human.&nbsp; Instead of retyping multiple types, or copying and pasting, let's build from the start a construct that can be reused to boost consistency and quality without some of the flexibility restrictions of referencing.

We create here the Character interface with the common fields:

![GraphQL create an interface](<lib/GraphQL create an interface.png>)

&nbsp;

Then for the Human object type, we can select the Implements of the Character interface:&nbsp;

![GraphQL implements an interface](<lib/GraphQL implements an interface.png>)

then add any additional field that might be specific to the Human object type but not common with any other.&nbsp; The process of selecting an interface to implement performs a copy action for all of the fields of the interface at the time of the action:

This action results in the following structure:

![GraphQL result of implementing an interface](<lib/GraphQL result of implementing an interface.png>)

&nbsp;

We can then do the same for the Droid type, then see the results in the following auto-generated SDL:

![GraphQL StarrWars SDL](<lib/GraphQL StarrWars SDL.png>)

&nbsp;

### Root types operations entry points

It is in the Operations ERD lower tab of the central pane that you define the graphical and schema-centric entry points for your queries, mutations, and subscriptions.

&nbsp;

The idea is to graphically display the input arguments and the payload structure of the response.&nbsp; This graphical representation makes it more obvious to users how to query as well as the expected response:

![GraphQL operations root type entry points](<lib/GraphQL operations root type entry points.png>)

&nbsp;

This feature is currently evolving rapidly.&nbsp; This documentation page will be enriched when the feature matures.&nbsp; In the meantime, it is easy to create a graph and operation by clicking the Add Graph button in the Diagram Objects pane on the left of the workspace:

![GraphQL add graph and operation entry point](<lib/GraphQL add graph and operation entry point.png>)

&nbsp;

In the StarWars example, we want to define a query hero to return the Character who is the hero of the trilogy, and specify an optional argument to fetch the hero of a specific episode:&nbsp;

You start by adding the query response that you expect for the operation:

![GraphQL add query response](<lib/GraphQL add query response.png>)

&nbsp;

Then you define the input argument for your query:

![GraphQL input argument](<lib/GraphQL input argument.png>)

&nbsp;

The argument can be an input field, an input object, an object type, or an interface.&nbsp; And arguments can be used for input as well as output.

It results in this graphical representation of the operation:

![GraphQL StarWars hero query](<lib/GraphQL StarWars hero query.png>)

&nbsp;

Currently, Hackolade Studio does not yet support [GraphQL federation](<https://graphql.org/learn/federation/> "target=\"\_blank\"").&nbsp; But in preparation for it, you should include a "container" for each graph in your model.&nbsp; Alternatively you could have separate models for each graph.

&nbsp;

## Forward-engineer GraphQL Schema Definition Language

You may view the GraphQL Schema in the corresponding lower tab of the central pane.&nbsp; The GraphQL-compliant output can be copied and pasted into the tool of your choice within your technology stack, for example Apollo Studio, as described below.&nbsp; Or you may generate a SDL file with the .graphql extension, so it can be imported into other tools, such as Postman, as described below.

![GraphQL Schema Definition Language generation](<lib/GraphQL Schema Definition Language generation.png>)

&nbsp;

## Reverse-engineer an SDL file

It is possible to import (reverse-engineer) an existing GraphQL API into Hackolade Studio, either by choosing an SDL file, or by performing an introspection from a GraphQL endpoint.

![GraphQL reverse-engineering menu](<lib/GraphQL reverse-engineering menu.png>)

&nbsp;

Schema Definition Language files are typically stored in text files with the extension *.graphql* (sometimes *.gql*)

&nbsp;

&nbsp;

&nbsp;

## Perform a schema introspection from a URL

[Introspection](<https://github.com/graphql/graphql-spec/blob/main/spec/Section%204%20--%20Introspection.md>) is a powerful feature of GraphQL that allows to dynamically discover and explore the schema of a GraphQL API.&nbsp; The schema can be examined to get information about its types, fields, and other elements. In GraphQL, this is done by querying the \_\_schema and \_\_type introspection fields, which are provided by the GraphQL server.

&nbsp;

Hackolade Studio allows users to create a connection, with authentication if necessary, to&nbsp;

![GraphQL introspection connection parameters](<lib/GraphQL introspection connection parameters.png>)

&nbsp;

&nbsp;

## How does the Hackolade Studio plugin for GraphQL compare with Apollo Studio?

The Apollo page for [GraphQL Schema *Basics*](<https://www.apollographql.com/docs/apollo-server/schema/schema> "target=\"\_blank\"") is a different version of the information you can find above.&nbsp; But instead of having to type it all up without making any typos, Hackolade Studio provides a way to build your schema with a few click of a mouse.&nbsp; Or better yet, based on an existing target model, or by importing DDLs, etc.&nbsp; As such, it is a great completment to the Apollo suite of tools for GraphQL.&nbsp;

&nbsp;

With our GraphQL plugin, we can do much more than design schemas.&nbsp; More on that below in a section below.

&nbsp;

If you don't yet have an API endpoiint up and running, you may stiill use the [Apollo Studio](<ttps://studio.apollographql.com> "target=\"\_blank\"") where you can import the Schema Definition Language SDL file out of Hackolade Studio.&nbsp; When you create a new a new graph, you're first prompted to provide an endpoint.&nbsp; If you provide one that is not accessible, Apollo Studio proposes to upload your schema:

&nbsp;

&nbsp;

![GraphQL Apollo Studio](<lib/GraphQL Apollo Studio.png>)

&nbsp;

You can simply copy from the Hackoalde Studio and paste in the Apollo Studio dialog:

![GraphQL Apollo Studio upload schema dialog](<lib/GraphQL Apollo Studio upload schema dialog.png>)

&nbsp;

You will then be able to build your queries, mutations, and subscriptions based on the schema you just uploaded.&nbsp; The schema is also visible in the schema tab:

&nbsp;

![GraphQL Apollo Studio schema tab](<lib/GraphQL Apollo Studio schema tab.png>)

&nbsp;

&nbsp;

&nbsp;

## How does the Hackolade Studio plugin for GraphQL compare with Postman?

At Hackolade, we're big fans of [Postman](<https://www.postman.com/> "target=\"\_blank\"").&nbsp; Our solution is a complement to [Postman's support of GraphQL](<https://learning.postman.com/docs/sending-requests/graphql/graphql-overview/> "target=\"\_blank\"") with no overlap.&nbsp; Hackolade Studio with its GraphQL plugin is a design tool for GraphQL schemas.&nbsp; Whereas Postman is a client with which you can make GraphQL requests that leverage a schema. &nbsp;

&nbsp;

With our GraphQL plugin, we can do much more than design schemas.&nbsp; More on that below in a section below.

&nbsp;

A GraphQL schema describes all the data available to clients, the set of operations (queries, mutations, and subscriptions) that can be performed, and how types and fields relate to each other.&nbsp; Hackolade take a schema-centric approach so that you can easily navigate the graph with multiple entry points in your queries, mutations, and subscriptions. &nbsp;

&nbsp;

While you may already have existing APIs that you wish to document with Hackolade and publish to data dictionaries and maintain, the added value of Hackolade Studio is the ability to create a schema and discuss it with stakeholders before the server has been built.&nbsp; You can build the GraphQL schema with a few clicks of a mouse, then generate a syntactically correct schema SDL (Schema Definition Language) without any knowledge of the details of the syntax (just like you can build an ERD and the DDL gets generated automatically.)   You can forward-engineer the SDL artifact to a .graphql file.

&nbsp;

Then, in Postman, you just import the GraphQL schema:&nbsp;

&nbsp;

![GraphQL Postman import schema](<lib/GraphQL Postman import schema.png>)

&nbsp;

&nbsp;

After import, you can easily assemble your queries, mutations, and subscription on the schema created with Hackolade Studio:

![GraphQL Postman query creation](<lib/GraphQL Postman query creation.png>)

&nbsp;

&nbsp;

&nbsp;

## Other added value of building GraphQL schemas with Hackolade

Beyond the creation from scratch of GraphQL schemas with Hackolade Studio, the added value of our solution is:

\- Use one single tool with harmonized user interface for modeling of data-at-rest and data-in-motion

\- Model-driven GraphQL API generation: start from a model in any target, and generate the GraphQL schema file in just a couple of clicks, then keep the target model and the GraphQL models in sync

\- Integration with our Polyglot modeling approach so all models can easily be kept in sync

\- Publish GraphQL models to data dictionaries

\- Command-Line Interface to automate the above

\- Etc.&nbsp;

&nbsp;

&nbsp;

