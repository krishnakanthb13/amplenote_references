# `linkOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds a button to the Rich Footnote popup, shown when the cursor is in a specific link.

## Signature
`linkOption(app, link)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `link` (`Object`) — Link object describing the link (e.g. its `description`).

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. The check function receives the same `(app, link)` arguments as `run`.

## Example
```javascript
linkOption(app, link) {
  const newDescription = (link.description || "") + "\n\nmore";
  app.context.updateLink({ description: newDescription });
}
```

## Related
- [linkTarget](./linkTarget.md)
- [imageOption](./imageOption.md)
