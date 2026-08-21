# Model Hub technical architecture

The Hackolade Model Hub is a&nbsp; product licensed separately from Hackolade Studio.&nbsp; It includes a security-first database and portal entirely controlled by the customer.&nbsp; Contrary to many SaaS solutions, we do not collect, process, or store any of your information, data, or data models.&nbsp; This serverless architecture gives you full control of the residency for your data models, and is described in the diagram below:

&nbsp;

&nbsp;

![Image](<lib/Hub Studio Desktop Browser Architecture.png>)

&nbsp;

Hackolade does not host anything: not the database, not the replication agent, and not the portal application.&nbsp; You install the database and replication service on your own cloud account, using a Docker container that we provide on [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"\_blank\""). The image contains the app server and utilisites, plus the portal application. All you need is to connect Model Hub to your own instance Oracle 26ai or PostgreSQL 17+ database, while you continue to maintain, store, and access your data models inside the network entirely controlled by you.

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

With the browser deployment of Hackolade Model Hub delivered to you via a Docker containe, there is no effort necessary to always have access to the latest feature enhancements.

&nbsp;

We periodically deliver a new version of the Model Hub with new features and feature enhancements&nbsp; To make installation and upgrades simple, we deliver the Model Hub in a Docker image and make it available on [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"\_blank\"").

