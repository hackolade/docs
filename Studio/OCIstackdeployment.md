# OCI stack deployment

A manual deployment of OCI's diverse components could be error-prone and challenging. To simplify this, OCI provides a tool known as [Resource Manager](<https://docs.oracle.com/en-us/iaas/Content/ResourceManager/Concepts/resourcemanager.htm>). This tool facilitates a user-friendly experience by allowing straightforward deployment directly from a UI, significantly reducing complexity and improving usability for customers. &nbsp;

&nbsp;

Under the hood, the OCI Resource Manager uses configuration by [Terraform](<https://developer.hashicorp.com/terraform> "target=\"\_blank\""), a very popular infrastructure-as-code tool to build, change, and version infrastructure safely and efficiently. The OCI Resource Manager lets you define, provision, and manage cloud infrastructure-as-code without having to install or manage Terraform yourself.

&nbsp;

In **OCI Resource Manager**, a [stack](<https://docs.oracle.com/en/cloud/paas/cloud-stack-manager/csmug/oracle-cloud-stack-manager.html> "target=\"\_blank\"") empowers users to automate the provisioning of OCI services as a single unit.&nbsp; It is essentially a **Terraform configuration package** (set of .tf files and variables) that defines a collection of OCI resources.

&nbsp;

Hackolade has open-sourced the Terraform configuration needed to seamlessly create the OCI stack for the Model Hub in their own OCI accounts.&nbsp; The configuration can be scrutinized, if needed, so you can be confident of the security and reliability of the configuration. The configuration is accessible in this GitHub [repository](<https://github.com/hackolade/model-hub-deployment> "target=\"\_blank\"").

&nbsp;

Our stack includes:

* creates and configures all necessary components.
* ensures compatibility and coordination between services.
* streamlines the setup process to avoid manual, error-prone procedures.

&nbsp;

The configuration creates the following components:

\- a dynamic group and a policy to manage permissions

\- an always-free Autonomous JSON database (can be upgraded later to larger instance)

\- both an admin username/password and a schema username and password

\- a container registry including an image with the latest version of the Docker images of the Model Hub

\- OCI functions, including models replication from the configured repositories

\- a Queue and a service connector

\- a key management store for secrets

\- various network resources

\- an API gateway

\- a resource scheduler (checks for the availability of new Docker images, based on a schedule)

\- a logging group

&nbsp;

If you have not done so yet, make sure first that all documented prerequisites have been fulfilled. &nbsp;

&nbsp;

Before we start, let's briefly discuss additional preparation steps, including sizing estimates and naming conventions for the different elements that will be created with this operation...

&nbsp;

## Installation variables

### Naming guidelines

Having a clear **naming convention** in OCI is important because resources are the backbone of governance, access control, and cost tracking. Oracle doesn’t enforce a standard, but many organizations follow conventions that reflect **organization, environment, and purpose**.&nbsp; Choosing the right names is helpful for many different resources.

&nbsp;

A [compartment](<https://docs.oracle.com/en/cloud/foundation/cloud\_architecture/governance/compartments.html> "target=\"\_blank\"") is a **logical container location** you use to organize and isolate OCI resources (like compute instances, VCNs, databases, buckets, etc.). Think of it like a **folder** in a file system, but instead of files, it holds cloud resources.&nbsp; Compartments allow fine-grained access control, so you can grant or restrict groups of users access to specific compartments.&nbsp; They allow to separate workloads (e.g., Prod, Dev, Test) or separate environments (e.g., HR apps vs. eCommerce apps).&nbsp; They allow to tag resources, for example for billing and cost tracking.&nbsp; They help enforce least-privilege access and let you keep unrelated workloads isolated to reduce risk.

&nbsp;

Since compartments are long-lived and organizational, a **clear naming strategy** helps a lot.&nbsp; If you don't already have internal compartments [naming conventions](<https://docs.oracle.com/en/cloud/foundation/cloud\_architecture/governance/naming.html#compute-resources---naming-convention> "target=\"\_blank\""), we suggest to create one that is consistent across your organization.&nbsp; One that reflects your **environment**, **function/team**, organizational unit, shared services, or **region/project, and one that keeps names human-readable** (avoid cryptic codes only admins understand). &nbsp; For example: \[Department\] - \[Application\] - \[Environment\]&nbsp; For simplicity, the Model Hub can be placed in its own compartment.&nbsp; Then, if you need access its resources from other compartments, it will be possible to create a cross-compartment IAM policy to do so. &nbsp;

&nbsp;

[Stack](<https://docs.oracle.com/en/cloud/paas/cloud-stack-manager/csmug/oracle-cloud-stack-manager.html> "target=\"\_blank\"") names should reflect their purpose, environment, and scope.&nbsp; For example: \[Project or App\] - \[Environment\] - \[Layer/Function\] - \[Region (if needed)\].&nbsp; You may want to align with **compartment naming conventions** (so it’s easy to map stacks to their resource location.) &nbsp;

&nbsp;

OCI provides a [tagging framework](<https://docs.oracle.com/en-us/iaas/Content/General/Concepts/resourcetags.htm> "target=\"\_blank\"") that lets you [attach metadata](<https://www.ateam-oracle.com/post/oracle-cloud-infrastructure-tagging-best-practices-enable-mandatory-tagging-for-compartments> "target=\"\_blank\"") to resources.&nbsp; Think of them as flexible labels that travel with your resources.&nbsp; They can be used for cost tracking, ownership and responsibility, automation, lifecycle management, governance, etc.&nbsp; [Tags](<https://docs.oracle.com/en/cloud/foundation/cloud\_architecture/governance/tags.html> "target=\"\_blank\"") can be **free-form (key**-value pairs with no enforced schema), or organization-controlled key-value pairs with predefined namespaces. &nbsp;

&nbsp;

**Warning: t**he database name must begin with an alphabetic character and can contain a maximum of 30 alphanumeric characters. Special characters are not permitted. The database name must be unique in the tenancy.

&nbsp;

### Instance sizing

An OCI Elastic Compute Unit (ECPU) is an abstracted measure of compute resources for the Oracle Autonomous Database to provide a consistent price metric independent of the underlying hardware.&nbsp; ECPUs allow for elastic resource allocation, enabling dynamic adjustments based on workload and contributing to cost savings through features like [elastic pools](<https://www.google.com/search?cs=0\&sca\_esv=00d2b9dd415bfb1f\&sxsrf=AE3TifNX-t1yzBIKc5maFlhJvJBkZN2-2Q:1756205286918\&q=elastic%20pools\&sa=X\&ved=2ahUKEwi00e\_BpqiPAxVw3wIHHfiPBUAQxccNegQIBRAB\&mstk=AUtExfCAUNumP5\_kk2g8cPedK-1WllV0VoQuvGmeclm8R5QVOltfTECszWjwNAC9BgUHsXoKagfEErdWfqM2GqOoizGTNfEZ2G0ZJypyKiVEtw-CjdK4c5uVcGvI5C3Oz\_prfsn8Yur-wXLtjsc9ILCXK\_MM7YwCYBwG\_cRnYEM-LFKCyO86FT8ROqxDTGiBIMqQD7sog4Ymu8-27muKzDeh9kjeL6lrbbElSby9ZzKJIAdWy1ztiF1R-sX5pMjIkS3VDSHUg7k-qo0v19eHp0PvVtqL\&csui=3>).&nbsp; An ECPU is based on the number of cores per hour elastically allocated from a pool of compute and storage servers.  It is not to be confused with an OCPU which is defined as the equivalent of one physical core with hyper-threading enabled.&nbsp; In contrast, an ECPU is not explicitly defined in terms of an amount of physical hardware.&nbsp; By introducing ECPU’s, Oracle is providing a durable pricing metric which is not tied to the exact make, model, or clock speed of the underlying processor.

&nbsp;

The OCI pricing information is provided for information purposes, and only to help with your sizing estimates.&nbsp; The information was taken at the time of writing this documentation from this Oracle [ECPU FAQ document](<https://www.oracle.com/a/ocom/docs/autonomous-database-ecpu-faq.pdf> "target=\"\_blank\""), and may change without notice. **Hackolade is not responsible for OCI pricing.**&nbsp; **Prices listed here are as of the time of writing this article and are subject to change.**&nbsp; **Customers are billed directly by Oracle.&nbsp; Prices below are in US Dollars.**&nbsp; Please refer to the pricing list at [https://www.oracle.com/cloud/price-list/](<https://www.oracle.com/cloud/price-list/> "target=\"\_blank\""))&nbsp; &nbsp;

&nbsp;

Unless you set the number of ECPU to 0 which sets your instance with always-free (but limited) capacity, ECPU databases need to be provisioned with a minimum of 2 ECPUs.&nbsp; At the time of writing this documentation, the prices for ECPU’s are (in US dollars):&nbsp;

\- Autonomous JSON Database: $0.0807 per ECPU per hour (0 ECPUs for always-free tier, or minimum of 2 ECPUs)

\- Autonomous Database Serverless storage for Autonomous Transaction Processing, Autonomous JSON Database, and APEX Service: 1 GB at $0.1156 with 1 GB increment (minimum of 20 GB)

\- Autonomous Transaction Processing: $0.336 per ECPU per hour.&nbsp; Alternatively, Bring-You-Own-License pricing is available with Autonomous Transaction Processing: $0.0807 per ECPU per hour.&nbsp; (Up to 8 ECPU’s may be activated for each supported Processor license of Oracle Database Enterprise Edition and up to 16 ECPU’s for each supported Processor license of Oracle Database Standard Edition)

&nbsp;

We suggest that you start small, then [monitor usage](<OCImonitoringofModelHub.md>), and adjust if necessary.&nbsp; Videos about OCI cost analysis and management are available [here](<https://www.oracle.com/uk/cloud/architecture-center/oci-in-5/#costs> "target=\"\_blank\"").

&nbsp;

### Instance storage

The initial creation of the dat base requires 6.5GB of the minimum 20GB of storage, meaning that more than 13GB remain available for the operations of the Model Hub.&nbsp; It is advised to consider alerts when reaching 75% utilization.&nbsp; Waiting until storage is nearly full (above 85%) can risk service interruption or failed writes, so timely scaling or expansion at 75-80% usage ensures database continuity and smooth operations.&nbsp; 75% of 20MB minus ~7GB, that leaves 8GB for Model Hub operation.

&nbsp;

&nbsp;

## Deploying the Hackolade Model Hub stack on OCI

This infrastructure-as-code deployment is useful for the initial setup.&nbsp; It is run just once to set up a new stack.&nbsp; It cannot be used to update the infrastructure.&nbsp; For updates, an OCI administrator will need to update the stack configuration.

&nbsp;

Log in to your OCI account, the follow these steps:

&nbsp;

### Create a compartment

Use the navigation menu to go to [Identity \& Security \> Identity \> Compartments](<https://cloud.oracle.com/identity/compartments> "target=\"\_blank\"") and click the Create compartment button

![Hub OCI compartments](<lib/Hub OCI compartments.png>)

&nbsp;

Then provide a name and description, and choose the appropriate parent compartment, typically the root compartment.

&nbsp;

&nbsp;

![Hub OCI create compartment](<lib/Hub OCI create compartment.png>)

&nbsp;

&nbsp;

### Create a configuration source provider

Use the navigation menu to go to [Developer Servcies \> Resource Manager \> Configuration source providers](<https://cloud.oracle.com/resourcemanager/configSourceProviders> "target=\"\_blank\"").&nbsp; Make sure to select the correct compartment in the dropdown list on the left:

![Hub OCI select compartment](<lib/Hub OCI select compartment.png>)

&nbsp;

Then click the button Create configuration source provider:

![Hub OCI source provider configs](<lib/Hub OCI source provider configs.png>)

&nbsp;

&nbsp;

The server URL is [https://github.com/hackolade-public/](<https://github.com/hackolade-public/> "target=\"\_blank\"") and the Personal access token will have been given to you by the Hackolade Helpdesk at [support@hackolade.com](<mailto:support@hackolade.com?subject=Personal%20access%20token%20for%20Hub%20deployment%20on%20OCI%20>)

&nbsp;

![Hub OCI create source provider config](<lib/Hub OCI create source provider config.png>)

&nbsp;

Once created, it is useful to validate the connection before proceeding, to ensure that the setup is correct.&nbsp; &nbsp;

![Hub OCI source provider config details](<lib/Hub OCI source provider config details.png>)

&nbsp;

Click the link Validate connection and make sure to get the proper acknowledgment:

![Hub OCI source provider config validation](<lib/Hub OCI source provider config validation.png>)

&nbsp;

&nbsp;

&nbsp;

### Create a stack

Use the navigation menu to go to [Developer Services \> Resource Manager \> Stacks](<https://cloud.oracle.com/resourcemanager/stacks> "target=\"\_blank\"") and make sure to select the appropriate region, typically the one closest to the majority of your Model Hub users.&nbsp; It is possible, but not covered here, to replicate regions for higher availability.

&nbsp;

Make sure to select the proper compartment in the dropdown list on the left:

&nbsp;

![Hub OCI stacks](<lib/Hub OCI stacks.png>)

&nbsp;

&nbsp;

Click the button Create stack and select the radio button for Source code control system.&nbsp; Select Github, the source provider config created above in the selected compartment, then select the repository we provide and the main branch:

&nbsp;

![OCI Hub create stack part 1](<lib/OCI Hub create stack part 1.png>)

&nbsp;

&nbsp;

Optionally provide a name and decription, then ensure that the stack is created in the correct compartment, then click Next:

&nbsp;

![OCI Hub create stack part 2](<lib/OCI Hub create stack part 2.png>)

&nbsp;

&nbsp;

&nbsp;

In the next scree, you must provide values for the stack variables.&nbsp; Be careful to enter the proper values according to guidelines below, and document them:

&nbsp;

The deployed stack comes with the variables below.&nbsp; They are sorted in alphabetical order:

\- **compartment\_ocid:** do not change this value. It is the OCID of the parent compartment

\- **hub\_db\_admin password:** password of the **admin** user for the hub\_db\_name instance of the autonomous database

\- **hub\_db\_ecpu\_count:**&nbsp; number of ECPUs provisioned for this new database. If set to 0, it will create an always-free database

\- **hub\_db\_name:** name of the Hub database to be created.&nbsp; The name must begin with an alphabetic character and can contain a maximum of 30 alphanumeric characters. Special characters are not permitted. The database name must be unique in the tenancy.&nbsp;

\- **hub\_db\_schema\_password:** password of the schema for the hub\_db\_name instance the autonomous database

\- **hub\_db\_schema\_username:** user that will be created in the database. It's in this user schema that the Hub database schema will be deployed. &nbsp; You must communicate this database schema username to Hackolade Helpdesk, as detailed in [these instructions](<Parameterstoconnectfront-endandb.md>).

\- **hub\_db\_storage\_count:** specify the storage you wish to make available to your database in gigabytes. Minimum starts at 20GB

\- **hub\_domain\_name:** the domain name used to serve the application. It is used to enable CORS in ORDS. OCI IAM also uses it to redirect the user to the correct application after a successful login.&nbsp; It is critical that:&nbsp;

1. &nbsp;
   1. the domain remains .hackolade.com, and&nbsp;
   1. that you assign (and keep a record of) the subdomain. &nbsp;

For example \<yourcompany-prod\>.hackolade.com&nbsp; You must communicate this subdomain to Hackolade Helpdesk&nbsp; as detailed in [these instructions](<Parameterstoconnectfront-endandb.md>).

\- **oci\_username:** this is the username&nbsp; of the user doing the installation. It's going to be used as a user to push Docker images in the internal Docker registry.&nbsp;

\- **region:** you can leave this as is. It's the region where this compartment will be deployed, and it's going to be the same as the one you are in

\- **tenancy\_ocid:** do not change this value. It's the OCID of the tenancy

&nbsp;

![OCI Hub create stack variables](<lib/OCI Hub create stack variables.png>)

&nbsp;

&nbsp;

You have the opportunity to review your configuration prior to launching the creation:

&nbsp;

![OCI Hub create stack review](<lib/OCI Hub create stack review.png>)

&nbsp;

&nbsp;

When you click the Create button, it takes a few minutes for the Resource Manager to create the stack:

&nbsp;

![OCI Hub create stack job](<lib/OCI Hub create stack job.png>)

&nbsp;

&nbsp;

Go to Resources Manager \> Stacks and click in the stack name.&nbsp; Then click on the job name for the job which was applied for your stack

![OCI Hub create stack job failed](<lib/OCI Hub create stack job failed.png>)

&nbsp;

&nbsp;

The status of the job is provided in just a few minutes.

&nbsp;

![OCI Hub create stack job success](<lib/OCI Hub create stack job success.png>)

&nbsp;

You can also verify the presence of the different resources created in the specified compartment, for example in Oracle Database \> Autonomous Databases:

![OCI Hub create stack job success DB created](<lib/OCI Hub create stack job success DB created.png>)

&nbsp;

&nbsp;

&nbsp;

## Troubleshooting

The status of the job is provided in just a few minutes.

&nbsp;

![OCI Hub create stack troubleshooting job list](<lib/OCI Hub create stack troubleshooting job list.png>)

&nbsp;

&nbsp;

For a failed job, you can see the details.

&nbsp;

![OCI Hub create stack troubleshooting job fail](<lib/OCI Hub create stack troubleshooting job fail.png>)

&nbsp;

&nbsp;

The bottom of the log file should explain the reason for the failure, for example

![OCI Hub create stack troubleshooting job fail](<lib/OCI Hub create stack job log.png>)

&nbsp;

&nbsp;

In the above example, the message is clear and the corrective actions explained.

&nbsp;

If necessary, you may open a ticket with our Helpdesk at [support@hackolade.com](<mailto:support@hackolade.com?subject=Troubleshooting%20Model%20Hub%20Resource%20Manager%20stack%20failing%20job>) and provide the downloaded log file.

&nbsp;

