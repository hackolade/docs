# Symbols

In Entity Relationship Diagrams, it may be useful to add indications to help understand the diagram.&nbsp; Hackolade Studio currently allows 2 types of symbols: annotation and rectangle.

&nbsp;

Symbols can be added to a model diagram, either by doing a right-click in the diagram or Object Browser:

![Image](<lib/Symbol contextual menu.png>)

&nbsp;

or through the menu Actions \> Add Symbol&nbsp;

![Symbol Actions menu](<lib/Symbol Actions menu.png>)

&nbsp;

## Annotation

In Hackolade Studio, an annotation is a box that allows you to enter a text, legend, instructions, and other information that might be useful to users and readers of the diagram.&nbsp; You may create multiple annotations in an ERD.&nbsp; Annotations can be selected to be included in [ER Diagram Views](<DiagramViews.md>).&nbsp; And it is possible to create annotations that are specific to an ERDV.&nbsp; By design, annotation boxes are always displayed above entity boxes and container boxes.&nbsp; Annotation boxes can be sized using the handle in the bottom right-hand corner, or auto-sized, by clicking the double-headed arrow in the top right-hand corner.

&nbsp;

![Symbol annotation](<lib/Symbol annotation.png>)

&nbsp;

The annotation text can be entered in Markdown with HTML rendering.

![Symbol annotation properties](<lib/Symbol annotation properties.png>)

&nbsp;

You may want to attach an annotation to a container/schema/database, but this is not mandatory.&nbsp; If attached to a container, the size of the container will be auto-adjusted to include the annotation box(es.)&nbsp;

&nbsp;

Like entity boxes, it is possible to set the color and font style:

![Symbol annotation options](<lib/Symbol annotation options.png>)

&nbsp;

&nbsp;

## Rectangle

Starting with v8.4.0, Hackolade Studio also includes the possibility to create a rectangle in ER diagrams.&nbsp; A rectangular shape is a symbol that can be used to delineate diagram parts without impacting the model itself, for example to group entities together.&nbsp; Note that grouping of a subset of objects of a larger diagram is also possible using [ER Diagram Views](<DiagramViews.md>).&nbsp; Rectangles provide a different way to visually group entities.

&nbsp;

The model object container (schema/database/namespace/keyspace) has an impact on the schema or DDL being forward-engineered.&nbsp; A rectangle symbol on the other hand can be used to create grouping or associations of entities in a diagram to facilitate understanding of the diagram, but without impacting the physical model artifacts.

&nbsp;

![Symbol rectangle example](<lib/Symbol rectangle example.png>)

&nbsp;

&nbsp;

By default, rectangles are created to appear above container boxes and below entity boxes.&nbsp; That way you can create visual groups of entities within a container, or across multiple containers.&nbsp; If you need to, it is possible to slide a rectangle below a container.&nbsp; While the container is somewhat transparent, moving a rectangle behind a container means that the container title bar and the boundaries of the container are visible above the rectangle.

&nbsp;

![Symbol rectangle properties](<lib/Symbol rectangle properties.png>)

&nbsp;

&nbsp;

For a rectangle symbol, you may specify a text (which appears above the rectangle), a fill color with an opacity percentage, and the border color, if any.

&nbsp;

![Image](<lib/Symbol rectangle fill color properties.png>)

&nbsp;

Rectangle boxes can be sized using the handle in the bottom right-hand corner,

&nbsp;

When you have multiple rectangles with overlap, you may want to adjust the opacity and layering. &nbsp;

&nbsp;

&nbsp;

![Symbol rectangle above with low opacity](<lib/Symbol rectangle above with low opacity.png>)

&nbsp;

&nbsp;

&nbsp;

When rectangles overlap, you may want to be able to set which one is on top of the other.&nbsp; This is done either with the up/down arrow keys in the toolbar&nbsp;

![Symbol rectangle up-down layering toolbar](<lib/Symbol rectangle up-down layering toolbar.png>)

&nbsp;

or with the contextual menu&nbsp;

![Symbol rectangle up-down layering context menu](<lib/Symbol rectangle up-down layering context men.png>)

&nbsp;

you may adjust the layering of the boxes if they overlap:

&nbsp;

![Symbol rectangle behind with low opacity](<lib/Symbol rectangle behind with low opacity.png>)

Note that rectangles set to be behind containers cannot overlap above rectangles that have been set to be on top of containers, or vice versa.&nbsp; Each group, rectangles behind containers and rectangles on top of containers, are arranged separately.

&nbsp;

Rectangles can be selected to be included in [ER Diagram Views](<DiagramViews.md>).&nbsp; And it is possible to create rectangles that are specific to an ERDV. &nbsp;

