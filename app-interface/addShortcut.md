# `app.addShortcut`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Shortcuts

## Description
Adds a shortcut to one of the shortcut areas shown in the sidebar (the lists of saved filters/links shown under the Jots, Notes, Tasks, and Calendar areas).

## Signature
`app.addShortcut(area: string, shortcut: object) → Promise<boolean>`

## Parameters
- `area` (`string`) — one of `"calendar"`, `"jots"`, `"notes"`, or `"tasks"`
- `shortcut` (`object`) — object with at least one of `group`, `query`, `references`, `remoteUUID`, `tag` (all strings); optional `name` (string), `isDefault` (boolean)

## Returns
`Promise<boolean>` — resolves to `true` once the shortcut is added.

## Example
```javascript
async appOption(app) {
  await app.addShortcut("notes", { name: "To-Do notes", tag: "todo" });
}
```

## Related
- [`app.getShortcuts`](./getShortcuts.md)
- [`app.removeShortcut`](./removeShortcut.md)
