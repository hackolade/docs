# DevOps CI/CD architecture

In the How-To Guide [Integrate CLI with DevOps CI/CD pipelines](<IntegratetheCLIwithDevOpsCICDpip.md>), we detail a Governance-first use case to illustrate the power and flexibility of the [Command-Line Interface](<CommandLineInterface.md>).in the context of our [Metadata-as-Code](<https://hackolade.com/metadata-as-code.html> "target=\"\_blank\"") strategy.

![CLI governance-first use case](<lib/CLI governance-first use case.png>)

&nbsp;

Let's describe here the architecture setup to support this use case, and others as well.

&nbsp;

The setup assumes that:

\- data models are stored in your Git repository

\- you have an instance of Hackolade Studio ready to run in Docker containers, as documented [here](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"\_blank\""), and allowing you to run in multi-threaded mode.&nbsp; The instance running the Hackolade Studio Command-Line Interface in Docker requires a license key, which must be a Professional (or Workgroup) Concurrent key.

\- you create Git repository provider triggers for your use case (GitHub Actions, Bitbucket pipelines or equivalent.)

&nbsp;

The diagram below shows a simple architecture leveraging Hackolade Studio CLI in Docker containers::

&nbsp;

![Image](<lib/CLI architecture in Docker containers.png>)

&nbsp;

&nbsp;

The CLI instance running the Hackolade Studio Command-Line Interface requires its own license seat.&nbsp; If running single-threaded, a dedicated license key is sufficient.&nbsp; If running multi-threaded, then a Docker license key is required, which must be a Professional (or Workgroup) Concurrent key..

&nbsp;

If the CLI instance is not connected to the Internet, then you must run the [offline validation process](<https://hackolade.com/help/Softwareregistration.html#Offline%20validation> "target=\"\_blank\"").

&nbsp;

Below is a description of the process steps for the above diagram:

&#49;) users maintain data models in Hackolade Studio

&#50;) users commit and push new model versions, possibly merging a pull/change request to the main branch, possibly with a tag to mark a new release

&#51;) an event-driven trigger has been created to execute the orchestration of a set of successive CLI operations (may also include git commands and OS commands)

&#52;) the first command is to reverse-engineer the database instance.&nbsp; This could be done with different instances (for example dev, test, acceptance, prod) to keep them in sync, but maybe at different times, based on branch lifecycle.

&#53;) the repo is pulled locally so the latest version of the model is accessible

&#54;) the next CLI command is to compare models (the new model version and the model just created with the earlier reverse-engineering step) and create a delta model

&#55;) the next CLI command forward-engineers the ALTER script artifact (for applicable targets)

&#56;) ideally a DBA reviews the ALTER script for validity prior to applying it to the database instance

&nbsp;

The above is just an example among others to inspire the reader.&nbsp; There are many permutations and variations possible based on the above scenario.

&nbsp;

**Note:** the responsibility for the creation of the Git repo provider triggers and the CLI commands is the responsibility of the customer

