# Enterprise semantics

Hackolade Studio supports semantic modeling, ontologies, and knowledge graphs through a combination of **technology-independent data modeling, explicit representation of business semantics, graph database modeling, and transformation of models into technology-specific representations.**

Its distinguishing approach is to bridge the gap between traditional data modeling and semantic modeling, rather than treating them as separate disciplines. Controlled vocabulary of of business terms, business concepts, their definitions, properties, relationships, constraints, and hierarchies can be captured independently of their eventual technical implementation.

Perhaps the most distinctive aspect of Hackolade's approach is that an ontology does not need to exist in isolation from the rest of the enterprise data architecture.

![Architectural vision, including semantic web capabilities](<lib/Architectural vision including semantic web capabilities.png>)

Unlike standalone ontology editors, Hackolade's approach is to integrate semantic modeling into the broader data modeling lifecycle, connecting business concepts and formal knowledge representation with the actual structures used to store, exchange, and consume data.

**Hackolade's vision is to establish an independent, technology-agnostic semantic metadata layer that bridges business understanding, formal ontologies, physical data architectures, and AI consumption, without requiring organizations to maintain disconnected representations of the same business knowledge.**

## Related and complementary concepts

A simple way to remember the difference:

[**Taxonomy**](Taxonomy.md) → How are business concepts classified and organized?\
[**Semantic model**](Semanticmodeling.md) → how structured data should be understood and queried?\
[**Ontology**](Ontology.md) → what business concepts exist and how they can relate?\
[**Knowledge graph**](Semanticlayer.md) → what actual entities exist and how they are connected?\
[**Semantic layer**](Semanticlayer.md) → how can consumers consistently access and leverage this meaning and knowledge?

\
They overlap. They complement each other. But they are not interchangeable.

Many AI architecture conversations use these terms interchangeably.  They shouldn't.  Each plays a different role in helping AI understand the enterprise.

![Enterprise Context Concepts Compared](<lib/Enterprise Context Concepts Compared.png>)

\
\
And in an **Enterprise Context Layer**, each contributes a different kind of context that helps AI systems reason more accurately about the business.
