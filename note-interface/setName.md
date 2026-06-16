# `note.setName`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Metadata

## Description
Sets a new name (title) for the note.

## Signature
`note.setName(newName)`

## Parameters
- `newName` (`String`) — the new title to assign to the note. Becomes the note's `name` (see [noteHandle](../appendices/types.md#notehandle)).

## Returns
`Promise<void>`

## Equivalent `app` method
—

## Example
```javascript
await note.setName("My renamed note");
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the `name` field this method updates.
- [Note Interface index](./index.md)

## Related
- [`note.name`](./name.md)
