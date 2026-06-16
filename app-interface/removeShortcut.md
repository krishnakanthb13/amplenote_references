# `app.removeShortcut`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Shortcuts

## Description
Removes a shortcut from one of the shortcut areas. The shortcut to remove is matched on its filter properties (`group`, `query`, `references`, `remoteUUID`, and `tag`).

## Signature
`app.removeShortcut(area: string, shortcut: object) → Promise<boolean>`

## Parameters
- `area` (`string`) — one of `"calendar"`, `"jots"`, `"notes"`, or `"tasks"`
- `shortcut` (`object`) — object containing the filter properties to match

## Returns
`Promise<boolean>` — resolves to `true` (removal is a no-op if not found).

## Example
```javascript
async appOption(app) {
  await app.removeShortcut("notes", { tag: "todo" });
}
```

## Related
- [`app.addShortcut`](./addShortcut.md)
- [`app.getShortcuts`](./getShortcuts.md)
