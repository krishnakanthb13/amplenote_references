# `app.searchNotes`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Search note content. This matches the in-app "full search" functionality.

## Signature
`app.searchNotes(query: string) → Promise<noteHandle[]>`

## Parameters
- `query` (`string`) — term to search for in note content

## Returns
`Promise<noteHandle[]>` — array of matching noteHandles ordered by relevance.

## Example
```javascript
async insertText(app) {
  const noteHandles = await app.searchNotes("something");
  return `note count: ${noteHandles.length}`;
}
```

## Related
- [`app.filterNotes`](./filterNotes.md)
- [`app.findNote`](./findNote.md)
