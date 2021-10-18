# Team collaboration

**Note:** You may wish to view the [how-to video](<https://hackolade.com/videos.html#collaboration> "target=\"\_blank\"") on this subject.

&nbsp;

The Hackolade roadmap foresees specific versions to support workgroup collaboration, assuming the base version is successful commercially, and that the market needs this feature.&nbsp; But what can be done in the meantime?

&nbsp;

It was a design choice from the start to store Hackolade data, not only in JSON format, but also in a non-proprietary text based form.&nbsp; This choice enables easy tracking, control, and versioning of model changes in Hackolade.

&nbsp;

Hackolade has been promoting a GitOps approach for the lifecycle of data models stored in JSON files. Git technology provides the following benefits:

* **change tracking:** a Git repository holds a complete record of every change to the text files it contains. It’s easy to look through a repository and see what was changed, when, and by whom.
* **peer review:** changes aren’t typically pushed to the main branch of a Git repository. Instead, changes are pushed to a branch or fork, then a pull/merge request is created, and the changes are reviewed by someone other than their creator before they are approved and merged.
* **versioning:** Git tags can be used to mark a specific commit as important. Upcoming versions can be prepared in feature branches.
* **easy rollbacks:** if, for any reason, on decides changes made aren't desirable, it’s easy to roll back to an older tag or commit.
* **testing:** many customers use Hackolade data models as part of a CI/CD pipeline. When testing new application versions, it is easy to include the corresponding feature branch.
* **build and deploy:** while this may seem software-specific, such process can be leveraged to produce artifacts such as corresponding schemas, scripts, documentation, etc.

&nbsp;

To leverage Git in the context of Hackolade, it is suggested to follow these steps:

&#49;. Sign up and setup a repository on [Bitbucket](<https://bitbucket.org/> "target=\"\_blank\""), [GitHub](<http://github.com> "target=\"\_blank\""), [GitLab](<https://gitlab.com/> "target=\"\_blank\"") or equivalent

&#50;. Download a GUI client for Git:&nbsp; [SourceTree](<https://www.atlassian.com/software/sourcetree> "target=\"\_blank\"") or any other equivalent [client](<http://git-scm.com/downloads/guis> "target=\"\_blank\"")&nbsp;

&#51;. Clone your repository into a local directory in which you'll be keeping your Hackolade models

&#52;. Use the combination of your Git client and Hackolade to manage the lifecycle of your models

* &nbsp;
  * your Git client to fetch, pull, branch, checkout
  * Hackolade to create and modify models
  * your Git client to commit and push, view differences
  * at this stage, merging and conflict resolutions would need to be performed (carefully) in a manual way... until a Workgroup edition of Hackolade is released.

&nbsp;

Here are some basic Git principles and commands to be used in combination with Hackolade.&nbsp; The commands are executed with a Git client (such as SourceTree), as Hackolade does not yet have a Git client integrated.

![Git workflow](<lib/Git%20workflow.png>)

&nbsp;

After initial cloning of the Remote repository for models, it is a good idea to change the user parameters to point the default path for models in Hackolade to the Local Git repository.

&nbsp;

Before making any changes to a model, it is a good practice to perform a Pull (which in effect does a Fetch from the Remote repository, followed by a Merge.) &nbsp; After making further changes locally in the model using Hackolade, don't forget to save your changes, then perform a Commit (and a description) and a Push so your changes are made available in the Remote repository.

&nbsp;

Resolving conflicting changes can be a tedious process involving manual intervention.&nbsp; It is therefore advised, if several users collaborate on the same models, to Pull the latest changes from the Remote repository prior to making new changes.&nbsp; Then make sure to save changes, then Commit and Push to the Remote repository.

&nbsp;

Sometimes, it may be a good idea, if working on the model for a new release, to Save As the current model to a new version by giving the model file a new name, for example by appending a version number at the end of the file name.

