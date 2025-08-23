# Non-Ultimate edition integration

If you do not have the Ultimate package and did not get the Federated Operating model add-on, then starting with v8.3.6, we provide an integration, albeit with some graceful degradation, some limitations, and some required manual configuration.

&nbsp;

The primary limitation is that it is impossible to publish Hackolade Studio polyglot data models to the Logical Layer of Collibra, in support of their [Guided Stewardship operating model](<https://productresources.collibra.com/docs/collibra/latest/Content/Catalog/GuidedStewardship/OperatingModel/to\_catalog-om.htm> "target=\"\_blank\""), or of course the related lineage relations.

&nbsp;

![Collibra Guided Stewardship missing](<lib/Collibra Guided Stewardship missing.png>)

&nbsp;

And without Guided Stewardship on the Collibra instance, it is not possible to publish lineage from physical models to polyglot models (since polyglot models cannot be published to Collibra...):

![Collibra Guided Stewardship limited lineage](<lib/Collibra Guided Stewardship limited lineage.png>)

&nbsp;

Publishing physical data models to the Physical Layer of Collibra is possible.&nbsp; The process is identical for Ultimate and non-Ultimate editions of Collibra.&nbsp; Please refer to the main pages above for more details.

However, additional configuration is required on the Collibra side if you don't have the Ultimate edition subscription.

&nbsp;

## Additional Collibra configuration

When publishing a Hackolade Studio physical data model to Collibra, several Hackolade-specific assetType characteristics are created in Collibra.&nbsp; With non-Ultimate edition instances, these are not visible by default.&nbsp; They must be manually mapped to Collibra attributes to ensure that they are included in the layouts of the following asset types:

* **Schema, Table, Column, Database View**
* **Data Model, Data Entity, Data Attribute** - for users who publish Polyglot models and have the *Guided Stewardship* feature enabled, but do not have an Ultimate subscription.

&nbsp;

To add a characteristic to an asset type layout

1. Open **Collibra Settings**.
1. Go to the **Asset Types** page and click the asset type you want to customize.
1. Select **Global Assignment → Characteristics**, then click the **Edit Layout** button in the top-right corner.
1. In the *Edit Layout* page, click **Add a Characteristic**, find the desired characteristic, check **Add directly to the layout**, and click **Add**.

Adjust the characteristic position if necessary.

&nbsp;

This [short video](<https://youtu.be/R5hBnpyAeEI> "target=\"\_blank\"") illustrates the process.

&nbsp;

This process must be repeated for each of the following characteristics that you wish to see in Collibra for published Hackolade Studio data models:

&nbsp;

**Schema / Data Model:**

* Description
* HCK Data Source Type
* HCK Technical Name
* HCK Activated
* URL
* Any custom Hackolade container/schema properties that mapped to characteristic with the HCK Custom prefix (My own attribute - in Hackolade -\>  HCK Custom My own attribute - in Collibra)

&nbsp;

**Table / Data Entity / Database View:**

* Description
* HCK SELECT AS / Pipeline
* HCK Technical Name
* HCK Activated
* Any custom Hackolade entity properties that mapped to characteristic with the HCK Custom prefix (My own attribute - in Hackolade -\>  HCK Custom My own attribute - in Collibra)

&nbsp;

**Column / Data Attribute:**

* Data Type
* HCK Data Type(s)
* HCK Activated
* HCK Technical Name
* Description
* Description from source system
* Size
* Number of Fractional Digits
* Is Nullable
* Char Octet Length
* Is Primary Key
* Is Auto Incremented
* Primary Key Name
* Default Value
* Personally Identifiable Information
* Security Classification
* Minimum Value
* Maximum Value
* Minimum Text Length
* Maximum Text Length
* Date and/or Time Pattern
* Any custom Hackolade field properties that mapped to characteristic with the HCK Custom prefix (My own attribute - in Hackolade -\>  HCK Custom My own attribute - in Collibra)

&nbsp;

&nbsp;

&nbsp;

