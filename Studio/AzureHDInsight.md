---
description: Configure Azure HDInsight and its HTTP transport path so Hackolade Studio can connect to Hive for reverse-engineering.
seoTitle: Connect to Hive on Azure HDInsight
image: lib/Hive - HDInsight authentication.png
---
# Azure HDInsight

The Microsoft Azure cloud-based service provides support for Hive in the HDInsight. The HDInsight resource is controlled by the Ambari interface. It is used to adjust the Azure HDInsight configuration.

![Hive - HDInsight connection](<lib/Hive - HDInsight connection.png>)

## 1) Using Plain SASL authentication type

Go to the Hive section, open the "Configs" tab then the "Advanced" tab. There user can find the option "hive.server2.thrift.http.path". The default value must be changed from "/", to "/hive2".

Select the authentication type: None (Plain SASL):\
![Hive - HDInsight authentication](<lib/Hive - HDInsight authentication.png>)

Then transport mode http with the HTTP path corresponding to the default value set in HDInsight > Configs > Advanced\
![Hive - HDInsight options](<lib/Hive - HDInsight options.png>)

Finally, set SSL type to HTTPs:\
![Hive - HDInsight SSL](<lib/Hive - HDInsight SSL.png>)

## 2) Using LDAP

Select the authentication type: LDAP

![Hive - HDInsight - LDAP auth](<lib/Hive - HDInsight - LDAP auth.png>)

Then select the transport mode corresponding to your HDInsight setup: "binary" of "http".If "http",\
![Hive - HDInsight - http transport](<lib/Hive - HDInsight - http transport.png>)
