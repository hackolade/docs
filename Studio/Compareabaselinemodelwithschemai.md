# Compare a baseline model with schema in prod

A typical use case with Hackolade Studio is where you have a physical data model which, in this use case, is derived from a polyglot model, and you want to compare this physical model with the reality of a database instance. A similar scenario is already introduced from a DevOps point of view in the code-first example in [this article](IntegratetheCLIwithDevOpsCICDpip.md). The purpose could be to validate that the data model is up-to-date with production in terms of having captured all of the structures in the database. It could be also simply to enrich the physical model with physical-only metadata, such as indexes and partitions, etc.

&nbsp;

> [!IMPORTANT]
> The position of the models in the comparison is critical for the merge process. The convention, in case of conflicts, is that the values in right-hand models are the ones selected by default. Similarly, if you want to compare and merge a model derived from polyglot (hence including references to one or more polyglot models) with an independent model, and you want to preserve the references to the polyglot model in the derived model, then it is critical that the derived model be in the right pane for the compare & merge operation. Same for external references.

&nbsp;

Let's illustrate this a concrete example.

&nbsp;

At a high level, the process consists of reverse-engineering the database, and merging updates into the derived physical model, making sure to preserve the reference link to the parent polyglot model.

&nbsp;

![Compare and merge flow](<lib/Compare and merge flow.png>)

&nbsp;

## Update a derived physical model after compare with a database instance

In this example, we have a baseline physical model, which is derived from a Polyglot model. We want to update it by including changes that may have been made to the database instance. This is useful, for example, if you fear that your data model is not fully up-to-date with reality.

&nbsp;

The first step is to reverse-engineer the database instance to create a new physical data model. This temporary model is used to compare with the baseline model.

&nbsp;

1\. On the left, we have the physical model reverse-engineered from the database. It happens to contain additional elements not present in the baseline derived model: an *ExtraTable,* plus also new columns in an existing table.\
2\. On the right, we have the derived physical model that has a reference to its parent Polyglot model.\
3\. In the middle, by default, the merged model includes the objects from from both the left and the right model. It includes the metadata of the right-hand model, including the references to the parent polyglot model. It also includes the objects ExtraTable and additional columns in the existing table. In the merge screen, the user may deselect objects from the left-hand model that maybe should not be merged, if there's a good reason for that.

&nbsp;

![Update derived model with db instance](<lib/Update derived model with db instance.png>)

&nbsp;

The result is a new derived physical model that integrates selected changes from the database while continuing to inherit its reference link to the Polyglot model.

&nbsp;

> [!WARNING]
> When saving the merged model, you may wonder what name to give to your model file. Assuming that your models are stored in a Git repository, remember that Git performs automatic versioning of any changed file (after commit and push.) We suggest that you save the merged model with the same file name as the right-side model, i.e. the derived physical model. When you commit and push your merge operation, a new immutable version of the physical derived model is automatically created by Git. In case you want to revert your operation, you can still go back to the previous commit.

&nbsp;

Another way to illustrate the importance of putting the derived model in the right-hand pane is with the diagram below. Let's say you have a derived model as the left side model, and you compare and merge with the right side model which is not derived (hence has no reference link to any parent polyglot), then the merged model will have no reference link to any polyglot model.

&nbsp;

![Merge derived model with a non-derived model](<lib/Merge derived model with a non-derived model.png>)

&nbsp;

## Warning: merge models when both are derived from polyglot

What if both left and right models in the comparison are derived from different polyglot models?

&nbsp;

This scenario can occur in collaborative environments, such as a in the Workgroup Edition, where two versions of the same model are compared during a conflict resolution. There is a hurdle only in case the reference link is different.

&nbsp;

As stated before, during the merge operation, we only preserve the reference link of the right side model. It is important to place on the right-hand side the model whose reference links you want to preserve.

&nbsp;

![Merge 2 derived models](<lib/Merge 2 derived models.png>)
