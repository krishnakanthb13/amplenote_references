# `app.htmlFromContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Utilities

## Description
Converts markdown-formatted content to an HTML string, rendered with the same markup the Amplenote editor uses to display note content. Throws if content is not a string.

## Signature
`app.htmlFromContent(content: string) → Promise<string>`

## Parameters
- `content` (`String`) — [markdown](../guides/markdown-reference.md)-formatted content to convert

## Returns
`Promise<String>` — a `String` of HTML rendering the given content, wrapped in a readonly `ample-editor` container element.

## Types & references
- [Markdown reference](../guides/markdown-reference.md) — formatting accepted in `content`
- [Markdown content appendix](../appendices/markdown-content.md) — how note content is represented as markdown
- [App Interface index](./index.md)

## Example
```javascript
async noteOption(app, noteUUID) {
  const content = await app.getNoteContent({ uuid: noteUUID });
  const html = await app.htmlFromContent(content);
}
```

## Related
- [`app.getNoteContent`](./getNoteContent.md)
- [`app.evaluateExpression`](./evaluateExpression.md)
