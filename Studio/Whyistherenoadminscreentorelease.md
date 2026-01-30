# Why is there no admin screen to release seats?

We understand the request for an admin tool that would allow you to release license seats.&nbsp; To be clear, we do provide convenient and self-service ways to:

\- [monitor real-time the usage of license seats](<Managingmultiplelicensekeysandse.md>),&nbsp;

\- [release a dedicated license seat](<https://hackolade.com/help/Softwareregistration.html#Release%20the%20license%20key%20from%20one%20computer%20to%20move%20to%20another>) if no longer needed on a machine,&nbsp;

\- [gracefully release a concurrent seat](<https://hackolade.com/help/Concurrentlicensekeybehavior.html#Be%20considerate%20of%20others>) so it can be used by a colleague,&nbsp;

\- [transfer a license](<Transferalicensetoanewcomputer.md>) from one machine to another,&nbsp;

\- [move your preferences and settings to a new computer](<Movingtoanothercomputer.md>),&nbsp;

&nbsp;

We do not provide an admin tool that would arbitrarily release seats in addition to the above features.&nbsp; While technically possible, we have disabled this feature because it has been previously abused by customers, even by some large very well known companies.

&nbsp;

The architecture of the Hackolade solution is quite different than other tools.&nbsp; You can read all about it in [this article](<WhylegacyandSaaSdatamodelingarch.md>).

&nbsp;

Specifically about license keys, we manage them with a modern 3rd-party service in the cloud.&nbsp; There are many advantages with this approach.&nbsp; Among others, we get world-class license management, plus high-availability and low maintenance redundant service.

&nbsp;

For our customers, our approach is beneficial because much cheaper and more convenient than having to install, maintain, monitor, upgrade, backup,... a license server in their data center.&nbsp; Moreover, it avoids for customers to have to endure license audits for overuse or misuse - a process inevitably uncomfortable for both sides, as per the confrontational reputation of some leading software vendors ;-)...

&nbsp;

Please leverage the above self-service resources.&nbsp; And if, by accident, a machine crashes, or a user has left the organization without respecting the exit checklist item to release the license seat, you can simply send an email to [support@hackolade.com](<mailto:Please%20release%20license%20seat?subject=support@hackolade.com>) explaining the reason, and our helpdesk will release the seats.
