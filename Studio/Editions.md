# Editions

There are different permutations to be aware of: Hackolade Studio is available in several different editions, 2 deployments, and 2 license models.&nbsp; All run the exact same code base.&nbsp; The license key, with its parameters in our license server, determines whether a given feature is enabled or not.

&nbsp;

| &nbsp; **Edition** | **Deployment** |  |  **License Key** **Required** | &nbsp; **License model** | **Git repo interactions** |  |
| --- | :---: | :---: | :---: | :---: | :---: | :---: |
|  | **Desktop** | **Browser** |  |  | **Desktop** | **Browser** |
| Community | **Yes** | **Yes** | *No* | n/a | *No* | *No* |
| Trial | **Yes** | *No* | **Yes** | Dedicated | **Local clone or remote** | n/a |
| Viewer | **Yes** | **Yes** | **Yes** | Dedicated or Concurrent | **Read-only** | **Read-only** |
| Personal | **Yes** | *Partially\** | **Yes** | Dedicated | *No* | *No* |
| Professional | **Yes** | *Partially\** | **Yes** | Dedicated or Concurrent | *No* | *No* |
| Workgroup | **Yes** | *Partially\** | **Yes** | Dedicated or Concurrent | **Local clone or remote** | **Remote repo only** |


&nbsp;

\*: since v7.9.3, it is allowed to use of license keys in the browser for all editions except free trial.&nbsp; Warning: not all features of Personal, Pro, and Workgroup Editions are enabled yet in the browser.&nbsp; We will progressively enable additional features in the browser, within the limits allowed by W3C security concerns. **The desktop app remains the flagship with all feature capabilities.** &nbsp;

&nbsp;

For example we recently enabled reverse-engineering with the browser from a Databricks instance, and will soon add from a BigQuery and also Snowflake instance.&nbsp; But you will never be able with the browser to reverse-engineer from an Oracle on-prem database, at least not without an “agent” (for security reasons as explained [here](<Security-firstbrowserdeployment.md>).)&nbsp; Our agent will remain the desktop.&nbsp; Also, we currently cannot execute, in the browser, some features of the desktop:&nbsp; external references, derive from polyglot, update references, or handle the Git workflow such as submit for review, review change/pull requests.

&nbsp;

The license seat can be shared across the desktop and the browser on a single machine, for example is a desktop user wants to verify that a [model link](<SharemodellinkURL.md>) works as expected in the browser.&nbsp; Again for browser security reasons, it is impossible for the browser to access the license information of the desktop.&nbsp; The process allows such exchange without causing any security risk, and without impeding our revenue protection.&nbsp; This license seat sharing process is described [here](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop>).

&nbsp;

## Deployment

Hackolade Studio has traditionally been available as an offline desktop application for Windows, Mac, and Linux.&nbsp; Starting with v7.0.0, it is now also available as a security-first [cross-browser](<https://en.wikipedia.org/wiki/Cross-browser> "target=\"\_blank\"") [serveless](<https://en.wikipedia.org/wiki/Serverless\_computing> "target=\"\_blank\"") [web app](<https://en.wikipedia.org/wiki/Web\_application> "target=\"\_blank\"") which can open data models from and save them to your local environment.&nbsp; All from the same code base, meaning that, as we add [weekly enhancements](<https://hackolade.com/versionInfo/ReadMe.txt> "target=\"\_blank\"") and new features, they are deployed automatically to the offline desktop (provided that you upgrade to that latest version...) and the online browser.&nbsp; The latest version is exactly the same for the browser deployment and all desktop operating systems.&nbsp; &nbsp;

&nbsp;

The main benefit of a browser deployment is that users don't need to download an application to their desktop, and are always running the latest version of the application.&nbsp; The Hackolade Studio deployment in the browser has a unique security-first approach in the sense that data models are not stored on our servers.&nbsp; They never leave your network because you store them on your own local file system or Git repository, for enhanced confidentiality, data security, and privacy of your information.&nbsp; Processing is performed locally within your browser tab. There are no cookies, no advertisements, no analytics, no browser fingerprinting, and no tracking beacons

&nbsp;

Our browser deployment supports the latest versions of Chrome, Edge, Brave, Firefox browsers and Safari.&nbsp; For the best user experience, you should use Chrome or Edge, because Brave, Firefox, and Safari do not currently support the [File System Access API](<https://wicg.github.io/file-system-access/> "target=\"\_blank\""), resulting in some features having a graceful degradation of the user experience. &nbsp;

&nbsp;

Whether you're using Chrome, Edge, Brave, Firefox, or Safari, enabling site data is a simple yet effective step towards enhancing your user experience with Hackolade Studio Browser.&nbsp;

&nbsp;

It is also better to use your browser in its standard mode, i.e. NOT in a guest, private, or incognito tab.&nbsp; While we don't use cookies, we do leverage some features of what's called "site data" capabilities in your browser.&nbsp; Adjusting your browser settings to enable site data for Hackolade Studio Browser ensures that your settings are preserved, even after reloading the application or starting a new session in a new tab. This includes:

&nbsp;

\- Application options

\- [License key information](<Softwareregistration.md>), if applicable

\- [Naming conventions](<Namingconventions.md>)

\- [Custom properties](<Userdefinedcustomproperties.md>)

\- [Excel options](<Excelfile.md>)

&nbsp;

More information can be found in [this page](<Security-firstbrowserdeployment.md>).

&nbsp;

**Note:** while it is possible to consult a model on a tablet, you should be aware of the fact that the application has not been optimized for touchscreen experience, but well for mouse interactions.

&nbsp;

## Edition

The different editions are listed below.&nbsp; Access this page to [compare the different editions](<https://hackolade.com/editions.html> "target=\"\_blank\"").

&nbsp;

* &nbsp;
  * Workgroup Edition: The Workgroup Edition of Hackolade Studio includes all of the features of the Professional edition, plus a native integration with Git repositories for your data models.&nbsp; The Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool, to leverage versioning, branching, change tracking, collaboration, peer review, and other related capabilities.&nbsp; The Workgroup does NOT include the Collibra integration features. This option requires the purchase of an optional upgrade.
  * Professional Edition: The Professional Edition of Hackolade includes all the features of the Community and Personal editions, and much more\!&nbsp; With no limit on the size of models, this premium version produces documentation in different flexible formats.&nbsp; The Professional does NOT include the Collibra integration features, or the Workgroup-specific features such as the Git integration. These options require the purchase of an optional upgrade. Key features include forward- and reverse-engineering functions tightly integrated with supported technology. Maintain your schema documentation in sync with your production instance, thanks to the ability to compare different versions of your model.&nbsp;
  * Personal Edition: The Personal Edition of Hackolade is ideal for startups and individual developers. It includes all the features of the Community edition plus very flexible HTML or Markdown documentation to share models with team members, and the capability to model an unlimited number of objects. You may also compare models and suggest the denormalization of existing relational models.&nbsp; The Personal edition does not include the advanced features of the Professional such as Forward- and Reverse-Engineering functions for each database target.
  * Viewer Edition: The read-only viewer allows navigation through models for consultation purposes only -- no creation or editing, no forward-engineering (except JSON Schema and Excel) or reverse-engineering. When connected to Git repositories, it also allows pull operations and commenting on change requests.
  * Evaluation Edition:&nbsp; Free 14-day evaluation of all the great features of Hackolade, without any restrictions.
  * Community Edition: The Community Edition of Hackolade Studio is completely FREE. It is an entry-level data modeling software with a subset of the Hackolade Personal and Professional Editions. It is a great way for students and those new to modeling to get started with an industry-leading data modeling tool.&nbsp; The Community edition offers many of the core features of data modeling with a limit of 50 model objects (an object being a table or an attribute.) It includes Entity Relationship diagrams; the hierarchical schema view of JSON collections, and PDF documentation.&nbsp; But it does not include forward and reverse engineering, or HTML documentation.

&nbsp;

&nbsp;

The&nbsp; above editions are packaged in the same software.&nbsp; The activation key obtained through the Hackolade store determines feature access within the application.

&nbsp;

&nbsp;**(\*):** License metric is per "per seat", meaning that the number of Authorized Users specified on the Invoice may use the software. A license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed. \
**(\*\*):** concurrent (aka floating) licenses do NOT require a license server on premises.

&nbsp;

Each edition is available natively for the following platforms:

* &nbsp;
  * Windows: 64-bit
  * Mac OSX, both Intel processor and Apple Silicon ARM
  * Linux: 64-bit

&nbsp;

## License model

Most of the paid for licenses are available in 2 models: dedicated or concurrent.&nbsp; The price is quite different because of the added flexibility and value of the concurrent model.&nbsp; Also, you do not need as many concurrent seats for the same number of users. &nbsp;

&nbsp;

All details are described in [this page](<WhichlicenseshouldIchoose.md>).

&nbsp;

