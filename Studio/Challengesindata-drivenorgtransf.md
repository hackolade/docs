# Challenges in data-driven org transformation

According to a 2023 [survey](<https://static1.squarespace.com/static/62adf3ca029a6808a6c5be30/t/63a477e23d7f9162b7771d6b/1671722982363/WAVESTONE%20NVP--%20Data%20\&%20Analytics%20Executive%20Leadership%202023--Survey%20Findings.pdf> "target=\"\_blank\"") by Wavestone's New Vantage Partners, and relayed by [Harvard Business Review](<https://hbr.org/2023/06/why-chief-data-and-ai-officers-are-set-up-to-fail> "target=\"\_blank\""),&nbsp; 80% of data executives and business leaders cite cultural impediments – people, business process, organizational alignment – as the primary barrier to data-driven organizational transformation.&nbsp; That's well above the 20% scored by technical limitations.

&nbsp;

![Vision - survey of data-driven challenges](<lib/Vision - survey of data-driven challenges.png>)

&nbsp;

## Complexity and polarization in data-driven organizations

Without organizational alignment, it is hard to implement process changes, to mobilize people and make them receptive to the necessary changes to establish a data culture.&nbsp; One particularly difficult alignment to realize is between the business and IT sides of organizations.&nbsp; [Bill Inmon](<https://en.wikipedia.org/wiki/Bill\_Inmon> "target=\"\_blank\"") has referred to this issue as "[The great divorce between IT and Business](<https://www.linkedin.com/pulse/grea-divorce-business-bill-inmon/> "target=\"\_blank\"")", the consequences of which are just too important to ignore, and for which he offers some tactical actions. &nbsp;

&nbsp;

Before we can propose our own solution for this situation, it is important to identify some of the critical root causes:

\- technology stacks have dramatically increase in complexity;

\- data, its definition, its transmission, its processing, its storage, its management -- all of it is a complex business -- there is no magic wand;

\- if business and IT are not pulling together, everything gets harder for all parties;

\- many promises of technology solutions remain unfulfilled

&nbsp;

### Increased complexity in technology stacks

The architecture of monolithic applications used to be fairly simple with 3 tiers:

![Vision - Tech stack complexity before](<lib/Vision - Tech stack complexity before.png>)

&nbsp;

The evolution towards modern event-driven architecture patterns, microservices, serverless computing, container orchestration, and cloud architectures represents a shift towards more modular, scalable, and flexible systems that can adapt to the dynamic demands of today's technology landscape. This transformation has brought about a wealth of new possibilities and capabilities facilitated by new tools, technologies, and practices to help organizations design and manage increasingly complex applications.&nbsp;

&nbsp;

![Vision - Tech stack complexity now](<lib/Vision - Tech stack complexity now.png>)

&nbsp;

However, this evolution also introduces new challenges related to monitoring, security, and data consistency, which require careful consideration in the design and operation of these systems.

&nbsp;

Polyglot persistence is a natural response to the diversity of data types and access patterns in modern applications. It empowers organizations to select the right database for the right job, improving performance, scalability, and data modeling choices. However, it also introduces complexity in terms of data integration, synchronization, and management, which should be carefully addressed in the application architecture to ensure data consistency and overall system reliability.

&nbsp;

![Vision - Polyglot persistence](<lib/Vision - Polyglot persistence.png>)

&nbsp;

It used to be that a single team could determine the business needs, then design the whole application, build it, then run the infrastructure.&nbsp; The complexity today is such that collaboration between complementary teams is the only way to run complex projects on state-of-the-art technology.

&nbsp;

### Impatience, and the illusion of "quick-and-dirty" solutions

The venture capitalist Mark Andreesen wrote in the Wall Street Journal that “software is eating the world”, highlighting the growing influence and ubiquity of software in various industries.&nbsp; Also encouraged by other quotes like Mark Zuckerberg's "move fast and break things", as well as by an erroneous interpretation of the principles of the Agile Manifesto, many developers have adopted a code-first approach which carries inherent risks, including poor quality and a lot of rework, when it turns out that a little forethought would have helped tremendously.&nbsp;

&nbsp;

&nbsp;

![Vision - Design-First vs Code-First](<lib/Vision - Design-First vs Code-First.png>)

&nbsp;

It used to be that data modelers facilitated well-designed structures from the start of software projects, thanks to their unique ability to understand the business and translate business requirements into quality data structures.&nbsp; Earlier in the century, data modeling started to grow out of fashion, due to several factors.&nbsp; Some Enterprise Data Modeling initiatives went rogue and got in the way of getting things done.&nbsp; Some agile developers assumed that they knew enough about the business needs to do their own data modeling, or just started to code first, thinking that data was self-described or that schema-on-read was sufficiently self-explanatory.&nbsp; NoSQL vendors started to push the concepts of schemaless databases and schema-on-read, giving a false sense that data interpretation was intuitively obvious.&nbsp; And some business executives preferred quick-and-dirty approaches to future-proof solutions. &nbsp;

&nbsp;

### Polarization, or the impacts of an "us and them" culture

The ownership of data in an organization is a complex and often debated topic. In reality, it's not a matter of the business or IT owning the data exclusively.&nbsp; Instead, it's a shared responsibility that involves both business stakeholders and IT teams. The roles and responsibilities of these groups may differ, but they should work together to ensure the proper management, governance, and utilization of data.

&nbsp;

According to the same report by Wavestone's New Vantage Partners, there was previously a general agreement that the Chief Data Officer (CDO) function was best suited to fit within the Chief Information Officer (CIO) organization.&nbsp; Now, a majority – 56% – of CDOs (or CDAOs -- Chief Data Analytics Officers) appear to report to business rather than technology functions.

&nbsp;

The key to successful data management is collaboration between business and IT. Ownership of data should be seen as a partnership. Business stakeholders define what they need from data, while IT teams provide the tools, infrastructure, and expertise to support those needs.&nbsp; Effective data governance practices can help establish roles and responsibilities and ensure that data is used responsibly, securely, and in alignment with business objectives.&nbsp; Ultimately, the organization as a whole benefits from this shared approach to data ownership, as it ensures that data is both a valuable business asset and a well-managed technical resource.&nbsp;

&nbsp;

The installation of Data Catalogs, Metadata Management (MDM), and Data Quality Management (DQM) solutions was supposed to facilitate the collaboration.&nbsp; Unfortunately, their adoption in organization has been limited mostly to business users.&nbsp; There is a misalignment between the business-focused ownership of metadata management solutions (typically overseen by Chief Data Officers or business stakeholders) and the technical needs of IT developers, leading to challenges and inefficiencies in data management and utilization. &nbsp;

&nbsp;

![Vision - Polarization of Business and IT](<lib/Vision - Polarization of Business and IT.png>)

&nbsp;

In particular, these solutions lack a critical aspect of data management: the robust support for schema design, definition, evolution, validation, version control and lifecycle management.&nbsp; Such shortcomings explain the struggle for adoption of Metadata Management suites by technical users in the organization.

&nbsp;

### Absence of a single source-of-truth for metadata

A contributing factor to the lack of built-in hand-in-hand collaboration between business and IT, or maybe a cause of it(?), is the absence of a single source-of-truth (SSOT) for the meaning and context of data and data structures.&nbsp; Instead of a genuinely **single** source-of-truth, organizations have a multitude of receptacles for metadata containing often out-of-date and/or contradictory information.&nbsp; Such fragmentation and lack of synchronization&nbsp; leads to tensions, ambiguity, errors, and most likely distrust for the tools in place and a drop of adoption. &nbsp;

&nbsp;

Typically, each organization may own several of these families of metadata receptacles:&nbsp;

\- Git repository of source code for application developers, most likely with a Git platform (GitHub, GitLab, Bitbucket or Azure DevOps Repos), possibly with some schemas and/or descriptions of structures in application code;

\- technical data catalog used to facilitate queries (AWS Glue, Databricks Unity, Hive Metastore, Oracle Data Catalog, etc.);&nbsp;

\- schema registry for pub/sub pipelines so producers and consumers of transactions can understand each other (Confluent, RedPanda, Amazon MSK, Pulsar, Azure EventHub, etc.);&nbsp;

\- documentation site for REST APIs (own website, SwaggerHub, ...);&nbsp;

\- repository for data models stored in a proprietary format, from a legacy provider, and used by data architects and data modelers;

\- data governance solutions used by the data citizens on the business side (Alation, Acryl DataHub, Apache Atlas, Azure Purview, BigID, Collibra, Informatica EDC, or some sort of homegrown solution.)

&nbsp;

![Vision - metadata receptacle silos](<lib/Vision - metadata receptacle silos.png>)

&nbsp;

These tactical and fragmented solutions quickly create additional silos, each owned by different communities in the organization with different requirements and objectives.&nbsp; They foster the lack of collaboration and coordination between the different stakeholders.&nbsp; Each of them wants information to be organized for their own needs, and according to their own processes, without concern for the other communities.

&nbsp;

It was the promise of data governance and metadata management solutions to solve this challenge.&nbsp; Unfortunately, these often very expensive solutions have revealed serious shortcomings in meeting expectations of organizations and their data leaders. &nbsp;

&nbsp;

They may be fine for business metadata, but they fail to recognize the needs surrounding technical metadata.&nbsp; Business metadata helps business stakeholders understand and interpret data without delving into technical details, whereas technical metadata focuses on the technical attributes of data, and is used to manage and maintain data, design databases and data exchanges, and ensure data quality and performance.&nbsp; They are both essential for comprehensive data management, and they often complement each other in describing and maintaining data assets within an organization.

&nbsp;

As each community goes its own way, metadata management solutions failed to fulfill the promise of creating a single up-to-date source-of-truth for the metadata of organizations. Mainly because their implementation has been biased towards one community, at the expense of the others.&nbsp; CDOs and data citizens in the business might be originally happy to own the platform, until they realize that developers have their own interpretation of data, and make applications evolve without consulting them. &nbsp;

&nbsp;

On the business side, metadata management suites primarily focus on harvesting, documenting and organizing metadata well after data structures have been in place, an inherently reactive method. Such a reactive approach greatly increases the risks for inaccuracies and omissions in both the data itself and its metadata that may not fully reflect the complexities and nuances of the data structures, resulting in incorrect assumptions, misunderstandings, and errors.&nbsp; Let's add to that inconsistencies, operational inefficiencies, data security and compliance risks, scalability challenges, higher costs and lack of trust.

&nbsp;

Data model marts by legacy data modeling providers also fail to deliver on the promise of a single source-of-truth, if only because the solution they provide is proprietary and not fully integrated with any of the other silos.

&nbsp;

## Conclusion

While it is clear that cultural impediments – people, business process, organizational alignment – are the primary barrier to data-driven organizational transformation, it is also obvious that many technical factors contribute to the problem instead of providing solutions:

\- technology stacks and architecture patterns are increasingly complex;

\- misunderstood agile principles, code-first development, and management impatience have created enormous technical debt and decreasing data quality;

\- instead of treating collaboration and ownership of data as a partnership, business and IT have worked in their corner and implemented tools that tend to polarize teams;

\- every vendor is pushing it own "single" source-of-truth solution to replace x silos.&nbsp; After implementation, it becomes obvious that now the organization has x+1 silos..

&nbsp;

It is time to address these root causes head-on\!&nbsp; Proceed to the [next page](<Solutionoverview.md>) to see the solution we propose with Hackolade Studio to improve collaboration, make complexity manageable, align the interests, and in the end restore the trust between business and IT...Hint...it does NOT involve the creation of yet another receptacle\!

