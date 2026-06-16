# Amplenote Plugin Examples

> [← API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/examples)

This section collects common, end-to-end patterns for building Amplenote plugins —
acting on tasks, parsing rich content, calling external services, and integrating LLMs.
Each example links to the relevant App Interface / Note Interface calls it uses.

## Starter Repositories

Several foundational repositories are available to bootstrap a plugin:

- **Plugin Embed Starter Project** — build a React-based application that can be rendered
  in a note, sidebar, or anywhere else.
- **Plugin Template** — a barebones plugin scaffold that includes testing capabilities.
- **AmpleAI & 100+ existing plugins** — reference implementations available for study.
  AmpleAI in particular demonstrates LLM integration across OpenAI, Gemini, and
  Anthropic.

## Examples Index

1. [Task action via slash command](./task-action-slash-command.md) — show a command in
   the context of a task using `appOption` + a `check` method, `app.context.taskUUID`,
   and `app.getTask()`.
2. [Parsing rich footnotes](./parsing-rich-footnotes.md) — how tasks containing images,
   links, and connected tasks are represented as markdown footnotes through the API.
3. [External services & fetch](./external-service-fetch.md) — using `fetch()`, working
   around CORS with a Cloudflare Worker proxy, and reporting progress with
   `app.openEmbed()`.
4. [LLM integration](./llm-integration.md) — calling OpenAI / Gemini / Anthropic with an
   API key from `app.settings`, request body and model, timeouts via `Promise.race()`,
   and error handling.

## Related references

- [Appendices](../appendices/index.md) — types, execution environment, markdown content,
  external libraries, and the CORS proxy.
- [Guides](../guides/index.md) — getting started and the markdown reference.
