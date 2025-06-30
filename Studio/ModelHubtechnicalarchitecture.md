# Model Hub technical architecture

The Hackolade Model Hub is a new product licensed separately from Hackolade Studio.&nbsp; It includes a security-first database and portal entirely controlled by the customer.&nbsp; Contrary to many SaaS solutions, we do not collect, process, or store any of your information, data, or data models.&nbsp; This serverless architecture gives you full control of the residency for your data models, and is described in the diagram below:

&nbsp;

&nbsp;

![Image](<lib/Architecture Hub Studio Desktop Browser.png>)

&nbsp;

Hackolade does not host anything: not the database, not the replication agent, and not the portal application.&nbsp; You install the database and replication service on your own Oracle Cloud Infrastructure account, using a script that we provide. And we publish the application on a [Content Delivery Network](<https://en.wikipedia.org/wiki/Content\_delivery\_network> "Content Delivery Network") like [Azure Front Door](<https://azure.microsoft.com/en-us/products/frontdoor> "Azure Front Door") or [AWS CloudFront](<https://en.wikipedia.org/wiki/Amazon\_CloudFront> "AWS CloudFront"), while you continue to maintain, store, and access your data models inside the network entirely controlled by you.

&nbsp;

The main benefits of this architecture are that you remain in complete control of your data while always running the latest version of the Hub software, and without having to deploy software to your users or in your data center.  

&nbsp;

## Security-first, bring-your-own-storage approach

Hackolade Model Hub is a unique security-first platform in the sense that we maintain, enhance, and regularly publish the application, but your data models remain entirely under your control.&nbsp; Your data and data models are never sent to us.

&nbsp;

![Image](<lib/SaaS - Security-First - Bring You Own Storage.png>)

&nbsp;

### Why the Oracle Autonomous JSON database on Oracle Cloud Infrastructure?

The data models created and maintained with Hackolade Studio are persisted in files with an open JSON format.&nbsp; This was a conscious choice made during the initial design of the application back in 2015, and which has been instrumental in our our ability to deliver as we have been able to.&nbsp; And it was also foreseen from the start that those data models could reside in Git repositories and also be stored in a NoSQL document database.

&nbsp;

For this Model Hub product, literally every significant document database on the market was evaluated against a strict list of evaluation criteria, including: ability to store large documents, API access, indexing capabilities across deeply nested objects and arrays, rules mechanisms, security, authentication mechanisms, scalability, total cost of ownership, etc.

&nbsp;

The choice has been made to base our product on the [Oracle Autonomous JSON database](<https://www.oracle.com/ca-en/autonomous-database/autonomous-json-database/> "target=\"\_blank\"").&nbsp; AJD provides a combination of SQL tables and JSON collections, combined with data APIs and functions to give us the necessary flexibility and power to satisfy all of our requirements.&nbsp; OCI also includes many additional services needed for our solution: [API Gateway](<https://docs.oracle.com/en-us/iaas/Content/APIGateway/home.htm> "target=\"\_blank\""), [Rest Data Services](<https://www.oracle.com/in/database/technologies/appdev/rest.html> "target=\"\_blank\"") (ORDS), [Identity and Access Management](<https://www.oracle.com/be/security/identity-management/> "target=\"\_blank\""), [serverless Functions](<https://www.oracle.com/be/cloud/cloud-native/functions/> "target=\"\_blank\""), database [Multi-Language Engine](<https://labs.oracle.com/pls/apex/f?p=94065:12:32018698560791:15> "target=\"\_blank\""), [serverless Queuing service](<https://www.oracle.com/be/cloud/queue/> "target=\"\_blank\""), [key management Vault](<https://www.oracle.com/be/security/cloud-security/key-management/> "target=\"\_blank\""), [Container Registry](<https://www.oracle.com/cloud/cloud-native/container-registry/> "target=\"\_blank\""), and more.

&nbsp;

The autonomous aspect of the database service is important to deliver elastic scalability and fast query performance without administration.&nbsp; No need to configure or manage any hardware or install any software. AJD handles provisioning, backup, patching and upgrading, and growing or shrinking the database.

&nbsp;

Oracle Cloud Infrastructure includes a variety of deployment options: public cloud, private cloud, hybrid cloud, community cloud, and [sovereign cloud](<https://www.oracle.com/be/cloud/sovereign-cloud/> "target=\"\_blank\"").&nbsp;

&nbsp;

OCI places a [significant emphasis on security](<https://dev.to/adityabhuyan/how-oracle-cloud-infrastructure-enhances-security-and-scalability-for-businesses-2d34> "target=\"\_blank\""), integrating a comprehensive set of features and technologies that help businesses safeguard their operations.

&nbsp;

Based on customer needs and feedback, we chose the database and hosting technology that best fits the needs for the Hackolade Model Hub.&nbsp; The installation of your database takes place on your OCI account. Hackolade has no access to your instance which remains 100% within your control.&nbsp; OCI costs are charged to your account.&nbsp; Installation is scripted by us in an Infrastructure-as-Code approach, and executed by you, the customer. We of course provide instructions, documentation, and support.

&nbsp;

### We are fully committed to data security and privacy

Because none of your sensitive data leaves your infrastructure and is never stored on our servers, Hackolade Model Hub is a platform which lets you comply with data protection certifications (ISO 27000, 27001 and 27002) and GDPR:&nbsp;

\- we do not track your use of the [https://hub.hackolade.com](<https://hub.hackolade.com> "target=\"\_blank\"") website[ ](<https://www.drawio.com/blog/google-analytics.html>) - there are no cookies, no advertisements, no analytics, no browser fingerprinting, and no tracking beacons;

\- Hackolade Model Hub does not allow your data models to be stored on our servers.

&nbsp;

The serverless architecture addresses any security or confidentiality concern users might have with a SaaS platform.&nbsp; Many Software-as-a-Service solutions host not only the software but also your data, sometimes with certification programs such as [ISO 27001](<https://en.wikipedia.org/wiki/ISO/IEC\_27001> "target=\"\_blank\"") or [SOC 2](<https://us.aicpa.org/interestareas/frc/assuranceadvisoryservices/aicpasoc2report> "target=\"\_blank\"").&nbsp; While security concerns are legitimate for full SaaS solutions, they are simply not applicable in the case of the browser deployment of the Hackolade Model Hub, as we never collect or store any of your data or data models.&nbsp; We also do not collect any telemetry.&nbsp; Nothing. &nbsp;

&nbsp;

The secure cloud CDN architecture takes a zero-trust approach to protect against automated bots, injection attacks and application-layer denial-of-service attacks.

&nbsp;

## Always run the latest and greatest version of Hackolade Model Hub

With the browser deployment of Hackolade Model Hub, there is no effort necessary to always have access to the latest feature enhancements.

&nbsp;

The question is sometimes asked whether the browser deployment of the Hackolade Model Hub portal could be run on an internal server in your organization.&nbsp; While it would technically be possible, we do not offer this possibility.&nbsp; The reasons are:&nbsp;

\- it would remove the main benefit of this architecture, i.e. that you would always access the latest version of the application.&nbsp; We'd be back in the situation where you'd be dependent on your IT Department's validation, installation and deployment of each new version of our software;

\- it would require to support a server-based product, which is an entirely different business model.

&nbsp;

## Browser deployment architecture

For those interested in the inner workings, [Azure Front Door](<https://azure.microsoft.com/en-us/blog/introducing-the-new-azure-front-door-reimagined-for-modern-apps-and-content/> "target=\"\_blank\"") and [AWS CloudFront](<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html> "target=\"\_blank\"") deliver our static application content to you from the edge location closest to you in terms of latency.&nbsp; Processing takes place in your browser and never leaves your network.&nbsp; No data or telemetry is being collected by Hackolade from the processing of your data models. Your data models are persisted locally and never leave your network. &nbsp;

&nbsp;

&nbsp;

![Browser - Azure FrontDoor CDN network](<lib/Browser - Azure FrontDoor CDN network.png>)

&nbsp;

&nbsp;

WAF and DDoS protections are enabled using the respective capabilities of [Azure Front Door](<https://learn.microsoft.com/en-us/azure/frontdoor/front-door-ddos> "target=\"\_blank\"") and [AWS CloudFront](<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-awswaf.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

## Overview of the Hub database instance architecture

Your instance is created in your own OCI account with a script that you can obtain from us when you purchase the Hub product.&nbsp; The script creates all the necessary components for the Hub to function autonomously, according to the architecture diagram below:

&nbsp;

Oracle provides the [autonomous JSON database](<https://www.oracle.com/ca-en/autonomous-database/autonomous-json-database/> "target=\"\_blank\"") (AJD). This database can act like a collection of documents (in our case data models), accepting JSON data without any constraint and running queries on it later. Oracle offers standard SQL tables and [collections](<https://docs.oracle.com/en/database/oracle/oracle-database/23/adjsn/json-collections.html?source=:so:tw:or:awr:ocl:> "target=\"\_blank\""). The idea behind collections is that Oracle provides a table with predefined columns, one of which is JSON. We can take it on a case-by-case basis, but having a standard table gives us the greatest flexibility by having a column of type JSON to store the models and any extra column when needed.

&nbsp;

The [JSON type](<https://docs.oracle.com/en/database/oracle/oracle-database/23/adjsn/json-in-oracle-database.html#GUID-E075CA14-DC89-4F9D-AD6F-C351F774575A> "target=\"\_blank\"") in Oracle can store up to 32MB of compressed data with its OSON format. Storing the JSON in textual format can increase the limit to 2GB, but we lose the ability to run queries on the JSON without serializing it, which can be costly. So far, all our test schemas fit in the 32MB, so supporting bigger schemas shouldn't be the nominal case but rather exceptional, which we will address in a later iteration.

&nbsp;

&nbsp;

&nbsp;

![Hub OCI Architecture](<lib/Hub OCI Architecture.png>)

&nbsp;

&nbsp;

[Oracle Rest Data Services (ORDS)](<https://docs.oracle.com/en/database/oracle/oracle-rest-data-services/24.2/orddg/introduction-to-Oracle-REST-Data-Services.html#GUID-A16BCCA2-8081-4062-A635-9F7C36FC394F> "target=\"\_blank\""): ORDS provides features like REST APIs for the data in the database by offering ways to automatically create REST endpoints per table or by letting a developer create custom endpoints.

&nbsp;

AutoREST automatically creates CRUD endpoints for a table but is limited in terms of the queries we can run and cannot select the columns we want.

&nbsp;

In terms of security, ORDS defines privileges that allow users to access a resource if they have it. When integrating with a 3rd party authentication system, the privilege must be added to the JWT token.

&nbsp;

The [OCI functions](<https://docs.oracle.com/en-us/iaas/Content/Functions/Concepts/functionsoverview.htm> "target=\"\_blank\"") supports NodeJS 20+ and many other languages on the [Oracle Database Multilingual Engine for JavaScript](<https://docs.oracle.com/en/database/oracle/oracle-database/23/mlejs/introduction-to-mle.html> "target=\"\_blank\"") (Oracle MLE). They run in a Docker container, meaning any library on NPM could be installed. &nbsp;

In combination with [API Gateway](<https://docs.oracle.com/en-us/iaas/Content/APIGateway/Concepts/apigatewayoverview.htm> "target=\"\_blank\""), the function can be called from an endpoint to support calls from a Webhook.

&nbsp;

User authentication is handled by [OCI Identity and Access Management](<https://www.oracle.com/be/security/cloud-security/identity-cloud/> "target=\"\_blank\"") (OCI IAM).

&nbsp;

The sync of hck.json files will be handled by an OCI function, which will receive a webhook for the git repository to download the changes and apply them to the database.&nbsp;

&nbsp;

&nbsp;

