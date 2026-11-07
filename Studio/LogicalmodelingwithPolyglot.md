---
description: Use a Hackolade Studio Polyglot model as a technology-independent logical model shared by targets with different paradigms.
seoTitle: Logical modeling with Polyglot data models
---
# Logical modeling with Polyglot

## Choosing the right approach

Once you've decided to create a logical model, it's important to define your technology-independent model needs, based on the diversity of your technical environment.

In Hackolade Studio, the Polyglot Model serves as a shared foundation for multiple physical implementations, ensuring consistency while allowing for technological diversity. As a reminder, a Polyglot model is like a logical model, in the sense that it is technology-independent. And it can be normalized like a traditional logical data model. But it can also be structured to accommodate downstream physical models that require hierarchical structures, denormalization, and polymorphism. So a Polyglot data model is like a logical model, but with the optional capability to be a lot more.

The complexity of designing this polyglot/logical model depends on the nature of your target technologies.

If all your target technologies share similar paradigms, for example, only relational databases, or only document-oriented databases, then designing the logical model is more straightforward. You can rely on the common principles of that family to build a polyglot model that naturally fits all your technologies.

However, when your ecosystem combines different types of technologies such as relational databases, document stores, graph databases, APIs, or other formats, then designing a logical model that remains truly technology-agnostic becomes more challenging. In such cases, you'll need to carefully define your logical model to avoid technology-specific biases, ensuring that it provides a solid, neutral foundation for all physical models, while still being meaningful and functional across the board.

## When technologies follow different paradigms

In environments where all your technologies belong to the same family -- for example, all relational databases, or all document stores -- we assume that as an experienced modeler, you know how to design accordingly. In such cases, the logical model naturally reflects the principles of that technology family.

Where things get more interesting, and more challenging, is when your ecosystem involves multiple technologies with fundamentally different paradigms.

Imagine a scenario where you need to design a logical model that serves as the foundation for different physical implementations across your system. For example, you may have:

- Relational databases to manage structured, transactional data
- An event-driven architecture leveraging Kafka pub/sub with Avro files
- APIs that expose structured and semi-structured data to external consumers
- Document-oriented databases supporting specific application features requiring flexibility
- Big Data platforms to handle large volumes of analytical or semi-structured data

In this type of project, the different technologies coexist, but they follow distinct paradigms. Your logical model becomes the common denominator, abstract enough to remain technology-agnostic, yet concrete enough to drive practical physical designs for each target.

In these situations, creating a Polyglot Model that remains technology-agnostic yet practical for all targets requires careful consideration and compromise.

### There is no perfect universal model

The reality is that you cannot create a logical model that perfectly fits all technological paradigms without making trade-offs. The objective here is not perfection. It is to find the right level of abstraction that provides value, clarity, and consistency, while still leaving enough flexibility to adapt in each physical model.

This is where the art of data modeling comes into play. Data modeling is not an exact science. It is an art of finding the right balance.

There is no single "correct" way to design a Polyglot Model in heterogeneous environments. What works depends on:

- the specific technologies involved
- your project priorities (performance, maintainability, simplicity, etc.)
- the compromises your teams are willing to accept

### Guidance through real world trade offs

In our experience, it is always beneficial to start with baby steps and progressively increase complexity, rather than trying to "boil the ocean" from the start. It is always better to break down complex problems into smaller manageable ones.

In the next section, we present different practical strategies for building a Polyglot Model across mixed paradigms.

Each approach comes with its own advantages, limitations, and best-fit scenarios. There is no universal recipe -- only informed choices. Our goal is to provide you with examples and insights, so you can apply your expertise and decide what works best for your organization.
