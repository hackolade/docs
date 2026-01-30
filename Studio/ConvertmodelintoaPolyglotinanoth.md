# Convert model into a Polyglot in another repository

When converting a model into a Polyglot model, you can choose to make the original model dependent on the generated Polyglot.&nbsp; This dependency works seamlessly, even when both models live in different repositories (cross-repository [remote references](<Remotereferences.md>).)

&nbsp;

However, during the conversion of a model to Polyglot, you cannot select a remote location for the generated Polyglot model.&nbsp; The target Polyglot must be created locally, which means you cannot generate it directly inside another repository.&nbsp; As a matter of fact, you might not even have write credentials in that remote repository, and would need to create a pull request.

&nbsp;

Fortunately, you can still reach the desired outcome by following the steps below.

&nbsp;

## Prerequisite: work with local clones

Make sure that both repositories (the one of the model to convert and the one for the Polyglot to generate) are also as a local clone.

&nbsp;

This operation cannot be performed from the Browser or from a remotely opened model.

&nbsp;

## Steps

1. in Hackolade Studio Desktop, open from your local clone the model to be converted
1. initiate the process Convert to Polyglot and choose "Dependent, relative path"
1. for the Polyglot location, select the local destination on your machine, inside the local clone of the *other* repository.\
**&nbsp; &nbsp; Warning:** the link will be stored as a relative local path, which is not what we ultimately want. We will fix this later.
1. save the model which is now derived from the generated Polyglot\
&nbsp; &nbsp; the Polyglot model is created, and a dependency link is established -- but this link is still local
1. commit and push the generated Polyglot model to the *other* repository, so it becomes available remotely for everyone
1. go back to the original model (the one that was converted and is now derived)
1. edit the Polyglot link so that it now references the Polyglot from its remote location\
&nbsp; &nbsp; this step stores the link as a proper cross-repository reference, which is the expected configuration

&nbsp;

## Important notes

### Risk: local-only link

If you do not update the Polyglot link, the link will still work only on your machine, because it points to a local path. Your colleagues will have a broken link.

&nbsp;

### Convert \& Merge

Storing the Polyglot directly in the local clone of the other repository allows you to following these steps for a Convert\\\&Merge feature, when the Polyglot already exists and needs to be merged with the newly generated one.
