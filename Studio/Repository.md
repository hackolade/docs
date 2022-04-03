# Repository

The Workgroup Edition of Hackolade Studio introduces, starting with v6 and with the appropriate license key upgrade, native integration with Git repositories. Previously, an integration with Git was possible, but required either a separate Git desktop application, or the use of the Git command line interface.&nbsp; Our Workgroup Edition makes it easy for users who are not so familiar with Git to leverage the tremendous power of this popular tool.

&nbsp;

&nbsp;![Commit your local changes](<lib/Workgroup%20commit.png>)&nbsp; ![Workgroup pull conflict](<lib/Workgroup%20pull%20conflict.png>)

&nbsp;

![Image](<lib/Workgroup%20merge%20dialog.png>)

## What is a repository?

A repository is a central folder where you can store data models and other files.&nbsp; Using a repository not only allows you to easily share your models with other users in your organization, it also enables co-authoring, versioning, branching, change tracking, peer reviews, and more.&nbsp; It is the perfect solution for sustaining an efficient collaboration and flow of information between the different stakeholders involved in your design and development process.&nbsp; Such full integration with Git repositories enables the possibility to co-locate data models with code, and it also facilitates Metadata-as-Code.

&nbsp;

**Note:** tool vendors have different definitions of the term "repository".&nbsp; Ours is strictly focused on handling the lifecycle of data model files and schema artifacts. The upcoming Enterprise Edition of Hackolade will bring additional features like data models metadata, reports, and much more.

&nbsp;

## What is Git?

Instead of expecting you to adopt a new proprietary solution for managing repositories, we decided to leverage a standard technology that is already extremely popular for software development: [Git](<https://en.wikipedia.org/wiki/Git>), the software code version control technology behind the popular services GitHub, GitLab, and other DevOps platforms.

&nbsp;

Git takes care of tracking all changes that are made in files belonging to specific folders. In Git terms, such a folder is called a repository.&nbsp; A repository is like any other traditional folder: the only specificity being the presence of a sub-folder named .git containing the history of all file changes.

&nbsp;

Git supports setting up a central repository, called "remote", that users can copy onto their computer, called "local". They make changes in their local repository, then publish them to the remote repository.

&nbsp;

## Disclaimer

Git is a super powerful tool with many features, some of which have not been integrated in Hackolade Studio.&nbsp; Following our agile mindset, we will continue to iteratively develop and ship additional features in upcoming releases. In case you find an important feature to be missing, you may [submit a feature request](<https://hackolade.zendesk.com/hc/en-us/requests/new> "target=\"\_blank\"").

&nbsp;

Also note some potentially relevant [questions and answers](<QuestionsAnswers.md>).

