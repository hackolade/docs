# Concepts

Even if you have little or no experience with Git, we made it very easy to use Git from inside Hackolade Studio, without compromise on the power of Git in more advanced situations. You just need to become familiar with the concepts below.

&nbsp;

**Note:** as with any new technology, concepts may be different than what you've been used to with other vendors.&nbsp; Maybe you are used to doing "checkout" of a data model and lock it so other users cannot make any changes until you "checkin" that model.&nbsp; Git works differently, so you may need to adjust your habits.&nbsp; But you'll quickly realize that it is much more flexible, letting different users make changes simultaneously, then reconciling them at a later stage, most often without manual intervention.&nbsp;

&nbsp;

**Warning:** some terms used in a Git context may have a different meaning than in other technologies, e.g. checkout.

&nbsp;

## Remote repository

The term "remote repository" may be intimidating, but it simply means the "central storage", in this case for your data models.&nbsp; It is "remote", in the sense that it is not "local".&nbsp; And it differs from a traditional folder in the sense that it is enabled for tracking changes in text files.&nbsp; As a result, every time someone "saves" a file into a remote repo, an immutable state and history is automatically logged and accumulated.&nbsp; Immutability does not mean that you cannot make additional changes.&nbsp; It simply means that you cannot rewrite history: you may only make additional changes (possibly if necessary, to undo some other change made in the past) in a new version of that file.&nbsp; It is easy to see when a change was made and by whom. &nbsp;

&nbsp;

Note that an additional benefit of Git is that it is not necessary to explicitly create new versions of a file: each new commit made on the remote repo is a new and automatic version of the file.&nbsp; It is possible to capture a milestone in the Git history, generally to mark a version release (i.e. v1.0.1), by creating a tag, which is a marker pointing to a specific state of the repository, an arbitrary commit.

&nbsp;

## Remote vs Local repo

One of the many advantages of Git vs previous source control systems, is that it can be (and often is) "distributed", as opposed to strictly central.&nbsp; In the old days, collaborating on a central file imposed a big constraint on collaboration.&nbsp; In most cases, it was necessary for one user to "checkout" the file and lock it so no one could make changes in parallel.&nbsp; Then when finished, the user would do a "checkin" of the new version into the central storage.&nbsp; When using the distributed nature of Git, users are able to make changes in parallel on the same file, being confident that these changes will be automatically merged.&nbsp; If a conflict occurs, there is a method for a user to easily resolve these conflicts.

&nbsp;

There are 2 ways to work with a remote repository:

\- for occasional access, or users simply consulting models in read-only mode, they may access the central storage directly.&nbsp; It is&nbsp; possible to operate in read-write mode to create a new or modify an existing file (and Hackolade Studio supports this mode since v8.1.2), but users lose several benefits, as described below. &nbsp;

&nbsp;

![Workgroup Git direct remote repo](<lib/Workgroup Git direct remote repo.png>)

&nbsp;

&nbsp;

\- for more intensive use with a richer experience and feature set, by cloning the remote repository on the user's local machine.&nbsp; The richer experience includes the benefits related to the distributed nature of Git: advanced features, ability to group changes to multiple files in sets, more flexible collaboration, offline access, multiple backups, etc.

&nbsp;

&nbsp;

![Workgroup Git local remote repos](<lib/Workgroup Git local remote repos.png>)

&nbsp;

## Clone&nbsp;

Cloning a repository is the action of creating a copy of that repository.&nbsp; The most typical use case is for a user to clone a "remote" repository into a "local" folder.

&nbsp;

Note that every clone of a repository contains the full content and history of that repository.&nbsp; This makes it possible for you to explore and work in your local repository while being offline.&nbsp; You only need a network connection when you decide to upload your changes to the remote repository, or to download the changes made by other users.

&nbsp;

You can clone as many repositories as you want.&nbsp; You can open each of them individually in Hackolade Studio.&nbsp; If you start multiple instances of Hackolade Studio, each instance can have a different repository open, or the same one.

&nbsp;

Cloning a remote repository should normally happen only once, whereas the other actions below typically happen on a regular basis.&nbsp;

&nbsp;

**Note:** we skipped on purpose the concept of *creating* a repository.&nbsp; In most cases, you will work with existing repositories, created by the administrator in your organization.&nbsp; If you need to create a new repo, you should create it first on your provider's platform ([GitHub](<https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository> "target=\"\_blank\""), [GitLab](<https://docs.gitlab.com/ee/user/project/working\_with\_projects.html#create-a-project> "target=\"\_blank\""), [Bitbucket](<https://support.atlassian.com/bitbucket-cloud/docs/create-a-git-repository/> "target=\"\_blank\""),[ Azure Repos](<https://azure.microsoft.com/en-us/services/devops/repos/> "target=\"\_blank\"")), then clone it in Hackolade Studio as described [here](<Clonearemoterepository.md>).

&nbsp;

## Commit

Once you have your local clone of a repository, you can start making changes in the files that it contains, mainly Hackolade data models in our case.&nbsp; You may also create new data models and save them into your local repository folder and sub-folders.

&nbsp;

When you save your changes to a data model, they are, as usual, written to your file system.&nbsp; However, at this stage, they are not tracked by Git yet.&nbsp; You need one extra step to add your changes to the Git history: you need to commit them.&nbsp; Once you have committed your changes, they appear as an atomic modification in the history of your local repository.

&nbsp;

The changes that you commit are not immediately available to other users in your team. The next step is to push your commits to the remote repository.

&nbsp;

Note that a commit can contain multiple changes, possibly in multiple files. It is a good practice to include, in a single commit, file changes that relate to one another, and to give every commit a meaningful description.

&nbsp;

It is important to note that a commit, once it has been pushed to the remote repo, is a fairly immutable piece of Git history.&nbsp; For integrity reasons, Hackolade Studio does not let users erase or cancel a commit from the Git history.&nbsp; It can only be discarded undone via a revert operation.&nbsp; If more specific actions are required, only experts should [rewrite history](<https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History> "target=\"\_blank\""), and perform these actions outside of Hackolade Studio.

&nbsp;

Prior to being pushed, a commit can be discarded, or stashed.

&nbsp;

## Pull

Pulling remote commits is the action of downloading from the remote repository the commits that have been pushed by other users.&nbsp; As long as you don't pull these commits, those changes are not available to you.

&nbsp;

## Push

Pushing your local commits is the action of publishing them to the remote repository to make them available to other users.&nbsp; As long as you don't push your local commits, changes are only available to you.

&nbsp;

Note that you need to commit your changes prior to pushing them. Uncommitted changes will not be pushed.&nbsp; Also, you may make several local commits before pushing them to the remote repository (e.g. after working in offline mode for a while.)

&nbsp;

## Conflict

Conflicts can happen when pulling remote commits, in case you modified a line in a file that has also been modified differently by someone else. Hackolade Studio assists you in solving conflicts in data model files through an interactive merge dialog.

&nbsp;

Chances for conflicts are minimized by the structure of Hackolade data model files, whereby each property, of each attribute, of each entity, of each container is its own line in a data model file.&nbsp;

&nbsp;

**Best practice**: to reduce the risks of facing conflicts, we recommend that you regularly pull remote commits.&nbsp; This will ensure that your local repository is up-to-date with all the changes that have been recently pushed by other team members to the remote repository.&nbsp; If you are about to start modifying a data model, then you should definitely pull first from the remote repository.&nbsp;

&nbsp;

It is also a good idea to regularly push your commits to the remote so other team members are aware of your changes.&nbsp;

&nbsp;

## Branch

Git does more than tracking a linear sequence of commits. It supports branching to create independent sequences of commits that belong together. Such a sequence is called a branch.

&nbsp;

A branch can be short-lived, to track small fixes for example. A branch could also be open for awhile, for example when developing the features of a new major version.

&nbsp;

The picture below is an example of what the history of a repository can look like. Every circle represents one commit. There are sometimes multiple distinct sequences of commits (branches) running in parallel.

&nbsp;

![Workgroup Git commit history](<lib/Workgroup Git commit history.png>)

&nbsp;

When you open a repository, what you see is the content of the repository on the branch that is currently active (there is always at least one branch in a repository).

&nbsp;

When you commit your changes, you commit them on the active branch.

&nbsp;

You can create as many branches as you need. You can switch from one branch to another.&nbsp; In Git terms, these actions are both called "checkout".&nbsp; This term is not to be confused with the concept of *checkout* in other technologies. The term *checkout* in a Git context means *selecting a branch*, whether the branch is an existing one or a new one.&nbsp;

&nbsp;

When you checkout a branch, it becomes the active branch.&nbsp; Every change you make only affects that branch.&nbsp; Other branches remain untouched.

&nbsp;

When you checkout a new branch, it is only available to you in your local repository.&nbsp; It becomes available for other people only after you push the commits that you made on that branch to the remote repository.

&nbsp;

You can merge a branch into another one.

&nbsp;

You can delete a branch (after merging it, or not merging it.)

&nbsp;

**Note:** you should should choose carefully the basis for your new branch, if that basis is any other branch than main/master.&nbsp; This is because a new branch inherits all the history and content of the branch on which it is based. This article [explains Git branches with a LEGO analogy](<https://opensource.com/article/22/4/git-branches> "target=\"\_blank\"").

&nbsp;

&nbsp;

## Create a change/merge/pull requests

The peer review feature is a very popular collaboration extension to Git, supported by most of the repository hubs.&nbsp; It allows changes made by a user to be submitted for review and approval by another user before being merged into a target branch. &nbsp;

&nbsp;

Changes to data models are proposed in a branch, to ensure that the target branch only contains finished and approved work.&nbsp; Anyone with read access to a repository is allowed to submit changes for review.

&nbsp;

**Note:**&nbsp; the naming conventions differ slightly between repository hub providers.&nbsp; GitHub, for example, uses the terminology *pull requests*, whereas GitLab uses *merge requests*.&nbsp; Both refer to the same concept.&nbsp; Hackolade Studio takes into account the specific terminology of the hub provider.&nbsp; However, in this documentation, we abstract them and refer to the more generic "change requests".

&nbsp;

&nbsp;

## Review of change/merge/pull requests

Peers may comment a change request and solicit adjustments to be made to the data models in the branch.&nbsp; Designated reviewers may approve or reject change requests.

&nbsp;

&nbsp;

## Tags

A [Git tag](<https://git-scm.com/docs/git-tag> "target=\"\_blank\"") is a reference pointing to a specific commit in the Git history. [Tagging](<https://git-scm.com/book/en/v2/Git-Basics-Tagging> "target=\"\_blank\"") is used to capture a milestone in the Git history, generally to mark a version release (i.e. v1.0.1).&nbsp; The Git client makes it possible to tag a given commit with an arbitrary name. It is also possible - but not mandatory - to provide a description when tagging a commit.

&nbsp;

