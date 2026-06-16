# `note.backlinks`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Backlinks

## Description
Gets the list of notes that link to the note. Returns an async iterator that yields the note handles of each referencing note.

## Signature
`note.backlinks()`

## Parameters
None.

## Returns
Async iterator of note handles — each yielded value is the handle of a note that links to this note. Iterate with `for await ... of`.

## Equivalent `app` method
—

## Example
```javascript
let count = 0;
for await (const referencingNoteHandle of note.backlinks()) {
  count++;
}
app.alert(`This note has ${count} backlinks.`);
```

## Related
- [`note.backlinkContents`](./backlinkContents.md)
