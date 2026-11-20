---
description: The Ultimate Edition of Hackolade Studio offers AI-assisted data modeling with your choice of LLM and your own API key, and nothing goes through Hackolade.
seoTitle: AI-assisted data modeling in Hackolade Studio
image: lib/AI-Assisted Data Modeling panel.png
---
# AI-assisted data modeling

> [!NOTE]
> AI-Assisted Data modeling features are available only in the Ultimate and in the 14-day free trial editions. They currently work in only the desktop application, and with Polyglot models

> [!WARNING]
> Results may differ depending on many factors, including provider, model, version, effort, etc.  In particular, users wanting more realistic results should provide sufficient details and context in their prompts.
>
> AI does make mistakes, and even the best AI requires a review by a good data modeler.  Input and feedback from and reviews by subject matter experts are irreplaceable.

Most vendors these days claim to have integrated "AI features".  But not all integrations are equal...  We encourage evaluators to compare offerings side-by-side.

> [!IMPORTANT]
> Aside from the import of GenAI-created artifacts such as [xDBML](Gen-AIcreatedxDBML.md), [DBML](GenAI-createdDBML.md) or [Mermaid](GenAI-createdMermaidERdiagram.md), which are available in Pro and Workgroup editions, integrated AI features are available only in the [Ultimate Edition](<https://hackolade.com/help/Editions.html#Edition>).

> [!NOTE]
> To serve different use cases, [an MCP server is shipped](MCPserver.md) with Model Hub.

## Philosophy

Our approach to AI integration is built on **customer control, confidentiality, and responsible use**. AI capabilities remain inactive until you configure a connection to the AI provider of your choice, with your own credentials. The AI features must be specifically invoked. Customers remain free to select the LLM, model, or provider that best meets their security, regulatory, and operational requirements, including self-hosted or on-premises models where appropriate.

This approach helps protect your sensitive metadata, schemas, and data models from unintended exposure, third-party retention, or unauthorized use for model training.

We also believe that human oversight must be meaningful: AI should support expert judgment, not replace it with superficial approval of algorithmic outputs under pressure.

## AI on your own terms

When comparing solutions, it is important to understand: where are your prompts, your data models, your schemas, and your metadata actually disclosed?

The solution architecture is a critical aspect in the sovereignty of your information to avoid data leakage.

### The competition records all your AI prompts and responses

With well known legacy tools, the application (whether a client tool via a proprietary server, or the server of a SaaS solution) calls the vendor's own AI service, which relays the call to a single vendor-selected LLM. The vendor stores a log of user ids, prompts, and responses on its own servers.  Your models and metadata are shared, if not stored with the vendor, with all the risks that this may represent.

![How the competition does AI architecture](<lib/AI competitors architecture.png>)

### Hackolade let's you use AI on your own terms

The Hackolade solution architecture supports your AI Governance.  By AI Governance, we primarily mean capabilities such as bring-your-own key (BYOK), support for local LLMs, model selection, usage policies, and analytics (consumption and ROI) for AI features in the product.

In all cases, **nothing goes through Hackolade infrastructure**.  Your environment calls the AI model directly, with your own credentials, under your own contract.

![AI-Assisted Data Modeling on your own terms](<lib/AI Hackolade Architecture.png>)

You may connect to local LLMs, AI gateways, or directly to the online provider of your choice.

## Getting started

1. [Configure a connection](ManageAIconnections.md) to your AI provider, with your own API key.
2. Open a Polyglot model, or create a new one.
3. Ask your questions and give your instructions in the [AI chat panel](AIchatpanel.md), or right-click a model object and choose [Assist me](<https://hackolade.com/help/AIchatpanel.html#Use%20Assist%20me%20on%20a%20model%20object>) to work on that object only.

Every change made through the AI chat panel can be reviewed in the ERD and the Properties pane, and [undone](<https://hackolade.com/help/AIchatpanel.html#Undo%20AI%20changes>) like any other change.
