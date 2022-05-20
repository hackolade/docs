# Generate mock data for testing

Hackolade Studio allows you to generate fake but realistic data for your data models.&nbsp; Using fake data can be useful during system development, testing, and demos, mainly because it avoids using real identities, full names, real credit card numbers or Social Security numbers, etc.&nbsp; while using "Lorem ipsum" strings and random numbers is not a realistic enough to be meaningful.&nbsp; Alternatively, one could use cloned production data, except that it generally does not exist for new applications, plus you would still have to mask or substitute sensitive data to avoid disclosing any personally identifiable information.

&nbsp;

Moreover, manually generating fake data takes time and slows down the testing process, particularly if large volumes are required.

&nbsp;

The solution is to use Hackolade Studio to generate mock data, i.e. fake but realistic data.&nbsp; With Hackolade, you can generate first names and last names that look real but are not, and the same for company names, product names and descriptions, street addresses, phone numbers, credit card numbers, commit messages, IP addresses, UUIDs, image names, URLs, etc..

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

![Image](<lib/NewItem4.png>)

&nbsp;

All you need to do is to copy a function from the Faker guide pages and paste it in the property in Hackolade, for example:

![Image](<lib/NewItem5.png>)

to be pasted&nbsp;

![Image](<lib/NewItem6.png>)

&nbsp;

You may also paste functions with arguments, such as ***faker.name.firstName("female")*** or compose more sophisticated results by assembling functions with placeholders, for example:

> faker.fake('Hi, my name is {{name.firstName}} {{name.lastName}}\!')&nbsp;

which uses the faker.name.firstName() and faker.name.lastName() method to resolve the placeholders respectively, or&nbsp;

> faker.fake(\`You can call me at {{phone.phoneNumber(+\!# \!## #### #####\!)}}.')

&nbsp;

It is NOT possible to use any non-faker method or plain JavaScript.

&nbsp;

You can check the result in the JSON Data pane of the JSON/YAML Preview tab for the entity.&nbsp; If a function is not correctly composed or is missing, our JSON Data generation will fallback on the sample property, if defined, or to a random string 'Lorem'

&nbsp;

The Faker function property is only enabled for selected data types, mainly string and numeric, and associated data types.

&nbsp;

The following model illustrates the capabilities to generate JSON Data:

![Image](<lib/NewItem7.png>)

&nbsp;

&nbsp;

using the following functions (in this case exported to Excel for easy bulk edit):

&nbsp;

| **Name** | **Type** | **Faker function** |
| --- | --- | --- |
| name | string | faker.name.findName(undefined, undefined, 'female') |
| title | string | faker.name.title() |
| company | string | faker.fake('{{company.companyName}}, {{company.companySuffix}}') |
| jobtitle | string | faker.name.jobTitle() |
| jobDescriptor | string | faker.name.jobDescriptor() |
| seniority | number | faker.random.numeric() |
| dayOff | string | faker.date.weekday() |
| phone | string | faker.phone.phoneNumber('+1 (###) ###-####') |


&nbsp;

&nbsp;

**Note:** you may change the locale, if different than English, in Tools \> Options \> Forward-Engineering \> JSON Data.

&nbsp;

## Generate test data in bulk

Hackolade can generate 2 types of test data:

* JSON documents for any model entity
* records or documents to be inserted in database instances, where applicable

&nbsp;

### Create test JSON documents on file system

&nbsp;

&nbsp;

### Insert documents or records in database instance

TBA

&nbsp;

&nbsp;

&nbsp;

