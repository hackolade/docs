# Best practices for collaboration and change management

Hackolade Studio supports strong Git-based workflows, so the best practices are essentially “treat models like code” with a clear branching, review, and release process.

​

**Core collaboration setup**

* Use Workgroup Edition with a shared Git repository (GitHub, GitLab, Bitbucket, Azure DevOps) as the single source-of-truth for all Hackolade models.
* You may store all your models in a single repository with a folder structure, or in multiple repositories, depending on the boundary needs of your organization.&nbsp; Or you can optionally co-locate models with application/schema repositories when possible so model changes are traceable alongside code and CI/CD artifacts.
* Make sure each modeler works against their own local clone, not shared file shares, to leverage Git’s distributed model and avoid file locking.

&nbsp;

**Daily work best practices**

* Before editing any model, you may want to pull from the remote so your workspace is up-to-date and you minimize potential conflicts.
* Save frequently in Hackolade, then commit small, logical changes with meaningful messages and push often rather than large “big bang” commits.

&nbsp;

**Branching and versioning strategy**

* Remember that Git automatically creates a new immutable version of a model with each commit.&nbsp; Avoid the use of version numbers in file names.
* Maintain a protected main (or master) branch for production-quality models that reflect what is deployed in data stores and downstream consumers.
* Use short-lived feature branches for new modeling work (new entities, refactors) and separate “minor fixes” branches for small corrections; merge via pull requests.

&nbsp;

**Example branching table**

| **Purpose** | **Branch example** | **Practice** |
| --- | --- | --- |
| Production model | main | Locked down, only PRs from reviewed branches, tagged per release.​ |
| Hotfixes | minor-fixes | Small corrections merged frequently into main.​ |
| New capabilities | new-features | Bigger refactors, merged less frequently, often for major versions.​ |
| Individual work | feature/x | Per-feature or per-modeler branches, rebased on latest main.​ |


&nbsp;

**Change management and governance**

* Use pull requests with mandatory reviewers so model changes are peer-reviewed; reviewers can review model changes is Hackolade’s handy side-by-side comparison dialog, and refer to Git history before approving.
* Treat the Git history as your audit log: use it to track who changed which entities, when, and why; never rewrite shared history, prefer forward fixes.​
* Standardize commit message conventions (for example, referencing Jira tickets or change requests) to tie model evolution to business requirements.

&nbsp;

**Conflict resolution and release integration**

* While conflicts are minimized given the file structure of Hackolade models, it is a good practice to pull remote changes before starting work and again before pushing; resolve any remaining conflicts in Hackolade’s merge UI, then validate the model.
* Avoid making changes or resolving conflicts with a Git client, as they are not aware of the modeling context that Hackolade’s UI handles much better.
* When two branches have diverged significantly, merge frequently and test early instead of waiting until just before a release.​​
* Integrate model branches into your CI/CD: generate schemas, scripts, and documentation from the same branch used by the application so deployments always match the approved model.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

