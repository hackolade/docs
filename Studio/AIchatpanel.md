---
description: In the Ultimate Edition of Hackolade Studio, use the AI chat panel to create, modify and enrich data models in natural language, and review changes in the ERD.
seoTitle: AI chat panel for data modeling in Hackolade Studio
image: lib/AI-Assisted Data Modeling panel.png
---
# AI chat panel

> [!IMPORTANT]
> AI features are available only in the [Ultimate](<https://hackolade.com/help/Editions.html#Edition>) and in the 14-day free trial editions. They currently work in only the desktop application, and with Polyglot models.

The AI Assistant is a movable and adjustable side panel in Hackolade Studio where you ask an AI model about your data model. You may also direct it to create a new model and modify an existing one.

> [!NOTE]
> Our [AI integration philosophy](<https://hackolade.com/help/AI-assisteddatamodeling.html#How%20Hackolade%20does%20AI>) is such that Hackolade does not get any of your data model, prompts and responses.

Go to the menu option `AI > AI-Assisted Data Modeling Panel` or click the sparkling icon in the toolbar.

![AI-Assisted Data Modeling panel](<lib/AI-Assisted Data Modeling panel.png>)

The **AI-Assisted Data Modeling** panel lets you interact with AI models directly within Hackolade Studio to create, modify, and enrich data models using natural language. Through a conversational interface, you can describe modeling requirements, request changes to existing structures, and ask questions about your data model.

AI-generated modeling changes are applied directly to the model and reflected in the Entity Relationship Diagram (ERD), allowing you to review and refine the results interactively.

## What are the prerequisites?

Before using AI-Assisted Data Modeling, you must [configure at least one AI provider connection](ManageAIconnections.md) in Hackolade Studio.

Open **Manage AI Connections** from the AI menu, or from the model selector in the AI-Assisted Data Modeling panel. Select your preferred provider and enter the corresponding API key. You can optionally specify a custom Base URL to connect through an enterprise gateway or to a compatible self-hosted model endpoint.

An active API subscription or appropriate API access is required for the selected provider. This is generally separate from consumer AI chat subscriptions.

You must also have a data model open in Hackolade Studio. You can start with an empty model and ask the AI to generate its structure, or work with an existing model to modify and enrich it.

## Open and position the panel

To open the AI-Assisted Data Modeling panel, select **AI > AI-Assisted Data Modeling Panel** from the main menu, or click the **sparkling icon** <img src="lib/AI sparkling icon.png" alt="AI sparkling icon" width="18"> towards the right side of the toolbar.

The panel opens as a side pane on the left of the window, at full height. It can be moved and resized to suit your workspace. It can be displayed alongside the ERD, or expanded to provide more space for longer conversations: use the **Expand to full screen** and **Collapse to side pane** icons in the header of the panel. This flexibility allows you to alternate between conversational instructions and visual inspection of the model.

## Select an AI model

At the bottom of the panel, click the **model selector** to display the available AI models. The list is populated from the providers configured in the **Manage AI Connections** dialog.

<img src="lib/AI model selector.png" alt="AI model selector" width="265">

You can search for a specific model by name and select the one you prefer. Different models may offer different capabilities, response speeds, reasoning abilities, and pricing.

Only the AI models of the configured providers are listed. For each provider, one model is marked **Recommended**, and older models announced for retirement by their provider are marked **Deprecated**. If the selected model is no longer available, Hackolade Studio switches to another available model and tells you in the conversation.

The model selector also provides access to **Manage AI connections...**, where you can add, edit, or remove [provider configurations](ManageAIconnections.md), including API keys and custom endpoints.

You can switch between available models as needed during your modeling activities.

## Configure model parameters

Depending on the selected model, additional parameters may be available to control its behavior.

Click the **Intelligence & speed** indicator next to the model selector to inspect and adjust the available settings.

<img src="lib/AI model intelligence and speed dialog.png" alt="AI model intelligence and speed dialog" width="264">

**Effort:** Controls how much reasoning the model applies to a request. Higher effort levels may be appropriate for complex modeling tasks, while lower levels generally favor faster responses. The available levels depend on the selected model, and some models do not support this parameter.

**Fast mode:** When supported by the provider and model, enables faster responses, potentially at a higher cost.

**Cost:** Provides an indication of the relative cost of using the selected model and displays its token pricing. The cost indicator helps compare models and understand how changes in reasoning effort or fast mode may affect API consumption.

Not all models support the same options. Unsupported settings are indicated accordingly. Click **Reset** to restore the default settings.

## Interact with the data model

Enter your instructions or questions in the text box at the bottom of the panel and submit them to the selected AI model.

<img src="lib/AI panel prompt text box.png" alt="AI panel prompt text box" width="330">

You can use natural language to describe the desired data structures, request modifications, or progressively refine an existing model.

For example, you might ask the AI to:

- Create a data model for a car maintenance company;
- Rename an entity from Customer to Client;
- Update attribute names to reflect the renamed entity;
- Add descriptions to all entities and attributes;
- Create or modify relationships between entities.

The AI interprets your instructions in the context of the current data model and provides textual explanations of the changes it performs, making it easier to understand and verify the results.

The conversation maintains context across successive requests, so you can progressively refine the model without repeating the entire specification. For example, after renaming an entity, you can simply ask the AI to adapt the corresponding attribute names.

## Mention a specific model object in your prompt

To easily reference a specific object of your model in your prompt, type `@` in the text box and keep typing to filter the dynamic list, then select the object.  After a mention, type `.` to drill down into the children of the object, for example from an entity to one of its attributes.

<img src="lib/AI mention narrowing list.png" alt="AI mention narrowing list" width="355">

The mentioned object appears as a tag in your prompt, so that the AI knows exactly which container, entity, view or attribute you mean, even when several objects have similar names.

<img src="lib/AI mention object list.png" alt="AI mention object list" width="360">

Use the **@mention display** toggle to show mentions with their name only, or with their full path in the model.

<img src="lib/AI mention specific object.png" alt="AI mention specific object" width="252">

## Stop a response

While the AI works on your request, the **Send** button becomes a **Stop** button. Click it to interrupt the response, for example when you realize your instructions were incomplete. Changes already applied to the model before you clicked **Stop** remain, and can be [undone](<https://hackolade.com/help/AIchatpanel.html#Undo%20AI%20changes>).

## How are changes applied to the model?

Unlike conventional AI chat interfaces that merely generate text or code, the AI-Assisted Data Modeling panel is integrated directly with Hackolade Studio's data modeling capabilities.

When you request a modeling change, the AI interprets your instructions and interacts with Hackolade Studio to perform the corresponding operations on the active data model. These may include creating entities, adding or modifying attributes, defining relationships, renaming objects, or updating descriptions.

**Changes are applied directly to the data model**, without requiring you to manually transcribe the AI's response, copy generated code, or recreate the structures yourself. The ERD and Properties pane reflect the resulting modifications, allowing you to inspect them immediately.

The AI can also perform multiple related operations within a single request. For example, you can ask in one prompt to rename an entity and update its associated attribute names, while preserving the relevant relationships.

You can then continue refining the model through additional prompts or make manual adjustments using Hackolade Studio's standard modeling interface. AI-assisted and manual data modeling are complementary and operate on the same model.

The AI chat panel currently works only on Polyglot models, and supports the same objects as the xDBML reverse-engineering: containers, entities, attributes, primary and unique keys, relationships and views. It cannot create or modify an index, an enumeration or a model definition yet, for example. When you ask for a change it cannot perform, the AI tells you so in its response.

The resulting changes become part of the current data model and can be saved through Hackolade Studio's normal model-saving workflow, subject to the Auto save setting.

## Undo AI changes

All the changes performed by the AI in response to one prompt are recorded as a single step in the undo history. To revert them, click **Edit > Undo**, or press Ctrl+Z (Cmd+Z on macOS) while the focus is on the model, outside the text box of the panel. Use **Edit > Redo** to apply them again.

This lets you try an instruction, inspect the result in the ERD, and go back if it does not suit you.

## Navigate between responses and model objects

When an AI response references an object of the data model, such as a container, an entity or an attribute, its name appears as a **clickable link**.

![AI response clickable link](<lib/AI response clickable link.png>)

Click the name to navigate directly to the corresponding object in Hackolade Studio. This makes it convenient to inspect an object mentioned in a response, review its properties, or verify modifications performed by the AI.

This integration between the conversation and the model provides a direct connection between textual explanations and the graphical representation of the data structures.

## Copy responses

AI responses include a **Copy** icon that lets you copy the response text to the clipboard.

This is useful for sharing modeling explanations, documenting design decisions, or reusing generated descriptions in other applications.

## Monitor conversation length and token consumption

As a conversation progresses, the AI accumulates context from previous interactions. AI models have a limited context window, measured in tokens, which determines how much information they can process at once.

Click the **Conversation length** indicator near the model selector to inspect context usage.

<img src="lib/AI conversation length and token consumption.png" alt="AI conversation length and token consumption" width="220">

The indicator shows how much of the selected model's context window is currently occupied, expressed as a percentage and a token count.

The indicator also tells whether the conversation is short, long or very long, with advice on what to do. Token usage is particularly relevant when working with large data models or lengthy sequences of interactions: answers can become less precise, and each new message costs more, since the whole context is sent to the AI model again.

## Compact a conversation

As the conversation grows, it may approach the context window limit of the selected AI model.

To continue working without losing the essential context, Hackolade Studio **compacts the conversation** automatically before the limit is reached, so you are never blocked. Compaction summarizes the previous exchanges, retaining the most relevant information while reducing the number of tokens required to represent the conversation history.

You may also compact the conversation yourself, for example when a topic is done: click the **Conversation length** indicator, then **Compact conversation**.

The **Compact at** setting, in the same popup, defines the conversation length at which the automatic compaction occurs. By default, it is half of the context window of the selected model. With a higher value, the conversation is compacted later.

This makes it possible to continue a long data modeling session while limiting context-window usage and associated token consumption.

Because compaction summarizes previous interactions, some details from earlier exchanges may no longer be retained in full.

## Start a new chat

Click **+ New chat** at the top of the panel to start a fresh conversation.

A new chat resets the conversational context, allowing you to begin a separate modeling discussion without carrying over the previous exchange history.

This can be useful when switching to a different data modeling task, exploring a new approach, or starting over with a clean conversation.

Starting a new chat does not imply resetting the current data model. The model remains available for subsequent AI interactions.

## Use Assist me on a model object

You can also work with the AI on one model object at a time, without typing a prompt from scratch. Right-click a container, an entity, a view or an attribute, then choose **Assist me**:

- **Ask anything** opens the AI chat panel with the object already mentioned in the text box, ready for your question;
- **Write description** asks the AI to write the description of the object.

<img src="lib/AI Assist me contextual menu.png" alt="AI Assist me contextual menu" width="354">

The same command is available in the Properties pane: click **Generate with AI** next to the description of the object.

For a description, the AI does not change the model directly. The panel shows the current description and the proposed one. You may edit the proposal, then click **Apply** to write it to the model. Click **Show prompt** to see the instructions that Hackolade Studio sent to the AI model.

**Assist me** works on one object at a time: it is not shown when several objects are selected.

## Review AI-generated changes

AI-assisted modeling can significantly accelerate the creation and evolution of data models, but AI-generated results should always be reviewed by a qualified data modeler.

Although the AI can interpret requirements, create structures, and modify model objects, it may make assumptions or produce results that do not fully reflect the intended business semantics, modeling conventions, or technical constraints.

The integration with Hackolade Studio allows you to inspect the generated structures directly in the ERD and Properties pane, make manual adjustments when necessary, and continue refining the model through conversational instructions.

**Even the best AI requires a review by a good data modeler.**
