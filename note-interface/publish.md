# `note.publish`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Publishing

## Description
Publish the note. See `app.publishNote` for more details. Returns the public URL of the published note.

## Signature
`note.publish()`

## Parameters
None.

## Returns
`Promise<String>` — the public URL of the published note.

## Equivalent `app` method
`app.publishNote(noteHandle)`

## Example
```javascript
const publicUrl = await note.publish();
app.alert(`Published at ${publicUrl}`);
```

## Related
- [`note.publicURL`](./publicURL.md)
