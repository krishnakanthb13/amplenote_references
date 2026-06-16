# Parsing Rich Footnotes

> Part of [Examples](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/examples)

When a task (or other note content) contains rich elements — images, links, or connected
tasks — the API represents that content as markdown using **footnote** syntax. The inline
text carries a footnote reference (`[^1]`, `[^2]`, …), and the corresponding footnote
definition further down holds the rich payload (description, image, linked content).

Example of how such content is represented:

```
[description and image][^1], [website link](amplenote.com), [text footnote][^2]

[^1]: [description and image]()
With description and picture
![](image-url)

[^2]: [text-only footnote]()
Only text?
```

Reading this:

- A plain link such as `[website link](amplenote.com)` appears inline as ordinary
  markdown.
- Richer elements are referenced inline by a footnote marker (`[^1]`) and defined below,
  where the footnote body can include a description, an image (`![](image-url)`), or
  other connected content.

Because the footnote structure can be arbitrarily rich, the recommended approach is:
most often, you'll want an LLM to parse this text (see
[LLM integration](./llm-integration.md)) rather than hand-rolling a parser.

## Types & references

- [Markdown content handling](../appendices/markdown-content.md) — how Amplenote
  represents note content (including footnote-encoded rich elements) as markdown.
- [Markdown reference](../guides/markdown-reference.md) — the markdown formatting
  conventions, including links, images, and footnotes.
- The [link](../appendices/types.md#link) type — the structure of links inline in note
  content.
- The [task](../appendices/types.md#task) type — the structure of connected tasks that
  can appear within footnote payloads.
