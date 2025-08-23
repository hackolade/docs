# ArchiMate application data objects

ArchiMate is an open-standard, visual modeling language for enterprise architecture, developed and maintained by [The Open Group’s ArchiMate Forum](<https://www.opengroup.org/archimate-forum/archimate-overview> "target=\"\_blank\""). Its mission is to enable architects to **describe**, **analyze**, and **visualize** the relationships across business processes, organizational structures, information flows, IT systems, and infrastructure.&nbsp; This is done using a common, lean notation of around 50 core concepts, deliberately designed to be simpler and more accessible than UML or BPMN.

&nbsp;

ArchiMate is a vendor‑neutral Open Architecture framework that aligns with TOGAF and enables **multi-layer modeling, i.e.** covering strategy, business, application, technology, and physical layers.&nbsp; [TOGAF](<https://www.opengroup.org/togaf> "target=\"\_blank\""), also maintained by The Open Group, is the most widely used enterprise architecture framework, covering governance, design, planning, and implementation.&nbsp; In that context, Archimate is the modeling language that complements TOGAF by visually representing architecture layers and relationships.

&nbsp;

ArchiMate has a structured and layered approach to modeling, and while it’s not a full-fledged data modeling language like ER diagrams, it **does offer essential constructs to model data,** specifically to support enterprise architecture decision-making.&nbsp; At the Application Layer, data objects represent a **discrete unit of information** implemented, used, produced, or persisted by applications.

&nbsp;

Note that there is no built-in support in ArchiMate for **attributes, cardinality**, or **normalization** like in ER models.

&nbsp;

When it comes to data, it uses data objects to describe containers, entities and their relationships.

&nbsp;

Since v8.3.0, Hackolade Studio allows you to generate ArchiMate-compliant files with applications data objects for your Hackolade Studio data models.&nbsp; To be clear, Hackolade Studio does not cover any of the many other layers of the [Archimate specification](<https://www.opengroup.org/xsd/archimate/> "target=\"\_blank\"") -- only applications data objects -- so they can be imported in specialized tools such as Archi, Bizzdesign, Mega, LeanIX, etc.

&nbsp;

This feature is only available in the editions: Professional, Workgroup, Free Trial, and Community. &nbsp;

## ArchiMate application data objects file

Hackolade Studio generates a .archimate file, in XML format.&nbsp; This file format can be opened by tools such as the open-source [Archi](<https://www.archimatetool.com/> "target=\"\_blank\"") tool.

&nbsp;

![Archimate Applicaiton Data Objects](<lib/Archimate Applicaiton Data Objects.png>)

&nbsp;

## ArchiMate Open Exchange file

The [Open Exchange file format](<https://www.opengroup.org/open-group-archimate-model-exchange-file-format> "target=\"\_blank\"") is tailored for third party tools that are Archimate-aware to exchange data structures, paradigms, concepts, etc...This format is also an XML structure that is quite close to the .archimate internals.&nbsp; It uses UTF-8 encoding (e.g. support special characters).&nbsp; The main difference is that the organization of the objects is separated from the objects declaration themselves.

&nbsp;

