---
description: A knowledge graph connects actual business entities and facts. Hackolade Studio models property graphs, and support for RDF triple stores is in progress.
seoTitle: Knowledge graph modeling for property graphs and RDF
image: lib/Architectural vision including semantic web capabilities.png
---
# Knowledge graphs

**“What are the actual entities and relationships?”**

A knowledge graph **represents actual business entities, their characteristics, and the meaningful relationships that connect them.** While an ontology defines the concepts and relationships that can exist within a domain, a knowledge graph populates this conceptual framework with real-world facts and instances. It connects information about customers, orders, products, suppliers, contracts, projects, and other enterprise entities, potentially bringing together data from multiple heterogeneous sources into a coherent, interconnected representation of enterprise knowledge.

By making these connections explicit and machine-interpretable, a knowledge graph enables both humans and AI systems to navigate relationships, discover hidden connections, understand dependencies, identify patterns, and derive insights that would be difficult to obtain from isolated datasets. Rather than simply retrieving individual records, AI systems can traverse networks of related information, answer complex questions spanning multiple business domains, and, when supported by formal ontologies, infer new facts from existing knowledge.

Knowledge graphs are particularly valuable for contextual search, impact analysis, GraphRAG (Graph-based Retrieval-Augmented Generation), and agentic AI, as they provide a rich, interconnected knowledge foundation for more informed, context-aware, and explainable responses and decisions.

## **Knowledge graph modeling**

Hackolade distinguishes between two major graph paradigms:

|  | Labeled Property Graphs | Semantic Knowledge Graphs |
| --- | --- | --- |
| Structure | Nodes, edges, labels, properties | RDF triples, classes, predicates |
| Semantics | Explicitly named relationships | Formal vocabularies and ontologies |
| Query languages | Cypher, Gremlin | SPARQL |
| Technologies | Neo4j, JanusGraph, Neptune, Cosmos DB Gremlin | GraphDB, Stardog, AllegroGraph, Neptune RDF |
| Primary focus | Connected data and graph traversal | Knowledge representation, interoperability, and reasoning |

Hackolade already supports physical modeling for labeled property graph technologies and is extending its capabilities to the RDF triple-store ecosystem.

References:

[Data modeling techniques](DataModelingTechniques.md)

[Data modeling and schema design for semantic knowledge graph databases](<https://hackolade.com/semantic-knowledge-graph.html> "target=\"_blank\"")
