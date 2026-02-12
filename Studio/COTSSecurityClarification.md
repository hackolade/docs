# COTS Security Clarification

**Commercial Off-the-Shelf (COTS) deployment model clarification**

&nbsp;

Hackolade Studio is a client-installed COTS software. There is no server component.&nbsp; Hackolade Studio operates entirely within the customer’s environment. No customer data is transmitted to or processed by Hackolade. Hackolade does not operate a SaaS service, host infrastructure, or access customer production data.

&nbsp;

This page is provided to clarify the security, data handling, and operational model of the product in the context of third-party risk assessments.&nbsp; Many standard vendor security questionnaires are designed for Software-as-a-Service (SaaS) or managed service providers.&nbsp; This document explains the distinct risk posture and control boundaries applicable to client-installed commercial off-the-shelf software.

&nbsp;

## &#49;. Deployment and operating model

Hackolade Studio is a software product delivered as commercial off-the-shelf software installed and operated entirely within the customer’s environment.&nbsp; The software executes on infrastructure provisioned, configured, and controlled by the customer or their designated service providers.

&nbsp;

Hackolade does not provide a service.&nbsp; It does not operate hosting infrastructure on behalf of customers and does not provide a cloud service, managed service, or multi-tenant platform in relation to this product. All runtime processing occurs within the customer’s security boundary.

&nbsp;

![Client architecture diagram](<lib/Client architecture diagram.png>)

&nbsp;

* There is no server component operated by Hackolade or by the customer for Hackolade Studio
* All execution occurs locally on user endpoints
* Data models are stored locally or in customer-operated Git repository
* Hackolade provides digitally signed software updates. Customers may retrieve updates directly, mirror them internally, or deploy them through offline distribution workflows
* Hackolade validates product activation and feature entitlements. Exchanges are limited to licensing metadata such as license identifiers, activation tokens, and software version information
* Offline activation workflows are available for restricted environments
* No customer models, repository data, or business content are transmitted
* No telemetry is collected or transmitted to Hackolade

&nbsp;

## &#50;. Data processing and data flow

Customer data processed by Hackolade Studio remains within customer-controlled systems and storage repositories.&nbsp; Hackolade does not receive, transmit, store, or process customer production data as part of normal product operation.

&nbsp;

Where Hackolade Studio includes optional connectivity features, such as update checks or licensing validation, these communications are limited to system and entitlement metadata necessary for software maintenance and legal use verification.&nbsp; Such communications do not include customer business data unless explicitly configured and initiated by the customer.

&nbsp;

Customers retain full control over network egress policies and may restrict or disable outbound connectivity in accordance with their internal security requirements.

&nbsp;

## &#51;. Vendor access to customer environments

The vendor has no administrative, remote, or persistent access to customer deployments.&nbsp; The product does not include vendor backdoors, remote command channels, or undisclosed access mechanisms.

&nbsp;

## &#52;. Infrastructure and physical security

Because Hackolade Studio is not vendor-hosted, responsibility for infrastructure security, physical data center controls, environmental safeguards, and cloud platform protections resides with the customer or their infrastructure providers.

&nbsp;

Hackolade does not operate production environments processing customer data and therefore does not maintain data center certifications or cloud hosting attestations specific to this product’s runtime operation.

&nbsp;

## &#53;. Installer and code integrity

Strong integrity controls are in place across all supported platforms. &nbsp;

&nbsp;

On Windows, installers are digitally signed weekly using a DigiCert Extended Validation (EV) Code Signing certificate, which allows the operating system to verify the publisher’s identity and detect tampering.&nbsp; &nbsp;

&nbsp;

On MacOS, installers for both Intel and Apple Silicon architectures are notarized weekly by Apple, ensuring that Gatekeeper validates the integrity of the application bundle before execution. Any modification to notarized files results in the operating system refusing to launch the application. &nbsp;

&nbsp;

For Linux distributions, Hackolade Studio is delivered as a compressed archive accompanied by a weekly generated SHA-256 checksum. Integrity testing confirmed that altering the contents of the archive results in a checksum mismatch, allowing users to detect tampering prior to installation.&nbsp;

&nbsp;

## &#54;. Local file-system access and privilege management

Hackolade Studio operates entirely within standard user privileges and does not request or require system-level permissions during installation or runtime. When the application processes or evaluates user-provided or untrusted code, execution occurs within a sandboxed environment that is isolated from the underlying file system. This design prevents untrusted inputs from reading or writing arbitrary files or escalating privileges beyond the intended execution scope.

&nbsp;

## &#55;. Identity and Access Management

Authentication and authorization mechanisms to the data models is delegated to the storage layer.&nbsp; When accessed within Hackolade Studio, it integrates with or operates under customer-managed identity systems where configured.&nbsp; User provisioning, role assignment, credential governance, and access reviews are performed by the customer as part of their internal security administration.

&nbsp;

## &#56;. Sensitive data handling, encryption and cryptographic controls

Sensitive information persisted to disk is encrypted using industry-standard cryptographic mechanisms, and access to encrypted data is restricted to application components that require it for legitimate functionality.

&nbsp;

## &#57;. Logging and monitoring

Hackolade does not receive operational logs unless customers elect to share them for troubleshooting purposes.

&nbsp;

Where logging capabilities exist, they are limited to software operational metadata necessary to maintain product quality, security, and compatibility. This metadata may include product version information, module activation status, performance metrics, error events, and environment characteristics such as operating system type or hardware profile.

&nbsp;

Logging is designed and governed according to data minimization principles. Collection is purpose-limited to software improvement, defect resolution.

&nbsp;

## &#49;0. Telemetry, usage data, and product analytics

Hackolade Studio does not transmit customer business data, customer content, or customer records to the vendor as part of telemetry or product analytics functions.

&nbsp;

## &#49;1. Licensing communications and entitlement validation

Hackolade Studio includes licensing mechanisms to verify lawful use and enforce contractual entitlements.&nbsp; Licensing may be implemented through offline license files, or online entitlement validation depending on customer preference and deployment constraints.

&nbsp;

In online validation modes, the product communicates with a 3rd party-operated licensing services to confirm license status, expiration dates, and feature entitlements.&nbsp; These communications do not include customer business data or processed content.

&nbsp;

Licensing exchanges are limited to product identifiers, license keys, software version, and activation timestamps.&nbsp; System identifiers are used solely to bind licenses to authorized installations and prevent unauthorized duplication.

&nbsp;

Customers operating in air-gapped or high-security environments may use offline activation workflows.&nbsp; These workflows rely on manual exchange of license challenge and response files and do not require persistent connectivity.

&nbsp;

Licensing services do not provide the vendor with remote access to customer systems, do not enable command execution, and do not create inbound connectivity paths into customer networks.

&nbsp;

## &#49;2. Customer control and network governance

All licensing endpoints are documented and may be allow-listed by customers.&nbsp; Customers retain full authority to block, proxy, inspect, or monitor outbound communications generated by the product.

&nbsp;

All network interactions are transparent, documented, and customer-governed.

&nbsp;

## &#49;3. Software updates management

Hackolade Studio updates are delivered as signed software packages. Customers control when and whether updates are applied.&nbsp; Update distribution is entirely customer-managed.

&nbsp;

## &#49;4. Vulnerability management and disclosure

Hackolade maintains a coordinated vulnerability disclosure process and investigates reported security issues in accordance with internal severity classification and remediation timelines.&nbsp; Security advisories and patches are issued to customers when vulnerabilities are confirmed and remediated.

&nbsp;

## &#49;5. Subprocessors and third parties

As Hackolade does not process customer production data in operating the product, subprocessors are not engaged for customer data handling.&nbsp; Third-party components embedded within the software are governed through Hackolade's software supply chain security and dependency management processes.

&nbsp;

## &#49;6. Shared responsibility summary

In this deployment model, security responsibilities are distributed as follows:

* the customer is responsible for infrastructure security, system hardening, access control operations, network protections, and data governance within their environment.
* Hackolade is responsible for secure software design, development, testing, maintenance, and vulnerability remediation of the product codebase.

&nbsp;

