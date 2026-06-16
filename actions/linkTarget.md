# `linkTarget`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
A plugin's `linkTarget` action will be called when a plugin link (`plugin://<plugin UUID>`) is clicked/pressed. Any query string included in the plugin link URL is passed along as arguments.

## Signature
`async linkTarget(app, ...args)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `...args` (`String`, optional) — The query string from the plugin link URL.

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to make the link target unavailable. The check function receives the same `(app, ...args)` arguments as `run`.

## Example
```javascript
async linkTarget(app, ...args) {
  await app.alert("link " + JSON.stringify(args));
}
```

## Related
- [linkOption](./linkOption.md)
- [onNavigate](./onNavigate.md)
