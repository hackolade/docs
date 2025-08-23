# Deployment schedule

&nbsp;

\- Architecture \& Design: the architecture of the solutions is super simple and described in this diagram:

&nbsp;

![Client architecture diagram](<lib/Client architecture diagram.png>)

&nbsp;

Even when leveraging the browser deployment, the security-first architecture is very simple:

&nbsp;

![Desktop and Browser architecture](<lib/Desktop and Browser architecture.png>)

&nbsp;

\- Installation: installation is super simple and takes less than 1 minute per user.

\- Configuration : configuration of connections to the Git repository and databases is done in a few seconds.

\- Migration of existing data models : the length of this step depends on the number of models and whether special adjustments are required.

\- Acceptance Testing : customer may run testing at any time test against a list of specified requirements

\- Knowledge Transfer : Hackolade provides&nbsp; [online user documentation](<WelcometoHackoladeStudio.md>), [tutorials](<Tutorial.md>), [how-to guides](<How-toguides.md>), and an [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"\_blank\"") with self-paced progressive video tutorials.&nbsp;

\- Post-Implementation Support : maintenance and support are provided for as long as the subscription is valid.

&nbsp;

&nbsp;

**🔍 Deployment Project Plan**

| **Week** | **Activities** |
| --- | --- |
| **Week 1** | Kickoff meeting, architecture \& design, tool installation, environment setup, select pilot models, document objectives. |
| **Week 2** | Rebuild or import models into Hackolade Studio; validate mappings from legacy data modeling tools; resolve mismatches. |
| **Week 3** | Go/No-Go for full migration |
| **Week 4** | Hands-on workshop with users. Review CLI automation and Git workflows,&nbsp; Integrate at least one model into CI/CD pipeline.&nbsp; Test reverse- and forward engineering |
| **Week 5** | Wrap-up: document results, team feedback, and ongoing support. |


&nbsp;

![Image](<lib/Deployment project plan.png>)

