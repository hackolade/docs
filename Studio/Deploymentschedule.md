# Deployment schedule

- Architecture & Design: the architecture of the solutions is super simple and described in this diagram:

&nbsp;

![Client architecture diagram](<lib/Client architecture diagram.png>)

&nbsp;

Even when leveraging the browser deployment, the security-first architecture is very simple:

&nbsp;

![Desktop and Browser architecture](<lib/Desktop and Browser architecture.png>)

- Installation: installation is super simple and takes less than 1 minute per user.
- Configuration : configuration of connections to the Git repository and databases is done in a few seconds.
- Migration of existing data models : the length of this step depends on the number of models and whether special adjustments are required.
- Acceptance Testing : customer may run testing at any time test against a list of specified requirements
- Knowledge Transfer : Hackolade provides [online user documentation](WelcometoHackoladeStudio.md), [tutorials](Tutorial.md), [how-to guides](How-toguides.md), and an [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"_blank\"") with self-paced progressive video tutorials.
- Post-Implementation Support : maintenance and support are provided for as long as the subscription is valid.

&nbsp;

**🔍 Deployment Project Plan**

&nbsp;

<table style="width:70%">
<thead>
<tr>
<th>Week</th>
<th>Activities</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Week 1</strong></td>
<td>Kickoff meeting, architecture &amp; design, tool installation, environment setup, select pilot models, document objectives.</td>
</tr>
<tr>
<td><strong>Week 2</strong></td>
<td>Rebuild or import models into Hackolade Studio; validate mappings from legacy data modeling tools; resolve mismatches.</td>
</tr>
<tr>
<td><strong>Week 3</strong></td>
<td>Go/No-Go for full migration</td>
</tr>
<tr>
<td><strong>Week 4</strong></td>
<td><p>Hands-on workshop with users. Review CLI automation and Git workflows, <br>Integrate at least one model into CI/CD pipeline.</p><p>Test reverse- and forward engineering</p></td>
</tr>
<tr>
<td><strong>Week 5</strong></td>
<td>Wrap-up: document results, team feedback, and ongoing support.</td>
</tr>
</tbody>
</table>

&nbsp;

![Deployment project plan](<lib/Deployment project plan.png>)
