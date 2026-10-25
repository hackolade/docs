# MongoDB Field-Level Encryption

Starting with v4.2, MongoDB provides a field level encryption ("FLE") framework, both server-side and client-side. Applications can encrypt fields in documents *prior* to transmitting data over the wire to the server. Only applications with access to the correct encryption keys can decrypt and read the protected data. Deleting an encryption key renders all data encrypted using that key as permanently unreadable.

&nbsp;

Starting with v5.4.9 of Hackolade Studio, we support MongoDB FLE functionality, which is also known as [In-Use Encryption](<https://www.mongodb.com/docs/compass/current/in-use-encryption-tutorial/> "target=\"_blank\"").

&nbsp;

> [!NOTE]
> Using Client-Side FLE alongside in-flight and at-rest encryption gives an end-to-end, complementary approach in building applications that provide a defense-in-depth security posture to address different threat models.

&nbsp;

- In-flight encryption protects all data traversing the network, but does not encrypt data in-memory or at-rest.
- At-rest encryption protects all stored data, but does not encrypt data in-memory or in-flight.
- With client-side encryption, the most sensitive data never leaves applications in plain text. Fields that are encrypted client-side remain encrypted over the network, as they are being processed in database server memory, and at-rest in storage, backups, and logs.

&nbsp;

As explained in [this MongoDB page](<https://docs.mongodb.com/manual/core/security-client-side-encryption/#std-label-field-level-encryption-algorithms> "target=\"_blank\""), consider the following document:

&nbsp;

```json
{
  "name" : "John Doe",
  "address" : {
    "street" : "1234 Main Street",
    "city" : "MongoDBVille",
    "zip" : 99999
  },
  "phone" : "949-555-1212",
  "ssn" : "123-45-6789"
}
```

&nbsp;

With field-level encryption, sensitive information like the `ssn` and `phone` can be encrypted. Encrypted fields are stored as [`binary data`](<https://docs.mongodb.com/manual/reference/mongodb-extended-json/#mongodb-bsontype-Binary> "target=\"_blank\"") with [subtype 6](<https://github.com/mongodb/specifications/blob/master/source/client-side-encryption/subtype6.rst> "target=\"_blank\"")

&nbsp;

```json
{
  "name" : "John Doe",
  "address" : {
    "street" : "1234 Main Street",
    "city" : "MongoDBVille",
    "zip" : 99999
  },
  "phone" : BinData(6,"U2FsdGVkX1+CGIDGUnGgtS46+c7R5u17SwPDEmzyCbA="),
  "ssn" : BinData(6,"AaloEw285E3AnfjP+r8ph2YCvMI1+rWzpZK97tV6iz0jx")
}
```

&nbsp;

> [!NOTE]
> While MongoDB calls this feature "Field-Level Encryption", the encryption can actually be applied at the collection level as well.

&nbsp;

Watch an [animation](<https://webimages.mongodb.com/_com_assets/cms/FLE-s7oxojve2n-shxql4cyij.gif> "target=\"_blank\"") of the field-level encryption process, along with the following legend of the steps:\
![MongoDB Field-Level Encryption process legend](<lib/MongoDB Field-Level Encryption process legend.png>)

&nbsp;

## Enforcement strategies

Either server-side or client-side encryption can be used, or both. It is a good idea to have both server-side and client-side FLE because they complement each other. In case of a legacy client, or a misconfigured client, server-side FLE eliminates the possibility that any plain text is used to insert or update a document, when it was meant to be encrypted. Conversely, a single person with access to the database does not have the power to disconnect field-level encryption if it is also implemented client-side.

&nbsp;

The configuration server-side leverages the familiar [$jsonschema validator](<https://docs.mongodb.com/manual/core/schema-validation/> "target=\"_blank\"") to declare the encryption rules, for example for the `phone` and `ssn` fields below:

&nbsp;

```javascript
db.runCommand({
    "collMod": "employee",
    "validator": {
        "$jsonSchema": {
            "bsonType": "object",
            "title": "employee",
            "properties": {
                "_id": { "bsonType": "objectId" },
                "name": { "bsonType": "string" },
                "address": {
                    "bsonType": "object",
                    "properties": {
                        "street": { "bsonType": "string" },
                        "city": { "bsonType": "string" },
                        "zip": { "bsonType": "int"
                        }
                    },
                    "additionalProperties": false
                },
                "phone": {
                    "encrypt" : {
                        "keyId" : [UUID("e114f7ad-ad7a-4a68-81a7-ebcb9ea0953a")],
                        "algorithm" : "AEAD_AES_256_CBC_HMAC_SHA_512-Random",
                        "bsonType": "string"
                    }
                },
                "ssn": {
                   encrypt" : {
                        "keyId" : [UUID("33408ee9-e499-43f9-89fe-5f8533870617")],
                        "algorithm" : "AEAD_AES_256_CBC_HMAC_SHA_512-Deterministic",
                        "bsonType": "string"
                    }
                }
            },
            "additionalProperties": false
        }
    },
    "validationLevel": "off",
    "validationAction": "warn"
});
```

&nbsp;

MongoDB also supports two methods of client-side field level encryption:

- Automatic encryption of fields: applications must create a database connection object using the [`Mongo()`](<https://docs.mongodb.com/manual/reference/method/Mongo/#connect-to-a-mongodb-cluster-with-automatic-client-side-encryption-enabled> "target=\"_blank\"") constructor with the automatic encryption configuration settings. The configuration settings must include automatic encryption rules using a strict subset of the $jsonschema validator (same as the server-side encryption described above.) Applications do not have to modify code associated with the read/write operation. See [Automatic Encryption Rules](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#std-label-field-level-encryption-json-schema> "target=\"_blank\"") for complete documentation on automatic encryption rules.
- Explicit (manual) encryption of fields: applications are responsible for selecting the appropriate data encryption key for encryption/decryption on a per-operation basis. The connection is also established using the [`Mongo()`](<https://docs.mongodb.com/manual/reference/method/Mongo/#connect-to-a-mongodb-cluster-with-client-side-encryption-enabled> "target=\"_blank\"") constructor, but without declaring a $jsonschema validator. For more information, see [this page](<https://docs.mongodb.com/manual/core/security-explicit-client-side-encryption/> "target=\"_blank\"").\
  In theory this method should not affect Hackolade Studio from a data modeling perspective. But when performing reverse-engineering, we'll be encountering encrypted fields not declared in the $jsonschema validator.

&nbsp;

> [!WARNING]
> The automatic feature of field level encryption is only available in MongoDB Enterprise 4.2 or later, and MongoDB Atlas 4.2 or later clusters. Most of our major customers are on Enterprise or Atlas.

&nbsp;

<table>
<colgroup><col style="width:25%"><col style="width:25%"><col style="width:25%"><col style="width:25%"></colgroup>
<thead>
<tr>
<th></th>
<th>Community</th>
<th>Enterprise</th>
<th>Atlas</th>
</tr>
</thead>
<tbody>
<tr>
<td>Automatic encryption</td>
<td>--</td>
<td>X</td>
<td>X</td>
</tr>
<tr>
<td>Explicit (manual) encryption</td>
<td>X</td>
<td>X</td>
<td>X</td>
</tr>
</tbody>
</table>

&nbsp;

## Encryptions algorithms

MongoDB client-side field level encryption uses the encrypt-then-MAC approach combined with either a deterministic or random initialization vector to encrypt field values. MongoDB *only* supports the [AEAD](<https://en.wikipedia.org/wiki/Authenticated_encryption#Authenticated_encryption_with_associated_data_(AEAD)> "target=\"_blank\"") AES-256-CBC encryption algorithm with HMAC-SHA-512 MAC.

- deterministic: gives the same value every time the data is encrypted. While deterministic encryption provides greater support for read operations, encrypted data with low cardinality is susceptible to frequency analysis recovery.
  - supports direct match (equality) against encrypted fields
  - uses indexes to provide efficient data access
  - does not support the more complex queries (ranges, aggregations) directly against encrypted fields
- randomized: gives a different value every time the data is encrypted. While randomized encryption provides the strongest guarantees of data confidentiality, it also prevents support for any read operations which must operate on the encrypted field to evaluate the query.
  - strongest level of protection
  - prevents direct match (equality) queries against encrypted fields

&nbsp;

> [!NOTE]
> Randomized encryption also supports encrypting entire objects or arrays. While this protects all fields nested under those fields, it also prevents querying against those nested fields.

&nbsp;

**More info:** For sensitive fields that *are* used in read operations, applications must use Deterministic Encryption for improved read support on encrypted fields.\
For sensitive fields that are *not* used in read operations, applications may use Randomized Encryption for improved protection.\
More advanced queries should be run on unencrypted fields.

&nbsp;

## $jsonschema validator syntax

### [`encrypt` Schema Keyword](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#encrypt-schema-keyword> "target=\"_blank\"")

The `encrypt` object can contain **only** the following fields:

- [`keyId`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt.keyId> "target=\"_blank\"")`:` *Array of single UUID.* The UUID of the data encryption key to use for encrypting field values. The UUID is a BSON [binary data](<http://bsonspec.org/spec.html> "target=\"_blank\"") element of subtype `4`.
- [`algorithm`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt.algorithm> "target=\"_blank\"")`:` Indicates which encryption algorithm to use when encrypting values of `<fieldName>`. Supports the algorithms:
  - `AEAD_AES_256_CBC_HMAC_SHA_512-Random`
  - `AEAD_AES_256_CBC_HMAC_SHA_512-Deterministic`
- [`bsonType`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt.bsonType> "target=\"_blank\"")

&nbsp;

> [!WARNING]
> - if the algorithm is **deterministic**, then:
>   - `bsonType` must specify a **single** value -- multiple data types are NOT allowed
>   - `bsonType` does **not** support any of the following BSON types:
>     - `double`
>     - `decimal128`
>     - `bool`
>     - `object`
>     - `array`
>     - `javascriptWithScope`
>     - `minKey`
>     - `maxKey`
>     - `null`
>     - `undefined`
> - if the algorithm is **random**, then:
>   - `bsonType` may specify an array of supported bson types -- multiple data types are allowed
>   - for fields with `bsonType` of `array` or `object`, the client encrypts the *entire* array or object and not their individual elements.
>   - `bsonType` does **not** support any of the following BSON types:
>     - `minKey`
>     - `maxKey`
>     - `null`
>     - `undefined`

&nbsp;

- `encrypt` cannot have any sibling fields in the `<fieldName>` object. `encrypt` must be the **only** child of the `<fieldName>` object. -- all other constraints should ideally be disabled, or at least filtered from the validator
- `encrypt` cannot be specified within any subschema of the `items` or `additionalItems` keywords. Specifically, automatic client-side field level encryption does not support encrypting individual elements of an array.

&nbsp;

```json
"phone": {
    "encrypt" : {
        "keyId" : [UUID("e114f7ad-ad7a-4a68-81a7-ebcb9ea0953a")],
        "algorithm" : "AEAD_AES_256_CBC_HMAC_SHA_512-Random",
        "bsonType": "string"
    }
},
```

&nbsp;

### [`encryptMetadata` Schema Keyword](<https://www.mongodb.com/docs/manual/reference/security-client-side-automatic-json-schema/#encryptmetadata-schema-keyword> "target=\"_blank\"")

> [!NOTE]
> Only at collection level (root object), and optionally for objects inside a collection

&nbsp;

`encryptMetadata` defines encryption options which an [`encrypt`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt> "target=\"_blank\"") object nested in the sibling `properties` may inherit. If an [`encrypt`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt> "target=\"_blank\"") in a nested field is missing an option required to support encryption, `mongocryptd` searches the entire tree of parent objects to locate an [`encryptMetadata`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encryptMetadata> "target=\"_blank\"") object that specifies the missing. option.

&nbsp;

`encryptMetadata` must be specified in subschemas with `bsonType: "object"`. `encryptMetadata` cannot be specified to any subschema of the `items` or `additionalItems` keywords. Specifically, automatic client-side field level encryption does not support encrypting individual elements of an array.

&nbsp;

The `encryptMetadata` object can contain ***only*** the following fields:

- [`keyId`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt.keyId> "target=\"_blank\"")`:` *Array of single UUID.* The UUID of the data encryption key to use for encrypting field values. The UUID is a BSON [binary data](<http://bsonspec.org/spec.html> "target=\"_blank\"") element of subtype `4`.
- [`algorithm`](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#mongodb-autoencryptkeyword-autoencryptkeyword.encrypt.algorithm> "target=\"_blank\"")`:` Indicates which encryption algorithm to use when encrypting values of `<fieldName>`. Supports the algorithms:
  - `AEAD_AES_256_CBC_HMAC_SHA_512-Random`
  - `AEAD_AES_256_CBC_HMAC_SHA_512-Deterministic`

&nbsp;

Including any other field to the `encrypt` object results in errors when issuing automatically encrypted read or write operations.

&nbsp;

```javascript
db.runCommand({
    "collMod": "employee",
    "validator": {
        "$jsonSchema": {
            "title": "employee",
            "bsonType": "object",
            "encryptMetadata" : {
                "keyId" : [UUID("6c512f5e-09bc-434f-b6db-c42eee30c6b1")],
                "algorithm" : "AEAD_AES_256_CBC_HMAC_SHA_512-Deterministic"
            },
            "properties": {
                "_id": { "bsonType": "objectId" },
                "name": { "bsonType": "string" },
                "address": {
                    "bsonType": "object",
                    "properties": {
                        "street": { "bsonType": "string" },
                        "city": { "bsonType": "string" },
                        "zip": { "bsonType": "int"
                        }
                    },
                    "additionalProperties": false
                },
                "phone": { "bsonType": "string" },
                "ssn": { "bsonType": "string" }
            },
            "additionalProperties": false
        }
    },
    "validationLevel": "off",
    "validationAction": "warn"
});
```

&nbsp;

> [!NOTE]
> The structure is slightly different than for `encrypt`, with `"bsonType": "object",` being **outside** the `encryptMetadata` structure.

&nbsp;

See detailed examples [here](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#examples> "target=\"_blank\"") on how to encrypt multiple fields with [individual](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#std-label-field-level-encryption-auto-encrypt-multiple-fields> "target=\"_blank\"") `encrypt`, or with `encryptMetadata` [inheritance](<https://docs.mongodb.com/manual/reference/security-client-side-automatic-json-schema/#std-label-field-level-encryption-auto-encrypt-multiple-fields-inheritance> "target=\"_blank\"").

&nbsp;

> [!NOTE]
> In an object that had `encryptMetadata`for inheritance, it is possible for a nested field to have its own encryption that overrides the parent object `encryptMetadata`. This is to allow a stricter random algorithm in a nested field than the parent, or a different `keyId`.

&nbsp;

## Forward-Engineering

### JSON Data sample

The encrypted field appears encrypted in the JSON sample, specifically with random [`binary data`](<https://docs.mongodb.com/manual/reference/mongodb-extended-json/#mongodb-bsontype-Binary> "target=\"_blank\"") with [subtype 6](<https://github.com/mongodb/specifications/blob/master/source/client-side-encryption/subtype6.rst> "target=\"_blank\""), e.g; BinData(6,"U2FsdGVkX1+CGIDGUnGgtS46+c7R5u17SwPDEmzyCbA="). In the case of objects with inheritance, the object must appear, but each nested field should be encrypted with a sample in random [`binary data`](<https://docs.mongodb.com/manual/reference/mongodb-extended-json/#mongodb-bsontype-Binary> "target=\"_blank\"") with [subtype 6](<https://github.com/mongodb/specifications/blob/master/source/client-side-encryption/subtype6.rst> "target=\"_blank\"").

&nbsp;

### MongoDB script (both individual collection tab and model tab)

The $jsonschema validator is enriched:

- if encryption is enabled AND explicit (manual) is disabled
- taking into account the difference in structure
  - if `encrypt`, then create structure with `bsonType`, `keyId`, and `algorithm`
  - if `encryptMetadata`, then create structure with `keyId`and `algorithm`

&nbsp;

> [!NOTE]
> That the `keyId` and/or `algorithm` properties can be empty for a given field that has been flagged for encryption, but only if there's an `encryptMetadata` higher in the object hierarchy. We should probably add this rule to the MongoDB script linter, rather than creating PP rules?

&nbsp;

## Reverse-Engineering

When performing reverse-engineering, the usual process is to fetch the $jsonschema validator script, then to go through the sampling and schema inference process.\
If the $jsonschema validator includes the `encrypt` and/or `encryptMetadata` keywords, the process populates the collection and field properties accordingly.

&nbsp;

If during schema inference, we encounter a field with [`binary data`](<https://docs.mongodb.com/manual/reference/mongodb-extended-json/#mongodb-bsontype-Binary> "target=\"_blank\"") with [subtype 6](<https://github.com/mongodb/specifications/blob/master/source/client-side-encryption/subtype6.rst> "target=\"_blank\"") that was not identified as encrypted in the $jsonschema validator (or there was not $jsonschema validator), we can assume that there was explicit (manual) encryption.

&nbsp;

But for this process to work as described above, it is necessary to provide the proper parameters in Connections Settings. In [this page](ConnecttoaMongoDBinstance.md), you will find the parameters required for the application to infer the data type of encrypted fields as well as all the necessary metadata.\
Failing to do so will show every encrypted field with a binary data type:\
![MongoDB FLE reverse-engineering without param](<lib/MongoDB FLE reverse-engineering without param.png>)

&nbsp;

instead of the actual data type:\
![MongoDB FLE reverse-engineering with params](<lib/MongoDB FLE reverse-engineering with params.png>)

&nbsp;

Consult this MongoDB [field-level encryption guide](<https://www.mongodb.com/docs/drivers/security/client-side-field-level-encryption-guide/> "target=\"_blank\"") for more details.
