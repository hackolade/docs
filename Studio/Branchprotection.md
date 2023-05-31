# Branch protection

Most of the [repository hubs](<Connecttoarepositoryhub.md>) provide the ability for repository administrators to protect branches. The most common use case for protecting a branch is to prevent its deletion and to force all contributions to that branch to be peer reviewed before being integrated.

&nbsp;

Protections only apply to branches within the remote repository. In [your own local clone](<Clonearemoterepository.md>), you are free to checkout a protected branch, modify it and even delete it, since these operations are local and do not affect the remote repository.&nbsp;

&nbsp;

However, pushing changes to a protected branch will most likely fail. So what if you end up in that situation? What should you do in case you have local commits that you cannot push due to branch protections?&nbsp; What if you get an error message such as "TF402455: Pushes to this branch are not permitted; you must use a pull request to update this branch."

&nbsp;

&nbsp;

![Image](<lib/Workgroup%20-%20branch%20protection%20error.png>)

&nbsp;

You should follow all 5 steps below:

&#49;) Start by [creating a new branch](<Checkoutabranch.md>) from the top bar. That branch will include the commits that you were not allowed to push from the previous branch.

![Workgroup - branch protection step 1](<lib/Workgroup%20-%20branch%20protection%20step%201.png>)

&nbsp;

&#50;) [Push your local commits](<Pushlocalcommits.md>). This time, they will not be rejected because you will be pushing your newly created branch instead of targeting the protected branch.

![Workgroup - branch protection step 2](<lib/Workgroup%20-%20branch%20protection%20step%202.png>)

&nbsp;

&nbsp;

&#51;) Submit your changes for review by opening a [change request](<Submitforreview.md>). Make sure to choose the protected branch as target branch.

![Workgroup - branch protection step 3](<lib/Workgroup%20-%20branch%20protection%20step%203.png>)

&nbsp;

At this stage, your local copy of the protected branch is not par with its remote counterpart, as it still contains the commit(s) that you could not push.&nbsp;

&nbsp;

&#52;) To reset your local copy of the protected branch, you must [delete it](<Checkoutabranch.md>) from the top bar. This will not affect the remote repository. Moreover, there is no risk to lose your contribution since you just pushed it.

![Workgroup - branch protection step 4](<lib/Workgroup%20-%20branch%20protection%20step%204.png>)

&nbsp;

&#53;) [Checkout a new local copy of the protected branch](<Checkoutabranch.md>). The changes that you were not allowed to push will not be available in that branch as long as your change request has not been [reviewed and merged](<Reviewchangerequests.md>) by one of your teammates.

![Workgroup - branch protection step 5](<lib/Workgroup%20-%20branch%20protection%20step%205.png>)

&nbsp;

&nbsp;

## Related content

* [Branch protection rules in GitHub](<https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches> "target=\"\_blank\"")
* [Branch permissions in Bitbucket Cloud](<https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/> "target=\"\_blank\"")
* [Branch permissions in Bitbucket Server](<https://confluence.atlassian.com/bitbucketserver/using-branch-permissions-776639807.html> "target=\"\_blank\"")
* [Branch policies and settings in Azure DevOps Repos](<https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies> "target=\"\_blank\"")
* [Branch protection in GitLab](<https://docs.gitlab.com/ee/user/project/protected\_branches.html> "target=\"\_blank\"")

&nbsp;

