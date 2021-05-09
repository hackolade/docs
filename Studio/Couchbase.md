# Couchbase

Couchbase Server is an open-source, distributed multi-model NoSQL document-oriented database software package that is optimized for interactive applications.&nbsp; It has a long [history and evolution](<http://stackoverflow.com/questions/5578608/difference-between-couchdb-and-couchbase> "target=\"\_blank\"").&nbsp; It natively manipulates data in key-value form or in JSON documents.&nbsp; Nevertheless Couchbase may be used to store non-JSON data for various use cases.

&nbsp;

Hackolade was specially adapted to support the data modeling of multiple object types within one single bucket, while supporting multiple buckets as well.&nbsp; The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of the sample travel application described [here](<https://docs.couchbase.com/java-sdk/current/ref/travel-app-data-model.html> "target=\"\_blank\"").

![Image](<lib/Couchbase%20workspace.png>)

## Buckets ##

There is a fundamental difference with many other NoSQL document databases: Couchbase strongly suggests to store documents of different kinds into the same "bucket".&nbsp; A bucket is equivalent to a database. Objects of different characteristics or attributes are stored in the same bucket. It may seem counter-intuitive when moving from a RDBMS or MongoDB, but records from multiple tables should be stored in a single bucket, with a “type” attribute to differentiate the various objects stored in the bucket. &nbsp;

&nbsp;

Most deployments have a low number of buckets (usually 2 or 3) and only a few upwards of 5. Although there is no hard limit in the software, the maximum of 10 buckets comes from some known CPU and disk IO overhead of the persistence engine and the fact that Couchbase allocates a specific amount of memory to each bucket. &nbsp;

&nbsp;

But having multiple buckets is something that can be quite useful for different use cases:

\- multi-tenancy: you want to be sure all data are separated

\- different types of data: you can for example store all documents (JSON) in one bucket, and use another one to store "binary" content. The setup would have a bucket with views, and the other one without any. &nbsp;

\- for data with differing caching and RAM quota needs, compaction requirements, availability requirements and IO priorities, buckets act as the control boundary.

&nbsp;

For example, if you choose to create 1 replica for medical-codes data that contain drug, symptom, and operation codes for a standard based electronic health record.&nbsp; This data can be recovered easily from other sources, so a single replica may be fine.&nbsp; However, patient data may require higher protection with 2 replicas.&nbsp; To achieve better protection for patient data without wasting additional space for medical-codes you could choose separate buckets for these 2 types of information.

&nbsp;

There are 2 types of buckets, each with its properties: [Couchbase buckets and Memcached buckets](<https://docs.couchbase.com/server/current/learn/buckets-memory-and-storage/buckets.html> "target=\"\_blank\"").

&nbsp;

## Document kind ##

When mixing different kinds of objects into the same bucket, it becomes necessary to specify a "type" attribute to differentiate the various objects stored in the bucket.&nbsp; In Hackolade, each Document Kind is modeled as a separate entity or box, so its attributes can be defined separately.&nbsp; A specific attribute name must be identified to differentiate the different document kinds.&nbsp; The unique key and the document kind field are common to all document kinds in the bucket, and displayed at the top of each box in the ERD document:

![Image](<lib/Couchbase%20ERD%20shapes.png>)

&nbsp;

## Keys ##

Another modeling characteristic distinguishes Couchbase from some other NoSQL document databases: the unique key of each document is stored 'outside' the JSON document itself.&nbsp; Couchbase was originally a key-value store.&nbsp; With version 2.0, Couchbase bridged the gap to being a multi-model database supporting JSON documents.&nbsp; In essence, the key part remains, and the value part can also be a JSON document.&nbsp; The fundamental difference is that a pure key-value database doesn't understand what's stored in the value, while a document database understands the format in which documents are stored and can therefore provide richer functionality for developers, such as access to documents through queries.

&nbsp;

Couchbase does not automatically generate IDs.&nbsp; Document IDs are assigned by the software application.&nbsp; A valid document ID must:

* Conform to UTF-8 encoding
* Be no longer than 250 bytes

Users are free to choose any ID for their document, so long as they conform to the above restrictions.&nbsp; This feature can be [leveraged](<https://blog.couchbase.com/key-pattern-delimiter-in-couchbase/> "target=\"\_blank\"") to define natural keys where possible, so they can be human-readable, deterministic, and semantic.

&nbsp;

## Attributes data types ##

Couchbase attributes support standard JSON [data types,](<https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/datatypes.html> "target=\"\_blank\"") including lists and sets (arrays), and maps (objects).&nbsp; The Hackolade menu items, contextual menus, toolbar icon tooltips, and documentation are adapted to Couchbase's terminology and feature set.&nbsp; The following words are [reserved](<https://docs.couchbase.com/server/current/analytics/appendix\_1\_keywords.html> "target=\"\_blank\""). &nbsp;

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Couchbase.

&nbsp;

![Image](<lib/Couchbase%20DTD.png>)

&nbsp;

## Indexes ##

An index is a data-structure that provides quick and efficient means to query and access data, that would otherwise require scanning a lot more documents.&nbsp; Couchbase Server provides different types of indexes, as documented [here](<https://docs.couchbase.com/server/current/learn/services-and-indexes/indexes/indexes.html> "target=\"\_blank\""). .

&nbsp;

Hackolade supports the creation, documentation, forward- and reverse-engineering of:

* **Primary:** Provided by the Index Service, this is based on the unique key of every item in a specified bucket. Every primary index is maintained asynchronously. A primary index is intended to be used for simple queries, which have no filters or predicates.&nbsp;
* **Secondary:** Provided by the Index Service, this is based on an attribute within a document. The value associated with the attribute can be of any type: scalar, object, or array.&nbsp; A Secondary Index is frequently referred to as a Global Secondary Index, or GSI. This is the kind of index used most frequently in Couchbase Server, for queries performed with the N1QL query-language.

&nbsp;

## Views (TBA) ##

Views and indexes support querying data in Couchbase Server.&nbsp; Querying of Couchbase data is accomplished via the following:

* MapReduce views accessed via the View API.
* Spatial views accessed via the Spatial View API.
* N1QL queries with Global Secondary Indexes (GSI) and MapReduce views.

There are a number of differences between views and GSIs. At a high level, GSIs are built for N1QL queries, which are great for supporting interactive applications that require fast response times. Views, on the other hand, provide sophisticated user defined functions to provide great flexibility in indexing. Views can support complex interactive reporting queries with a pre-calculated result.

&nbsp;

More information on views can be found [here](<https://docs.couchbase.com/server/current/learn/views/views-intro.html> "target=\"\_blank\"").

## Reverse-Engineering ##

The connection is established using a connection string including (IP) address and port (typically 8091), and authentication using username/password if applicable.

&nbsp;

The Hackolade process for reverse-engineering of Couchbase databases is different depending on the Couchbase version.&nbsp; For versions 3.x, the indexed views are queried via the REST API.&nbsp; Starting with version 4.0, Hackolade uses [N1QL](<https://docs.couchbase.com/server/current/learn/data/n1ql-versus-sql.html> "target=\"\_blank\"") syntax to perform the statistical sampling followed by the schema inference.&nbsp; And starting with version 4.5 Enterprise edition, Hackolade leverages the [INFER](<https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/infer.html> "target=\"\_blank\"") statement.

&nbsp;

For more information on Couchbase in general, please consult the [website](<http://www.couchbase.com/> "target=\"\_blank\"").

&nbsp;

## Forward-Engineering ##

For those developing Node.js applications on top of a Couchbase database, you may want to leverage the object document mapper (ODM) [Ottoman](<https://github.com/couchbaselabs/node-ottoman> "target=\"\_blank\"") that allows you build what your object model would look like, then auto-generate all the boilerplate logic that goes with it.&nbsp; Hackolade dynamically generates the Ottoman script based on model attributes and constraints.&nbsp; More information on Ottoman [here](<https://blog.couchbase.com/easily-develop-node-js-and-couchbase-apps-with-ottoman/> "target=\"\_blank\"") and [here](<https://blog.couchbase.com/firstapp-couchbase-nodejs-ottoman/> "target=\"\_blank\"").

&nbsp;

We provide a sort of "forward-engineering by example", with an automatic JSON data sample generation.&nbsp; The script also includes the creation of indexes, and it can be applied to the database instance, provided that appropriate credentials are granted to the user.&nbsp; If the specified bucket does not exist, we attempt to create it.

&nbsp;

![Image](<lib/Couchbase%20forward-engineering%20script.png>)

&nbsp;

&nbsp;

A possible alternative could be to implement soft validation using the Eventing feature, which has been available since release 5.5.

 

With Eventing, one defines a javascript function that gets called with every document mutation. That function can do any of the following: 

* log output to a data file
* create documents in a separate bucket
* run N1QL commands

 

An Eventing function can be deployed, then un-deployed once it has processed all the current documents, so one could get a snapshot of whether the current document set matches the established schema. It need not run all the time, unless schema validation is terribly important.

 

Also, one can deploy the Eventing service on additional nodes so that Eventing does not impact the performance of the rest of the cluster. Fitting with the philosophy of Couchbase, it provides \***eventual**\* validation.

&nbsp;

/////////////////////////////////////////////////////////////////////////////////////////////////

// SCHEMA VALIDATION FUNCTION

//

// This function will monitor the documents in a bucket and send errors to the output file and

// target bucket when a new or modified document doesn't match any of the provided schemas.

//

// This is a very simple implementation, supporting only name/type validation. It does not yet

// support any value validation (e.g., enumerations, array length constraints, string pattern

// matching, etc. etc.).

//

// You must specify an array of one or more valid schemas in the "get\_top\_level\_schema()" function

// below.

//

// You may also specify two options in the functions immediately below.

//

// The first indicates whether to raise an error when fields are seen that do not exist in the schema.

//

// The second relates to schemas generated by Couchbase's INFER statement, where properties have a "%docs"

// field that indicates in what percentage of documents a property was seen. When set to 'true', this

// option treats properties with "%docs": 100 as required.

//

// Disclaimer: THIS SAMPLE CODE IS PROVIDED "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING

// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.

/////////////////////////////////////////////////////////////////////////////////////////////////

 

function test\_for\_extra\_fields() {return(false);} // should we raise an error when seeing fields not in the schema?

function treat\_100pc\_as\_required() {return(true);} // are fields listed as %docs: 100 in the INFER schema required?

 

function OnUpdate(doc, meta) {

    var errors = \[\];

    log("doc",doc);

 

    try {

        // sanity check, make sure we have some schemas to test with

        var top\_level\_schema = get\_top\_level\_schema();

        if (\!top\_level\_schema \|\| \!top\_level\_schema.length) {

            log("Invalid schema, unable to validate document: " + JSON.stringify(top\_level\_schema));

            return;

        }

 

        // loop through the schema flavors in the top level schema and see if

        // we can find a match for the document

        var matched = false;

        for (var i=0; i\<top\_level\_schema.length; i++) {

            var res = validateDocAgainstSchema(doc,top\_level\_schema\[i\],"");

            if (res \!= null) {

                errors.push({"schema": i + top\_level\_schema\[i\].Flavor, error: res});

            }

            else {

                matched = true;

                break;

            }

        }

 

        if (\!matched) {

            log("no match")

            target\[meta.id\] = errors;

        }

    } catch (e)

    {

        log("Error checking schema.",e);

    }

   

}

 

// not used

function OnDelete(meta) {

}

 

/////////////////////////////////////////////////////////////////////////////////////////////////

//

// validateDocAgainstSchema

//

// given a document and a json-schema structure, determine if the

// document matches the scehma. This function is compatible with

// the extensions to json-schema used by the N1QL INFER command,

// though it does not require them.

//

 

function validateDocAgainstSchema(doc,schema,path) {

    // sanity checks

    if (doc == null)

        return(\[{"generalError": "doc is null"}\]);

    else if (schema == null)

        return(\[{"generalError": "schema is null"}\]);

 

    // it's possible for docs to be primitive values, or objects. Do basic type checking

    // we need two tests for string types

    else if (typeof doc == "string" \|\| doc instanceof String) {

        if (schema.type \!= "string")

            return(\[{"typeError": "For path: " + path + ", schema specified type: " + schema.type + ", found string" }\]);

    }

 

    // typeof will tell us the name of the type, except for arrays

    else if (schema.type \!= typeof doc \&\& schema.type \!= "array")

        return(\[{"typeError": "For path: " + path +", schema specified type: " + schema.type +

          ", found type: " + typeof doc}\]);

 

    else if (schema.type == "array" \&\& \!Array.isArray(doc))

      return(\[{"typeError": "For path: " + path + ", schema specified type: array, found type: " + typeof doc}\]);

 

    // if we have an array, each element of the array must match one of the types in the "items" list of schemas

    if (schema.type == "array") {

      var schemas = schema.items;

      if (\!Array.isArray(schemas)) // simplify by making sure items is an array

        schemas = \[schemas\];

 

      var failedItems = \[\];

 

      // check each element in the array

      for (var item=0; item \< doc.length; item++) {

        var itemMatched = false;

        for (var subschema = 0; subschema \< schemas.length; subschema++)

          if (\!validateDocAgainstSchema(doc\[item\],schemas\[subschema\])) {

            itemMatched = true; // no errors, we found a match

            break;

          }

 

        if (\!itemMatched)

          failedItems.push(doc\[item\]);

      }

 

      if (failedItems.length \> 0)

        return(\[{"typeError": "For path: " + path + ", some array elements didn't match any schema for that array.",

                 "invalidElements": failedItems, "schemas": schema.items}\]);

    }

 

 

    // if we have an object, each field in the doc must match a property in the schema, and vice versa

    else if (schema.type == "object") {

      var missing\_fields = \[\], extra\_fields = \[\], bad\_type\_fields = \[\];

 

      // make sure all the document's fields are in the schema

      if (test\_for\_extra\_fields()) for (var field in doc)

        if (\!schema.properties.hasOwnProperty(field)) // field not found in schema

          extra\_fields.push(path + field);

 

      // now check the fields in the schema, test for existence, type match

      for (var field in schema.properties) {

        // don't count missing fields that only appear is some documents, i.e., %docs \< 100

        var required = false;

        if ((schema.required \&\& schema.required.indexOf(field) \>= 0) \|\|

            (treat\_100pc\_as\_required() \&\& schema.properties\[field\].hasOwnProperty('%docs') \&\& schema.properties\[field\]\['%docs'\] == 100))

          required = true;

        if (\!doc.hasOwnProperty(field) \&\& required)

          missing\_fields.push(path + field);

        else if (doc.hasOwnProperty(field)){

          var type\_check = validateDocAgainstSchema(doc\[field\],schema.properties\[field\],field + ".");

          if (type\_check)

            bad\_type\_fields = type\_check;

        }

      }

 

      if (missing\_fields.length \|\| extra\_fields.length \|\| bad\_type\_fields.length) {

        var errors = \[\];

        if (missing\_fields.length)

          errors.push({"path:": path, "missing fields: ": missing\_fields});

        if (extra\_fields.length)

          errors.push({"path:": path, "extra fields: ": extra\_fields});

        if (bad\_type\_fields.length)

          errors.push.apply(errors,bad\_type\_fields);

 

        return(errors);

      }

 

    }

 

    return(null); // no problems if we get this far

}

 

 

/////////////////////////////////////////////////////////////////////////////////////////////////

//

// get\_top\_level\_schema

//

// This function returns an array of one or more json-schema's against which all

// documents will be validated.

//

 

function get\_top\_level\_schema() {

  return(

  \[

    {

      "#docs": 814,

      "$schema": "http://json-schema.org/schema#",

      "Flavor": "\`type\` = \\"beer\\", \`upc\` = 0",

      "properties": {

        "abv": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            0,

            5,

            6,

            6.25,

            8

          \],

          "type": "number"

        },

        "brewery\_id": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            "anchor\_brewing",

            "anderson\_valley\_brewing",

            "budjovick\_mansk\_pivovar",

            "magic\_hat",

            "wild\_duck\_brewing"

          \],

          "type": "string"

        },

        "category": {

          "#docs": 616,

          "%docs": 75.67,

          "samples": \[

            "British Ale",

            "German Lager",

            "North American Ale",

            "North American Lager",

            "Other Style"

          \],

          "type": "string"

        },

        "description": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            "Stiegl Weizengold. It has 12o ...",

            "An Ale Brewed with Honey\\r\\nOur ...",

            "Help us celebrate American Ind...",

            "Mogul is a complex blend of 5 ...",

            ""

          \],

          "type": "string"

        },

        "ibu": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            0,

            36,

            55

          \],

          "type": "number"

        },

        "name": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            "Braggot",

            "Imperial Sasquatch",

            "Our Special Ale 1992",

            "Samson Crystal Lager Beer",

            "Winter Solstice Seasonal Ale 2..."

          \],

          "type": "string"

        },

        "srm": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            0,

            6

          \],

          "type": "number"

        },

        "style": {

          "#docs": 616,

          "%docs": 75.67,

          "samples": \[

            "American-Style Amber/Red Ale",

            "American-Style Lager",

            "German-Style Pilsener",

            "Light American Wheat Ale or La...",

            "Old Ale"

          \],

          "type": "string"

        },

        "type": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            "beer"

          \],

          "type": "string"

        },

        "upc": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            0

          \],

          "type": "number"

        },

        "updated": {

          "#docs": 814,

          "%docs": 100,

          "samples": \[

            "2010-07-22 20:00:20",

            "2010-12-20 15:32:12",

            "2011-04-17 12:25:31",

            "2011-08-15 11:53:48",

            "2011-08-15 11:56:18"

          \],

          "type": "string"

        }

      },

      "type": "object"

    }

  \]

  );

}


***
_Created with the Personal Edition of HelpNDoc: [Free help authoring tool](<https://www.helpndoc.com/help-authoring-tool>)_
