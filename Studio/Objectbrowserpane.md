# Object browser pane

The left-hand pane shows a dynamic tree representing the hierarchy of objects maintained in your current model.&nbsp; The tree is collapsible, but expanded by default.&nbsp; For large models, it can be quite long.

&nbsp;

&nbsp;![Object browser](<lib/Object browser.png>)

&nbsp;

You may adjust the width of the pane by moving the vertical ellipse ![Central pane - ellipse hovered](<lib/Central pane - ellipse hovered.png>)separating the Object Browser and central panes.&nbsp; You may toggle the appearance of the Object Browser pane by choosing the menu option View \> Object Browser, or by double-clicking on the vertical ellipse.

&nbsp;

To collapse a tree branch, click on ![Object browser - Minus](<lib/Object browser - Minus.png>).&nbsp; To expand a tree branch, click on ![Object browser - Plus](<lib/Object browser - Plus.png>).

&nbsp;

It is possible to toggle the appearance of the Object Browser pane from the workspace by choosing the menu View \> Object Browser.Pane.

&nbsp;

A **single-click** on an object increases the ERD zoom on the selected object, and displays the corresponding properties in the Properties Pane.

&nbsp;

A **double-click** on an object opens the hierarchical schema view and zooms in on the selected object.

&nbsp;

A **right-click** displays a contextual menu of actions possible for the selected object.

![Object browser - contextual menu](<lib/Object browser - contextual menu.png>)

&nbsp;

&nbsp;

## Find and Replace

At the top of the Object browser pane, a handy search bar lets you type any part of an object name:

![Object browser - search box](<lib/Object browser - search box.png>)

&nbsp;

and the tree will be filtered to display only strings matching the entry:

&nbsp;

![Object browser - search and filter results](<lib/Object browser - search and filter results.png>)

&nbsp;

There are several controls available to fine-tune the find and replace function:

![Find - Case sensitive](<lib/Find - Case sensitive.png>)&nbsp; press this button if you want to enable case sensitive search

![Find - complete word](<lib/Find - complete word.png>) press this button if you want to match only complete words

![Find - Regular Expression](<lib/Find - Regular Expression.png>) press this button if you want to match according to a regular expression (see [RegEx cheatsheet by example](<https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285> "target=\"\_blank\""))

![Find - word part](<lib/Find - word part.png>)&nbsp; if match is not on complete words, you have may specify to match only on the beginning or the end of the word

![Find - object type](<lib/Find - object type.png>) you may restrict the search on specific types of objects or only on data types

![Find - navigation](<lib/Find - navigation.png>) you may navigate through search results using the F3 (next) or Shift+F3 (previous) keys or the arrows

![Find - clear search expression](<lib/Find - clear search expression.png>) clears the current search expression

![Find - search history](<lib/Find - search history.png>) displays a list of previous search expressions in the current session

&nbsp;

In the Replace tab:

![Find - replace matched](<lib/Find - replace matched.png>) replace the selected matched word

![Find - replace all matched](<lib/Find - replace all matched.png>) replace all matched words

&nbsp;

&nbsp;

Find in files lets you search Hackolade models on the file system.&nbsp; The searched model files must be of the same target as the one of the open model.&nbsp; With a right-click, the contextual menu allows to open the searched model in a separate instance of the application.

