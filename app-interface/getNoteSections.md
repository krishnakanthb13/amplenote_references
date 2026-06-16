# `app.getNoteSections`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Gets a list of the sections in a note. Sections are areas of the note delimited by either a heading or a horizontal rule.

## Signature
`app.getNoteSections(noteHandle: object) → Promise<section[]>`

## Parameters
- `noteHandle` (`object`) — object identifying the note

## Returns
`Promise<section[]>` — an array of section objects.

## Example
```javascript
async noteOption(app, noteUUID) {
  const sections = await app.getNoteSections({ uuid: noteUUID });
  await app.alert("Section count: " + sections.length);
}
```

## Related
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
