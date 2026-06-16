# `app.evaluateExpression`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Utilities

## Description
Evaluates a string expression, using the same logic used to evaluate in-editor `{expressions}`.

## Signature
`app.evaluateExpression(string: string) → Promise<string | number | null>`

## Parameters
- `string` (`string`) — the expression to evaluate

## Returns
`Promise<string | number | null>` — the string or number result of the expression, or `null` if invalid.

## Example
```javascript
async appOption(app) {
  const result = await app.evaluateExpression("tomorrow");
  await app.alert("Result: " + result);
}
```

## Related
- [`app.htmlFromContent`](./htmlFromContent.md)
