# Questions & Answers

### How to work with Git submodules?

Git submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project while keeping your commits separate.

&nbsp;

The presence of Git submodules in a repository will not prevent you from using Hackolade Studio. But there is no handling of Git submodules currently in Hackolade Studio.

&nbsp;

In case Git submodules are important for the handling of your data models, please [submit a feature request](<https://hackolade.zendesk.com/hc/en-us/requests/new> "target=\"\_blank\"").

### How to deal with non-ASCII symbols in file names?

By default, Git replaces non-ASCII symbols in file names with octal notation. For example, a file named "TrainScheduleф.json" will be treated by Git as "TrainSchedule\\321\\204.json".

&nbsp;

If you need to deal with non-ASCII symbols in file names, then open a terminal and run the command below in order to modify the default behavior of your local Git client.

&nbsp;

git config core.quotepath off

&nbsp;

See the official documentation about the Git configuration parameter [core.quotepath](<https://git-scm.com/docs/git-config#Documentation/git-config.txt-corequotePath> "target=\"\_blank\"") for more details.

