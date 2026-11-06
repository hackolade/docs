# AI-assisted data modeling

> [!WARNING]
> Results may differ depending on many factors, including provider, model, version, effort, etc.  In particular, users should provide sufficient details and context in prompts.
>
> AI does make mistakes, and even the best AI requires a review by a good data modeler.  Input and feedback from subject matter experts are irreplaceable.

&nbsp;

Most vendors these days claim to have integrated "AI features".  But not all integrations are equal...  We encourage evaluators to compare offerings side-by-side.

&nbsp;

> [!IMPORTANT]
> AI features are available only in the [Ultimate Edition](<https://hackolade.com/help/Editions.html#Edition>).

&nbsp;

## Philosophy

Our approach to AI integration is built on **customer control, confidentiality, and responsible use**. AI capabilities are disabled by default, and enabled only at the customer’s choice. Customers remain free to select the LLM, model, or provider that best meets their security, regulatory, and operational requirements, including self-hosted or on-premises models where appropriate.

&nbsp;

This helps protect sensitive metadata, schemas, and data models from unintended exposure, third-party retention, or unauthorized use for model training.

&nbsp;

We also believe human oversight must be meaningful: AI should support expert judgment, not replace it with superficial approval of algorithmic outputs under pressure.

&nbsp;

## AI on your own terms

When comparing solutions, it is important to understand: where are your prompts, your data models, your schemas, and your metadata actually disclosed?

&nbsp;

The solution architecture is a critical aspect in the sovereignty of your information to avoid data leakage.

&nbsp;

### How the competition does AI

With well known legacy tools, the application (whether a client tool via a proprietary server, or the server of a SaaS solution) calls the vendor's own AI service, which relays the call to a single vendor-selected LLM. The vendor stores a log of user ids, prompts, and responses on its own servers.  Your models and metadata are shared, if not stored with the vendor, with all the risks that this may represent.

&nbsp;

![How the competition does AI architecture](<lib/AI competitors architecture.png>)

&nbsp;

### How Hackolade does AI

The Hackolade solution architecture supports your AI Governance.  By AI Governance, we primarily mean capabilities such as bring-your-own key (BYOK), support for local LLMs, model selection, usage policies, and analytics (consumption and ROI) for AI features in the product.

&nbsp;

In all cases, **nothing goes through Hackolade infrastructure**.  Your environment calls the AI model directly, with your own credentials, under your own contract.

&nbsp;

You may connect to local LLMs, AI gateways, or directly to the online provider of your choice.

&nbsp;

![How Hackolade does AI architecture](<lib/AI Hackolade Architecture.png>)
