# Pragmatic guide to a data modeling strategy

# Data Modeling Approaches with Hackolade Studio

## Modeling with purpose

Data modeling is more than an academic exercise; it's a practical approach for building functional, high-quality systems. At Hackolade, we believe that data models should address real-world challenges, and not become an end in themselves. Our goal is to make data modeling a strategic tool for creating efficient, scalable solutions, not just an abstract process.

&nbsp;

Hackolade Studio offers flexibility across the three primary levels of data modeling:

1. Conceptual Model
1. Logical Model
1. Physical Model

&nbsp;

Traditionally, the standard approach is to begin with a high-level conceptual model, then proceed to the logical model, and finally to the physical model, each step refining the design progressively. Our tool fully supports this structured, step-by-step approach.

However, we also allow for a more pragmatic, goal-driven mindset:

* Start at any level that best fits your project's context
* Move through the layers as needed, with no explicit requirement to necessarily complete all three
* Focus on the value each model layer brings to your specific project

&nbsp;

Ultimately, the goal is to build efficient, maintainable, and relevant solutions for both business and technical users -- not to model for the sake of modeling.

## Understanding the three levels: when and why

### Conceptual model: aligning on terminology

The conceptual model is key for agreeing on scope and concepts, and establishing a shared business language. By focusing on common terminology, it helps prevent misunderstandings and sets the foundation for clear communication, especially in large or cross-functional teams. Using **Ubiquitous Language** principles, this level aligns stakeholders before diving into technical details. In complex projects, a **Polyglot Model** can assist in this alignment.

### Logical model: a technology-agnostic foundation

The logical model defines a neutral, unified data structure that transcends specific technologies. It serves as a blueprint for creating various physical models. Our **Polyglot** approach to logical modeling ensures that the design remains independent of the technology stack, making it adaptable for diverse environments.

We recommend the polyglot/logical model particularly in multi-technology ecosystems that include databases (RDBMS, Graph, NoSQL), APIs, Avro, or Big Data solutions. However, if your project relies on a single technology, you can skip the logical layer and design directly in your target platform using Hackolade Studio.

### Physical model: a technology specific design

The physical model customizes the design for the technical specifics of each platform (e.g., NoSQL, relational databases, Graph databases, APIs, Big Data). This model ensures that the design works within the constraints of the chosen technology and optimizes implementation. Hackolade Studio supports more than 40 physical targets, allowing for tailored models that fit your specific platform.

## Flexibility over dogma: choose your path

At Hackolade, we prioritize results over rigid methodologies:

* follow the traditional path: Conceptual → Logical → Physical
* start directly with Logical or Physical models, if that suits your project
* model only what is essential for your specific context

&nbsp;

Remember that conceptual and logical layers are both handled by our Polyglot data model.

&nbsp;

The right approach depends on:

* Project size and complexity
* Number of technologies involved
* Need for cross-team alignment
* Time-to-market constraints

&nbsp;

### The Ultimate Goal: Delivering Practical Solutions

Data modeling should always serve a clear purpose: delivering tools and systems that are functional, scalable, and valuable. Hackolade Studio gives you the flexibility to tailor your modeling strategy to the specific needs of your project, without the complexity of rigid, academic frameworks.

Always model with intention, and avoid modeling just for the sake of it.

