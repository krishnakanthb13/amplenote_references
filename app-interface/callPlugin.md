# `app.callPlugin`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Plugin Communication

## Description
Make a call to another installed plugin's `onPluginCall` function.

## Signature
`app.callPlugin(targetPlugin: object, ...args) → Promise<any>`

## Parameters
- `targetPlugin` (`object`) — object with optional keys:
  - `source` (`string`) — public note token of a published plugin
  - `uuid` (`string`) — note UUID of a plugin in the user's account
- `...args` — additional arguments passed to the target plugin's `onPluginCall`

## Returns
`Promise<any>` — whatever the target plugin returns, or `undefined` if unhandled.

## Example
```javascript
async appOption(app) {
  const result = await app.callPlugin({ source: "HXRa7ADW88bnyfA7hDwbXSLY" }, 1, "test");
  await app.alert("Got result: " + JSON.stringify(result));
}
```

## Related
- [`app.openEmbed`](./openEmbed.md)
