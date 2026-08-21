# Reverse-engineer existing Collibra assets

A fairly common use case occurs when a Hackolade Studio model must be published to Collibra, while Collibra already contains the necessary assets.

&nbsp;

Generally, we consider that the Hackolade Studio model is the source-of-truth being published to Collibra.&nbsp; But workflow and/or timing may be such that Collibra assets already exist prior to Hackolade Studio being in the picture.&nbsp; We understand that Collibra users don't want to lose or have to recreate information.

&nbsp;

By default, we do not allow to reverse-engineer random domains from Collibra, unless a Hackolade Studio model has been previously published to that domain.&nbsp; But there's a workaround described below...

&nbsp;

**Important:** given that Collibra is not a data modeling tool and does not have to generate accurate technical artifacts such as DDLs and schemas, it does not have all of the checks and constraints that Hackolade Studio provides.&nbsp; In particular, but not only, Collibra does not enforce data types like we do for the corresponding physical target technology.&nbsp; As a result, the reverse-engineering process may lead to unexpected results and even errors.&nbsp; We provide this capability on a "best effort" basis, and encourage users to first practice on a sample domain and data model to understand the complexity and behavior.

&nbsp;

## Publish Hackolade configuration

The step to publish the Hackolade configuration to Collibra is a prerequisite and must have been executed once.&nbsp; It is described in more details [here](<https://hackolade.com/help/CollibraDataDictionaryintegratio.html#Check%20for%20the%20proper%20configuration>).&nbsp; This step ensures that the necessary Hackolade setup exists in your Collibra instance.

&nbsp;

From a Hackolade Studio model, even if empty, just got to Tools \> Forward-Engineer \> Governance Platforms \> Collibra, select the connection to your instance, and click the Submit button.&nbsp; If you encounter a dialog asking to create the required configuration, click the Apply button.&nbsp; If you see the tree of Collibra communities, then the configuration is completed (there is no need to publish a model at this stage.)

&nbsp;

## Assign the Hackolade Attribute Scope

By default, a domain, created in Collibra by using the Collibra UI or through the standard harvesting process, belongs to a Default scope.&nbsp; Here, you must assign a Hackolade attribute scope to your existing domain.

&nbsp;

In the Collibra UI, go to the Settings page \> Operating model \> Scopes, then in the the pane "Organization by scope", navigate through the tree to find the domain that you would like to reverse-engineer into a Hackolade Studio model, and assign "Hackolade Attribute Scope" in the column "Belongs to scope". &nbsp;

&nbsp;

![Collibra org by scope assignment](<lib/Collibra org by scope assignment.png>)

&nbsp;

If the "Hackolade attribute scope" does not appear in the list of scopes, it means that you did not successfully execute the previous step "Publish Hackolade configuration".

&nbsp;

## Assign the Hackolade Data Source Type

Now, within the domain you would like to reverse-engineer into a Hackolade Studio model, you must assign the target technology that corresponds to your Hackolade Studio data model.&nbsp; This assignment must be done for each schema in the domain, and hence repeated if you have more than one schema in the domain.&nbsp; In the Summary Overview tab, you need to find the property **HCK Data Source Type** and select the appropriate value from the dropdown list.

&nbsp;

![Collibra assign Hackolade data source type](<lib/Collibra assign Hackolade data source type.png>)

&nbsp;

&nbsp;

&nbsp;

## Reverse-Engineer from Collibra into a data model

You must now create a new data model for the corresponding target.&nbsp; Then go to Tools \> Reverse-Engineer \> Governance Platforms \> Collibra select the connection to your instance, and click the Submit button.&nbsp; Then fetch for domains in your org hierarchy and select the appropriate domain.&nbsp; Save your Hackolade Studio data model.

&nbsp;

## Merge into an existing data model

Optionally, you may want to link your Collibra assets to an existing Hackolade Studio data model.&nbsp; You may do so by following the steps in [this article](<Compareabaselinemodelwithschemai.md>), treating Collibra as a database source.&nbsp; This process allow you to merge the Collibra asset IDs with the corresponding objects in the model. &nbsp;

&nbsp;

