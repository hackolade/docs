# Questions & Answers

### How to work with Git submodules?

Git submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project while keeping your commits separate.

&nbsp;

The presence of Git submodules in a repository will not prevent you from using Hackolade Studio. But there is no handling of Git submodules currently in Hackolade Studio.&nbsp; Even the GitHub Desktop application does not have any special support for submodules...

&nbsp;

This [article](<https://www.atlassian.com/git/tutorials/git-subtree> "target=\"\_blank\"") even suggests that a better alternative to Git submodules is to use Git subtrees.

&nbsp;

### How to deal with non-ASCII symbols in file names?

By default, Git replaces non-ASCII symbols in file names with octal notation. For example, a file named "TrainScheduleф.json" will be treated by Git as "TrainSchedule\\321\\204.json".

&nbsp;

If you need to deal with non-ASCII symbols in file names, then open a terminal and run the command below in order to modify the default behavior of your local Git client (omit the $ sign in Windows).

&nbsp;

$ git config core.quotepath off

&nbsp;

See the official documentation about the Git configuration parameter [core.quotepath](<https://git-scm.com/docs/git-config#Documentation/git-config.txt-corequotePath> "target=\"\_blank\"") for more details.

&nbsp;

## Where is my .gitconfig file?

From time to time, you may have to adjust [Git configuration parameters](<https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup> "target=\"\_blank\"").&nbsp; The problem might be to find the location of the .config file first... You can view all of your settings and where they are coming from using to following command (omit the $ sign in Windows):

$ git config --list --show-origin

&nbsp;

## In Task Manager, I see many orphan background processes for Git for Windows

The issue is not specific to Hackolade and is linked to an experimental feature introduced in Git version 2.31.0.&nbsp; If selected, Git will use a built-in file-system monitor, without the need to install Watchman.&nbsp; However, this feature is not yet stable so it is strongly advised to run the following command:

&nbsp;

For Git versions up to 2.35.x:

$ git config --global core.useBuiltinFSMonitor false

&nbsp;

&nbsp;

For Git version 2.36.0 and above:

$ git config --global core.fsmonitor false

&nbsp;

## I'm getting an error core.useBuiltinFSMonitor=true is deprecated

Starting with version 2.36.0, the config keyword useBuiltinFSMonitor has been deprecated, and replaced by fsmonitor. When opening a repository, if you get the error:

![Image](<lib/Workgroup useBuiltinFSMonitor deprecated erro.png>)

&nbsp;

The hint is accurate.&nbsp; You should run the following command at a command prompt (omit the $ sign in Windows):

$ git config --global core.fsmonitor false

&nbsp;

&nbsp;

## I have GitHub Desktop installed on my machine.&nbsp; Is it not a Git client?

Be careful that GitHub Desktop, SourceTree and other visual applications are NOT the Git client the we're looking for here.&nbsp; They are GUI applications also leveraging the system Git executable.&nbsp; If you specify a custom path, it must be to the Git executable.

&nbsp;

![Workgroup tools options repository](<lib/Workgroup tools options repository.png>)

&nbsp;

With GitHub Desktop, it is possible that the installation did not declare the location of the Git executable in the system PATH.&nbsp; This is a [well documented situation](<https://stackoverflow.com/questions/26620312/git-installing-git-in-path-with-github-client-for-windows> "target=\"\_blank\"")...&nbsp; Hackolade Studio has been enhanced to auto-detect the Git executable installed by GitHub Desktop, if in one of its standard locations: &nbsp;

**C:\\Program Files\\Git\\bin\\git.exe**

**C:\\Users\\%username%\\AppData\\Local\\GitHubDesktop\\app-3.0.0\\resources\\app\\git\\cmd\\git.exe** (GitHub Desktop version 1.1 and above)

&nbsp;

If installed elsewhere, like&nbsp;

**C:\\Users\\%username%\\AppData\\Local\\GitHub\\PortableGit\_\<guid\>\\cmd\\git.exe** (GitHub for Windows prior to version 1.1)

you may have to declare the custom path manually.

&nbsp;

See more info in the [pre-requisites page](<Pre-requisites.md>).

&nbsp;

## How should I organize our models in the repository?

Should we co-locate models in the application code repo?&nbsp; Or should we have a separate repo?&nbsp; Should we have one or more repos?

&nbsp;

These are excellent questions.&nbsp; But there is no black-and-white answer, except "it depends"...&nbsp; You should experiment, and discuss with multiple stakeholders, to find the best setup for your organization.

&nbsp;

You may already have reviewed our resources specific to the Git integration:

\- [online documentation](<Repository.md>) and pages below

\- eLearning platform [videos](<https://community.hackolade.com/slides/hackolade-studio-tutorial-5-workgroup-collaboration-and-versioning-5> "target=\"\_blank\"")

&nbsp;

On the specific question of the repo organization:

\- you may co-locate models with application code

\- advantages:&nbsp;

&nbsp; &nbsp; - model changes follow the same lifecycle as the application code

\- model changes provide additional context for the application code

\- disadvantages

&nbsp; &nbsp; - it is harder to decouple models from application code if, for example the target is shared across different applications

\- rights management whereby maybe you don't want modelers to have access to the application code

&nbsp;

\- you may want to have a separate repo for models

&nbsp; &nbsp; - pros and cons are the mirror of the above

&nbsp;

Some customers choose the former, others the latter.&nbsp; There is no rule.

&nbsp;

Also, when choosing a dedicated repo for models, the folder structure differs widely between customers.&nbsp; Some are domain-oriented, some are application-oriented, some are access rights-oriented, etc.

&nbsp;

And when using a dedicated repo, some wonder about whether there should be one repo per domain, or multiple repos.&nbsp; We generally advise to have a single repository.&nbsp; If you're worried about the protection of your models, so their changes follow a process, you have 2 options:

\- you can force in your repo that changes be made through change (pull) requests

\- better yet, you may want to force adopt a [fork \& pull strategy](<Workingwithforks.md>), also known as innersourcing.

&nbsp;

Our application can accommodate any and all of those repo organizations, but each customer has its own perspective, and we don't know enough to judge.

&nbsp;

## Why is there no auto-commit capability?

Git itself does not provide this feature.&nbsp; And the reason is that there are too many risks:

\- Risk of unintentional commits: auto-committing can cause unintended commits that might include unnecessary or incomplete changes.

\- Loss of control: it might push changes that you're not ready to share, or break models

\- Inconsistent history: it can create a mess in your commit history, making it harder to understand the changes over time.

&nbsp;

## How are permissions managed?

1. Even for the viewer edition, anyone who needs to have access to a file somewhere must be given proper access.  Same as in anywhere in the digital or physical world.&nbsp; If a model is stored on a shared drive or in a Git repository, the user must be granted access for that location in order for the user to be able to open the model. &nbsp;
1. &nbsp;
1. Just like with any client application, like Microsoft Excel for example, the access control is delegated to the storage layer: the local file system, a shared drive, or the Git repository.  If someone has access to a file, then the application can open it.  The right to edit a modelis shared between the license key (author or viewer -- if you only have viewer rights, you cannot edit a model, even if you have write rights) and the repository -- even if you have the workgroup edition, you cannot save the model in a place where you have no rights to do so.
1. 