# `app.insertNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Inserts content into a note. Throws if content exceeds 100k characters or if the note is readonly.

## Signature
`app.insertNoteContent(noteHandle: object, content: string, options?: object) → Promise<void>`

## Parameters
- `noteHandle` (`object`) — object identifying the note
- `content` (`string`) — markdown-formatted content to insert
- `options` (`object`, optional) — keys include `atEnd` (boolean, defaults to `false`)

## Returns
`Promise<void>`

## Example
```javascript
noteOption(app, noteUUID) {
  app.insertNoteContent({ uuid: noteUUID }, "this is some **bold** text");
}
```

## Related
- [`app.replaceNoteContent`](./replaceNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
