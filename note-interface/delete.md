# `note.delete`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Lifecycle

## Description
Delete the note.

## Signature
`note.delete()`

## Parameters
None.

## Returns
`Promise<void>`

## Equivalent `app` method
—

## Example
```javascript
await note.delete();
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note being deleted.
- [Note Interface index](./index.md)

## Related
- [`note.setName`](./setName.md)
- [`note.url`](./url.md)
