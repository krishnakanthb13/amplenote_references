# `linkOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds a button to the Rich Footnote popup, shown when the cursor is in a specific link.

## Signature
`linkOption(app, link)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `link` ([link](../appendices/types.md#link)) — The link the cursor is in. Exposes `href` and `description` (markdown Rich Footnote); either may be `null`.

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

## Types & references
- [link](../appendices/types.md#link) — the object passed as `link`.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its optional `check`/`run` form.

## Related
- [linkTarget](./linkTarget.md)
- [imageOption](./imageOption.md)
