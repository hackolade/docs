# Conceptual modeling with Polyglot

## Aligning on scope, concepts, and terminology

Before designing the logical and technical structure of your data models, it is essential to ensure that all participants -- business, technical, and cross-functional teams -- speak the same language. This is the primary role of the conceptual model, which provides a shared foundation before delving into technical complexity.

&nbsp;

The conceptual model helps to create alignment among stakeholders to:

\- clearly define and agree on the scope of the project

\- identify and formalize key concepts used in the domain

\- establish a common vocabulary, preventing misunderstandings early

&nbsp;

This phase aligns perfectly with the principles of [**Ubiquitous Language**](<https://martinfowler.com/bliki/UbiquitousLanguage.html> "target=\"\_blank\""), a core concept from Domain-Driven Design (DDD).&nbsp; Ubiquitous Language promotes using the same terminology across all discussions, documents,&nbsp; models, and even database tables and columns, and application code, thereby ensuring consistency from business conversations to technical implementation.

&nbsp;

During conceptual modeling, it is essential to ensure that all participants truly understand each other beyond just agreeing on technical diagrams.

&nbsp;

A proven communication technique to support this is the feedback loop, which consists of:

\- rephrasing what you understood in your own words

\- allowing your interlocutor to confirm or correct your interpretation

&nbsp;

This iterative approach helps identify misunderstandings early and leads to consensus on the right terminology to use for the rest of the project.

&nbsp;

Encourage all participants to practice this technique during conceptual modeling workshops. It's often by refining and repeating the language that teams naturally converge toward a shared, consistent vocabulary -- the foundation of an effective Ubiquitous Language.

&nbsp;

## Conceptual modeling with Polyglot

Hackolade Studio provides features specifically designed for conceptual modeling, including the Graph View in Polyglot data models, which offers a high-level, simplified visualization of entities and their relationships, without requiring attribute details at this early stage.

&nbsp;

This makes the model easy to understand for all stakeholders, even those without technical data modeling experience.

&nbsp;

Once the conceptual model is validated, teams can progressively move toward more detailed logical and physical models, grounded in a consistent and shared understanding.

&nbsp;

Make sure to read our article [Conceptual to Logical with Polyglot relationships](<ConceptualtoLogicalwithPolyglotr.md>).&nbsp; Polyglot relationships are designed to help you express meaning and structure first, without being constrained too early by implementation details such as foreign key constraints, join tables, or platform-specific rules.&nbsp; We make it easy to discuss concepts with business users, who might not be familiar with the technical aspects of data modeling, so as to focus on facts.

&nbsp;

Note that this graph representation of conceptual models has been adopted after observing that business users might find entity relationships diagrams to be somewhat more intimidating than graph views.&nbsp; However, both are possible with Hackolade Studio polyglot models:

&nbsp;

![Conceptual model polyglot graph view](<lib/Conceptual model polyglot graph view.png>)

&nbsp;

