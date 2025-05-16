# Which license should I choose?

At Hackolade, we try to make it easy and convenient to do business with us, and to respond to customer needs.  This includes a flexible pricing plan.  But so many options may make decisions more difficult. &nbsp;

&nbsp;

As per the terms of our [License Agreement](<Licenseagreement.md>), the license metric is per "per seat", and that a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

&nbsp;

A "seat" is an instance of a license key.&nbsp; A license key can be issued for multiple instances, which we call a seat.&nbsp; Here’s a [Wikipedia explanation](<https://en.wikipedia.org/wiki/Per-seat\_license> "target=\"\_blank\"") as well.&nbsp; We do not use the definition “per user”, because it could be interpreted as a possibility for individual users to use the software on as many machines as they wish, which is not the case.&nbsp; We do not use the definition “per machine” either, because with Virtual Machines, the term could be interpreted as a possibility to install it on a single machine and allow an unlimited number of users to use the software, which is not the case either.&nbsp; Therefore “per seat” seems to be the adequate definition.

&nbsp;

There are 2 dimensions in our pricing:

&#49;) Professional vs Workgroup\
&#50;) Dedicated vs Concurrent\
&nbsp;

## Professional vs Workgroup

The Workgroup Edition of Hackolade Studio includes all of the features of the Professional edition, plus a native integration with Git repositories for your data models. &nbsp; The Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool, to leverage versioning, branching, change tracking, collaboration, peer review, and other related capabilities detailed [here](<Repository.md>).

&nbsp;

Access this page to [compare the different editions](<https://hackolade.com/editions.html> "target=\"\_blank\"").

&nbsp;

## Dedicated vs Concurrent

You may want to view [this video](<https://community.hackolade.com/slides/slide/concurrent-license-key-behavior-66> "target=\"\_blank\"") to fully understand the behavior of a concurrent license key.

Each individually dedicated workstation license or subscription is attached to a single "seat".  It means that the license is not attached to a named user, but to an OS user instance (Windows, Mac, or Linux for the Desktop deployment, or browser in the case of the browser deployment.) &nbsp;

Many people are familiar with the concept of "named user" licenses.&nbsp; The fact we don’t have “named user” licenses but “dedicated” licenses is a subtle nuance, but unnamed dedicated licenses provides you with extra flexibility since we, at Hackolade, don’t care about who is using the license.  You may actually re-assign it self-service without involving us, as per the procedure in [this article.](<Movingtoanothercomputer.md>)  Plus, we don’t need to record any personal information about who is using the license., which is to everyone’s advantage.

However, If you have 2 PCs you need either 2 licenses, or a license for 2 seats.&nbsp; This type of license is often referred to as [node-locked](<https://en.wikipedia.org/wiki/Node-locked\_licensing> "target=\"\_blank\"").

Dedicated license keys are for exclusive use by regular, intensive users of the application, whereas the concurrent license key is for shared use across many occasional users.

Some organizations prefer the flexibility of concurrent licenses.  In this case, you may install the software on an unlimited number PCs, but only the licensed number of simultaneous users are allowed to use the application.  If the maximum number of seats has been reached, the next user will be denied access to the application until another user exits the application.  This scheme does not require a special server on-premises.&nbsp; This type of license is sometimes referred to as [floating](<https://en.wikipedia.org/wiki/Floating\_licensing> "target=\"\_blank\"").

![Dedicated vs concurrent license seat](<lib/Dedicated vs concurrent license seat 1.png>)

In the above example, the concurrent license was for a single seat, meaning that only one user at a time could use Hackolade Studio.&nbsp; If you purchase a concurrent license key with 2 seats, now you can have any combination of 2 simultaneous users:

![Dedicated vs concurrent license with 2 seats](<lib/Dedicated vs concurrent license with 2 seats.png>)

&nbsp;

While the unit price of a concurrent license is more expensive than an individual license, you need a lot less seats to satisfy an equivalent number of users.&nbsp; For example, you may need only 25 concurrent license seats to satisfy&nbsp; usage by 100 users, counting on the fact that only 25 out of the 100 users can use the software at the same time.

![License keys tracked in the cloud](<lib/License keys tracked in the cloud.png>)

There is no need to install and maintain a server inside your infrastructure.  The number of seats being used is tracked by our license server in the cloud. &nbsp;

&nbsp;

Many organizations purchase a mix of dedicated and concurrent keys.&nbsp; This mix allows for users who need Hackolade Studio all day every day to be confident that they will never be locked out of seat.&nbsp; And at the same time, the cost of allowing more ad-hoc users to access the application, for example half a day every 2 weeks during the design phase of each spring) is spread across a pool of users.

&nbsp;

Concurrent licenses are not available for purchase with a credit card.  They are 4 times more expensive per seat than an individual license.

You may also want to consult [this page](<Concurrentlicensekeybehavior.md>) with more details on the behavior of concurrent license keys.

## Virtual Machines or Remote Desktop access

License metric "per seat": what does it mean?&nbsp; License means the right to use the Product as defined by Authorized Use. License metric is "per seat", meaning that the number of Authorized Users specified on the Invoice may use the software. A license must be obtained for each device on or from which the Product is used or accessed.

&nbsp;

If I have a desktop at home and a laptop at work, does it mean that I can use the same license key? **No**, our license metric is not based on named users. A license must be obtained for each device on or from which the Product is used or accessed.

&nbsp;

My company wants to install Hackolade on a server accessed via Remote desktop: is it possible? **Yes**, Remote Desktop is possible. However, a license seat is required **for each combination of host, user login, and remote client** accessing the application.

&nbsp;

When installing Hackolade on a VM to share among multiple users and/or accessed via Windows Remote Desktop, it is important to realize that licensing is not attached to just the host machine, but to the combination of the host machine, the remote machine, the user login, and other parameters to determine the uniqueness of the session.

&nbsp;

If you have 1 machine with multiple users (using for example Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent Virtual Machine method), you will need one license per user and PC accessing the Hackolade installation on the server.  A license must be obtained for each device on or from which the Product is used or accessed.  As a result, you need a license seat per user of that VM.

&nbsp;

Example: having 4 Hackolade users on a single VM is the equivalent of having 4 individual PCs running Hackolade from a licensing point of view: you need 4 license seats to be validated.

&nbsp;

Using a concurrent license key simplifies greatly the behavior in case of VMs and RDP.

## Notes

**&#49;)** dedicated licenses, concurrent licenses, and subscriptions are all controlled by our license server in the cloud.

**&#50;)** the information above also applies to installations using only the Command-Line Interface in automated mode.  A CLI process requires a licensed installation, just as any desktop user.  If a CLI process is run from a user's workstation, it uses the same license as the GUI application.

&#51;) the Collibra integration is an add-on feature which requires a specific license key

