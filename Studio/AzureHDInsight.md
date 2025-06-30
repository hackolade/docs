# Azure HDInsight

The Microsoft Azure cloud-based service provides support for Hive in the HDInsight.&nbsp; The HDInsight resource is controlled by the Ambari interface.&nbsp; It is used to adjust the Azure HDInsight configuration.

&nbsp;

![Hive - HDInsight connection](<lib/Hive - HDInsight connection.png>)

&nbsp;

## &#49;) Using Plain SASL authentication type

&nbsp;

Go to the Hive section, open the "Configs" tab then the "Advanced" tab. There user can find the option "hive.server2.thrift.http.path". The default value must be changed from "/", to "/hive2".

&nbsp;

Select the authentication type: None (Plain SASL):

![Hive - HDInsight authentication](<lib/Hive - HDInsight authentication.png>)

&nbsp;

&nbsp;

Then transport mode http with the HTTP path corresponding to the default value set in HDInsight \> Configs \> Advanced

![Hive - HDInsight options](<lib/Hive - HDInsight options.png>)

&nbsp;

Finally, set SSL type to HTTPs:

![Hive - HDInsight SSL](<lib/Hive - HDInsight SSL.png>)

## &#50;) Using LDAP

&nbsp;

Select the authentication type: LDAP

&nbsp;

![Hive - HDInsight - LDAP auth](<lib/Hive - HDInsight - LDAP auth.png>)

&nbsp;

Then select the transport mode corresponding to your HDInsight setup: "binary" of "http".If "http",&nbsp;

![Hive - HDInsight - http transport](<lib/Hive - HDInsight - http transport.png>)

&nbsp;

