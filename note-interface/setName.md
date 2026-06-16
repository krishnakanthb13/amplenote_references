# `note.setName`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Metadata

## Description
Sets a new name (title) for the note.

## Signature
`note.setName(newName)`

## Parameters
- `newName` (`String`) — the new title to assign to the note.

## Returns
`Promise<void>`

## Equivalent `app` method
—

## Example
```javascript
await note.setName("My renamed note");
```

## Related
- [`note.name`](./name.md)
