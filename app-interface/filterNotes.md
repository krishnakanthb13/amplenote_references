# `app.filterNotes`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Find noteHandles for all notes matching a set of filter criteria. Tag filters support comma-separated values and negation with a `^` prefix.

## Signature
`app.filterNotes(filterParams?: object, sortOrder?: string) → Promise<noteHandle[]>`

## Parameters
- `filterParams` (`object`, optional) — keys include `group`, `query`, `tag`, `taskDomainUUID`
- `sortOrder` (`string`, optional) — one of `"changed"`, `"created"`, `"opened"`, `"relevance"`, `"title"`, `"updated"`

## Returns
`Promise<noteHandle[]>` — array of matching noteHandles.

## Example
```javascript
async insertText(app) {
  const noteHandles = await app.filterNotes({ tag: "daily-jots" });
  return `note count: ${noteHandles.length}`;
}
```

## Related
- [`app.searchNotes`](./searchNotes.md)
- [`app.findNote`](./findNote.md)
- [`app.notes` object](./notes-object.md)
