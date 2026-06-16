# `app.getNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Get the content of a note, as markdown.

## Signature
`app.getNoteContent(noteHandle: object) → Promise<string>`

## Parameters
- `noteHandle` (`object`) — object identifying the note

## Returns
`Promise<string>` — the markdown content of the note.

## Example
```javascript
async noteOption(app, noteUUID) {
  const markdown = await app.getNoteContent({ uuid: noteUUID });
  app.alert(markdown);
}
```

## Related
- [`app.insertNoteContent`](./insertNoteContent.md)
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteSections`](./getNoteSections.md)
