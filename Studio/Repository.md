# Repository

**Note:** this set of features is available ONLY in the Workgroup Edition of Hackolade Studio.

&nbsp;

The Workgroup Edition of Hackolade Studio introduces, starting with v6 and with the appropriate license key upgrade, native integration with Git repositories. Previously, an integration with Git was possible, but required either a separate Git desktop application, or the use of the Git command line interface.&nbsp; Our Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool.

&nbsp;

Most importantly, user-friendly context-aware screens are provided to review changes, compare versions, commits, and branches, or merge conflicts.

&nbsp;

&nbsp;![Commit your local changes](<lib/Workgroup%20commit.png>)&nbsp; ![Workgroup pull conflict](<lib/Workgroup%20pull%20conflict.png>)

&nbsp;

![Image](<lib/Workgroup%20merge%20dialog.png>)

&nbsp;

&nbsp;

## What is a repository?

A repository is a central folder where you can store data models and other files.&nbsp; Using a repository not only allows you to easily share your data models with other users in your organization, it also enables co-authoring, versioning, branching, change tracking, peer reviews, and more.&nbsp; It is the perfect solution for sustaining an efficient collaboration and flow of information between the different stakeholders involved in your design and development process.&nbsp; Such full integration with Git repositories enables the possibility to co-locate data models with code, and it also facilitates Metadata-as-Code.

&nbsp;

**Note:** tool vendors have different definitions of the term "repository".&nbsp; Ours is strictly focused on handling the lifecycle of data model files and schema artifacts. The upcoming Enterprise Edition of Hackolade will bring additional features like data models metadata, reports, and much more.

&nbsp;

## What is Git?

Git is currently the most popular distributed version control system, originally designed for software source code, and now used for many other purposes, including the operational framework known as [GitOps](<https://about.gitlab.com/topics/gitops/> "target=\"\_blank\"").

&nbsp;

Git takes care of tracking all changes that are made in files belonging to specific folders. In Git terms, such a folder is called a repository.&nbsp; A repository is like any other traditional folder: the only specificity being the presence of a sub-folder named .git containing the history of all file changes for the folder.

&nbsp;

Git supports setting up a central repository, called "remote", that users can copy (a.k.a. "clone") onto their computer, called "local". They make changes in their local repository, then publish them to the remote repository.

&nbsp;

## Why use Git for Hackolade data models?

Some industry analysts seem to consider as a drawback that Hackolade does not have its own proprietary repository\!?...&nbsp; We consider it an advantage for our users\!

&nbsp;

We decided to leverage a standard and non-proprietary technology that is already extremely popular for software development: [Git](<https://en.wikipedia.org/wiki/Git>), the software code version control technology behind the popular services GitHub, GitLab, and other DevOps platforms.&nbsp; Git is used by over a hundred fifty million developers worldwide, plus there's a huge advantage to co-locating data models, schemas, and code.&nbsp; Along with DevOps CI/CD pipelines and our [Command-Line Interface](<CommandLineInterface.md>), our repository integration supports our vision for [Metadata-as-Code](<https://hackolade.com/metadata-as-code.html>).

&nbsp;

The decision to store data models in non-proprietary JSON format was strategic from day 1 and has allowed us to leverage the powerful Git engine features.&nbsp; We did not have to re-invent the wheel when implementing collaboration, versioning, branching, peer review features.&nbsp; We focused on the integration of the workflow, on the design of a user-friendly and intuitive UI/UX, and mostly on the added value of [compare and merge](<Compareandmergemodels.md>) screens in the context of the data modeling mission of users.

&nbsp;

## Disclaimer

Git is a super powerful tool with many features, some of which have not been integrated in Hackolade Studio.&nbsp; Following our agile mindset, we will continue to iteratively develop and ship additional features in upcoming releases. In case you find an important feature to be missing, you may [submit a feature request](<https://hackolade.zendesk.com/hc/en-us/requests/new> "target=\"\_blank\"").

&nbsp;

Also note some potentially relevant [questions and answers](<QuestionsAnswers.md>).

