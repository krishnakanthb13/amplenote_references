# `onPluginCall`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Plugin Communication

## Description
Called when a plugin calls `app.callPlugin` with an identifier that matches this plugin. This enables plugin-to-plugin communication, where one plugin can invoke another and receive a return value back.

## Signature
`onPluginCall(app, sourcePlugin, ...args)`

## Parameters
- `app` — App Interface object (a limited version). See [App Interface](../app-interface/index.md).
- `sourcePlugin` (`Object`) — An object with `uuid` (string) and `source` (string or null) keys, identifying the calling plugin.
- `...args` — The remaining arguments passed from `app.callPlugin`.

## Returns
Any serializable value, which is returned to the caller.

## The `check` function
The `check` function receives the `sourcePlugin` argument and can be used to validate the identity of the calling plugin before allowing the call to run. Return falsy to reject the call.

## Example
```javascript
onPluginCall: {
  check(app, sourcePlugin) {
    return sourcePlugin.source === "HXRa7ADW88bnyfA7hDwbXSLY";
  },
  run(app, sourcePlugin, ...args) {
    return "got args: " + JSON.stringify(args);
  }
}
```

## Related
- [onEmbedCall](./onEmbedCall.md)
