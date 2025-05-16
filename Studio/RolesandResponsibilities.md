# Roles and Responsibilities

## Hackolade Responsibilities

• **Software and license keys:** Software is available for [download](<https://hackolade.com/download.html>) at any time, and can be used at with a 14-day free trial license.&nbsp; Upon receipt of a proper Purchase Order, Hackolade provides the production license keys for the purchased products and options.

• **Training \& Knowledge Transfer:** Hackolade provides self-service [online user documentation](<https://hackolade.com/help/ExhibitAOpenSourcecomponentslibr.html>), [tutorials](<https://hackolade.com/help/Tutorial.html>), [how-to guides](<https://hackolade.com/help/How-toguides.html>), and an [eLearning platform](<https://community.hackolade.com/slides/all>) with self-paced progressive video tutorials

• **Documentation:** Hackolade provides self-service [online user documentation](<https://hackolade.com/help/ExhibitAOpenSourcecomponentslibr.html>), [tutorials](<https://hackolade.com/help/Tutorial.html>), [how-to guides](<https://hackolade.com/help/How-toguides.html>), and an [eLearning platform](<https://community.hackolade.com/slides/all>) with self-paced progressive video tutorials

&nbsp;

## Customer Responsibilities

For a successful Hackolade Studio implementation, it’s beneficial to have the right mix of customer staff resources, both for technical support and for governance and adoption. &nbsp;

&nbsp;

Here's a suggestion for the key roles and responsibilities:

| **Role** | **Key Responsibility** | **Staff Type** | **Time Commitment** |
| --- | --- | --- | --- |
| **Project Manager** | Oversee the project timeline and resources | PM | **Full-Time** |
| **Data Architects/Modelers** | Design, define standards, and migrate data models | Technical | **Full-Time** |
| **IT Infrastructure Team** | Set up and maintain Hackolade Studio deployment | IT | **Partial** (as needed) |
| **Data Governance Officer** | Ensure compliance and model governance | Governance | **Partial** (as needed) |
| **Git/Version Control Specialist** | Configure Git, manage versioning | Technical | **Partial** (during setup and troubleshooting) |
| **Subject Matter Experts (SMEs)** | Validate models, provide feedback | Business/Technical | **On-Demand** (during review sessions) |
| **End Users** | Consume models, participate in adoption | Business | **On-Demand** (when interacting with models) |
| **Training \& Support Team** | Provide ongoing training and support | Support | **Partial** (during training and support phases) |
| **CI/CD Specialist** | Automate pipeline deployment for models | Technical (optional) | **Partial** (during pipeline setup and maintenance) |


&nbsp;

**Time Commitment Breakdown:**

* **Full-Time:** Involves a dedicated person working on the project during the majority of its duration.
* **Partial:** Involves team members contributing during specific phases (e.g., installation, validation, setup).
* **On-Demand:** This role is typically called upon for specific tasks or feedback at certain stages, like during reviews or troubleshooting.

&nbsp;

## Key roles

Here's a brief outline of the key roles needed:

**&#49;. Project Manager (PM)**

* Oversee the entire migration process, ensuring timelines, budgets, and KPIs are met.
* Coordinate between teams and stakeholders to ensure smooth communication.
* Manage risk and issue resolution.

**&#50;. Data Architects/Modelers**

* Lead the data modeling effort, ensuring the accurate conversion of existing models to Hackolade.
* Define modeling standards, including naming conventions, data structures, and quality checks.
* Collaborate with both business and technical teams to align on model requirements.

**&#51;. IT Infrastructure Team**

* Set up and maintain infrastructure for Hackolade Studio (either client-based installs or browser-based SPA).
* Ensure that all required IT tools (Git, CI/CD) are in place.
* Support the setup of the Git repository for versioning and collaboration on models.

**&#52;. Data Governance/Compliance Officer**

* Ensure that the migration process and new models meet data governance, security, and compliance standards.
* Work closely with the IT team to set up access controls and permissions for data models in Git repository.
* Assist in defining and enforcing data modeling standards and best practices across the organization.

**&#53;. Git/Version Control Specialist**

* Set up and configure Git repositories, manage branching, and establish workflows for collaboration between data teams.
* Ensure smooth integration between Hackolade Studio and Git repositories for version control of data models.
* Provide support for CI/CD pipeline setup and maintenance.

**&#54;. Subject Matter Experts (SMEs)**

* Validate the accuracy and relevance of data models during the migration process.
* Provide feedback on model designs, ensuring alignment with business requirements.
* Assist with testing, training, and documentation.

**&#55;. End Users (Model Consumers)**

* Use Hackolade Studio for daily operations, data modeling, and collaboration.
* Participate in training sessions and feedback loops to ensure adoption.
* Report any challenges faced with the tools to the PM or support team.

**&#56;. Training \& Support Team**

* Provide training on Hackolade Studio for both technical and business users.
* Create internal documentation and resources for ongoing support.
* Serve as the point of contact for troubleshooting, resolving user issues, and supporting the adoption process.

**&#57;. CI/CD Specialist (optional)**

* Set up automated pipelines for model deployment, versioning, and testing.
* Ensure that models can be seamlessly integrated into data pipelines and analytics workflows.
* Collaborate with the Git/Version Control Specialist for smooth automation.

&nbsp;

&nbsp;

## Persona Use cases

Developing user personas can be a useful part of ensuring that the change management strategy is tailored to the different needs, behaviors, and concerns of each group within the organization. Below are several **user personas** that could be considered in the context of migrating to Hackolade Studio, along with customized strategies to address their specific needs:

&nbsp;

| **Persona** | **Key Concerns \& Needs** | **Customized Strategy** |
| --- | --- | --- |
| **Data Architects/Modelers** | Learning curve, automation, collaboration, integration with workflows | Hands-on workshops, pilot program, focus on Git-based workflows, internal champions, community of practice |
| **IT Infrastructure/DevOps** | Deployment security, integration with DevOps, user role management | Technical workshops, setup docs, Git and CI/CD integration, security-focused setup |
| **Business Users (Analysts)** | Simple interface, easy access to data models, business-relevant insights | Cross-functional workshops, model transparency, onboarding support, easy-to-read model documentation |
| **Data Governance Teams** | Compliance, security, governance in data modeling | Governance-focused workshops, security-first architecture, compliance documentation, monitoring practices |
| **End Users (Operational)** | Reliable data models, access to reports, no technical complexity | Data quality assurance, communication on model improvements, accessible reports/dashboards |


&nbsp;

&nbsp;

Further details can be found below:

**Use Case 1: Data Architects/Modelers**

**Persona**:

* **Name**: “Emily”, Data Architect
* **Role**: Leads data modeling efforts, designs database schemas, and ensures the quality and consistency of data models.
* **Skillset**: Advanced technical expertise in legacy data modeling tools, deep understanding of data structures, and strong collaboration with business stakeholders.
* **Goals**: Increase efficiency in model creation, improve collaboration with cross-functional teams, and ensure alignment with governance standards.

**Key Needs \& Concerns**:

* Comfortable with existing legacy data modeling tools and may feel that the new tool is redundant.
* Concerned about the learning curve associated with a new tool.
* Interested in integrating data models into larger data pipeline workflows.

**Customized Change Strategy**:

* **Training \& Skill Development**: Provide in-depth, hands-on **advanced modeling workshops** to show how Hackolade Studio improves modeling efficiency (e.g., schema design, collaboration features).
* **Pilot Program**: Start by migrating smaller, simpler data models to Hackolade Studio to demonstrate the benefits without overwhelming the team.
* **Feature Emphasis**: Highlight **automation features** (e.g., DevOps-triggered CLI with Git) and **version control** that can streamline collaboration and reduce manual effort in model versioning.
* **Community of Practice**: Create a community of **Hackolade Champions** within the data architect team to share best practices, solve challenges, and provide feedback.

&nbsp;

**Use Case 2: IT Infrastructure/DevOps Team**

**Persona**:

* **Name**: “John”, Senior DevOps Engineer
* **Role**: Responsible for deploying, maintaining, and securing the Hackolade Studio environment, integrating it into the CI/CD pipeline, and ensuring that the infrastructure supports smooth usage by the data modeling teams.
* **Skillset**: Expertise in cloud infrastructure, security protocols, DevOps tools (e.g., Git, Jenkins), and a strong understanding of IT governance and compliance.
* **Goals**: Ensure smooth deployment, manage user access and permissions, and integrate Hackolade Studio into the broader IT ecosystem.

**Key Needs \& Concerns**:

* Needs to ensure secure deployment and configuration.
* Concerned about how Hackolade Studio integrates with existing DevOps tools (e.g., Git, CI/CD pipelines).
* Requires easy management of user roles, access, and compliance of the solution.

**Customized Change Strategy**:

* **Technical Training**: Offer **technical workshops** focusing on the deployment, configuration, and security features of Hackolade Studio, including integration with **Git repositories** and **CI/CD pipelines**.
* **Documentation**: Provide comprehensive **setup documentation** and guidelines for integrating Hackolade Studio into the organization’s existing infrastructure (e.g., GitHub, Jenkins, Azure DevOps).
* **Automation \& Security**: Emphasize the ability to leverage **Git-based workflows** and automated version control for data models to streamline deployments and reduce operational overhead.
* **Support**: Set up a dedicated **IT support group** within the team to address deployment and integration issues quickly.

&nbsp;

**Use Case 3: Business Users (e.g., Analysts, Marketing, Sales)**

**Persona**:

* **Name**: “Sarah”, Marketing Analyst
* **Role**: Uses data models to gather insights and create reports, dashboards, and visualizations for decision-making purposes.
* **Skillset**: Strong business knowledge and analytical skills, but limited technical expertise in data modeling or database design.
* **Goals**: Access to high-quality, consistent data models that are easy to use and understand.

**Key Needs \& Concerns**:

* Concerned about having to learn a new technical tool.
* Wants a **simple interface** for accessing and interacting with data models without deep technical knowledge.
* Needs to ensure that the data models align with business needs and reporting requirements.

**Customized Change Strategy**:

* **User-Friendly Interface**: Highlight **Hackolade Studio’s user-friendly interface** and its ability to streamline **data model visualization**, making it easier for non-technical users to understand the models.
* **Data Model Transparency**: Provide **model documentation** and **easy-to-read diagrams** that show how the data relates to their business processes.
* **Cross-Functional Workshops**: Organize **cross-functional workshops** that involve both technical and business users to facilitate understanding of how data models support specific business outcomes.
* **Onboarding \& Support**: Offer **light-touch onboarding** that focuses on using models rather than technical training. Provide quick-access support for questions related to business data needs.

&nbsp;

**Use Case 4: Data Governance \& Compliance Teams**

**Persona**:

* **Name**: “Rajesh”, Data Governance Lead
* **Role**: Oversees data compliance, quality, security, and metadata management, ensuring that data governance standards are met across all organizational models.
* **Skillset**: Strong understanding of **data governance** principles, compliance regulations (GDPR, PII), and data security best practices.
* **Goals**: Ensure Hackolade Studio meets **data governance standards**, including **security**, **model versioning**, and **metadata documentation**.

**Key Needs \& Concerns**:

* Concerned about ensuring **compliance** and **security** of the data models.
* Wants to ensure that Hackolade Studio aligns with **data governance policies** (e.g., data lineage, data quality, audit trails).
* Needs to ensure that the tool supports **collaboration** without compromising on governance.

**Customized Change Strategy**:

* **Governance Training**: Provide **governance-focused workshops** explaining how Hackolade Studio supports **data governance** (e.g., metadata management, version history, schema version control).
* **Security \& Compliance Focus**: Demonstrate **Hackolade Studio’s security-first architecture**, data model verification, and its integration with data governance tools (data catalog, data dictionary.)
* **Documentation**: Create specific **compliance documentation** on how to use Hackolade Studio while adhering to legal or regulatory requirements.
* **Ongoing Monitoring**: Set up **regular audits** of the data models and processes, ensuring that governance is maintained throughout the modeling lifecycle.

&nbsp;

**Use Case 5: End Users (Operational Teams, Data Consumers)**

**Persona**:

* **Name**: “David”, Operational Data Consumer
* **Role**: Uses data models to inform operational decisions but doesn’t directly interact with data modeling tools. Instead, relies on insights and reports generated by business analysts.
* **Skillset**: Basic understanding of data but not involved in creating or modifying data models.
* **Goals**: Access to accurate, up-to-date, and consistent data for decision-making.

**Key Needs \& Concerns**:

* Wants to ensure that **data models** are reliable and trustworthy without needing to understand the technical details.
* Needs easy access to **reports** and **dashboards** created by analysts using the models.
* Concerned that a shift in modeling tools could affect data quality or timeliness.

**Customized Change Strategy**:

* **Data Quality Assurance**: Communicate how Hackolade Studio ensures high data quality by implementing **model governance** and **version control** to keep models accurate and up-to-date.
* **Impact Communication**: Regularly update end-users on **how data models** are being improved to support better decision-making.
* **Accessibility**: Ensure that data models are well-documented and that **dashboards** and reports created using the models are easy to understand and consume for non-technical users.

&nbsp;

