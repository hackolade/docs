# Editions

There are different permutations to be aware of: Hackolade Studio is available in several different editions, 2 deployments, and 2 license models. All run the exact same code base. The license key, with its parameters in our license server, determines whether a given feature is enabled or not.

&nbsp;

<table style="width:100%">
<colgroup><col style="width:12%"><col style="width:9%"><col style="width:10%"><col style="width:10%"><col style="width:11%"><col style="width:12%"><col style="width:12%"><col style="width:13%"><col style="width:11%"></colgroup>
<thead>
<tr>
<th rowspan="2">Edition</th>
<th colspan="2">Deployment</th>
<th rowspan="2"><p>License Key</p><p>Required</p></th>
<th rowspan="2">License model</th>
<th colspan="2">Git repo interactions</th>
<th colspan="2">AI-Assisted Data Modeling</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Desktop</strong></td>
<td><strong>Browser</strong></td>
<td><strong>Desktop</strong></td>
<td><strong>Browser</strong></td>
<td><strong>Desktop</strong></td>
<td><strong>Browser</strong></td>
</tr>
<tr>
<td>Community</td>
<td><strong>Yes</strong></td>
<td><strong>Yes</strong></td>
<td><em>No</em></td>
<td>n/a</td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
</tr>
<tr>
<td>Trial</td>
<td><strong>Yes</strong></td>
<td><em>No</em></td>
<td><strong>Yes</strong></td>
<td>Dedicated</td>
<td><strong>Local clone or remote</strong></td>
<td>n/a</td>
<td><strong>Yes</strong></td>
<td><strong>Yes</strong></td>
</tr>
<tr>
<td>Viewer</td>
<td><strong>Yes</strong></td>
<td><strong>Yes</strong></td>
<td><strong>Yes</strong></td>
<td>Dedicated or Floating</td>
<td><strong>Read-only</strong></td>
<td><strong>Read-only</strong></td>
<td><em>No</em></td>
<td><em>No</em></td>
</tr>
<tr>
<td>Personal</td>
<td><strong>Yes</strong></td>
<td><em>Partially*</em></td>
<td><strong>Yes</strong></td>
<td>Dedicated</td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
</tr>
<tr>
<td>Professional</td>
<td><strong>Yes</strong></td>
<td><em>Partially*</em></td>
<td><strong>Yes</strong></td>
<td>Dedicated or Floating</td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
<td><em>No</em></td>
</tr>
<tr>
<td>Workgroup</td>
<td><strong>Yes</strong></td>
<td><em>Partially*</em></td>
<td><strong>Yes</strong></td>
<td>Dedicated or Floating</td>
<td><strong>Local clone or remote</strong></td>
<td><strong>Remote repo only</strong></td>
<td><em>No</em></td>
<td><em>No</em></td>
</tr>
<tr>
<td>Ultimate</td>
<td><strong>Yes</strong></td>
<td><em>Partially*</em></td>
<td><strong>Yes</strong></td>
<td>Dedicated or Floating</td>
<td><strong>Local clone or remote</strong></td>
<td><strong>Remote repo only</strong></td>
<td><strong>Yes</strong></td>
<td><strong>Yes</strong></td>
</tr>
</tbody>
</table>

&nbsp;

\*: since v7.9.3, it is allowed to use of license keys in the browser for all editions except free trial. Warning: not all features of Personal, Pro, and Workgroup Editions are enabled yet in the browser. We will progressively enable additional features in the browser, within the limits allowed by W3C security concerns. **The desktop app remains the flagship with all feature capabilities.**

&nbsp;

For example we recently enabled reverse-engineering with the browser from a Databricks instance and BigQuery. But you will never be able with the browser to reverse-engineer from an Oracle on-prem database, at least not without an “agent” (for security reasons as explained [here](Security-firstbrowserdeployment.md).) Our agent will remain the desktop application. For Snowflake and other cloud databases that do not allow modifications to the CORS configuration, there are at least 3 possible alternatives:

- Use the Desktop app as an “agent”, when a reverse-engineering action is required, then place the resulting data model in the Git repository, then have the data modelers continue their work in the browser
- Execute the same action, but more automated via an instance of our Command-Line Interface, possibly running in a “bastion” architecture and behind a customer-developed portal, as described in [this page](BastioninstanceforHackoladeStudi.md). The added benefit of this architecture, as implemented at many of our finance industry customers, is that it is not even necessary to provide database access credentials to data modelers, if this matter is a concern for your customer.
- Deploy a reverse-proxy, as described [here](<https://hackolade.com/help/ConfluentSchemaRegistry.html#Configure%20CORS%20to%20access%20Confluent%20Schema%20Registries%20from%20Hackolade%20Studio%20in%20the%20browser>), but this solution seems too complex to implement and maintain, and one of the previous 2 options is generally judged not only to be sufficient but also more desirable.

&nbsp;

More generally, all operation that exchange with external systems where CORS security and/or multiple file handling are involved, are hard to handle in the browser. This includes publishing to governance platforms such as Collibra or DataHub. Or the generation of the documentation in HTML, Markdown, or PDF. Or the API model generation. All these operations are better handled via the CLI or the Desktop deployment.

&nbsp;

Also, we currently cannot execute, in the browser, some features of the desktop: bundle changes to multiple data models in a single commit (same limitation as github.com versus GitHub Desktop for WIndows), or handle the Git workflow such as submit for review, review change/pull requests, all of which having workarounds using the web pages of the Git provider.

&nbsp;

The license seat can be shared across the desktop and the browser on a single machine, for example is a desktop user wants to verify that a [model link](SharemodellinkURL.md) works as expected in the browser. Again for browser security reasons, it is impossible for the browser to access the license information of the desktop. The process allows such exchange without causing any security risk, and without impeding our revenue protection. This license seat sharing process is described [here](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop>).

&nbsp;

## Deployment

Hackolade Studio has traditionally been available as an offline desktop application for Windows, Mac, and Linux. Starting with v7.0.0, it is now also available as a security-first [cross-browser](<https://en.wikipedia.org/wiki/Cross-browser> "target=\"_blank\"") [serveless](<https://en.wikipedia.org/wiki/Serverless_computing> "target=\"_blank\"") [web app](<https://en.wikipedia.org/wiki/Web_application> "target=\"_blank\"") which can open data models from and save them to your local environment. All from the same code base, meaning that, as we add [weekly enhancements](<https://hackolade.com/versionInfo/ReadMe.txt> "target=\"_blank\"") and new features, they are deployed automatically to the offline desktop (provided that you upgrade to that latest version...) and the online browser. The latest version is exactly the same for the browser deployment and all desktop operating systems.

&nbsp;

The main benefit of a browser deployment is that users don't need to download an application to their desktop, and are always running the latest version of the application. The Hackolade Studio deployment in the browser has a unique security-first approach in the sense that data models are not stored on our servers. They never leave your network because you store them on your own local file system or Git repository, for enhanced confidentiality, data security, and privacy of your information. Processing is performed locally within your browser tab. There are no cookies, no advertisements, no analytics, no browser fingerprinting, and no tracking beacons

&nbsp;

Our browser deployment supports the latest versions of Chrome, Edge, Brave, Firefox browsers and Safari. For the best user experience, you should use Chrome or Edge, because Brave, Firefox, and Safari do not currently support the [File System Access API](<https://wicg.github.io/file-system-access/> "target=\"_blank\""), resulting in some features having a graceful degradation of the user experience.

&nbsp;

Whether you're using Chrome, Edge, Brave, Firefox, or Safari, enabling site data is a simple yet effective step towards enhancing your user experience with Hackolade Studio Browser.

&nbsp;

It is also better to use your browser in its standard mode, i.e. NOT in a guest, private, or incognito tab. While we don't use cookies, we do leverage some features of what's called "site data" capabilities in your browser. Adjusting your browser settings to enable site data for Hackolade Studio Browser ensures that your settings are preserved, even after reloading the application or starting a new session in a new tab. This includes:

- Application options
- [License key information](Softwareregistration.md), if applicable
- [Naming conventions](Namingconventions.md)
- [Custom properties](Userdefinedcustomproperties.md)
- [Excel options](Excelfile.md)

&nbsp;

More information can be found in [this page](Security-firstbrowserdeployment.md).

&nbsp;

> [!NOTE]
> While it is possible to consult a model on a tablet, you should be aware of the fact that the application has not been optimized for touchscreen experience, but well for mouse interactions.

&nbsp;

## Edition

The different editions are listed below. Access this page to [compare the different editions](<https://hackolade.com/editions.html> "target=\"_blank\"").

- Ultimate Edition: The Ultimate Edition of Hackolade Studio includes all of the features of the Workgroup edition, plus features of AI-assisted data modeling. Our approach to AI integration is built on customer control, confidentiality, and responsible use. AI capabilities are disabled by default and enabled only at the customer’s choice. Customers remain free to select the LLM, model, or provider that best meets their security, regulatory, and operational requirements, including self-hosted or on-premises models where appropriate. This helps protect sensitive metadata, schemas, and data models from unintended exposure, third-party retention, or unauthorized use for model training.\
  The Ultimate Edition makes it easy for users to leverage the AI of their choice, even proprietary or on-prem, without any data leakage. Nothing passes through Hackolade infrastructure. [this section](DatamodelingandtheAIlifecycle.md) of our online documentation.\
  The Ultimate Edition does NOT include the Governance Platform Integration features for Collibra, DataHub, etc. This option requires the purchase of an optional upgrade. Make sure to consult the full comparison of editions below.
- Workgroup Edition: The Workgroup Edition of Hackolade Studio includes all of the features of the Professional edition, plus a native integration with Git repositories for your data models. The Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool, to leverage versioning, branching, change tracking, collaboration, peer review, and other related capabilities.\
  The Workgroup does NOT include the Governance Platform Integration features for Collibra, DataHub, etc. . This option requires the purchase of an optional upgrade.
- Professional Edition: The Professional Edition of Hackolade includes all the features of the Community and Personal editions, and much more! With no limit on the size of models, this premium version produces documentation in different flexible formats.\
  The Professional does NOT include the Governance Platform Integration features for Collibra, DataHub, etc., or the Workgroup-specific features such as the Git integration. The Professional Edition does NOT include the AI-assisted data modeling features of the Ultimate Edition. These options require the purchase of an optional upgrade. Key features include forward- and reverse-engineering functions tightly integrated with supported technology. Maintain your schema documentation in sync with your production instance, thanks to the ability to compare different versions of your model.
- Personal Edition: The Personal Edition of Hackolade is ideal for startups and individual developers. It includes all the features of the Community edition plus very flexible HTML or Markdown documentation to share models with team members, and the capability to model an unlimited number of objects. You may also compare models and suggest the denormalization of existing relational models.\
  The Personal edition does not include the advanced features of the Professional such as Forward- and Reverse-Engineering functions for each database target.
- Viewer Edition: The read-only viewer allows navigation through models for consultation purposes only -- no creation or editing, no forward-engineering (except JSON Schema and Excel) or reverse-engineering. When connected to Git repositories, it also allows pull operations and commenting on change requests.
- Evaluation Edition: Free 14-day evaluation of all the great features of Hackolade, without any restrictions.
- Community Edition: The Community Edition of Hackolade Studio is completely FREE. It is an entry-level data modeling software with a subset of the Hackolade Personal and Professional Editions. It is a great way for students and those new to modeling to get started with an industry-leading data modeling tool. The Community edition offers many of the core features of data modeling with a limit of 50 model objects (an object being a table or an attribute.) It includes Entity Relationship diagrams; the hierarchical schema view of JSON collections, and PDF documentation. But it does not include forward and reverse engineering, or HTML documentation.

&nbsp;

The above editions are packaged in the same software. The activation key obtained through the Hackolade store determines feature access within the application.

&nbsp;

**(\*):** License metric is per "per seat", meaning that the number of Authorized Users specified on the Invoice may use the software. A license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.\
**(\*\*):** floating (aka concurrent) licenses do NOT require a license server on premises.

&nbsp;

Each edition is available natively for the following platforms:

- Windows: 64-bit
- Mac OSX, both Intel processor and Apple Silicon ARM
- Linux: 64-bit

&nbsp;

## License model

Most of the paid for licenses are available in 2 models: dedicated or floating. The price is quite different because of the added flexibility and value of the floating model. Also, you do not need as many floating seats for the same number of users.

&nbsp;

All details are described in [this page](WhichlicenseshouldIchoose.md).
