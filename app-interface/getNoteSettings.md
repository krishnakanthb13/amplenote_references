# `app.getNoteSettings`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Metadata

## Description
Gets settings specific to a note that are not included in noteHandle metadata, generally related to note styling and secondary displays.

## Signature
`app.getNoteSettings(noteHandle: object) → Promise<object | null>`

## Parameters
- `noteHandle` (`object`) — object identifying the note

## Returns
`Promise<object | null>` — object with possible keys `backgroundColor`, `bannerImageURL`, `maxOpenTasks`, or `null`.

## Example
```javascript
async noteOption(app, noteUUID) {
  const settings = await app.getNoteSettings({ uuid: noteUUID });
  await app.alert("Settings: " + JSON.stringify(settings));
}
```

## Related
- [`app.setNoteSetting`](./setNoteSetting.md)
