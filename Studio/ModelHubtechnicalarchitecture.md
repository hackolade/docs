# Model Hub technical architecture

The Hackolade Model Hub is a new product licensed separately from Hackolade Studio.&nbsp; It includes a security-first database and portal entirely controlled by the customer.&nbsp; Contrary to many SaaS solutions, we do not collect, process, or store any of your information, data, or data models.&nbsp; This serverless architecture gives you full control of the residency for your data models, and is described in the diagram below:

&nbsp;

&nbsp;

![Hub Studio Desktop Browser Architecture](<lib/Hub Studio Desktop Browser Architecture.png>)

&nbsp;

Hackolade does not host anything: not the database, not the replication agent, and not the portal application.&nbsp; You install the database and replication service on your own cloud account, using a script that we provide. And we publish the application on a [Content Delivery Network](<https://en.wikipedia.org/wiki/Content\_delivery\_network> "Content Delivery Network") like [Azure Front Door](<https://azure.microsoft.com/en-us/products/frontdoor> "Azure Front Door") or [AWS CloudFront](<https://en.wikipedia.org/wiki/Amazon\_CloudFront> "AWS CloudFront"), while you continue to maintain, store, and access your data models inside the network entirely controlled by you.

&nbsp;

The main benefits of this architecture are that you remain in complete control of your data while always running the latest version of the Hub software, and without having to deploy software to your users or in your data center.  

&nbsp;

## Security-first, bring-your-own-storage approach

Hackolade Model Hub is a unique security-first platform in the sense that we maintain, enhance, and regularly publish the application, but your data models remain entirely under your control.&nbsp; Your data and data models are never sent to us.

&nbsp;

![Image](<lib/SaaS - Security-First - Bring You Own Storage.png>)

&nbsp;

&nbsp;

### We are fully committed to data security and privacy

Because none of your sensitive data leaves your infrastructure and is never stored on our servers, Hackolade Model Hub is a platform which lets you comply with data protection certifications (ISO 27000, 27001 and 27002) and GDPR:&nbsp;

\- we do not track your use of the [https://hub.hackolade.com](<https://hub.hackolade.com> "target=\"\_blank\"") website - there are no cookies, no advertisements, no analytics, no browser fingerprinting, and no tracking beacons;

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

## 