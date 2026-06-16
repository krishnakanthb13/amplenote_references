# `replaceText`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Text Insertion / Replacement

## Description
Called to replace some highlighted text, invoked via the selection menu. The string returned replaces the currently selected text.

## Signature
`replaceText(app, text)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `text` (`String`) — The currently selected text.

## Returns
`String` — the replacement text, or `null` to cancel (leave the text unchanged).

## The `check` function
The `check` function can return a string to use as a custom menu label, instead of the plugin name. Return a falsy value to hide the option.

## Example
```javascript
replaceText(app, text) {
  return "new text";
}
```

Custom label variant (use a `check`/`run` object to set the menu label):

```javascript
replaceText: {
  check(app, text) {
    return "some text";
  },
  run(app, text) {
    return "new text";
  }
}
```

## Types & references
- `text` and the return value are plain `String`s (return `null` to cancel); takes no API object types.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its `check`/`run` form for a custom label.

## Related
- [insertText](./insertText.md)
