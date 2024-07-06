# Working with forks

## Repository strategies

There are 2 main strategies for dealing with contributions to a Git repository: *shared repository* and *fork \& pull*.

&nbsp;

### Shared repo strategy

With a *shared repository* strategy, contributors are granted push access rights to a single (remote) repository.&nbsp; Branches are created when changes need to be made.&nbsp; Pull requests are useful to initiate peer review and discussions about a set of changes prior to merging them into the main branch. The use of shared repositories is more prevalent with small teams and within organizations working on private projects.

&nbsp;

### Fork \& Pull strategy

The purpose of a fork and pull strategy in Git repositories is to allow contributors to independently work on their own copies (forks) of a project, and then propose changes (pull requests) to the original repository for review and integration.

&nbsp;

With the *fork \& pull* strategy, contributors create their own (remote) copy of the original repository and push changes to that copy, which is referred to as a *fork*.&nbsp; Once a contribution is ready, it can be submitted through a pull request: the contributor basically requests the maintainer(s) of the original repository to pull into that repository the work that has been prepared in a fork.&nbsp; Note that nothing prevents multiple contributors from working together in the same fork prior to submitting their changes to the original repository.

&nbsp;

The main advantage of the *fork \& pull* strategy is that the contributors do not need to be explicitly granted push access rights to the original repository. That's why that strategy is typically used for large-scale open source projects where most contributors are not known by the maintainers of the repository.

&nbsp;

Another advantage of the *fork \& pull* strategy is that it prevents the original repository from being polluted with branches that are created and then abandoned but never deleted by their author.

&nbsp;

## Adopting Innersource practices

This section is very much inspired by this [Introduction to InnerSource ](<https://resources.github.com/innersource/fundamentals/> "target=\"\_blank\"") with its principles adapted to data modeling.

&nbsp;

[*Innersource*](<https://en.wikipedia.org/wiki/Inner\_source> "target=\"\_blank\"") (by analogy to *open source*) is a trend that consists of bringing into enterprises the best practices of the open source community, such as the *fork \& pull* strategy. The ambition is to improve the collaboration but without sharing proprietary information publicly. This trend is supported by some Git providers, such as GitHub and its [internal repositories](<https://docs.github.com/en/enterprise-cloud@latest/repositories/creating-and-managing-repositories/about-repositories#about-internal-repositories> "target=\"\_blank\"").

&nbsp;

Adopting innersource practices is like starting an open source community, but for the purpose of improving the development experience for data modeling inside your organization. As with open source software development, transparent collaboration mobilizes a community’s collective knowledge and skills to create better data models. An innersource community, in contrast, contains the knowledge, skills, and abilities of people and tools within a single organization.

&nbsp;

Innersource does not imply reduced security or privacy. You don’t have to share proprietary data models publicly or invite any outside individuals to view or access innersource projects. Organizations can rest assured that any non-public data models will remain securely within their environment, and only subject-matter experts, data architects, modelers and engineers with appropriate permissions will be able to contribute.

&nbsp;

Within an enterprise, “contributors” are data architects and modelers, as well as subject-matter experts across your organization, while “maintainers” are project’s leaders and key decision makers:

\- maintainers: data architects and modelers, project managers, and other key decision makers within your company who are responsible for driving a project’s vision and for managing day-to-day contributions.

\- contributors: subject-matter experts, data modelers and data engineers, and other roles within your company that help drive data modeling forward. Contributors are not necessarily part of the direct project team but help build the data models by contributing evolutions, submitting enrichments and adjustments, and more.

&nbsp;

Innersource is as much a cultural shift as it is a technological one, and it’s important not to underestimate what a challenge this can pose to some organizations. Like their open source counterparts, innersource projects thrive in places where efforts naturally lean toward discoverability and reuse. It also helps to have small, cross-functional communities of the organization that share similar interests and expertise. This vision is very much in line with the principles of [Domain-Driven Data Modeling](<https://hackolade.com/domain-driven-data-modeling.html>) that we advocate.

&nbsp;

An effective innersource process should be informal, mentored, self-selecting, and supportive of its participants. To effectively adopt innersource practices, contributors need to be able to work easily across silos and other organizational divisions. The degree to which an organization supports knowledge-sharing initiatives can be a good indication of how well they’ll be able to adapt.

&nbsp;

Innersource is one approach to modernizing your processes, speeding up development of data models, overcoming organizational barriers, and improving quality.

&nbsp;

In order, to support InnerSource without compromising integrity and security, it is advised to adopt a Fork \& Pull strategy for your repositories.

&nbsp;

![Image](<lib/Innersource%20fork%20and%20pull%20process.png>)

&nbsp;

## Fork the upstream repo (once)

Please refer to the user documentation of your Git provider to know how to fork a repository. Once you have created a fork, you can [clone it using Hackolade Studio](<Clonearemoterepository.md>), like any other repository.

\- [Creating a fork in GitHub](<https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository>)

\- [Creating a fork in GitLab](<https://docs.gitlab.com/ee/user/project/repository/forking\_workflow.html#create-a-fork>)

\- [Creating a fork in Bitbucket](<https://support.atlassian.com/bitbucket-cloud/docs/fork-a-repository/>)

\- [Creating a fork in Azure DevOps](<https://learn.microsoft.com/en-us/azure/devops/repos/git/forks?view=azure-devops\&tabs=visual-studio#create-a-fork>)

&nbsp;

**Note:** Hackolade Studio supports the *fork \& pull* strategy currently only for GitHub. Other providers will be covered in future releases.

&nbsp;

## Clone your fork locally (once)

A local repository is the repo that resides on your computer. In order to be able to work locally, we need to create a local copy of the remote repository.&nbsp; In Hackolade Studio, clone the forked remote repository, using [these instructions](<Clonearemoterepository.md>).

&nbsp;

Let's assume that you have forked a repository and that you have [cloned your fork](<Clonearemoterepository.md>). Working in a fork is like working in a traditional repository: you can [checkout branches](<Checkoutabranch.md>), [commit your local changes](<Commitlocalchanges.md>) and [push your local commits](<Pushlocalcommits.md>). You can also [pull remote commits](<Pullremotecommits.md>), for example if you are collaborating with other contributors on a same fork.

&nbsp;

## Create and checkout a branch

With this workflow, all new work is done on a branch, so it’s important to remember to create a new branch before you begin working.&nbsp; When you’re ready to start working on something new, create a new branch. **Do not reuse a merged branch.** Each model evolution should get its own branch and be deleted after it’s been merged.

&nbsp;

To create a branch, follow [these instructions](<Checkoutabranch.md>).  Give your new branch a meaningful name.

&nbsp;

## Work, commit, and push

**Warning:** work that isn’t committed, even if it is saved, doesn’t belong to a branch until you commit, so it will move with you if you change branches.&nbsp; This should be viewed as an advantage, since you can do your work, then decide to create the appropriate branch for it.&nbsp; You must [commit on a branch](<Commitlocalchanges.md>) for your work to be saved in that branch, and [push](<Pushlocalcommits.md>) to your remote forked repo.

&nbsp;

## Submit a Pull Request from a fork

The only difference with non-forked repo is the presence of an additional dropdown list when you [submit your changes for review](<Submitforreview.md>). After you select the target branch, you must choose a target repository:

\- if your changes are ready to be reviewed by the maintainers of the original repository, which is named *upstream*, then you should open a pull request in that repository directly.

\- if you are collaborating with other contributors and your changes are just an intermediary step, then you should open a pull request in the fork itself.

&nbsp;

![Innersource - Fork and Pull contribute to a fork](<lib/Innersource%20Fork%20N%20Pull%20contribute%20to%20a%20fork.png>)

&nbsp;

**Note** that, if you choose to create a pull request in the upstream repository, then that pull request will not be accessible through the left menu. The left menu only lists the pull requests that belong to the repository that is currently opened in Hackolade Studio, aka the fork in our example.&nbsp; The reason is that your current repo is the one selected, i.e. the one from which you create the PR onto the upstream repo.&nbsp; To view you PR, you would have to select the upstream repo.

&nbsp;

## Keep a fork up-to-date

If multiple people contribute to the same upstream repository from different forks (which is typically the case in a *fork \& pull* strategy), then your own fork will at some point become outdated, as it does not contain the contributions that have been merged in the upstream repository after you created it.

&nbsp;

This section explains how you can keep your fork up-to-date.

&nbsp;

As soon as you choose to contribute to the upstream repository, Hackolade Studio makes the branches of that repository available in your local clone, which enables a bunch of interesting features.&nbsp; First, every time you pull remote commits, the new commits not only get pulled from your fork, but also from its upstream repository. You can then use the [MERGE action](<Otheractions.md>) to keep your fork up-to-date with the upstream repository.

&nbsp;

If the repository opened in Hackolade Studio is a fork of an upstream repository that you chose to contribute to, then the MERGE action selects the default branch of that upstream repository (e.g. *upstream/main*) as the source of the merge operation.

&nbsp;

![Innersource Fork and Pull - keep a fork up-to-date](<lib/Innersource%20Fork%20N%20Pull%20keep%20fork%20up-to-date.png>)

&nbsp;

So to keep the active branch of your fork up-to-date with the default branch of the upstream repository, you must trigger the PULL action and then click on the button *Merge \& Push* of the MERGE action.

&nbsp;

## Compare a fork with its upstream repository

As explained in the previous section, Hackolade Studio makes the branches of the upstream repository available in your local clone of the fork as soon as you choose to contribute to that upstream repository. Those branches are also visible in [the *History* view](<Explorehistory.md>).

&nbsp;

![Innersource Fork and Pull - compare a fork with its upstream repo](<lib/Innersource%20Fork%20N%20Pull%20compare%20fork%20with%20ups.png>)

&nbsp;

&nbsp;

The branches prefixed with *origin/* belong to your fork. The branches prefixed with *upstream/* belong to the upstream repository. Since the *History* view allows to compare arbitrary commits, you can review the differences between your fork and the upstream repository. You can for example compare the latest commit on the branch *origin/main* with the latest commit on the branch *upstream/main*.

&nbsp;

If you are only interested in the history of one repository (the fork or the upstream repository but not both at the same time), you can filter the *History* view for a given *Remote.*

&nbsp;

![Innersource Fork and Pull - compare fork filter history](<lib/Fork%20and%20Pull%20-%20compare%20fork%20filter%20history.png>)

&nbsp;

Select the remote *origin* to only see the commits that belong to your fork. Select the remote *upstream* to only see the commits that belong to the upstream repository.

&nbsp;

## Compare a repository with one of its forks

As a maintainer of a repository, you might be interested in tracking progress in a given fork by comparing that fork with the repository that you are in charge of. You might also be interested in comparing forks with each others.&nbsp;

&nbsp;

**Note** that, in this section, the repository that is opened in Hackolade Studio is the upstream repository, not a fork as it was the case for the previous use cases.

&nbsp;

In the history of the upstream repository, you see a dropdown list named *Remote.*&nbsp; When you add a new remote, a list of forks are displayed.&nbsp; Select the fork(s) that you want to compare with/across and click on *Add*. Then close the dialog.

&nbsp;

![Innersource Fork and Pull - compare a repo with one of its forks](<lib/Fork%20and%20Pull%20-%20compare%20repo%20with%20its%20forks.png>)

&nbsp;

You now have access to the branches of the selected fork(s): branches are prefixed with the name of their owner. With the *History* view to [compare arbitrary commits](<Explorehistory.md>), you can&nbsp; review the differences between the upstream repository and a fork, or between 2 forks.

&nbsp;

