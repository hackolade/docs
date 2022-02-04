# Cookie name-value pair

In some cases, it is necessary to cookie name-value pair to be inserted in the HTTP header, for example to address BlueCoat SSL inspection re-encrypting with an internal certificate.

&nbsp;

The HTTP cookie entry is passed in the HTTP request header when using the REST API to communicate with the Confluent Schema Registry.

&nbsp;

The Advanced tab allows you to enter name-value pairs in the form of \<cookie-name\>=\<cookie-value\> according to [MDN WebDocs](<https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cookie#syntax> "target=\"\_blank\"") syntax. Pairs in the list are separated by a semicolon and a space ('; ').&nbsp;

&nbsp;

![Confluent advanced cookie name-value](<lib/Confluent%20advanced%20cookie%20name-value.png>)

&nbsp;

If you wish to reference an environment variable, you may do so, wrapped in double braces:

&nbsp;

![Confluent advanced cookie environment var](<lib/Confluent%20advanced%20cookie%20environment%20var.png>)

&nbsp;

&nbsp;

