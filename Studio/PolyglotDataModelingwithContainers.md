# How to organize polyglot data modeling for teams: containers, domains, collaboration, and governance in Hackolade Studio

This guide explains common challenges in polyglot data modeling (organizing master data, team boundaries, collaboration, access control, and sharing) and shows practical ways to address them with Hackolade Studio features: container management, domain modeling, Git integration, access control, and export/sharing options.

Audience: Data modelers, data product owners, platform teams.
Prerequisites: Hackolade Studio installed, access to a Git platform (GitHub/GitLab/Azure DevOps/Bitbucket), and a team repo for models.

---

## The challenge
In a polyglot landscape, multiple teams model entities across different technologies. You need to:
- Avoid stepping on each other’s work while enabling parallel progress
- Organize master data (e.g., People, Product, Finance) for reuse across domains
- Control who can change what and when (authorization and approvals)
- Compose data products that draw from multiple domains
- Export and share only relevant slices (by team, container, or product)
- Keep logical/polyglot models aligned with physical targets (RDBMS schemas, document stores, Avro, keyspaces/namespaces, etc.)

Key nuance about containers: In Hackolade Polyglot, “containers” are logical aggregations that map to physical structures at derivation time (for example, RDBMS schema, Cassandra keyspace, Avro namespace). Use them deliberately with downstream physical targets in mind.

---

## Solution overview with Hackolade Studio

- Domain-driven modeling
  - Use domains to define ownership boundaries (People, Product, Finance…).
  - Keep shared master data in dedicated domain(s) with clear ownership.

- Container management
  - Create containers to structure entities with an eye on physical derivation (schema/keyspace/namespace).
  - Avoid using containers solely as a collaboration boundary if that conflicts with physical targets.

- Collaboration with Git
  - Use distributed version control for concurrent work without locks.
  - Branch by feature/domain, open pull requests, and merge with Model Compare & Merge when needed.

- Access control and authorization
  - Enforce permissions on the Git server (branch protection, code owners, reviewer policies).
  - Use separate repositories or subfolders with protected branches for sensitive master data.

- Export and sharing
  - Export models or slices at container/domain level to share limited sets (desktop license or external consumers).
  - Generate JSON Schema, Avro, relational DDL, etc., from selected scope.

---

## Step-by-step: recommended setup

1) Structure the repository
- Root repo (e.g., data-models)
  - polyglot/ (main polyglot model and domain folders)
    - domains/
      - people/
      - product/
      - finance/
      - shared-master/
  - physical/
    - rdbms/
    - document/
    - streaming/

Tip: For highly sensitive master data, keep shared-master in a separate repo with stricter permissions, and include it as a Git submodule in the main repo.

2) Create domains and shared master data
- In Polyglot model, create domains to reflect your organization (e.g., People, Product, Finance).
- Place shared master entities (e.g., Person, Organization, Currency) in a Shared Master domain. Document owning team and change policy.

3) Define containers with physical alignment in mind
- For each domain, create containers that will map to the physical target:
  - RDBMS: map container to schema (e.g., product_core, finance_ref).
  - Cassandra: keyspace.
  - Avro/JSON: namespace.
- Keep the container count purposeful; avoid using containers only to limit editing if that breaks physical mapping.

4) Set up Git collaboration
- Initialize a Git repo (or use existing). Connect Hackolade Studio to the remote.
- Branching model:
  - main: protected; production-ready models.
  - domain/*: domain teams’ integration branches (e.g., domain/product).
  - feature/*: short-lived branches for specific changes.
- Enable PR checks: schema validation, lints, required reviewers (CODEOWNERS).

5) Protect master data and critical domains
- Use Git server controls:
  - Branch protection on main and shared-master branches.
  - CODEOWNERS to enforce reviews from owning teams.
  - Optional: separate repo for shared-master with stricter access; pull via submodule.

6) Compose data products across domains
- When a product needs entities from multiple domains, reference the shared entities rather than duplicating.
- Use Model Compare & Merge to reconcile branch changes into the parent Polyglot model.
- Maintain clear dependency documentation between product models and shared master.

7) Export and share scoped artifacts
- From Hackolade Studio, export by container or domain to share a limited set of the model when needed.
- Generate downstream artifacts from the chosen scope:
  - JSON Schema for API or event contracts
  - Avro schemas for streaming
  - Relational DDL for RDBMS
- Store generated artifacts under physical/ subfolders by target technology and environment.

8) Review, validate, and publish
- Validate models in Studio (consistency checks, references, naming rules).
- Create PRs with a change summary. Use the diff in Model Compare & Merge for reviewers.
- On approval, merge to main and tag a release (e.g., vYYYY.MM.DD). Your documentation portal can point to the latest main or tagged release.

---

## Practical examples

Example A: People master shared across domains
- Context: People entities (Person, Address, Identity) are shared by HR, CRM, and Finance.
- Setup:
  - Domain: Shared Master
  - Container: people_master (maps to RDBMS schema or namespace)
  - Git: separate repo with protected main; included as submodule in data-models
- Workflow:
  - HR proposes a change in feature/people-id-verification
  - PR requires Shared Master owners’ review (CODEOWNERS)
  - On merge, downstream schemas regenerated (CI) and published for consumers

Example B: Finance reference data with restricted edits
- Context: Currency, TaxRate entities used across domains; only Finance team may change.
- Setup:
  - Domain: Finance
  - Container: finance_ref (maps to keyspace/schema/namespace)
  - Git: single repo; branch protection + required Finance reviewers
- Workflow:
  - Product domain needs a new attribute on Currency
  - They open an issue + PR; Finance reviewers must approve before merge

Example C: Export a limited model for a vendor
- Context: External vendor needs only Order and Payment entities.
- Steps:
  - In Studio, select the OrderMgmt container and Payment subdomain
  - Export JSON Schemas and a light documentation bundle
  - Share exported artifacts without exposing full enterprise model

---

## Best practices for teams

Modeling and structure
- Design domains around business capabilities. Keep master data centralized and versioned.
- Use containers to mirror physical targets. Avoid container sprawl.
- Standardize naming conventions for domains, containers, entities, and attributes.

Collaboration
- Prefer short-lived feature branches and frequent merges to reduce drift.
- Use Model Compare & Merge to resolve conflicts and keep polyglot + physical views aligned.
- Document change intent in PR descriptions with links to user stories/tickets.

Governance and access control
- Enforce CODEOWNERS and branch protection on critical areas.
- For high-sensitivity master data, use a separate repo and submodules; restrict write access.
- Establish a deprecation policy and versioning strategy for breaking changes.

Release and distribution
- Automate validation and artifact generation in CI (JSON Schema, Avro, DDL) for each PR and on main.
- Tag releases and publish artifacts to an internal registry or documentation site.
- Export model slices for targeted sharing with partners/vendors.

Operational hygiene
- Regularly clean unused branches. Archive deprecated containers/entities with clear annotations.
- Keep references healthy: avoid duplication; prefer shared definitions.
- Periodically review domain boundaries as org structures evolve.

---

## Frequently asked questions

Q: Should we use containers to isolate team work?  
A: Prefer Git-based isolation (branches, repos, permissions). Use containers primarily to reflect physical mapping (schema/keyspace/namespace). This avoids mismatch when deriving physical models.

Q: How do we prevent people from “stepping on each other’s toes”?  
A: Git enables concurrent edits; conflicts are resolved on merge. Combine this with CODEOWNERS, branch protection, and required reviews.

Q: How do we apply the same authorization in Git to exported schema files?  
A: Generate artifacts into protected folders/branches or separate repos with appropriate permissions. Use CI to gate changes and enforce code owner reviews.

Q: Can we share only a part of the model with limited desktop licenses?  
A: Yes. Export by container/domain to share a limited set without exposing the full model.

---

## Next steps
- Set up domains and containers in your Polyglot model per the guidance above.
- Configure your Git repo with branch protections and CODEOWNERS.
- Automate exports in CI for each target platform.
- Socialize the best practices within your teams and iterate.

If you need help tailoring this approach to your environment, contact Hackolade support.
