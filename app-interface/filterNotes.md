# `app.filterNotes`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Filtering & Search

## Description
Find noteHandles for all notes matching a set of filter criteria. Tag filters support comma-separated values and negation with a `^` prefix.

## Signature
`app.filterNotes(filterParams?: object, sortOrder?: string) → Promise<noteHandle[]>`

## Parameters
- `filterParams` (`Object`, optional) — keys include `group` (`String`), `query` (`String`), `tag` (`String`, a [tag](../appendices/types.md#tag) filter; comma-separated for multiple, `^` prefix to negate), `taskDomainUUID` (`String`).
- `sortOrder` (`String`, optional) — one of `"changed"`, `"created"`, `"opened"`, `"relevance"`, `"title"`, `"updated"`.

## Returns
`Promise<Array<`[noteHandle](../appendices/types.md#notehandle)`>>` — array of matching noteHandles.

## Example
```javascript
async insertText(app) {
  const noteHandles = await app.filterNotes({ tag: "daily-jots" });
  return `note count: ${noteHandles.length}`;
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the returned array elements; each accepts a String uuid as shorthand.
- [tag](../appendices/types.md#tag) — tag text format used in the `tag` filter.
- [App Interface index](./index.md)

## Related
- [`app.searchNotes`](./searchNotes.md)
- [`app.findNote`](./findNote.md)
- [`app.notes` object](./notes-object.md)
