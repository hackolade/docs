# Neptune with Gremlin API

As you develop the model for your Neptune-Gremlin graph database, with vertex labels and edge labels, Hackolade dynamically generates the corresponding Gremlin script.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

The information can be viewed in the Gremlin script tab.&nbsp; The script can be applied to the Neptune instance via the an [EC2 instance](<https://docs.aws.amazon.com/neptune/latest/userguide/get-started-access-graph.html> "target=\"\_blank\"") and following instructions on [this page](<ConnecttoaNeptuneinstance.md>).

&nbsp;

![Neptune-Gremlin script forward-engineering](<lib/Neptune-Gremlin script forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create graph vertices and edges by example.

&nbsp;

Or you may apply these scripts to a Gremlin directly to the selected instance with the menu option Tools \> Forward-Engineering \> Gremlin script:

![Neptune-Gremlin forward-engineering menu](<lib/Neptune-Gremlin forward-engineering menu.png>)

&nbsp;

&nbsp;

