# `app.setNoteSetting`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Set the value of a note setting. The value will be synchronized to all of the user's devices. Allowed keys are `"backgroundColor"` (hex color string) or `"maxOpenTasks"` (integer).

## Signature
`app.setNoteSetting(noteHandle: object, key: string, value: any) → Promise<boolean>`

## Parameters
- `noteHandle` (`object`) — object identifying the note
- `key` (`string`) — the setting key (`"backgroundColor"` or `"maxOpenTasks"`)
- `value` (`any`) — the value to set

## Returns
`Promise<boolean>` — whether the setting was updated.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.setNoteSetting({ uuid: noteUUID }, "backgroundColor", "#ff0000");
}
```

## Related
- [`app.getNoteSettings`](./getNoteSettings.md)
