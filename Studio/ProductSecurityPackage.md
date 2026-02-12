# Product Security Package

**Software Assurance and Secure Development Overview**

&nbsp;

## &#49;. Objective and scope

This document describes the security practices applied to the design, development, testing, release, and maintenance of Hackolade Studio and Model Hub.&nbsp; It is intended to provide assurance that the software is engineered and maintained in accordance with recognized secure development and software supply chain security principles.

&nbsp;

## &#50;. Secure Software Development Lifecycle

Hackolade software products are developed under a defined Secure Software Development Lifecycle integrating security activities from requirements through release.&nbsp; Security considerations are incorporated into architecture design, feature development, and change management processes.

&nbsp;

Threat modeling is performed for new features and significant architectural changes to identify trust boundaries, attack surfaces, and abuse scenarios.&nbsp; Security requirements are documented and tracked alongside functional requirements.

&nbsp;

Developers receive secure coding guidance aligned to industry standards such as OWASP practices.&nbsp; Code reviews include security considerations proportionate to component risk and exposure.

&nbsp;

Hackolade operates a gated development pipeline in which every code change is introduced through a formal pull request workflow.&nbsp; Each pull request is subject to mandatory peer review, during which reviewers explicitly assess correctness, maintainability, and security considerations. Changes cannot be merged without explicit reviewer approval.

&nbsp;

In parallel with peer review, automated static code analysis is executed for every pull request. This analysis identifies insecure coding patterns, potential vulnerabilities, and quality issues. Findings are reported directly in the development workflow and block merges until resolved. This ensures that known insecure constructs are systematically prevented from entering the codebase.

&nbsp;

All code changes are further validated through an automated CI/CD pipeline that executes unit tests, UI tests, and end-to-end tests across supported platforms.&nbsp; Security-relevant regressions are therefore detected early and consistently.&nbsp; Automated testing is supplemented with targeted manual security testing, particularly for high-risk scenarios such as code integrity enforcement, sandbox boundaries, and handling of sensitive data.

&nbsp;

## &#51;. Source code management and change control

Source code is maintained in controlled repositories with role-based access restrictions.&nbsp; All code changes are traceable to authenticated contributors and are subject to peer review prior to integration.

&nbsp;

Branch protection controls, commit signing where applicable, and automated build validations are enforced to maintain code integrity.

&nbsp;

## &#52;. Application security testing

Security testing is embedded into the build and release pipeline.&nbsp; Static application security testing is performed to detect code-level weaknesses.&nbsp; Dynamic and interactive testing methods are employed where applicable to evaluate runtime behavior.

&nbsp;

Manual security assessments are conducted for high-risk components and prior to major releases.&nbsp; Identified findings are risk-rated, tracked, and remediated according to defined service levels.

&nbsp;

## &#53;. Dependency and supply-chain security

Third-party libraries and open-source components are inventoried, are pinned, and are continuously monitored for known vulnerabilities.&nbsp; Software composition analysis tools are used to identify outdated or vulnerable dependencies.

&nbsp;

Remediation actions include patching, upgrading, replacing components, or applying compensating controls.&nbsp; A Software Bill of Materials may be made available to customers upon request.

&nbsp;

## &#54;. Build and release security

Build processes are automated and executed in controlled environments.&nbsp; Access to build systems is restricted to authorized personnel and service accounts.

&nbsp;

Release artifacts are cryptographically signed to enable customers to verify authenticity and integrity.&nbsp; Hash verification mechanisms are provided where appropriate.

&nbsp;

## &#55;. Vulnerability management

Hackolade maintains a formal vulnerability management program governing intake, triage, remediation, and disclosure of security issues.

&nbsp;

## &#56;. Patch and update governance

Security patches are developed, tested, and distributed in accordance with release management procedures.&nbsp; Critical vulnerabilities may trigger out-of-band security advisories and expedited patch releases.

&nbsp;

## &#57;. Logging within the product

The software includes logging capabilities designed for troubleshooting purposes.&nbsp; Logged events may include authentication activity, configuration changes, administrative actions, and system errors.

&nbsp;

## &#49;0. Cryptography and data protection controls

Industry-recognized cryptographic libraries and protocols are used to protect data handled by the product.&nbsp; Deprecated algorithms and insecure protocols are not permitted in supported configurations.

&nbsp;

Key storage and lifecycle management are designed to align with customer-managed security controls where deployed.

&nbsp;

## &#49;1. Personnel security and training

Security awareness and secure development training are provided periodically to reinforce secure coding and data protection responsibilities.

&nbsp;

## &#49;2. Incident response

Hackolade maintains an incident response process governing detection, containment, eradication, and recovery from security incidents affecting the product or development environment.

&nbsp;

## &#49;3. Compliance and assurance

Where applicable, Hackolade aligns product security practices with recognized frameworks such as NIST Secure Software Development Framework, and OWASP Software Assurance guidance.

&nbsp;

&nbsp;

