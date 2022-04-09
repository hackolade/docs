# Perpetual license or subscription: which one should I choose?

At Hackolade, we try to make it easy and convenient to do business with us, and to respond to customer needs.  This includes a flexible pricing plan.  But so many options may make decisions more difficult. &nbsp;

As per the terms of our [License Agreement](<Licenseagreement.md>), the license metric is per "per seat", and that a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Citrix XenDesktop or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

A "seat" is an instance of a license key.&nbsp; A license key can be issued for multiple instances, which we call a seat.&nbsp; Here’s a [Wikipedia explanation](<https://en.wikipedia.org/wiki/Per-seat\_license> "target=\"\_blank\"") as well.&nbsp; We do not use the definition “per user”, because it could be interpreted as a possibility for individual users to use the software on as many machines as they wish, which is not the case.&nbsp; We do not use the definition “per machine” either, because with Virtual Machines, the term could be interpreted as a possibility to install it on a single machine and allow an unlimited number of users to use the software, which is not the case either.&nbsp; Therefore “per seat” seems to be the adequate definition.

&nbsp;

There are 2 dimensions in our pricing:\
&#49;) Perpetual vs Subscription\
&#50;) Individual vs Concurrent\
&#51;) Professional vs Workgroup

## Perpetual vs Subscription

For credit card purchases, Hackolade Studio is only available using the subscription model.

If you hesitate between the subscription model and the perpetual model, here are a few aspects to consider when making your choice:

### Accounting

Capex vs Opex: some finance departments wish to capitalize software licenses and amortize then over several years.  They may prefer to purchase a perpetual license.  Others prefer to expense as fast as possible and will opt for a subscription.

### Cash flow and Total Cost of Ownership

For one license, it is easy to create a spreadsheet and visualize the tipping point between a perpetual license with annual maintenance and a subscription.  Assuming maintenance renewal annually for a perpetual license, it is in year 3 that a perpetual license becomes advantageous for the user, over a subscription.

### Protection against price increases

Prices are subject to change without notice.  Price increases affect perpetual licenses and their annual maintenance, and also subscriptions.  Some customers purchasing perpetual licenses, also prepay annual maintenance and support for several years in advance.  Others prepay several years of subscriptions.

### Major upgrades and support

Customers are entitled to free major and minor upgrades plus support for a perpetual license, but only as long as they have paid for the renewal (first year is mandatory and included in the original purchase.)  If the license key is purchased via our e-commerce platform, the renewal is announced via email a couple of weeks prior to the transaction, and it is automatically charged to the credit card on file, unless the renewal is cancelled.  If renewal fails or has been canceled, the user retains the right to use the software perpetually, but will no longer be entitled to upgrades or support.

Subscriptions include minor and major upgrades plus support for as long as the subscription is valid.  If the subscription is canceled or not renewed, the user will no longer have access to the software.

&nbsp;

## Individual vs Concurrent

Each individual workstation license or subscription is attached to a single "seat".  It means that the license is not attached to a named user, but to an OS user instance (Windows, Mac, or Linux.)  If you have 2 PCs you need either 2 licenses, or a license for 2 seats.  

Large organizations prefer the flexibility of concurrent (a.k.a. floating) licenses.  In this case, you may install the software on many PCs, but only the licensed number of simultaneous users are allowed to use the application.  If the maximum number of seats has been reached, the next user will be denied access to the application until another user exits the application.  This scheme does not require a special server on-premises.

The concurrent approach is possible for either perpetual licenses or subscriptions.  Concurrent licenses are not available for purchase with a credit card.  They are 4 times more expensive per seat than an individual license.

&nbsp;

## Virtual Machines

When installing Hackolade on a VM to share among multiple users, it is important to realize that licensing is not attached to just the machine, but to the combination of the machine, the user login, and other parameters to determine the uniqueness of the session.

If you have 1 machine with multiple users (using for example Terminal Server, Remote Desktop, Citrix XenDesktop or an equivalent Virtual Machine method), you will need one license per user and PC accessing the Hackolade installation on the server.  A license must be obtained for each device on or from which the Product is used or accessed.  As a result, you need a license seat per user of that VM.

Example: having 4 Hackolade users on a single VM is the equivalent of having 4 individual PCs running Hackolade from a licensing point of view: you need 4 license seats to be validated.

&nbsp;

## Professional vs Workgroup

The Workgroup Edition of Hackolade Studio includes all of the features of the Professional edition, plus a native integration with Git repositories for your data models. &nbsp; The Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool, to leverage versioning, branching, change tracking, collaboration, peer review, and other related capabilities detailed [here](<Repository.md>).

&nbsp;

Access this page to [compare the different editions](<https://hackolade.com/editions.html> "target=\"\_blank\"").

&nbsp;

## Notes

**&#49;)** individual licenses, concurrent licenses, and subscriptions are all controlled by our license server in the cloud.

**&#50;)** the information above also applies to installations using only the Command-Line Interface in automated mode.  A CLI process requires a licensed installation, just as any desktop user.  If a CLI process is run from a user's workstation, it uses the same license as the GUI application.

