# `note.replaceContent`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Content

## Description
Replaces the content of the entire note, or a section of the note, with new content. See `app.replaceNoteContent` for more details.

## Signature
`note.replaceContent(markdown, sectionIndex?)`

## Parameters
- `markdown` (`String`) — the new markdown content.
- `sectionIndex` (`Number`, optional) — when provided, replaces only the content of the specified section instead of the entire note.

## Returns
`Promise<void>`

## Equivalent `app` method
`app.replaceNoteContent(noteHandle, content, options?)`

## Example
```javascript
// Replace the whole note
await note.replaceContent("All new content for the note.");
```

## Related
- [`note.insertContent`](./insertContent.md)
- [`note.content`](./content.md)
- [`note.sections`](./sections.md)
