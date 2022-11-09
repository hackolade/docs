# Security concerns

Security is a key concern for us and is part of our continuous improvement process. &nbsp;

&nbsp;

## Compliance certifications or accreditation like SOC 2 Type 2 or 3, or ISO 27001: what are Hackolade's internal controls related to: network security, security personnel, data security, operational security, risk management, asset management, business continuity, and disaster recovery?

The architecture of our solution must be taken into account.&nbsp; Hackolade Studio is a downloadable client, and **NOT** a Software-as-a-Service solution that would store your data or data models.&nbsp; Also, our software has no telemetry, meaning that no information goes outside of your network.  We don’t collect or store any of your information, except for the license key-related information as described in our [Privacy Policy](<https://hackolade.com/privacy.html>). &nbsp;

&nbsp;

As a result, typical SaaS-related security assessments just don’t apply to us.&nbsp; Our software, since it is installed on hardware controlled by you, relies on your own security measures and controls.

&nbsp;

## Is the Hackolade Studio installer "code signed"?

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

We carefully select and manage 3rd-party libraries.  We make sure to embed the latest security patches by regularly updating these libraries based on the vulnerability reports that are generated by our package manager.  Our desktop application has no runtime dependency on any external services: nothing leaves the customer's premises, unless requested by the user.&nbsp;

 

Our desktop client application encrypts connection strings, and other secrets that are configured by the user, even if they remain local.  We also make sure to obfuscate the parts of our codebase that deal with security concerns.   We have from time to time published [advisories](<Vulnerabilities.md>) to alert our users about possible vulnerabilities.

 

Our most senior engineers organize punctual “white hat hacking sessions” where they analyze if and how specific parts of our product could be attacked.  These sessions sometimes result in the creation of new actions for security improvements that are prioritized, then processed by the development team.

&nbsp;

## What is our engineering team's usage of static code analysis tools (SAST, SCA)?

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

## What about unmasking of passwords in Connection Settings?

This is just one of the physically-local attacks described in the previous section, and all of those points apply here as well.&nbsp; The reason the password is masked is only to prevent disclosure via “shoulder-surfing” (i.e. the passive viewing of your screen by nearby persons), not because it is a secret unknown to the application. The application knows the password at many layers, including JavaScript, developer tools, process memory, and so on.&nbsp; When you are physically local to the computer, and only when you are physically local to the computer, there are, and always will be, tools for extracting the password from any of these places.

&nbsp;

## How does Hackolade studio handle Role-based Access Control for data models?

The tool is a downloadable client and not a client-server or SaaS solution.&nbsp; As a result, it has no Role-Based Access Control.&nbsp; Security of the data models is delegated to the the storage layer, i.e. shared network drives or repositories. &nbsp;

&nbsp;
