# Amplenote Plugin Development — Overview

> [← API Reference Index](./00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins)

Amplenote provides support for client-side plugins that execute in the application on
all platforms, allowing for enhancement of the default client behavior. A plugin is a
single note in a user's account: the client reads that note and the plugin updates
dynamically as the note changes. Because plugins run client-side, they can react to the
user's notes and tasks, call out to external services, and render their own UI inside
the app.

## The Five Reference Areas

Plugin development is organized into five core reference areas:

- **Plugin creation** — the structure requirements for a valid plugin (the metadata
  table plus the first code block).
- **Actions** — the available hooks a plugin can implement (for example `insertText`,
  `appOption`, `noteOption`, `replaceText`, and others). Each action name corresponds to
  a function the plugin object exposes.
- **App Interface** — the primary way a plugin interacts with Amplenote, through
  `app.*` function calls that read and write note and task data.
- **Note interface** — an abstraction over the App Interface scoped to operations on a
  single note.
- **Examples** — common task implementations and end-to-end patterns.

## Supporting Reference Materials (Appendices)

These appendices provide the lower-level technical details:

- **[Types](./appendices/types.md)** — the type definitions used throughout the API.
- **[Plugin code execution environment](./appendices/execution-environment.md)** —
  specifications for the sandbox/environment in which plugin code runs.
- **[Markdown content handling](./appendices/markdown-content.md)** — how Amplenote
  represents and processes markdown content exchanged with plugins.
- **[External library loading](./appendices/external-libraries.md)** — procedures for
  loading third-party libraries from within a plugin.
- **[CORS proxy](./appendices/cors-proxy.md)** — setting up a proxy so plugins can reach
  external APIs that do not return permissive CORS headers.

### Guides

- **[Getting started](./guides/getting-started.md)** — a guide to writing your first
  plugin.
- **[Markdown reference](./guides/markdown-reference.md)** — the markdown formatting
  conventions used by Amplenote.

## Categories of Actions

Actions are the hooks that let a plugin extend the client. Broadly, they cover:

- **Insertion and replacement actions** — generate or transform text in a note (for
  example `insertText` and `replaceText`).
- **Option/command actions** — surface commands the user can invoke, such as global
  app options (`appOption`), note options (`noteOption`), and task/slash-command
  actions that appear contextually.
- **Lifecycle / event actions** — handlers that run in response to client events.

Each action can be implemented as a single function, as a set of multiple named
sub-actions, or in the advanced `check`/`run` form (see
[Plugin Creation](./01-plugin-creation.md)).

## Key Capabilities

Across the 2024–2025 updates, plugins can:

- Create, read, and manage **tasks**.
- Work with **note attachments** and images.
- Render **embeds** (custom UI in a note, sidebar, or elsewhere).
- Perform **clipboard** operations.
- Retrieve **backlinks** for a note.
- **Evaluate expressions** and otherwise compute over note content.
- Call **external services** over the network (subject to CORS — see
  [External Services & fetch](./examples/external-service-fetch.md)).
- Integrate with **LLMs** such as OpenAI, Gemini, and Anthropic.

## Getting Started

New plugin authors should start with the "Guide to getting started writing plugins" and
the markdown formatting guide, then explore the starter repositories and existing
plugins listed in the [Examples](./examples/index.md).

## Community Resources

- **Discord:** the `#plugin-atelier` channel on the
  [official Amplenote Discord server](https://discord.gg/nAj4wp4sJm).
- **Email:** `support@amplenote.com` (send from the email associated with your account).

## Reference Map
- [Plugin Creation](./01-plugin-creation.md)
- [Actions](./actions/index.md)
- [App Interface](./app-interface/index.md)
- [Note Interface](./note-interface/index.md)
- [Examples](./examples/index.md)
- Appendices: [Types](./appendices/types.md) ·
  [Execution environment](./appendices/execution-environment.md) ·
  [Markdown content](./appendices/markdown-content.md) ·
  [External libraries](./appendices/external-libraries.md) ·
  [CORS proxy](./appendices/cors-proxy.md)
- Guides: [Getting started](./guides/getting-started.md) ·
  [Markdown reference](./guides/markdown-reference.md)
