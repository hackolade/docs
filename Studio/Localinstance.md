# Local instance

In addition to the Amazon DynamoDB web service, AWS provides a downloadable version of DynamoDB that can be run locally.&nbsp; This edition of DynamoDB lets you write applications without accessing the actual Amazon DynamoDB web service.&nbsp; Instead, the database is self-contained on your computer.

&nbsp;

This local version of DynamoDB can help you save on provisional throughput, data storage, and data transfer fees.&nbsp; In addition, you do not need to have an Internet connection while your are developing your application. &nbsp;

&nbsp;

Assuming that have downloaded from [https://aws.amazon.com/blogs/aws/dynamodb-local-for-desktop-development/](<https://aws.amazon.com/blogs/aws/dynamodb-local-for-desktop-development/> "target=\"\_blank\"") and are running the database locally with the command java -Djava.library.path=./DynamoDBLocal\_lib -jar DynamoDBLocal.jar -sharedDb , you can access the database from a browser at [http://localhost:8000/shell/](<http://localhost:8000/shell/> "target=\"\_blank\"") .&nbsp; Make sure you're able to access your DynamoDB, and have created tables and data before you proceed.

&nbsp;

For a local instance, you don't need to fill in information in the Authentication tab.&nbsp; All you need is to give a name to the connection (e.g.; 'local') and check the option 'use local DynamoDB'.

If you local instance is installed on your computer and using port 8000, you should not modify the suggested parameters.

&nbsp;

![Image](<lib/Rev-Engineering%20-%20DynamoDB%20connection%20local.png>)

