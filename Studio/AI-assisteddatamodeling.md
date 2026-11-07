---
description: The Ultimate Edition of Hackolade Studio offers AI-assisted data modeling with your choice of LLM and your own API key, and nothing goes through Hackolade.
seoTitle: AI-assisted data modeling in Hackolade Studio
image: lib/AI-Assisted Data Modeling panel.png
---
# AI-assisted data modeling

> [!WARNING]
> Results may differ depending on many factors, including provider, model, version, effort, etc.  In particular, users should provide sufficient details and context in prompts.
>
> AI does make mistakes, and even the best AI requires a review by a good data modeler.  Input and feedback from subject matter experts are irreplaceable.

Most vendors these days claim to have integrated "AI features".  But not all integrations are equal...  We encourage evaluators to compare offerings side-by-side.

> [!IMPORTANT]
> Aside from the import of GenAI-created artifacts such as [DBML](GenAI-createdDBML.md) or [Mermaid](GenAI-createdMermaidERdiagram.md), integrated AI features are available only in the [Ultimate Edition](<https://hackolade.com/help/Editions.html#Edition>).

> [!NOTE]
> To serve different use cases, note that [an MCP server is shipped](MCPserver.md) with Model Hub.

## Philosophy

Our approach to AI integration is built on **customer control, confidentiality, and responsible use**. AI capabilities are disabled by default, and enabled only at the customer’s choice. Customers remain free to select the LLM, model, or provider that best meets their security, regulatory, and operational requirements, including self-hosted or on-premises models where appropriate.

This helps protect sensitive metadata, schemas, and data models from unintended exposure, third-party retention, or unauthorized use for model training.

We also believe human oversight must be meaningful: AI should support expert judgment, not replace it with superficial approval of algorithmic outputs under pressure.

## AI on your own terms

When comparing solutions, it is important to understand: where are your prompts, your data models, your schemas, and your metadata actually disclosed?

The solution architecture is a critical aspect in the sovereignty of your information to avoid data leakage.

### How the competition does AI

With well known legacy tools, the application (whether a client tool via a proprietary server, or the server of a SaaS solution) calls the vendor's own AI service, which relays the call to a single vendor-selected LLM. The vendor stores a log of user ids, prompts, and responses on its own servers.  Your models and metadata are shared, if not stored with the vendor, with all the risks that this may represent.

![How the competition does AI architecture](<lib/AI competitors architecture.png>)

### How Hackolade does AI

The Hackolade solution architecture supports your AI Governance.  By AI Governance, we primarily mean capabilities such as bring-your-own key (BYOK), support for local LLMs, model selection, usage policies, and analytics (consumption and ROI) for AI features in the product.

In all cases, **nothing goes through Hackolade infrastructure**.  Your environment calls the AI model directly, with your own credentials, under your own contract.

You may connect to local LLMs, AI gateways, or directly to the online provider of your choice.

![How Hackolade does AI architecture](<lib/AI Hackolade Architecture.png>)
