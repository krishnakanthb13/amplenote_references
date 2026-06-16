# `app.openEmbed`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Embeds

## Description
Adds a section to the sidebar (or drawer menu on the mobile app), allowing the user to open a full screen embed.

## Signature
`app.openEmbed(...args) → Promise<void>`

## Parameters
- `...args` (any) — anything; passed to `renderEmbed` after the `app` argument

## Returns
`Promise<void>`

## Types & references
- [Execution environment](../appendices/execution-environment.md) — how `renderEmbed` and embed code run
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  await app.openEmbed();
  // Navigate with:
  await app.navigate("https://www.amplenote.com/notes/plugins/" + app.context.pluginUUID);
}
```

## Related
- [`app.openSidebarEmbed`](./openSidebarEmbed.md)
- [`app.navigate`](./navigate.md)
