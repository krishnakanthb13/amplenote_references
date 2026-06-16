# `app.setNoteSetting`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Set the value of a note setting. The value will be synchronized to all of the user's devices. Allowed keys are `"backgroundColor"` (hex color string) or `"maxOpenTasks"` (integer).

## Signature
`app.setNoteSetting(noteHandle: object, key: string, value: any) → Promise<boolean>`

## Parameters
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — object identifying the note (accepts a String `uuid` shorthand).
- `key` (`String`) — the setting key (`"backgroundColor"` or `"maxOpenTasks"`).
- `value` (`String` | `Number`) — the value to set (a hex color String for `"backgroundColor"`, an integer Number for `"maxOpenTasks"`).

## Returns
`Promise<Boolean>` — whether the setting was updated.

## Example
```javascript
async noteOption(app, noteUUID) {
  await app.setNoteSetting({ uuid: noteUUID }, "backgroundColor", "#ff0000");
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — identifies the note; accepts a String uuid as shorthand.
- [App Interface index](./index.md)

## Related
- [`app.getNoteSettings`](./getNoteSettings.md)
