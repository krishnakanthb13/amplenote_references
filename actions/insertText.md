# `insertText`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Text Insertion / Replacement

## Description
Called to insert text at a specific location in a note (or note title), when using an `{expression}`. The string returned by the action is inserted in place of the expression.

## Signature
`insertText(app)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).

## Returns
`String` — the new text to insert in place of the expression.

## The `check` function
The `check` function can return a string to define a custom keyword that is used to invoke the action, instead of the plugin name. Return a falsy value to make the action unavailable.

## Example
```javascript
insertText(app) {
  return "hello world";
}
```

Custom keyword variant (use a `check`/`run` object to register a keyword other than the plugin name):

```javascript
insertText: {
  check(app) {
    return "keyword";
  },
  run(app) {
    return "hello world";
  }
}
```

## Related
- [replaceText](./replaceText.md)
