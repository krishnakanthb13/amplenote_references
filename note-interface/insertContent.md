# `note.insertContent`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Content

## Description
Inserts content at the beginning of a note. If the note does not yet exist, calling this method will create it. See `app.insertNoteContent` for more details.

## Signature
`note.insertContent(markdown)`

## Parameters
- `markdown` (`String`) — the markdown content to insert at the beginning of the note.

## Returns
`Promise<void>`

## Equivalent `app` method
`app.insertNoteContent(noteHandle, content)`

## Example
```javascript
await note.insertContent("# Heading\n\nSome new content at the top.");
```

## Types & references
- Accepts a markdown `String`.
- [Note Interface index](./index.md)

## Related
- [`note.replaceContent`](./replaceContent.md)
- [`note.content`](./content.md)
- [`note.insertTask`](./insertTask.md)
