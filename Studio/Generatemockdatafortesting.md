# Generate mock data for testing

Hackolade Studio allows you to generate fake but realistic data for your data models.&nbsp; Using fake data can be useful during system development, testing, and demos, mainly because it avoids using real identities, full names, real credit card numbers or Social Security numbers, etc.&nbsp; while using "Lorem ipsum" strings and random numbers is not a realistic enough to be meaningful.&nbsp; Alternatively, one could use cloned production data, except that it generally does not exist for new applications, plus you would still have to mask or substitute sensitive data to avoid disclosing any personally identifiable information.

&nbsp;

According to [ThoughtWorks TechRadar](<https://www.thoughtworks.com/radar/techniques?blipid=202210032> "target=\"\_blank\"") 27: "Synthetic data is also useful for exploring edge cases that lack real data or for identifying model bias."

&nbsp;

Moreover, manually generating fake data takes time and slows down the testing process, particularly if large volumes are required.

&nbsp;

The solution is to use Hackolade Studio to generate mock data, i.e. synthetic or fake but realistic data.&nbsp; With Hackolade, you can generate first names and last names that look real but are not, and the same for company names, product names and descriptions, street addresses, phone numbers, credit card numbers, commit messages, IP addresses, UUIDs, image names, URLs, etc..

&nbsp;

Data generated here may be fake, but it has the expected format and contains meaningful values.&nbsp; City and streets names for example are randomly composed from elements that mimic real names.&nbsp; And you can set the desired locale so the data elements are localized for better contextual meaning.

&nbsp;

Generating mock test data is a 2-step process:

* one-time setup for each model: you must associate each attribute with a function to get a contextually realistic sample
* each time you need to generate test data, you define the parameters of the run

&nbsp;

&nbsp;

## Assign a Faker function to data model attributes

Hackolade leverages an open-source library for this feature: [FakerJS](<https://fakerjs.dev/> "target=\"\_blank\""), a generator of fake data based on static string input.&nbsp; Faker provides a wide range of data categories, e.g. name, address, animal, company, commerce, date, database, finance, git, image, internet, phone, vehicle, etc.&nbsp; Each category contains many sub-categories and options.

&nbsp;

Before you start, you should familiarize yourself with the possibilities by consulting [this guide](<https://fakerjs.dev/guide/> "target=\"\_blank\"").&nbsp; Note that the question mark ? in our properties pane opens up the Faker guide page in your default browser:

![Faker function properties pane](<lib/Faker function properties pane.png>)

&nbsp;

All you need to do is to copy a function from the Faker guide pages and paste it in the property in Hackolade, for example:

![Faker function](<lib/Faker function.png>)

to be pasted&nbsp;

![Faker function pasted](<lib/Faker function pasted.png>)

&nbsp;

You may also paste functions with arguments, such as ***faker.person.firstName("female")*** or compose more sophisticated results by [assembling functions with helpers](<https://fakerjs.dev/api/helpers.html#fake> "target=\"\_blank\""), for example:

&nbsp; &nbsp; **faker.helpers.fake('{{person.firstName}} {{person.lastName}}')**

or

**'${faker.company.name()}, ${faker.company.suffixes()}'**

&nbsp;

&nbsp;

Note that we accept functions wrapped by either backticks or single quotes.

&nbsp;

For security reasons to avoid vulnerability injection, it is NOT possible to use any non-faker method or plain JavaScript.

&nbsp;

You can check the result in the JSON Data pane of the JSON/YAML Preview tab for the entity.&nbsp; If a function is not correctly composed or is missing, our JSON Data generation will fallback on the sample property, if defined, or to a random string 'Lorem'

&nbsp;

The Faker function property is only enabled for selected data types, mainly string and numeric, and associated data types.

&nbsp;

The following model illustrates the capabilities to generate JSON Data:

![Faker function JSON Data preview](<lib/Faker function JSON Data preview.png>)

&nbsp;

&nbsp;

using the following functions (in this case exported to Excel for easy bulk edit):

&nbsp;

| **Name** | **Type** | **Faker function** |
| --- | --- | --- |
| name | string | faker.name.fullName() |
| title | string | faker.name.title() |
| company | string | '${faker.company.name()}, ${faker.company.suffixes()}' |
| jobtitle | string | faker.name.jobTitle() |
| jobDescriptor | string | faker.name.jobDescriptor() |
| seniority | number | faker.random.numeric() |
| dayOff | string | faker.date.weekday() |
| phone | string | faker.phone.number('+1 (###) ###-####') |


&nbsp;

&nbsp;

**Note:** you may change the locale, if different than English, in Tools \> Options \> Forward-Engineering \> JSON Data.

&nbsp;

## Generate test data in bulk

Generating one sample document on screen is good, but of limited use.&nbsp; The real benefit comes when you can generate large, if not massive, amounts of test data, for general testing, as well as performance, and even load testing. &nbsp;

&nbsp;

Hackolade can generate 2 types of test data:

* JSON documents for any model entity
* records or documents to be inserted in database instances, where applicable

&nbsp;

## Assign a Faker function at the entity level

Since version 7.5.0 of Hackolade Studio, it is now possible to define a Faker function at the entity level, ensuring consistent and related attributes within an entity. This approach is particularly useful for generating coherent attributes, such as creating an email address from a person's first and last names.

&nbsp;

Note: the attributes defined in the Faker function at the entity level must correspond to actual attributes in the entity.

&nbsp;

### Example usage

Using this piece of code in the Faker function property of the entity:

&nbsp;

**(()=\> {**

**&nbsp; &nbsp; &nbsp; const sex = faker.person.sex();**

**&nbsp; &nbsp; &nbsp; const firstName = faker.person.firstName(sex);**

**&nbsp; &nbsp; &nbsp; const lastName = faker.person.lastName(sex);**

**&nbsp; &nbsp; &nbsp; const fullName = faker.person.fullName({ firstName, lastName, sex });**

**&nbsp; &nbsp; &nbsp; const domain = faker.internet.domainName();**

**&nbsp; &nbsp; &nbsp; const email = faker.internet.email({ firstName: firstName, lastName: lastName, provider: domain})**

**&nbsp; &nbsp; &nbsp; const normalized\_email = email.toLowerCase();**

**&nbsp; &nbsp; &nbsp; const alias = \`${firstName}@${domain}\`;**

**&nbsp; &nbsp; &nbsp; const initials = \`${firstName\[0\]}.${lastName\[0\]}.\`;**

&nbsp;

**&nbsp;&nbsp; &nbsp; return {**

**&nbsp;&nbsp; &nbsp; sex,**

**&nbsp;&nbsp; &nbsp; firstName,**

**&nbsp;&nbsp; &nbsp; lastName,**

**&nbsp;&nbsp; &nbsp; fullName,**

**&nbsp;&nbsp; &nbsp; domain,**

**&nbsp;&nbsp; &nbsp; normalized\_email,**

**&nbsp;&nbsp; &nbsp; email,**

**&nbsp;&nbsp; &nbsp; alias,**

**&nbsp;&nbsp; &nbsp; initials**

**&nbsp;&nbsp; &nbsp; }**

**})()**

&nbsp;

This function ensures logically related and consistent data across attributes, e.g.:

**{**

**&nbsp; &nbsp; "id": "4ace053785d90d3aa5f5c66359888e88",**

**&nbsp; &nbsp; "sex": "female",**

**&nbsp; &nbsp; "firstName": "Alexandra",**

**&nbsp; &nbsp; "lastName": "Upton",**

**&nbsp; &nbsp; "fullName": "Miss Alexandra Upton",**

**&nbsp; &nbsp; "initials": "A.U.",**

**&nbsp; &nbsp; "domain": "crooked-tomatillo.org",**

**&nbsp; &nbsp; "email": "Alexandra\_Upton@crooked-tomatillo.org",**

**&nbsp; &nbsp; "normalized\_email": "alexandra\_upton@crooked-tomatillo.org",**

**&nbsp; &nbsp; "alias": "Alexandra@crooked-tomatillo.org",**

**&nbsp; &nbsp; "age": 34**

**}**

&nbsp;

### Defining Faker Functions at Attribute and Entity Level

Faker functions can be defined at both the attribute level and the entity level for the same entity. This allows for flexible data generation where attributes that need to be coherent can be defined at the entity level, while independent attributes can remain at the attribute level.

#### Priority of Faker Functions

When an attribute has a Faker function defined both at the attribute level and the entity level, the Faker function at the entity level takes precedence. The Faker function at the attribute level will be ignored in this case, ensuring that coherent data is generated as specified by the entity-level Faker function.

&nbsp;

Referring to the example above, attributes such as *email*, *alias*, and *initials* are defined coherently at the entity level, while independent attributes like id and age can be defined separately at the attribute level. However, this is not mandatory; all attributes can be faked at the entity level if desired.

### Syntax

There are 3 ways to setup a custom function at the entity level:

&nbsp;

\- Via a self-calling function as in the example above:

**(()=\> { const firstName = faker.person.firstName(); const lastName = faker.person.lastName(); return { firstName, lastName, } })()**

&nbsp;

\- Via a function declaration:

**function getPersonData() { const firstName = faker.person.firstName(); const lastName = faker.person.lastName(); return { firstName, lastName, } } getPersonData();**

&nbsp;

\- Via a faker helper to return JSON string:

**faker.helpers.fake(\`{"firstName": "${faker.person.firstName()}", "lastName": "${faker.person.lastName()}"}\`);**

&nbsp;

### Create test JSON documents on file system

For any entity in a Hackolade data model, you can easily generate sample data with the menu Tools \> Forward-Engineer \> JSON Document.&nbsp; You can select the entity or entities of your choice.&nbsp; Then you specify the number of documents, and whether or not to minify the output:

&nbsp;

![Faker JSON Doc forward-engineering selection](<lib/Faker JSON Doc forward-engineering selection.png>)

&nbsp;

After you choose the folder path, the application will create a JSON file containing an array of sample documents:

&nbsp;

![Faker JSON Doc forward-engineering output](<lib/Faker JSON Doc forward-engineering output.png>)

&nbsp;

### Insert documents or records in database instance

Starting with v6.1.3 for MongoDB (and progressively thereafter for other targets), you may also generate synthetic data in bulk and apply it to a database instance.&nbsp; All you need to do it to go to the script tab, select "Include sample data", and specify the number of documents per collection.&nbsp; Then click the "Apply to instance" button and choose the target instance from the Connection settings dialog.

&nbsp;

![Faker bulk synthetic data applied to instance](<lib/Faker bulk synthetic data applied to instance.png>)

&nbsp;

