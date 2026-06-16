# `app.getShortcuts`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Shortcuts

## Description
Lists the shortcuts in one of the shortcut areas, including any default shortcuts that are present without the user having customized the area.

## Signature
`app.getShortcuts(area: string) → Promise<Array>`

## Parameters
- `area` (`String`) — one of `"calendar"`, `"jots"`, `"notes"`, or `"tasks"`

## Returns
`Promise<Array<Object>>` — array of shortcut objects, each containing `group`, `query`, `references`, `remoteUUID`, `tag`, `name` (all `String`).

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const shortcuts = await app.getShortcuts("tasks");
  await app.alert(`There are ${shortcuts.length} task shortcuts`);
}
```

## Related
- [`app.addShortcut`](./addShortcut.md)
- [`app.removeShortcut`](./removeShortcut.md)
