---
description: Hackolade Studio generates DynamoDB CreateTable and ConditionExpression scripts from model attributes and constraints.
seoTitle: Generate DynamoDB CreateTable scripts
image: lib/DynamoDB apply to instance.png
---
# DynamoDB scripts

Hackolade dynamically generates [CreateTable](<http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_CreateTable.html> "target=\"_blank\"") and [ConditionExpression](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Expressions.SpecifyingConditions.html> "target=\"_blank\"") scripts based on model attributes and constraints. These can be applied directly to the DynamoDB instance.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![DynamoDB apply to instance](<lib/DynamoDB apply to instance.png>)
