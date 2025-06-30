# Security concerns

Security is a key concern for us and is part of our continuous improvement process. &nbsp;

&nbsp;

## What type of software is Hackolade Studio?

Our software product is of the type Commercial Off-The-Shelf (COTS) in the form of a downloadable client installed on individual workstations.&nbsp; It is NOT a SaaS (Software-as-a-Service) solution that would collect or store information.&nbsp; We collect, process or store NO data models, NO telemetry, NO personal information of any kind.&nbsp; No data comes out of your network, and we do not collect or store anything on any server.

&nbsp;

Here's an architecture diagram to illustrate:

&nbsp;

![Client architecture diagram](<lib/Client architecture diagram.png>)

&nbsp;

&nbsp;

&nbsp;

The purpose of the software is for data modeling of SQL and NoSQL databases, APIs, and storage formats.

&nbsp;

## Compliance certifications or accreditation like SOC 2 Type 2 or 3, or ISO 27001: what are Hackolade's internal controls related to: network security, security personnel, data security, operational security, risk management, asset management, business continuity, and disaster recovery?

The architecture of our solution must be taken into account.&nbsp; Hackolade Studio is a downloadable COTS client, and **NOT** a Software-as-a-Service solution that would store your data or data models.&nbsp; Also, our software has no telemetry, meaning that no information goes outside of your network.  We don’t collect or store any of your information, except for the license key-related information as described in our [Privacy Policy](<https://hackolade.com/privacy.html>). &nbsp;

&nbsp;

The application runs with no backend and no data storage.&nbsp; As a result, typical SaaS-related security assessments just don’t apply to us.&nbsp; Our software, since it is installed on hardware controlled by you, relies on your own security measures and controls.

&nbsp;

As it seems to not be sufficient for some that we collect or store absolutely no data models or data from customers, we have completed a [full security assessment](<https://app.riskledger.com/p/shared/36724fc5ba0b4f9084c0cf2bc8834cce/assessment> "target=\"\_blank\"") with [Risk Ledger](<https://riskledger.com/> "target=\"\_blank\""), sort of a certification that our "[Fort Knox](<https://en.wikipedia.org/wiki/Fort\_Knox> "target=\"\_blank\"")" contains no gold...&nbsp;

&nbsp;

## Hackolade Studio is now also available in the browser.&nbsp; Is that not a SaaS solution?

The general understanding of SaaS solutions is that the provider stores customer data. &nbsp;

![Image](<lib/SaaS - Traditional understanding.png>)

&nbsp;

As a matter of fact, we tend to think that Saas is a bit of misnomer as it implies more than "software as a service" but "software and data storage as a service".&nbsp; As data modelers, we know how important it is to match the right name with the meaning...

&nbsp;

Hackolade Studio is a pioneer in a solution that we call "Bring Your Own Storage" to a true SaaS approach:

![SaaS - Security-First - Bring You Own Storage](<lib/SaaS - Security-First - Bring You Own Storage.png>)

&nbsp;

&nbsp;

Read all the details of our [security-first browser deployment](<Security-firstbrowserdeployment.md>).

&nbsp;

## Is Hackolade subject to DORA regulation?

The Digital Operational Resilience Act (DORA), officially known as [Regulation (EU) 2022/2554](<https://www.eiopa.europa.eu/digital-operational-resilience-act-dora\_en> "target=\"\_blank\""), is a European Union regulation aimed at enhancing the digital operational resilience of the financial sector. It establishes a comprehensive framework for managing information and communication technology (ICT) risks, ensuring that financial entities can withstand, respond to, and recover from ICT-related disruptions such as cyberattacks or system failures.

&nbsp;

As already established with several European customers in the financial sector, Hackolade is not subject to DORA because we sell a product and we do not provide ICT services.&nbsp; Additionally, the product is not mission-critical, and its architecture is such that there is no single point of failure as the client software is distributed to each user's workstation.&nbsp; And as demonstrate above in this page, we do not collect, process, or store any customer data.&nbsp; And we do not have any servers or database. &nbsp;

&nbsp;

Specifically, the following DORA articles exonerate Hackolade from being subject to DORA:

\-&nbsp; [Article 4](<https://www.springlex.eu/packages/dora/dora-regulation/article-4/> "target=\"\_blank\"") “**Proportionality principle**”: &nbsp; In addition, the application by financial entities of Chapters III, IV and V, Section I, shall be proportionate to their size and overall risk profile, and to the nature, scale and complexity of their services, activities and operations, as specifically provided for in the relevant rules of those Chapters.

\- [Article 7](<https://www.springlex.eu/packages/dora/dora-regulation/article-7/> "target=\"\_blank\"") "**ICT systems, protocols and tools**": In order to address and manage ICT risk, financial entities shall use and maintain updated ICT systems, protocols and tools that are: a) appropriate to the magnitude of operations supporting the conduct of their activities, in accordance with the proportionality principle as referred to in [Article 4](<https://www.dora-info.eu/dora/article-4/> "target=\"\_blank\"").

\- [Article 31 paragraph 2.1](<https://www.springlex.eu/packages/dora/dora-regulation/article-31/#r2.1> "target=\"\_blank\"") "**Designation of critical ICT third-party service providers**":&nbsp; The designation referred to in paragraph 1, point (a), **shall be based on all of the following criteria** in relation to ICT services provided by the ICT third-party service provider:&nbsp;

(a) the systemic impact on the stability, continuity or quality of the provision of financial services in the event that the relevant ICT third-party service provider would face a large scale operational failure to provide its services, taking into account the number of financial entities and the total value of assets of financial entities to which the relevant ICT third-party service provider provides services;

(b) the systemic character or importance of the financial entities that rely on the relevant ICT third-party service provider;

(c) the reliance of financial entities on the services provided by the relevant ICT third-party service provider in relation to critical or important functions of financial entities that ultimately involve the same ICT third-party service provider, irrespective of whether financial entities rely on those services directly or indirectly, through subcontracting arrangements;

(d) the degree of substitutability of the ICT third-party service provider.

&nbsp;

## Is the Hackolade Studio desktop installer "code signed"?

Code signing is a method of putting a digital signature on a program, file, software update or executable, so that its authenticity and integrity can be verified upon installation and execution. It guarantees to the recipient who the publisher is, and that the software hasn't been opened and tampered with.

&nbsp;

The code signing of our software depends on the OS platform capabilities:

&#49;) Windows: the downloadable installer for Hackolade Studio is signed with a valid [DigiCert](<https://www.digicert.com/signing/code-signing-certificates> "target=\"\_blank\"") SHA-256 certificate of the type "Extended Validity Code Signing" (a.k.a EV Code Signing) which entails extensive vetting of the publisher.&nbsp; Additionally, the private key must be stored in an external hardware token, thus preventing any unauthorized personnel from accessing them.&nbsp; The EV Code Signing certificate leverages the Windows SmartScreen filter, building the reputation of the publisher of the software to reassure users.

&nbsp;

&#50;) Mac: the downloadable installer for Hackolade Studio is code signed with a developer certificate issued by Apple and is notarized by Apple.&nbsp; Before an application can be installed on a device, it must be signed with a developer certificate issued by Apple.&nbsp; Beginning with macOS 10.14.5 (Mojave), signed software must also be notarized by Apple in order to run.&nbsp; Notarization is designed by Apple to give users more confidence that Apple developer-signed software has been checked by Apple for malicious components. The Apple notary service is an automated system that scans software for malicious content, checks for code-signing issues, and returns the results. If there are no issues, the notary service generates a ticket to staple to the software; the notary service also publishes that ticket online where Gatekeeper can find it.&nbsp; When the user first installs or runs software, the presence of a ticket (either online or attached to the executable) tells Gatekeeper that Apple notarized the software. Gatekeeper then places descriptive information in the initial launch dialog to help the user make an informed choice about whether to launch the app.

&nbsp;

&#51;) Linux: this OS platform does not provide an installer or standard code-signing.

&nbsp;

## Where are the checksums for the installer downloads?

Signed installers with SHA-256 certificates provide higher guarantees than MD5 checksums because the output size is twice longer and the probability of collisions is lower.

&nbsp;

## Anti-virus and anti-malware

We appropriately secure our devices, including by routinely checking for computer viruses or malware using up-to-date anti-virus software and anti-spyware in accordance with industry standard practices.&nbsp;

&nbsp;

## How do we integrate security into our Software Development Lifecycle process?

In our software development process, we incorporate secure coding practices, specifically addressing the OWASP Top 10 vulnerabilities, to significantly reduce the risk of common security flaws in software and enhance the overall security posture of our application:

&nbsp;

* Educate Developers to ensure that the development team is aware of secure coding practices, with training sessions to familiarize them with common vulnerabilities and mitigation techniques.
* Incorporate Security Requirements into the software development life cycle (SDLC): we define secure coding guidelines, standards, and best practices and align them with the OWASP Top 10. These requirements cover areas such as input validation, authentication, access control, secure communication, error handling, and secure configuration.
* Conduct Code Reviews with process to include security-focused reviews for adherence to secure coding practices and identify potential vulnerabilities. Using static code analysis to assist in identifying security flaws and coding mistakes.
* Perform Regular Security Testing, including vulnerability assessments, penetration testing, and security scanning, to identify potential issues. We test for vulnerabilities associated with the OWASP Top 10, such as injection attacks, broken authentication, cross-site scripting (XSS), and insecure direct object references.
* Use Secure Libraries and Frameworks in our software development.&nbsp; We stay up-to-date with security patches and ensure to be using the latest versions to avoid known vulnerabilities.
* Validate Input and Output: we implement strong input validation techniques to prevent common attacks like SQL injection, cross-site scripting, and command injection. We validate and sanitize user input on both the client and server sides. We implement output encoding and escaping to prevent cross-site scripting vulnerabilities.
* Implement Proper Authentication and Authorization: we use strong authentication mechanisms to verify user identities and enforce secure session management. We implement secure password storage practices, such as salted hashing, and enforce password complexity requirements. We implement appropriate authorization mechanisms to ensure that users have access only to the resources they need.
* Secure Data Handling: we apply secure coding practices when handling sensitive data, such as encryption, secure transmission protocols (e.g., HTTPS), secure storage, and proper data sanitization or destruction when no longer needed.
* Handle Errors Securely: we implement proper error handling mechanisms to avoid exposing sensitive information to attackers.&nbsp; We ensure that error messages provide minimal information to attackers.
* Stay Updated: we keep track of the latest vulnerabilities, security advisories, and updates related to the OWASP Top 10 and other common security issues. We stay informed about emerging security threats and adjust our coding practices accordingly.

&nbsp;

We carefully select and manage 3rd-party libraries.  We make sure to embed the latest security patches by regularly updating these libraries based on the vulnerability reports that are generated by our package manager.  Our desktop application has no runtime dependency on any external services: nothing leaves the customer's premises, unless requested by the user.&nbsp;

 

Our desktop client application encrypts connection strings, and other secrets that are configured by the user, even if they remain local.  We also make sure to obfuscate the parts of our codebase that deal with security concerns.   We have from time to time published [advisories](<Vulnerabilities.md>) to alert our users about possible vulnerabilities.

 

Our most senior engineers organize punctual “white hat hacking sessions” where they analyze if and how specific parts of our product could be attacked.  These sessions sometimes result in the creation of new actions for security improvements that are prioritized, then processed by the development team.

&nbsp;

Threat modeling is used during the application design phase to identify, evaluate, and mitigate potential security threats and vulnerabilities. It involves analyzing the application's architecture, components, and interactions to understand potential risks and prioritize security countermeasures.

&nbsp;

The process of threat modeling consists of the following steps:

&nbsp;

1. Identify Assets: Identify the key assets, data, and functionality that need protection within the application, including sensitive user information, intellectual property, financial transactions, or system resources.

&nbsp;

2. Create a Design Overview: Develop an architectural overview of the application, illustrating its various components, modules, and their interactions, to identify potential entry points, trust boundaries, and data flows.

&nbsp;

3. Identify Threats: Identify potential threats and attack vectors that could exploit vulnerabilities in the application, including unauthorized access, injection attacks, cross-site scripting (XSS), cross-site request forgery (CSRF), and more.&nbsp;

&nbsp;

4. Assess Risks: Evaluate the impact and likelihood of each identified threat. Assign risk ratings based on the potential damage, likelihood of occurrence, and ease of exploitation.&nbsp;

&nbsp;

5. Determine Countermeasures: Determine appropriate countermeasures and security controls to mitigate identified risks. This may involve employing secure coding practices, input validation, encryption, access controls, authentication mechanisms, and other defensive measures.

&nbsp;

6. Validate and Iterate: Review the threat model with relevant stakeholders, including developers, architects, and security experts. Incorporate their feedback and iterate on the design to enhance security.

&nbsp;

&nbsp;

## What is our engineering team's usage of static code analysis tools (SAST, SCA)?

The quality of our code base is continuously analyzed following a [Clean as you Code strategy](<https://docs.sonarsource.com/sonarcloud/improving/clean-as-you-code/> "target=\"\_blank\"") with SonarQube (previously SonarLint and SonarCloud), the solution trusted and used by 7 million developers around the world.&nbsp;

&nbsp;

In terms of Static Application Security Testing (SAST), we use [Abstract Syntax Tree](<https://en.wikipedia.org/wiki/Abstract\_syntax\_tree> "target=\"\_blank\"")-based tools to proactively detect, report, and fix undesired patterns and vulnerabilities in our codebase.&nbsp; All our software engineers have these tools enabled in their integrated development environment (IDE).&nbsp; They receive immediate feedback in case a problem is detected while they are writing code.&nbsp; We also leverage a Git hook to prevent pushing such problems to our central code repositories.&nbsp; As a last verification layer, the same tools are used in our continuous integration pipeline, making it impossible to build and publish a version of the software that would be affected by detected problems.

&nbsp;

As part of our internal continuous improvement process, we regularly evaluate additional options to broaden the scope of our SAST strategy, striking a balance between detecting more problems and dealing with too many false positives.

&nbsp;

Regarding Software Composition Analysis (SCA), we use industry standard audit tools to assess our 3rd-party dependencies and make sure to keep them up-to-date with the latest security patches.&nbsp; We also leverage "docker scan" (powered by Snyk) to detect vulnerabilities in the Docker images used in our DevOps CI/CD pipeline.

&nbsp;

## Why aren't physically-local attacks in Hackolade Studio's threat model?

The answer is greatly inspired by Google's [position for Chrome](<https://chromium.googlesource.com/chromium/src/%20/master/docs/security/faq.md#Why-arent-physically\_local-attacks-in-Chromes-threat-model> "target=\"\_blank\"").

&nbsp;

Could an attacker compromise Hackolade Studio and steal connections settings to the databases?&nbsp; We consider these attacks outside Hackolade Studio's threat model, because there is no way for Hackolade Studio (or any application) to defend against a malicious user who has managed to log into your device as you, or who can run software with the privileges of your operating system user account.&nbsp; Such an attacker can modify executables and DLLs, change environment variables like PATH, change configuration files, read any data your user account owns, email it to themselves, and so on.&nbsp; Such an attacker has total control over your device, and nothing Hackolade Studio can do would provide a serious guarantee of defense. This problem is not specific to Hackolade Studio — all applications must trust the physically-local user.

There are a few things you can do to mitigate risks from people who have physical control over **your** computer, in certain circumstances.

* take advantage of your operating system’s screen lock feature.
* if you share your computer with other people, take advantage of your operating system’s ability to manage multiple login accounts, and use a distinct account for each person.&nbsp;
* to stop people from reading your data in cases of device theft or loss, use full disk encryption (FDE). FDE is a standard feature of most operating systems, including Windows Vista and later, Mac OS X Lion and later, and some distributions of Linux. (Some older versions of Mac OS X had partial disk encryption: they could encrypt the user’s home folder, which contains the bulk of a user’s sensitive data.) Some FDE systems allow you to use multiple sources of key material, such as the combination of both a password and a key file on a USB token. When available, you should use multiple sources of key material to achieve the strongest defense. Chrome OS encrypts users’ home directories.

&nbsp;

## Does Hackolade Studio store and encrypt passwords?

It goes without saying that we would of course not leave secrets un-encrypted.&nbsp; We encrypt passwords, passphrases, and other secrets.&nbsp; We delegate the storage to known 3rd-party technologies: Git Credentials, OS-specific secret storage (Mac keychain, Windows Credentials Manager, Linux kwallet), and other safe storage methods.&nbsp;

&nbsp;

## What about unmasking of passwords in Connection Settings?

This is just one of the physically-local attacks described in the previous section, and all of those points apply here as well.&nbsp; The reason the password is masked is only to prevent disclosure via “shoulder-surfing” (i.e. the passive viewing of your screen by nearby persons), not because it is a secret unknown to the application. The application knows the password at many layers, including JavaScript, developer tools, process memory, and so on.&nbsp; When you are physically local to the computer, and only when you are physically local to the computer, there are, and always will be, tools for extracting the password from any of these places.

&nbsp;

## How does Hackolade Studio handle Role-Based Access Control for data models?

The tool is a downloadable client and not a client-server or SaaS solution.&nbsp; As a result, it has no Role-Based Access Control.&nbsp; Security of the data models is delegated to the the storage layer, i.e. shared network drives or repositories. &nbsp;

&nbsp;

