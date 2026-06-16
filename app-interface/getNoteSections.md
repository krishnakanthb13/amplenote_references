# `app.getNoteSections`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Gets a list of the sections in a note. Sections are areas of the note delimited by either a heading or a horizontal rule.

## Signature
`app.getNoteSections(noteHandle: object) → Promise<section[]>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).

## Returns
`Promise<Array<`[section](../appendices/types.md#section)`>>` — an array of section objects. Each has an `index` and a `heading` object (`anchor`, `href`, `level` 1–3, `text`) or `null` for the leading section before any heading.

## Example
```javascript
async noteOption(app, noteUUID) {
  const sections = await app.getNoteSections({ uuid: noteUUID });
  await app.alert("Section count: " + sections.length);
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [section](../appendices/types.md#section) — the returned array elements (`heading` {`anchor`, `href`, `level`, `text`} | `null`, `index`); pass one as `options.section` to [`app.replaceNoteContent`](./replaceNoteContent.md).
- [App Interface index](./index.md)

## Related
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
