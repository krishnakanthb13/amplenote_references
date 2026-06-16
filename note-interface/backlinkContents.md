# `note.backlinkContents`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Backlinks

## Description
Get the content of backlinks from a specific source note to the note. Returns the content fragments in the source note that reference this note.

## Signature
`note.backlinkContents(sourceNoteHandle)`

## Parameters
- `sourceNoteHandle` ([noteHandle](../appendices/types.md#notehandle)) — the origin note reference whose backlinking content should be retrieved. A bare `uuid` String is accepted as shorthand.

## Returns
`Promise<Array<String>>` — an array of markdown content fragments from the source note that reference this note.

## Equivalent `app` method
—

## Example
```javascript
for await (const sourceHandle of note.backlinks()) {
  const fragments = await note.backlinkContents(sourceHandle);
  app.alert(fragments.join("\n"));
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the type of the `sourceNoteHandle` argument (accepts a `uuid` String shorthand).
- [Note Interface index](./index.md)

## Related
- [`note.backlinks`](./backlinks.md)
