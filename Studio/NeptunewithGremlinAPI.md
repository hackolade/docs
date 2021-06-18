# Neptune with Gremlin API

As you develop the model for your Neptune-Gremlin graph database, with vertex labels and edge labels, Hackolade dynamically generates the corresponding Gremlin script.

&nbsp;

The information can be viewed in the Gremlin script tab.&nbsp; The script can be applied to the Neptune instance via the an [EC2 instance](<https://docs.aws.amazon.com/neptune/latest/userguide/get-started-access-graph.html> "target=\"\_blank\"") and following instructions on [this page](<ConnecttoaNeptuneinstance.md>).

&nbsp;

![Image](<lib/Neptune-Gremlin%20script%20forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create graph vertices and edges by example.

&nbsp;

Or you may apply these scripts to a Gremlin directly to the selected instance with the menu option Tools \> Forward-Engineering \> Gremlin script:

![Image](<lib/Neptune-Gremlin%20forward-engineering%20menu.png>)

&nbsp;

&nbsp;

