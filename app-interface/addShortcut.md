# `app.addShortcut`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Shortcuts

## Description
Adds a shortcut to one of the shortcut areas shown in the sidebar (the lists of saved filters/links shown under the Jots, Notes, Tasks, and Calendar areas).

## Signature
`app.addShortcut(area: string, shortcut: object) → Promise<boolean>`

## Parameters
- `area` (`String`) — one of `"calendar"`, `"jots"`, `"notes"`, or `"tasks"`
- `shortcut` (`Object`) — object with at least one of `group`, `query`, `references`, `remoteUUID`, `tag` (all `String`); optional `name` (`String`), `isDefault` (`Boolean`)

## Returns
`Promise<Boolean>` — resolves to `true` once the shortcut is added.

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  await app.addShortcut("notes", { name: "To-Do notes", tag: "todo" });
}
```

## Related
- [`app.getShortcuts`](./getShortcuts.md)
- [`app.removeShortcut`](./removeShortcut.md)
