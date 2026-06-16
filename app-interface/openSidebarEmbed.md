# `app.openSidebarEmbed`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Embeds

## Description
Opens an embed for the plugin in the Peek Viewer, if it is available for the user. If the plugin has already opened a sidebar embed, the existing sidebar embed will be re-rendered.

## Signature
`app.openSidebarEmbed(aspectRatioOrOptions: number | object, ...args) → Promise<boolean>`

## Parameters
- `aspectRatioOrOptions` (`Number | Object`) — a `Number` (aspect ratio) OR an object with keys:
  - `aspectRatio` (`Number`)
  - `id` (`String`) — unique identifier for multiple embeds
- `...args` (any) — arguments passed to the plugin's `renderEmbed` action

## Returns
`Promise<Boolean>` — `true` if the embed opened, `false` in the mobile app.

## Types & references
- [Execution environment](../appendices/execution-environment.md) — how `renderEmbed` and embed code run
- [App Interface index](./index.md)

## Example
```javascript
appOption(app) {
  app.openSidebarEmbed(1, "one", [ 2, 3, 4 ]);
},

renderEmbed(app, ...args) {
  return `<b>got:</b> ${JSON.stringify(args)}`;
}
```

## Related
- [`app.openEmbed`](./openEmbed.md)
