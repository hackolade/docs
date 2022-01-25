# Create a REST API model

In the previous tutorial, we reviewed how to create data models for property graph databases.&nbsp; By the end of this tutorial, you will master how to create a model for REST APIs using Swagger or OpenAPI specification.

&nbsp;

While it is useful to be familiar with REST APIs in general, and the Swagger/OpenAPI specification in particular, the great advantage of Hackolade Studio's handling of REST APIs documentation is that the user does not have to know the syntax for Swagger or OpenAPI.&nbsp; You create your API with the user interface, and the application takes care of generating the proper syntax, thereby avoiding costly mistakes, and increasing productivity and API quality.

&nbsp;

Hackolade takes a visual and schema-centric approach to building REST APIs, and fits well in API-first and design-first processes.&nbsp; It can also help understand existing APIs with a visual representation of Swagger or OpenAPI files, after reverse-engineering of such files, whether in JSON or YAML.

&nbsp;

Given the rise of OpenAPI version 3, replacing the previous Swagger version 2 specification, the rest of this tutorial will focus on OpenAPI.&nbsp; Most of the principles below apply also to Swagger, even if some implementation features may vary.

&nbsp;

For the purpose of this tutorial, we will build a very simple API for an URL shortener, i.e. a service letting:

\- a user create an entry based on a full URL, and receive a short [slug](<https://en.wikipedia.org/wiki/URL\_shortening> "target=\"\_blank\"") generated by the service;

\- any system send a slug and get back the full URL.

&nbsp;

The example is inspired by [Shorty](<https://shorty.skghosh.me/> "target=\"\_blank\""), an [existing service](<https://github.com/SkullTech/shorty.sls> "target=\"\_blank\""), but the OpenAPI documentation is enhanced to demonstrate best practices and how to leverage the features of Hackolade Studio.&nbsp; By the end of the tutorial, you will have created a visual model for your API:

![Tutorial OpenAPI resources](<lib/Tutorial%20OpenAPI%20resources.png>)

&nbsp;

and generated the corresponding OpenAPI file:

![Tutorial OpenAPI file tab](<lib/Tutorial%20OpenAPI%20file%20tab.png>)

&nbsp;

&nbsp;Here is the [link](<https://hackolade.com/schemas/OpenAPI/shorty\_URL\_shortener.hck.json> "target=\"\_blank\"") if you want to download this data model.

&nbsp;

## Design the API

An API is an interface for people or systems to consume a service.&nbsp; It is critical to put yourself in the shoes of the consumer, and make the API easy to understand and navigate the service.&nbsp; It must be usable, valuable, credible, and useful.&nbsp; Good design and good documentation go a long way towards adoption, along with collaboration and communication. &nbsp;

&nbsp;

The sequence diagram for the first process to create an entry based on a full URL and receive a short [slug](<https://en.wikipedia.org/wiki/URL\_shortening> "target=\"\_blank\"") generated by the service can be drawn as follows:

![Tutorial OpenAPI seq diagram use case 1](<lib/Tutorial%20OpenAPI%20seq%20diagram%20use%20case%201.png>)

&nbsp;

The sequence diagram for the second process to send a slug and get back the full URL is as follows:

![Tutorial OpenAPI seq diagram use case 2](<lib/Tutorial%20OpenAPI%20seq%20diagram%20use%20case%202.png>)

&nbsp;

&nbsp;

Typically, Swagger tutorials teach you to build an API in the order of sections in an OpenAPI file: first the info section, then the paths, and finish with components.&nbsp; That would be like wanting to paint the house before the foundations are built... We prefer to start with what matters most, the core foundation of the API: the schema describing the structure of the service contract being exchanged between the producer and the consumer.

&nbsp;

Accordingly, the process to create this API is as follows:

1. create reusable components
   1. a schema for the exchange
   1. a request body to submit a long URL, using the schema created in the previous step
   1. a simple parameter to fetch the full URL from a previously generated slug
   1. a couple of responses
      1. returning the generated slug (200 - OK) using the common schema
      1. returning an error message, reusable for different kinds of errors
   1. an OAuth2 security scheme (could also be done at a later stage)
1. create resources with requests and responses
1. add endpoint, tags, and metadata information, plus color coding of responses&nbsp;
1. generate the OpenAPI documentation file, with API testing

&nbsp;

&nbsp;

## Build the API

We will now use Hackolade Studio to build the API step by step.&nbsp; Let's create a new model and choose OpenAPI as a target.&nbsp; Remember that the application will automatically generate the OpenAPI file with proper syntax, as you build the API in the screens. You may check the progress at any time in the lower tab OpenAPI File.&nbsp;

&nbsp;

### Create reusable components

Often, multiple API operations have some common parameters or return the same response structure. To avoid code duplication and facilitate evolution, you can place the common definitions in the global components section and reference them using [$ref](<https://swagger.io/docs/specification/using-ref/> "target=\"\_blank\"").  In Hackolade, components are handled like model references, and are maintained in the lower tab Components.&nbsp; If a component evolves, these changes are automatically reflected in all places where the component is referenced.

&nbsp;

#### Schema components for the exchange

For this very simple service, we just need 2 schemas, one for the happy flow exchange, and one for error messages.&nbsp; Note that the url schema can be used both in the creation request and the 200 response.&nbsp; The url schema has just 2 fields: longURL and slug, both of string data type.&nbsp; And the error schema is also real simple with a status code according to the [RFC 7231 standard](<https://en.wikipedia.org/wiki/List\_of\_HTTP\_status\_codes> "target=\"\_blank\""), and a text message.

&nbsp;

The steps to create a schema in Hackolade have been covered in an [earlier tutorial](<Createyourfirstdatamodel.md>) in section "Hierarchical schema view".

&nbsp;

![Tutorial OpenAPI schema components](<lib/Tutorial%20OpenAPI%20schema%20components.png>)

&nbsp;

If you already have complex schemas defined in other Hackolade target data models (or JSON Schema files, or a Hackolade Polyglot model, or in other OpenAPI files, or on SchemaHub), you may reference any of those as [external references](<Reusableobjectsdefinitions.md>) so they can be kept in sync with their master version for higher data quality and consistency.

&nbsp;

#### Request body to submit a long URL

To create a request body in components, you do a right-click on the requestBodies box and get a contextual menu where you're guided to choose the appropriate option:

![Tutorial OpenAPI requestBodies context menu](<lib/Tutorial%20OpenAPI%20requestBodies%20context%20menu.png>)

&nbsp;

A template is created to guide you through the creation, with a standard media type application/json and its structure.&nbsp; You may create additional media types, from a list of popular ones, or by adding your own if needed:

![Tutorial OpenAPI requestBodiy template](<lib/Tutorial%20OpenAPI%20requestBodiy%20template.png>)

&nbsp;

In our case, we will rename the requestBody to urlBody and replace the schema object by a reference to the schema component created earlier. &nbsp;

&nbsp;

You may wonder why the slug is also in the requestBody.&nbsp; That's because a feature of the service is to allow the end-user to specify a preferred custom slug, as well as a random system-assigned slug.&nbsp; To allow the former, we need to provide a field for it, along with the long URL.&nbsp; An added advantage is that the same schema can be used both for the request and the response.

&nbsp;

We also want to give users examples to better understand how to use the API, for example with&nbsp;

\- a summary: Choosing your own custom slug

\- and a value: {"slug":"hck","longUrl":"https://hackolade.com"}

![Tutorial OpenAPI requestBodiy urlBody](<lib/Tutorial%20OpenAPI%20requestBodiy%20urlBody.png>)

&nbsp;

&nbsp;

#### Parameter to fetch a full URL from a previously generated slug

Next, we follow similar steps steps to create the parameter that will be used in the second use case, when submitting a slug (in order to retrieve the full URL)&nbsp; Here, we choose a path.&nbsp; In other APIs, you could also choose a query, a header, or a cookie.

![Tutorial OpenAPI parameters contextual menu](<lib/Tutorial%20OpenAPI%20parameters%20contextual%20menu.png>)

&nbsp;

Again here, a template automatically creates the structure and you just need to enter the properties and make the adjustments that suit your use case:

![Tutorial OpenAPI parameters component slug](<lib/Tutorial%20OpenAPI%20parameters%20component%20slug.png>)

&nbsp;

#### A couple of responses

Next, we right-click on the responses component to create a response structure:

![Tutorial OpenAPI responses contextual menu](<lib/Tutorial%20OpenAPI%20responses%20contextual%20menu.png>)

&nbsp;

A standard template gets created:

![Tutorial OpenAPI responses template](<lib/Tutorial%20OpenAPI%20responses%20template.png>)

&nbsp;

We start first with a good response 200 - OK.&nbsp; We rename the response to 200 and give it a description, "Successful operation" for example.&nbsp; We also right-click on the schema box and choose the url schema referenced earlier:

![Tutorial OpenAPI referencing schema component](<lib/Tutorial%20OpenAPI%20referencing%20schema%20component.png>)

&nbsp;

As a result, the structure now references the component schema:

![Tutorial OpenAPI response with schema ref](<lib/Tutorial%20OpenAPI%20response%20with%20schema%20ref.png>)

&nbsp;

Then we follow similar steps to define a generic error message:

&nbsp;

![Tutorial OpenAPI error with schema ref](<lib/Tutorial%20OpenAPI%20error%20with%20schema%20ref.png>)

&nbsp;

#### A security scheme

Finally, we create a security scheme for the OAusth2 access to the service:

![Tutorial OpenAPI securitySchemes](<lib/Tutorial%20OpenAPI%20securitySchemes.png>)

with its corresponding parameters:

![Tutorial OpenAPI securitySchemes params](<lib/Tutorial%20OpenAPI%20securitySchemes%20params.png>)

&nbsp;

### Create resources with requests and responses

We're done now with the creation of reusable components.&nbsp; It is time to assemble them in resource paths.&nbsp; This operation is done in the API Model lower tab.

&nbsp;

#### Add a resource

We right-click in the canvas to get the contextual menu and create a resource:

![Image](<lib/Tutorial%20OpenAPI%20Add%20resource%20menu.png>)

&nbsp;

and give the resource path a name:

![Tutorial OpenAPI resource path name](<lib/Tutorial%20OpenAPI%20resource%20path%20name.png>)

&nbsp;

#### Add a request

Then we right-click again the box to add a request:

![Tutorial OpenAPI Add request menu](<lib/Tutorial%20OpenAPI%20Add%20request%20menu.png>)

&nbsp;

The transaction is to submit a full URL and optionally a custom slug, so we choose a POST request operation

![Tutorial OpenAPI Request operation code](<lib/Tutorial%20OpenAPI%20Request%20operation%20code.png>)

&nbsp;

and add a description and a summary:

![Tutorial OpenAPI Request operation properties](<lib/Tutorial%20OpenAPI%20Request%20operation%20properties.png>)

&nbsp;

It is a good practice to assign a tag, which will allow grouping of requests in the documentation:

![Tutorial OpenAPI Tag grouping](<lib/Tutorial%20OpenAPI%20Tag%20grouping.png>)

&nbsp;

The easiest way to create the structure for a request is to work in the dedicated tab where a template is automatically created:

![Tutorial OpenAPI Request template](<lib/Tutorial%20OpenAPI%20Request%20template.png>)

&nbsp;

There are different ways to build a request, all represented in the template.&nbsp; In our case, we will replace the schema object by the reusable component created earlier:

![Tutorial OpenAPI Request urlBody reference](<lib/Tutorial%20OpenAPI%20Request%20urlBody%20reference.png>)

We also create examples of a custom slug and a random slug, which will help the developer visualize the possible inputs.

&nbsp;

**Tip:** If you ever need a requestBody or response to differ from its original definition, you may break the link with the definition by right clicking on the reference and choosing to replace by attributes.&nbsp; Then you may do your modifications, but you should be aware that the object will not be updated if the original component evolves.

![Tutorial OpenAPI Replace ref with attributes](<lib/Tutorial%20OpenAPI%20Replace%20ref%20with%20attributes.png>)

&nbsp;

#### Add a response

We right-click on the request and choose Add response from the contextual menu:

![Tutorial OpenAPI Add response contextual menu](<lib/Tutorial%20OpenAPI%20Add%20response%20contextual%20menu.png>)

&nbsp;

and choose the appropriate response code:

![Tutorial OpenAPI Response code](<lib/Tutorial%20OpenAPI%20Response%20code.png>)

&nbsp;

and give it a meaningful description:

![Tutorial OpenAPI Response properties](<lib/Tutorial%20OpenAPI%20Response%20properties.png>)

&nbsp;

Again here, it is easier to work in the dedicated tab to see the template and replace the schema with the reusable component created earlier, and which will be used to return information to the requester:

![Tutorial OpenAPI 200 response reference](<lib/Tutorial%20OpenAPI%20200%20response%20reference.png>)

&nbsp;

We also want to create a 400 response for requests that did not conform to the expected schema:

![Tutorial OpenAPI 400 response reference](<lib/Tutorial%20OpenAPI%20400%20response%20reference.png>)

&nbsp;

And a 403 response for forbidden requests that did not provide proper credentials:

![Tutorial OpenAPI 200 response reference](<lib/Tutorial%20OpenAPI%20403%20response%20reference.png>)

&nbsp;

The resulting API will visually look like this:

![Tutorial OpenAPI urls resource](<lib/Tutorial%20OpenAPI%20urls%20resource.png>)

&nbsp;

Now, we can build the resource for the second use case, including a request and 2 responses:

![Tutorial OpenAPI urls slugs resource](<lib/Tutorial%20OpenAPI%20urls%20slugs%20resource.png>)

&nbsp;

Note how easy it is to understand visually the schema contract of the exchanges.&nbsp; Note also the handy color-coding of the responses to make it easy to spot the response behavior: green for 200, red for 400, and yellow for 403.&nbsp;

&nbsp;

We made sure to tag the request with the same urls tag, so both requests are now grouped in the Swagger documentation:

![Tutorial OpenAPI tags grouping](<lib/Tutorial%20OpenAPI%20tags%20grouping.png>)

&nbsp;

We're almost done with the creation of the API: we just need to add some finishing touches.

&nbsp;

### Finishing touches

It is now time to add the metadata, including the server endpoints, tag descriptions, and links to external documentation:

![Tutorial OpenAPI metadata 1](<lib/Tutorial%20OpenAPI%20metadata%201.png>)

![Image](<lib/Tutorial%20OpenAPI%20metadata%202.png>)

&nbsp;

### Generate the OpenAPI documentation file

By clicking on the lower tab OpenAPI file, we can now see the end result:

![Tutorial OpenAPI interactive API pane](<lib/Tutorial%20OpenAPI%20interactive%20API%20pane.png>)

&nbsp;

On the left, we can see the generated JSON (or YAML) syntax for the API we just created with the application.&nbsp; An on-board validator verifies the compliance with the OpenAPI specification.&nbsp; You may select the text, and paste it in your API process or in the [Swagger editor](<https://editor.swagger.io/#/> "target=\"\_blank\"") to leverage server and client code generation for example.&nbsp; You may also export the file via Tools \> Forward-Engineering \> OpenAPI file.&nbsp; Or you can use the [Command-Line Interface](<CommandLineInterface.md>) forEng command to integrate the generation of this file into a DevOps CI/CD pipeline.

&nbsp;

On the right, you can now visualize the API interaction pane.&nbsp; If the service is connected, you may even give the API a try, and see the service in action.

&nbsp;

Don't forget to name your model and save it.&nbsp; Here is the [link](<https://hackolade.com/schemas/OpenAPI/shorty\_URL\_shortener.hck.json> "target=\"\_blank\"") if you want to download this data model.

&nbsp;

There's a raging debate about code-first vs design-first when it comes to API creation.&nbsp; The above approach should demonstrate the advantages of the latter.&nbsp; Design-first will let you think through all the details, discuss alternatives with other stakeholders, evaluate impacts, etc. all without writing a single line of code.&nbsp; Some developers may disagree, but the obvious advantages are: lower Total Cost of Ownership, higher quality, easier evolution, and even quicker delivery of the project.&nbsp; While it may seem slower at the beginning, design-first clearly saves time overall because it reduces risks of rework. &nbsp;

&nbsp;

In particular when multiple teams need to develop in parallel, it becomes indispensable to agree first on a contract for the API.&nbsp; Don't take our word for it: here's [an article ](<https://smartbear.com/blog/embracing-an-api-design-first-approach/> "target=\"\_blank\"")by Smartbear, the original creators of Swagger.

&nbsp;

## Next steps

The above API example was simple on purpose.&nbsp; In practice, APIs can be quite complex.&nbsp; And they inevitably evolve over time.&nbsp; We suggest the articles below to help think through a variety of addition considerations that go beyond the scope of this tutorial but are nevertheless important:

\- [versioning](<https://cloud.google.com/blog/products/api-management/api-design-which-version-of-versioning-is-right-for-you> "target=\"\_blank\"")

\- [links vs keys](<https://cloud.google.com/blog/products/application-development/api-design-why-you-should-use-links-not-keys-to-represent-relationships-in-apis> "target=\"\_blank\"")

\- [various best practices and common pitfalls](<https://cloud.google.com/blog/products/api-management/api-design-best-practices-common-pitfalls> "target=\"\_blank\"")

&nbsp;

&nbsp;

In this tutorial, we reviewed how to create a model for REST APIs using Swagger or OpenAPI specification.&nbsp; In the next tutorial, we will cover how to perform data modeling for polyglot storage and transmission, using our Polyglot Data Modeling capabilities.
