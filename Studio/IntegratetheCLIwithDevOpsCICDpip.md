# Integrate the CLI with DevOps CI/CD pipelines

At Hackolade, we're advocates of [Metadata-as-Code](<https://hackolade.com/metadata-as-code.html> "target=\"\_blank\""). &nbsp;

&nbsp;

This strategy has a business purpose to promote a shared understanding of meaning and context for data structures across business users and technical users, through the synchronization and publication of these data structures to business-facing data catalogs.

&nbsp;

It also has a technical purpose to ensure that the evolution of data models and their schema artifacts follow the same lifecycle as application code, through their co-location in Git repository and branches.

![Metadata-as-Code infinity loop](<lib/Metadata-as-Code%20infinity%20loop.png>)

&nbsp;

&nbsp;

This strategy gets executed through a combination of our [Workgroup Edition features](<Repository.md>) and our [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

&nbsp;

## Hackolade Studio Workgroup Edition

With the Workgroup Edition, Hackolade Studio integrates natively with the features, commands, and workflow of Git and the Git plaforms: GitHub, GitLab, Bitbucket, and Azure DevOps Repos.&nbsp; This allows for collaboration, versioning, branching, change tracking, peer reviews, conflict resolution, etc. &nbsp;

&nbsp;

In the context of Metadata-as-Code, the Workgroup Edition also allows for the co-location of data models and their schema artifacts with the corresponding application code and their respective but co-ordinated changes in a Git branch.&nbsp; Artifacts also include ALTER scripts, if applicable to the target technology, resulting from model evolutions.![Metadata-as-Code co-locate model schema code](<lib/Metadata-as-Code%20co-locate%20model%20schema%20code.png>)

&nbsp;

&nbsp;

&nbsp;

## Command-Line Interface

The CLI lets you automatically generate schemas and scripts, or reverse-engineer an instance to infer the schema, or to reconcile environments and detect drifts in indexes or schemas. The CLI also lets you automatically publish documentation to a portal or data dictionary when data models evolve.

&nbsp;

With the CLI, you can automate tasks that you would otherwise perform manually in the GUI application. Some Hackolade customers use this capability nightly in a batch process to identify attributes and structures that may have appeared in the data since the last run.  During a nightly run of the reverse-engineering function, a much larger dataset can be queried as a basis for document sampling, hence making schema inference more precise. Such capability can be useful in a data governance context to properly document the semantics and publish a thorough data dictionary for end users.  It can also be used in the context of compliance with privacy laws to make sure that the company does not store data that it is not supposed to store.  There are many more examples of how to use this functionality.

 

The Hackolade command line can of course be used on a stand alone machine.  It can also be easily combined with a [git repository](<Teamcollaboration.md>) for the storage of versioned models and schema artifacts, as well as with [Docker containers](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"\_blank\"").  Customers have been using this combination either in a push mode, triggered by saving or committing model changes, or in a pull mode, when invoked by a DevOps CI/CD pipeline or a scheduled job. ![Metadata-as-Code CLI workflow automation](<lib/Metadata-as-Code%20CLI%20workflow%20automation.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

The CLI can also be used for end-to-end synchronization of data structures with business-facing data dictionaries:

![Metadata-as-Code pipeline orchestration](<lib/Metadata-as-Code%20pipeline%20orchestration.png>)

&nbsp;

&nbsp;

&nbsp;

## CLI Orchestration

The orchestration of the commands and arguments is typically scripted, then triggered by an event or a schedule.&nbsp; But the sequence of steps depends on whether development has the upper hand or governance. &nbsp;

&nbsp;

Organizations operate in different ways.&nbsp; If development has the upper hand, evolutions tend to happen in a code-first manner, and we see what we've called "retroactive data modeling" or "data modeling after-the-fact."

&nbsp;

In other organizations, data modeling happens first, then code changes occur and are implemented in the different environments.

&nbsp;

The Hackolade Studio CLI commands can be assembled in the sequence that best fits your exact use case.

&nbsp;

## Governance-first use case

In a governance-first approach, a baseline model evolves.  When the branch for model changes is merged, the following steps occur:

1. Reverse-engineer the database instance using the command “revEng”
1. Compare the resulting model with the evolution of the baseline model, using the command “compMod”.  This produces a “delta model”
1. From the delta model, forward-engineer the ALTER script using the command “forwEng”
1. Commit the ALTER script
1. Have a DBA review the ALTER script.

&nbsp;

![CLI governance-first use case](<lib/CLI%20governance-first%20use%20case.png>)

&nbsp;

## Code-first use case

In a code-first approach, the structure in the production instance evolves.  Every night, a scheduled process goes through the following steps:

1. Reverse-engineer the Databricks instance using the command “revEng”
1. Compare the resulting model with the baseline model, using the command “compMod”.  This produces a “delta model” and optionally a “merged model”
1. We suggest here a manual step to review the model comparison and identify whether all changes in production are legitimate.  Maybe adjustments are necessary to the code, data needs migration, etc…  Produce a new merged model if necessary.
1. Commit the merged model which becomes the new baseline model

&nbsp;

![CLI development-first use case](<lib/CLI%20development-first%20use%20case.png>)

&nbsp;

&nbsp;

&nbsp;

## Developing and fine-tuning the CLI commands

Many other combinations are possible, and the examples above should inspire the approach fitting your specific use case.

&nbsp;

Creating the orchestration of the CLI commands with the proper arguments can be tricky so we suggest the following tips and best practices:

1. Start by executing with the GUI the different steps of the full workflows and ensure that the you can produce the expected results from the GUI application;
1. Familiarize yourself with the CLI, and start small before building up in complexity.&nbsp; For example, start by displaying the arguments for your command before writing a huge number of complex arguments.&nbsp; Also, folder paths quickly add complexity.&nbsp; Don't make your life too complicated at first, with complex locations or path variables without validating first that the command works well locally.
1. Divide and conquer: develop the command arguments and fine-tune each command, one at a time.&nbsp; And only assemble them in a script when each command has been fully validated.
1. When doing model comparisons, beware of which model is model1 and which is model2, as it has an influence on the direction of the [ALTER scripts](<DeltamodelandALTERscript.md>) (i.e. what object gets added or deleted), as well as on conflict resolution.&nbsp; We strongly suggest experimenting with the [Compare \& Merge screen](<Compareandmergemodels.md>) to visually understand the behavior.
1. Test, test, and re-test... And validate that the output is as expected in various circumstances. &nbsp;

&nbsp;

