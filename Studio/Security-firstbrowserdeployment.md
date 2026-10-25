# Security-first browser deployment

## The best of both worlds: keep your confidential data models private, and avoid software deployment

With **Hackolade Studio running as a single-page static app in the browser**, organizations gain the key benefits of Software-as-a-Service: immediate access to the **latest version** of the platform **without the need to deploy** or maintain software on user machines.\
At the same time, Hackolade eliminates the most common concern associated with SaaS: the loss of control over data. Through our innovative **serverless** architecture, users retain **complete ownership, confidentiality, residency, and sovereignty over their data models and metadata**.\
Hackolade does **not lock in your models**, nor do we collect, process, or store any of your data, data models, or metadata. Instead, your model files are securely persisted in the **private Git repository provider of your choice**, such as **GitHub, GitLab, Bitbucket, or Azure DevOps Repos**, ensuring that you always maintain full control over your intellectual property at all times.

&nbsp;

![Security-first browser deployment](<lib/Security-first browser deployment.png>)

&nbsp;

This feature is also very handy when combined with the ability to share a model link, as described in [this page](SharemodellinkURL.md), and demonstrated in [this video](<https://community.hackolade.com/slides/slide/share-and-socialize-data-models-67?fullscreen=1> "target=\"_blank\""). It also allows for authors to create and maintain models in the browser.

&nbsp;

> [!IMPORTANT]
> 1\) the browser deployment is fully available for the Community Edition, and the Read-Only Viewer Edition. The Community edition does not require a license key. Other editions do require a license key. Since v7.9.3, it is also possible to use a Personal, Professional, or Workgroup edition license key in the browser. However, users should be conscious that not all features of these editions are enabled in the browser for a variety of security and technical reasons. While we are progressively enabling many of those features, some might be only available in the desktop deployment.\
> 2\) our browser deployment currently supports the latest versions of Chrome, Edge, Brave, Firefox browsers and Safari. It also works with the latest AI browsers, generally Chromium based: Perplexity Comet, OpenAI Atlas, etc.\
> 3\) some features have a graceful degradation of the user experience due to limitations imposed by the browser. For example Brave, Firefox, and Safari do not support the [File System Access API](<https://wicg.github.io/file-system-access/> "target=\"_blank\""), and as a result, the action to save a model is implemented as the download of a new copy. For the best user experience, you should use Chrome or Edge.\
> 3\) some native features of the application may be restricted due to each browser's own restrictions, or due to W3C security standards. User experience may be somewhat degraded as a result, typically for legitimate security reasons. Workarounds are provided, for example with the use of the desktop deployment, or with a solution architecture that leverages our [Docker instance of the application](DevOpsCICDarchitecture.md). We are closely monitoring evolution of standards that would allow us to enable more desktop features in the browser, such as [Isolated Web Apps](<https://github.com/WICG/isolated-web-apps/blob/main/README.md> "target=\"_blank\"") or [Direct Sockets](<https://github.com/WICG/direct-sockets> "target=\"_blank\""). If and when such evolutions would be released in standard browser versions, we will make sure to leverage them.

&nbsp;

Obviously, the ability to run Hackolade Studio in **the browser requires no installation or deployment of an application** by your IT department. Just go to [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"") from your favorite browser and start your data modeling work. No sign-up necessary or complex user management. All the processing is done inside your browser -- there is no server-side processing, as their are no servers.

&nbsp;

Hackolade Studio has traditionally been available as an offline desktop application for Windows, Mac, and Linux. Starting with v7.0.0, it is now also available as a [cross-browser](<https://en.wikipedia.org/wiki/Cross-browser> "target=\"_blank\"") [serverless](<https://en.wikipedia.org/wiki/Serverless_computing> "target=\"_blank\"") [single-page web app](<https://en.wikipedia.org/wiki/Web_application> "target=\"_blank\"") which can open data models from and save them to your local environment, or preferably to your Git repository so you can collaborate on models. All from the same code base, meaning that, as we add [weekly enhancements](<https://hackolade.com/versionInfo/ReadMe.txt> "target=\"_blank\"") and new features, they are deployed automatically to the offline desktop and the online browser. The code base for the latest version is exactly identical for the browser deployment and all desktop operating systems.

&nbsp;

This serverless setup gives you full control of the residency for your data models, while leveraging the benefits of an online application. In other words, the Hackolade Studio online application runs without any kind of backend system or database. We don't host the application. We publish it on a [Content Delivery Network](<https://en.wikipedia.org/wiki/Content_delivery_network> "target=\"_blank\"") like [Azure Front Door](<https://azure.microsoft.com/en-us/products/frontdoor> "target=\"_blank\"") or [AWS CloudFront](<https://en.wikipedia.org/wiki/Amazon_CloudFront> "target=\"_blank\""), while you continue to maintain your data models locally, as you would do with the offline desktop deployment of Hackolade Studio. The app runs entirely **client-side in the browser**, but securely -- with no backend server, either on the customer side or on the Hackolade side. No server-side processing -- everything takes place inside your browser.

&nbsp;

Data isolation is possible because all your data model editing is "sandboxed" in your browser memory. When you save your model, the only possible locations are your own local machine or network, or your own repository. While it is possible that your repository is in the cloud, it is the repository of your choice. Hackolade never receives, process, or store your data models or data. It does not even transit through our network or systems. Our approach is similar to [Visual Studio Code for the Web](<https://code.visualstudio.com/docs/setup/vscode-web> "target=\"_blank\""), and is even more confidential as we don't even collect any anonymous telemetry. Or similar to [draw.io](<https://www.drawio.com/blog/data-protection> "target=\"_blank\"").

&nbsp;

The main benefits of this setup are that you remain in complete control of your data while always running the latest version of Hackolade Studio without having to install and deploy the software.

&nbsp;

![Desktop and Browser architecture](<lib/Desktop and Browser architecture.png>)

&nbsp;

<table style="width:100%">
<colgroup><col style="width:28%"><col style="width:72%"></colgroup>
<thead>
<tr>
<th>Feature</th>
<th>Benefit</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Zero server maintenance</strong></td>
<td>No backend servers required -- everything is static and serverless</td>
</tr>
<tr>
<td><strong>Enterprise-grade security</strong></td>
<td>Delivered over HTTPS via Azure Front Door</td>
</tr>
<tr>
<td><strong>Fast and responsive UX</strong></td>
<td>App loads once and runs entirely in the browser</td>
</tr>
<tr>
<td><strong>Anywhere access</strong></td>
<td>Ideal for distributed teams or remote modelers</td>
</tr>
</tbody>
</table>

&nbsp;

## Security-first, bring-your-own-storage approach

Hackolade Studio is a unique security-first data modeling tool in the sense that we provide the application platform, but your data model only lives in your browser on your local device while you are working on it. Upon saving, your data model is stored at the location of your choice: on your local device, on a shared internal network drive, or in a locally-cloned Git repository. Your data model is never sent to us, even when you save your data model or perform operations with it.

&nbsp;

Even if you export to JSON Schema or print the ER diagram, your data model never leaves your network and is never sent to any server of ours (which we don't have anyway...)

&nbsp;

The added advantage is that we don't create yet another silo for your data models. You keep on storing them wherever is makes the most sense to you. The fact that you run the latest version of the software in a browser does not affect the location of your data models.

&nbsp;

### We are fully committed to data security and privacy

Because your sensitive data model does not leave your infrastructure and is never stored on our servers (which we don't have anyway), Hackolade Studio is a tool which lets you comply with data protection certifications (`ISO 27000`, `27001` and `27002`, or `SOC2`) and GDPR:

- w[e do not track your use of the ](https://www.drawio.com/blog/google-analytics.html)[https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"") website - there are no cookies, no advertisements, no analytics, no browser fingerprinting, and no tracking beacons;
- we don’t track your use of the Hackolade Studio applications, whether online in the browser, or desktop;
- Hackolade Studio does not allow customer data or data models to be stored on any servers of ours.

&nbsp;

![SaaS convenience with zero data exposure](<lib/SaaS convenience with zero data exposure.png>)

&nbsp;

The serverless architecture addresses any security or confidentiality concern users might have with a SaaS platform. Many Software-as-a-Service solutions host not only the software but also your data, sometimes with certification programs such as [ISO 27001](<https://en.wikipedia.org/wiki/ISO/IEC_27001> "target=\"_blank\"") or [SOC 2](<https://us.aicpa.org/interestareas/frc/assuranceadvisoryservices/aicpasoc2report> "target=\"_blank\""). While security concerns are legitimate for full SaaS solutions, they are simply not applicable in the case of the browser deployment of Hackolade Studio, as we never collect or store any of your data or data models. We also do not collect any telemetry. Nothing.

&nbsp;

If you still have any doubts, we suggest this easy test: first load the application in your browser at [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\""), then disconnect entirely from the Internet. We do perform lazy loading of some code parts for UX and performance purposes, but no data ever goes outbound. You will see that you can continue to use the Hackolade Studio editor in your browser, then save your data model, or work on a previously saved model present on your local drive. You may also use a [network traffic sniffer/analyzer](<https://en.wikipedia.org/wiki/Packet_analyzer> "target=\"_blank\"") to validate this claim.

&nbsp;

The secure cloud CDN architecture takes a zero-trust approach to protect against automated bots, injection attacks and application-layer denial-of-service attacks.

&nbsp;

### Offline and secure data modeling with the desktop application

If you want to perform data modeling in a totally secure and offline environment, download and install [Hackolade Studio Desktop](<https://hackolade.com/download.html> "target=\"_blank\""). This stand-alone desktop application is available for Windows, MacOS, and Linux.

&nbsp;

### Do you need to obfuscate your data models before you share them?

Use the File > Save Obfuscated As... function to overwrite all texts so you can safely share sensitive ER Diagrams and structures with clients or partners without fear of breaching non-disclosure clauses or the GDPR. This can be particularly useful to help Hackolade support troubleshoot issues you might encounter.

&nbsp;

## Always run the latest and greatest version of Hackolade Studio

Given the weekly frequency of our new version releases bringing continuous enhancements, some organizations have been challenged to keep up. It can be hard sometimes to get the IT department to validate a new version, create an image, and deploy it to a large number of users. With the browser deployment of Hackolade Studio, there is no effort to always have access to the latest feature enhancements.

&nbsp;

The question is sometimes asked whether the browser deployment of Hackolade Studio could be run on an internal server in your organization. While it would technically be possible, we do not offer this possibility. The reasons are:

- it would remove the main benefit of this architecture, i.e. that you would always access the latest version of the application. We'd be back in the situation where you'd be dependent on your IT Department's validation, installation and deployment of each new version of our software;
- it would require to support a server-based product, which is an entirely different business model.

&nbsp;

![Architecture deployment matrix](<lib/Architecture deployment matrix.png>)

&nbsp;

## Browser deployment architecture

For those interested in the inner workings, the browser deployment of Hackolade Studio runs the exact same code base as the offline desktop application. The offline desktop deployment of Hackolade Studio was written from day 1 in ReactJS and packaged as a desktop application with [Electron](<https://en.wikipedia.org/wiki/Electron_(software_framework)> "target=\"_blank\""), the framework developed and maintained by GitHub. Electron runs the application code in the [Chromium](<https://en.wikipedia.org/wiki/Chromium_(web_browser)> "target=\"_blank\"") browser engine, which also powers the Chrome web browser. The browser deployment of Hackolade Studio is just a different packaging of the same code as the offline deployment, so you can now access the same functionality in a more convenient manner.

&nbsp;

[Azure Front Door](<https://azure.microsoft.com/en-us/blog/introducing-the-new-azure-front-door-reimagined-for-modern-apps-and-content/> "target=\"_blank\"") and [AWS CloudFront](<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html> "target=\"_blank\"") deliver our static application content to you from the edge location closest to you in terms of latency. Processing takes place in your browser and never leaves your network. No data or telemetry is being collected from the processing of your data models. Your data models are persisted locally and never leave your network. There is no data in transit, and if you're using the Workgroup features, all commits, pulls, pushes, change requests, branch merges, etc. take place locally and never across the public network.

&nbsp;

![Browser - Azure FrontDoor CDN network](<lib/Browser - Azure FrontDoor CDN network.png>)

&nbsp;

WAF and DDoS protections are enabled using the respective capabilities of [Azure Front Door](<https://learn.microsoft.com/en-us/azure/frontdoor/front-door-ddos> "target=\"_blank\"") and [AWS CloudFront](<https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-awswaf.html> "target=\"_blank\"").

&nbsp;

## Configure your browser to enable site data

It is also better to use your browser in its standard mode, i.e. NOT in a guest, private, or incognito tab. While we don't use cookies, we do leverage some features of what's called "site data" capabilities in your browser. Adjusting your browser settings to enable site data for Hackolade Studio Browser ensures that your settings are preserved, even after reloading the application or starting a new session in a new tab. This includes:

- Application options
- [License key information](Softwareregistration.md), if applicable
- [Naming conventions](Namingconventions.md)
- [Custom properties](Userdefinedcustomproperties.md)
- [Excel options](Excelfile.md)

&nbsp;

Whether you're using Chrome, Edge, Brave, Firefox, or Safari, enabling site data is a simple yet effective step towards enhancing your user experience with Hackolade Studio Browser.

&nbsp;

In private/incognito/guest mode, the browser does not block site data but it clears them when closing the window. From a user's perspective, the result is the same: the state of the application is lost. We provide a *Health Check* screen, as shown below to evaluate the environment and its impact on our functionality:

&nbsp;

You can reach the Health Check screen either by clicking the icon in the lower left-hand corner off the screen, or by choosing the menu option Help > Health Check. When all parameters are OK, you should see a screen like this one:\
![Browser health check OK](<lib/Browser health check OK.png>)

&nbsp;

Running the same in incognito mode, for example, reveals expected issues:\
![Browser health check NOK](<lib/Browser health check NOK.png>)

&nbsp;

**Note** that we do not use any cookies in general, or specifically any [cross-domain cookies](<https://syrenis.com/resources/blog/what-is-a-cross-domain-cookie/> "target=\"_blank\""). What we do use is a browser’s "siteData", which are not shared across domains. In other words, this information cannot be read when surfing on another site. No information is shared with other websites, which should address any privacy, security, consent or control concerns.

&nbsp;

### Google Chrome

In the address bar, type *chrome://settings/content/siteData*

&nbsp;

You have the option to enable site data universally or solely for selected websites. Should you prefer the latter, make sure to add the URL [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"") to the list of sites allowed to store data on your devices.

&nbsp;

Reload the application for the changes to take effect

&nbsp;

### Microsoft Edge

In the address bar, type *edge://settings/content/cookies*

&nbsp;

You have the option to enable site data universally or solely for selected websites. Should you prefer the latter, make sure to add the URL [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"") to the list of sites allowed to store data on your devices.

&nbsp;

Reload the application for the changes to take effect.

&nbsp;

### Brave

Click on the Brave icon located in the address bar.

&nbsp;

Select "Allow all cookies" or "Block cross-site cookies" from the menu. Brave automatically reloads the application, applying the new privacy settings.

&nbsp;

### Mozilla Firefox

In the address bar, type about:*preferences#privacy*

&nbsp;

In the "Cookies and Site Data" section, click on "Manage Exceptions."

&nbsp;

Make sure to add the [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"") to the list of sites allowed to store data on your devices.

&nbsp;

Reload the application for the changes to take effect

&nbsp;

### Safari

Go to Safari > Settings > Privacy > Advanced settings.

&nbsp;

Disable the "Block all cookies" option.

&nbsp;

Reload the application for the settings to take effect.
