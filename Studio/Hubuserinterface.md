# Hub user interface

## Home page

The Hackolade Model Hub home page displays a dashboard.&nbsp; For the repositories configured as sources for the Hub, each tile represents a category of assets in the database with a counter.&nbsp; &nbsp;

&nbsp;

Each tile is clickable so you can start browsing.&nbsp; There is also a Lineage button to display a graph of all your models in the repositories.

&nbsp;

![Hub home page](<lib/Hub home page.png>)

&nbsp;

Additional dashboard items will be added over time.

&nbsp;

## Workspace

The Hackolade Enterprise Model Hub portal page is divided in multiple panes which may vary depending on where you are in the application.

&nbsp;

You may select a model and its content by exploring the repositories displayed on the left, or you may perform a search by keyword.

&nbsp;

![Hub portal workspace](<lib/Hub portal workspace.png>)

&nbsp;

## Search bar

The Hub **search bar** is an interactive user interface element.&nbsp; It allows you to enter text and search for specific assets or model objects: containers, entities, attributes.&nbsp; When you select a search result, you will be able to consult their detailed properties, structure, lineage, etc. &nbsp;

&nbsp;

You may access the search at any time by clicking inside the search bar, or by pressing Ctrl/Cmd+K.

&nbsp;

![Hub portal search bar](<lib/Hub portal search bar.png>)

&nbsp;

As you type, the search bar displays suggested results, helping to refine the search query or select a suitable result. A preview of the first results is displayed in a dropdown panel.&nbsp; You may see the details for one of the search results, or you may display the full list of results in the central pane by pressing Enter or by clicking the link "View all results".

&nbsp;

If the list is too long, you may want to filter the search results by applying one or more filters on the right hand side of the dropdown panel.&nbsp; There are 3 families of filters: by repository, by model object, or by model target technology. By default, no filter is applied.&nbsp; If you check one or more boxes, the search results are narrowed to match the selected filter.

&nbsp;

Once you select a search result and you view the details, you may want to navigate up or down through the results without having to change the screen you're on.&nbsp; At any time, you may go back to the results list of your last search.

&nbsp;

To clear your search input, simply click the X in the search bar.

## Explorer pane

The explorer pane is on the left side of the workspace.&nbsp; You may adjust its width by dragging it left or right.

&nbsp;

The explorer pane is divided into an upper part so you may explore the repository or repositories and their folders, and a lower part so you may explore the selected model.&nbsp; Each part is made of a hierarchical structure with expandable/collapsible nodes.&nbsp; Blue text is clickable and displays the relevant details in the central pane.&nbsp; There is a handle between the upper and lower parts of the pane so you may adjust their size.

&nbsp;

![Hub explorer pane](<lib/Hub explorer pane.png>)

&nbsp;

&nbsp;

## Central pane

The central pane is where you can see detailed information for the selected object.&nbsp; There are tabs with a searchable and customizable grid so you can drill down further into the selected object.

&nbsp;

A breadcrumb at the top allows to selectively go back up in the hierarchy.&nbsp; At any time, you may open the corresponding model in Hackolade Studio.

&nbsp;

![Hub central pane](<lib/Hub central pane.png>)

&nbsp;

## Where-Used tab

The where-used grid display s list of downstream models to allow a view on impact analysis.

&nbsp;

![Hub where-used grid tab](<lib/Hub where-used grid tab.png>)

&nbsp;

&nbsp;

## Lineage tab

The lineage tab display a graph of the relationships between models, if any.&nbsp; While the where-used grid shows downstream models only, the lineage graph shows both upstream and downstream models, if any. &nbsp;

&nbsp;

Models can be derived from a polyglot model, and/or have references to external definitions.&nbsp; Given the modular capabilities we advocate with [domain-driven data modeling](<https://hackolade.com/domain-driven-data-modeling.html> "target=\"\_blank\"") and the capability to refer to parts of multiple other models, it may be handy to see how models relate to each other.&nbsp; This information is useful to measure the impact of a change upstream on models downstream. &nbsp;

&nbsp;

![Hub lineage diagram tab](<lib/Hub lineage diagram tab.png>)

&nbsp;

You may search the graph, zoom in or out, select any model in the graph, maximize the display, and toggle a mini map when the graph is particularly large.

&nbsp;

&nbsp;

## Properties pane

The properties pane is on the right side of the workspace.&nbsp; You may adjust its width by dragging it left or right.

&nbsp;

The properties pane is similar to the one you have in Hackolade Studio.&nbsp; It may display additional tabs, if applicable, and their corresponding properties.

&nbsp;

You may toggle the display of empty properties.

![Hub properties pane](<lib/Hub properties pane.png>)

&nbsp;

&nbsp;

&nbsp;

## Help button

The Help button allows you, at any time to:

\- restart the application quick tour

\- access this online documentation page

\- display the About box, including a list of the open-source libraries used in the application

&nbsp;

![Hub help button](<lib/Hub help button.png>)

&nbsp;

