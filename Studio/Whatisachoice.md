# What is a choice?

Each choice attribute contains an array, with each attribute of the array representing content that will be matched against. The choice of “allOf”, “anyOf”, “oneOf”, or “noneOf” determines how the validation processor will treat the results of the matches:

* allOf requires that all attributes in the array are matched successfully

![Choices - allOf](<lib/Choices - allOf.png>)

* anyOf requires one or more of the attributes in the array to be matched successfully

![Choices - anyOf](<lib/Choices - anyOf.png>)

* oneOf requires one, and only one, of the attributes in the array to match successfully

![Choices - oneOf](<lib/Choices - oneOf.png>)

* noneOf requires that no attribute in the array is matched successfully

![Choices - noneOf](<lib/Choices - noneOf.png>)

Schema definitions can use “allOf”, “anyOf”, “oneOf”, and “noneOf” individually or in combination, providing significant flexibility for defining attributes that have complex definitions or contextual relationships.  These choices apply both to fields and to field properties.  In both cases, the only possible attribute of Choice is a Subschema.

