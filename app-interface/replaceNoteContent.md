# `app.replaceNoteContent`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

## Description
Replace the entire content of a note with new content, or replace the content of a single section of the note.

## Signature
`app.replaceNoteContent(noteHandle: object, content: string, options?: object) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — object identifying the note
- `content` (`string`) — markdown content
- `options` (`object`, optional) — keys include `section`, `includeCompletedTasks`, `includeHiddenTasks`

## Returns
`Promise<boolean>` — whether the replacement was performed.

## Example
```javascript
async noteOption(app, noteUUID) {
  const newContent = "**new content**";
  await app.replaceNoteContent({ uuid: noteUUID }, newContent);
}
```

## Related
- [`app.insertNoteContent`](./insertNoteContent.md)
- [`app.getNoteContent`](./getNoteContent.md)
- [`app.getNoteSections`](./getNoteSections.md)
