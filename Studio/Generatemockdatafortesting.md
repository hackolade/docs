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

![Faker function properties pane](<lib/Faker%20function%20properties%20pane.png>)

&nbsp;

All you need to do is to copy a function from the Faker guide pages and paste it in the property in Hackolade, for example:

![Faker function](<lib/Faker%20function.png>)

to be pasted&nbsp;

![Faker function pasted](<lib/Faker%20function%20pasted.png>)

&nbsp;

You may also paste functions with arguments, such as ***faker.name.firstName("female")*** or compose more sophisticated results by assembling functions with placeholders, for example:

&nbsp; &nbsp; **\`${faker.address.zipCode()} ${faker.address.city()}\`**

&nbsp; &nbsp; '**${faker.address.zipCode()} ${faker.address.city()}'**

&nbsp;

Note that we accept functions wrapped by either backticks or single quotes.

&nbsp;

It is NOT possible to use any non-faker method or plain JavaScript.

&nbsp;

You can check the result in the JSON Data pane of the JSON/YAML Preview tab for the entity.&nbsp; If a function is not correctly composed or is missing, our JSON Data generation will fallback on the sample property, if defined, or to a random string 'Lorem'

&nbsp;

The Faker function property is only enabled for selected data types, mainly string and numeric, and associated data types.

&nbsp;

The following model illustrates the capabilities to generate JSON Data:

![Faker function JSON Data preview](<lib/Faker%20function%20JSON%20Data%20preview.png>)

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
| phone | string | faker.phone.phoneNumber('+1 (###) ###-####') |


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

### Create test JSON documents on file system

For any entity in a Hackolade data model, you can easily generate sample data with the menu Tools \> Forward-Engineer \> JSON Document.&nbsp; You can select the entity or entities of your choice.&nbsp; Then you specify the number of documents, and whether or not to minify the output:

&nbsp;

![Faker JSON Doc forward-engineering selection](<lib/Faker%20JSON%20Doc%20forward-engineering%20selection.png>)

&nbsp;

After you choose the folder path, the application will create a JSON file containing an array of sample documents:

&nbsp;

![Faker JSON Doc forward-engineering output](<lib/Faker%20JSON%20Doc%20forward-engineering%20output.png>)

&nbsp;

### Insert documents or records in database instance

Starting with v6.1.3 for MongoDB (and progressively thereafter for other targets), you may also generate synthetic data in bulk and apply it to a database instance.&nbsp; All you need to do it to go to the scripot tab, select "Include sample data", and specify the number of documents per collection.&nbsp; Then click the "Apply to instance" button and choose the target instance from the Connection settings dialog.

&nbsp;

![Faker bulk synthetic data applied to instance](<lib/Faker%20bulk%20synthetic%20data%20applied%20to%20instance.png>)

&nbsp;

