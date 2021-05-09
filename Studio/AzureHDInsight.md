# Azure HDInsight

The Microsoft Azure cloud-based service provides support for Hive in the HDInsight.&nbsp; The HDInsight resource is controlled by the Ambari interface.&nbsp; It is used to adjust the Azure HDInsight configuration.

&nbsp;

![Image](<lib/Hive%20-%20HDInsight%20connection.png>)

&nbsp;

## &#49;) Using Plain SASL authentication type ##

&nbsp;

Go to the Hive section, open the "Configs" tab then the "Advanced" tab. There user can find the option "hive.server2.thrift.http.path". The default value must be changed from "/", to "/hive2".

&nbsp;

Select the authentication type: None (Plain SASL):

![Image](<lib/Hive%20-%20HDInsight%20authentication.png>)

&nbsp;

&nbsp;

Then transport mode http with the HTTP path corresponding to the default value set in HDInsight \> Configs \> Advanced

![Image](<lib/Hive%20-%20HDInsight%20options.png>)

&nbsp;

Finally, set SSL type to HTTPs:

![Image](<lib/Hive%20-%20HDInsight%20SSL.png>)

## &#50;) Using LDAP ##

&nbsp;

Select the authentication type: LDAP

&nbsp;

![Image](<lib/Hive%20-%20HDInsight%20-%20LDAP%20auth.png>)

&nbsp;

Then select the transport mode corresponding to your HDInsight setup: "binary" of "http".If "http",&nbsp;

![Image](<lib/Hive%20-%20HDInsight%20-%20http%20transport.png>)

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Create cross-platform Qt Help files](<https://www.helpndoc.com/feature-tour/create-help-files-for-the-qt-help-framework>)_
