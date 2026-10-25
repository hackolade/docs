# What is a data model?

This is the first in a series of tutorials for Hackolade Studio. The first few tutorials cover basic concepts to provide a complete and progressive picture. If these concepts are known to you, you may skip directly to get [hands-on](Createyourfirstdatamodel.md) with Hackolade Studio.

&nbsp;

Watch this [short video tutorial](<https://community.hackolade.com/slides/slide/part-1-what-is-a-data-model-3> "target=\"_blank\"") to learn the basic principles of data modeling. And click here to consult the [slides](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-1-what-is-a-data-model> "target=\"_blank\"").

&nbsp;

## Overview

A data model is an abstract representation of how elements of data are organized, how they relate to each other, and how how they relate to real-world concepts. It is an explicit representation of the structure of data. The purpose of data modeling is to support the development of IT systems and to ensure consistency, compatibility, and quality of data.

&nbsp;

At a higher level, a data model describes a business. It is a blueprint for applications, a map helping evaluate design options beforehand, think through the implications of different alternatives, and recognize potential hurdles before committing sizable amounts of development effort. A data model helps plan ahead, in order to minimize later rework. In the end, the modeling process accelerates development, increases quality of the application, and reduces execution risks.

&nbsp;

A data model can be easily understood with an Entity-Relationship Diagram (ERD), a graphical representation of entities (things a business needs to remember in order to perform processes), their characteristics, and how they all relate to one another.\
![Physical data model](<lib/Physical data model.png>)

&nbsp;

While graphical representations are useful for humans, they are not "consumable" by systems. Hence, the purpose of data modeling does not stop when the model is created. It is useful to generate artifacts in the form of a schema -- a scope contract between a producing system and a consuming system, i.e. typically an application and a database, or 2 applications.

&nbsp;

![Physical schema](<lib/Physical schema.png>)

&nbsp;

In other words, a data model is not an end goal, it is only the means to an end -- to ensure compatibility of data-exchanging systems in a world evolving at an increasingly fast pace. By designing data structures and maintaining them via data models, teams can easily manage the rapid evolution of data structures across applications and data pipelines.

&nbsp;

## How to start a data model from scratch

When designing applications, it is common to start with "functional requirements", a text description of the service that the software must provide. A functional requirement typically includes descriptions of the data inputs, the operations performed by the system, the workflows, and the expected reports and outputs, as well as the roles of the actors.

&nbsp;

The creation of a data model is an iterative process. Don't try to model everything at once. You should start with the concepts representing the core purpose of the application, and progressively dive into the details. And make sure to validate your design with other application stakeholders and domain experts, and through a simulation of the different use cases of the application.

&nbsp;

## Components of a data model

When reading the description of a system, a data modeler will try to identify: entities, their attributes, and the relationships between the entities. While it may be a bit a caricature, one technique is to associate nouns in a sentence to entities, while verbs indicate either an attribute or a relationship.

&nbsp;

For example: a customer, with first and last name, owns a vehicle. The vehicle was registered on a given date and is manufactured by a make.

- Entities: customer, vehicle, and make
- Relationships: customer OWNS vehicle, and make MANUFACTURES vehicle
- Attributes: first name and last name are attributes of customer. Registration date is an attribute of vehicle.

&nbsp;

In relational databases, each entity will lead to a physical table with columns for each attribute. Foreign Key relationships will link tables together.

&nbsp;

With NoSQL databases and [denormalization](Relationshipsanddenormalization.md), it's a different story... Plus entities can be called collections, and attributes can be called fields. each vendor may call things differently, as you can see on [this page](SQLandNoSQLdatabasesAPIsandstora.md).
