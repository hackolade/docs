# Bastion instance for Hackolade Studio

A bastion instance is a special computer that plays the role of a gatekeeper between a device and a user's machine.&nbsp; The bastion instance runs Hackolade Studio [Command-Line Interface](<CommandLineInterface.md>) commands on behalf of users, most likely an orchestration of multiple commands.

&nbsp;

Such setup may be necessary for security reasons, for example because the organization does not want to allow access to database instances, or divulge access credentials.&nbsp; Another reason might be that an organization wants data modelers to use only the browser deployment of Hackolade Studio.&nbsp; As explained [here](<Security-firstbrowserdeployment.md>), browser security blocks access to on-premise databases via most protocols, forcing a different way of performing some operations. &nbsp;

&nbsp;

The diagram below shows a simple architecture leveraging a bastion instance:

![Bastion instance architecture](<lib/Bastion instance architecture.png>)

&nbsp;

In general,organizations don't want want to run the risk of queuing requests in a single-threaded mode.&nbsp; To that effect, it is possible to run the CLI in multi-threaded mode in Docker containers, as documented [here](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"\_blank\"").

&nbsp;

The bastion instance running the Hackolade Studio Command-Line Interface requires its own license seat.&nbsp; If running single-threaded, a dedicated license key is sufficient.&nbsp; If running multi-threaded, then a Docker license key is required, which must be a Professional (or Workgroup) Concurrent key..

&nbsp;

If the bastion instance is not connected to the Internet, then you must run the [offline validation process](<https://hackolade.com/help/Softwareregistration.html#Offline%20validation> "target=\"\_blank\"").

&nbsp;

Below is a description of the process steps for the above diagram:

&#49;) the user accesses a portal (developed by the customer, i.e. NOT by Hackolade) pre-configured to execute Hackolade Studio CLI commands with some default arguments, and some user-selected arguments

&#50;) the portal runs a set of commands, including the request for the CLI to execute the command with the specified arguments

&#51;) the the CLI command is executed in a Docker container, for example the reverse-engineering of a database instance.&nbsp; The database credentials are known only to the bastion instance and its administrators

&#52;) the portal takes the data model resulting from the reverse-engineering process, and performs a commit and push of the model to the Git repository

&#53;) after the user is notified of the completion of the process, the user can now leverage Hackolade Studio

&#54;) to access the data model for operations such as enrichment, evolution, artifact generation, model compare \& merge, etc...

&nbsp;

With the above scenario, the user has been able to achieve its objective or reverse-engineering without connecting directly to the database instance, and also without personally configuring CLI commands, provided that the portal page has been properly configured for the different use cases.

&nbsp;

The above is just an example among others to inspire the reader.&nbsp; There are many permutations and variations possible based on the above scenario.

&nbsp;

**Note:** the creation of the portal page and configuration of the CLI commands is the responsibility of the customer, to fit the exact needs of the organization

