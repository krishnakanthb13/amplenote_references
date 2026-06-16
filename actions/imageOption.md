# `imageOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds an option to the drop-down menu on each image in a note.

## Signature
`async imageOption(app, image)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `image` (`Object`) — Image object describing the selected image (e.g. its `src`).

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. The check function receives the same `(app, image)` arguments as `run`.

## Example
```javascript
async imageOption(app, image) {
  await app.alert("image: " + image.src);
}
```

## Related
- [noteOption](./noteOption.md)
- [linkOption](./linkOption.md)
