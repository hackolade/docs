# Which license should I choose?

At Hackolade, we try to make it easy and convenient to do business with us, and to respond to customer needs.  This includes a flexible pricing plan.  But so many options may make decisions more difficult. &nbsp;

&nbsp;

As per the terms of our [License Agreement](<Licenseagreement.md>), the license metric is per "per seat", and a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent method, a separate Product license seat is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

&nbsp;

A "seat" is an instance of a license key.&nbsp; A license key can be issued for multiple instances, which we call a seat.&nbsp; Here’s a [Wikipedia explanation](<https://en.wikipedia.org/wiki/Per-seat\_license> "target=\"\_blank\"") as well.&nbsp; We do not use the definition “per user”, because it could be interpreted as a possibility for individual users to use the software on as many machines as they wish, which is not the case.&nbsp; We do not use the definition “per machine” either, because with Virtual Machines, the term could be interpreted as a possibility to install it on a single machine and allow an unlimited number of users to use the software, which is not the case either.&nbsp; Therefore “per seat” seems to be the adequate definition.

&nbsp;

There are two main dimensions to our pricing:

**&#49;. Authors vs. Viewers**

**&#50;. Dedicated vs. Concurrent**

Both authoring and viewing license keys are available in either dedicated or concurrent types.\
&nbsp;

## Authors vs Viewers

Hackolade Studio licenses are available in two types: **authoring** (for creating and maintaining models) and **viewing** (for read-only access). Both types can be purchased as either **dedicated** or **concurrent** licenses.

**\- Authors**: Typically data modelers, data architects, or data engineers. They use the **Workgroup Edition**, which allows editing and saving data models, provided the user has appropriate write permissions in the storage layer.

**\- Viewers**: Typically subject-matter experts, business users, or any user -- technical or non-technical -- who only needs read-only access. Viewer licenses are priced at one-tenth the cost of Workgroup licenses.

&nbsp;

### Professional vs Workgroup

The Workgroup Edition of Hackolade Studio includes all of the features of the Professional edition, plus a native integration with Git repositories for your data models. &nbsp; The Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool, to leverage collaboration, versioning, branching, change tracking, peer review, and other related capabilities detailed [here](<Repository.md>). &nbsp;

&nbsp;

Because of the added value of Git integration, most new licenses today are for the **Workgroup Edition**, even for individual users

&nbsp;

See [this page](<https://hackolade.com/editions.html> "target=\"\_blank\"") for a detailed comparison of editions.

&nbsp;

## Dedicated vs Concurrent

**Dedicated licenses** are best suited for regular, intensive users. Each license is tied to a single seat rather than to a named user. A seat is associated with an OS user instance, whether on Windows, Mac, Linux for desktop deployments, or a browser instance for browser deployments. Seats can be reassigned through a [self-service process](<Transferalicensetoanewcomputer.md>) without providing personal information, which offers flexibility while protecting privacy and supporting regulatory compliance. However, if you use two PCs, you will need either two separate licenses or a license that covers two seats. This arrangement is often referred to as [node-locked](<https://en.wikipedia.org/wiki/Node-locked\_licensing> "target=\"\_blank\"").

&nbsp;

**Concurrent licenses**, on the other hand, are better suited for organizations with many occasional users. The software can be installed on an unlimited number of PCs, but only the licensed number of users can access it at the same time. If the maximum number of concurrent users is reached, additional users must wait until a seat becomes available. This setup does not require an on-premises server and is sometimes referred to as a [floating](<https://en.wikipedia.org/wiki/Floating\_licensing> "target=\"\_blank\"") license.&nbsp; View [this video](<https://community.hackolade.com/slides/slide/concurrent-license-key-behavior-66> "target=\"\_blank\"") to fully understand the behavior of a concurrent license key.

&nbsp;

Many customers choose to have a mix of dedicated and concurrent seats.&nbsp; Dedicated to support the needs of intensive users of Hackolade Studio, plus concurrent to support the needs of occasional users. &nbsp;

&nbsp;

The **pricing model for concurrent licenses** is based on the maximum number of simultaneous users (the size of the pool of seats licensed), rather than the total number of potential users. For example, an organization with 200 potential users but only 20 people who need to access the software at the same time would require just 20 seats. The ratio of total users to concurrent seats varies depending on how intensively the software is used within the organization, typically ranging from 10-to-1 down to 4-to-1. Concurrent seats are priced at four times the cost of dedicated seats.

&nbsp;

&nbsp;

![Dedicated vs concurrent license seat](<lib/Dedicated vs concurrent license seat 1.png>)

In the above example, the concurrent license was for a single seat, meaning that only one user at a time could use Hackolade Studio.&nbsp; If you purchase a concurrent license key with 2 seats, now you can have any combination of 2 simultaneous users:

![Dedicated vs concurrent license with 2 seats](<lib/Dedicated vs concurrent license with 2 seats.png>)

&nbsp;

While the unit price of a concurrent license is more expensive than an individual license, you need a lot less seats to satisfy an equivalent number of users.&nbsp; For example, you may need only 50 concurrent license seats to satisfy usage by 200 users, counting on the fact that only 50 out of the 200 users can use the software at the same time.

![License keys tracked in the cloud](<lib/License keys tracked in the cloud.png>)

There is no need to install and maintain a server inside your infrastructure.  The number of seats being used is tracked by our license server in the cloud. &nbsp;

&nbsp;

You may also want to consult [this page](<Concurrentlicensekeybehavior.md>) with more details on the behavior of concurrent license keys.

&nbsp;

## Virtual Machines or Remote Desktop access

**License metric “per seat”:&nbsp; what does it mean?**\
A license grants the right to use the product as defined by *Authorized Use*. The license metric is “per seat,” which means the number of authorized users specified on your invoice determines how many may use the software. A separate license is required for each device on or from which the product is used or accessed.

&nbsp;

**Can I use the same license key on both my home desktop and my work laptop?**\
No. Licenses are not tied to named users but to devices. You must obtain a separate license for each device you use to access the product.

&nbsp;

**Can Hackolade Studio be installed on a server accessed via Remote Desktop?**\
Yes, Remote Desktop access is supported. However, a license seat is required for each unique combination of host machine, user login, and remote client accessing the application.

When Hackolade is installed on a virtual machine (VM) and shared among multiple users or accessed through Windows Remote Desktop, licensing is not attached solely to the host machine. Instead, it is tied to the combination of the host, the remote machine, the user login, and other parameters that define the uniqueness of each session.

If multiple users access Hackolade on the same machine, whether through Terminal Server, Remote Desktop, Windows App, Citrix, or another VM solution, then each user and PC requires its own license seat. In other words, you need a license for every user/device combination that accesses the installation.

**Example:** Four Hackolade Studio users sharing a single VM require four license seats, the same as if they were running Hackolade Studio on four individual PCs.

&nbsp;

## Notes

**&#49;)** dedicated licenses, concurrent licenses, and subscriptions are all controlled by our license server in the cloud.

**&#50;)** the information above also applies to installations using only the Command-Line Interface in automated mode.  A CLI process requires a licensed installation, just as any desktop user.  If a CLI process is run from a user's workstation, it uses the same license as the GUI application.

&#51;) the Collibra integration is an add-on feature which requires a specific license key

