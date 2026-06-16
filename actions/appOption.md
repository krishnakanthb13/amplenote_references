# `appOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds app-wide options that can be invoked from the "jump to note" (web) or quick search (mobile app) dialogs. The option is not tied to any particular note, task, or image — it is always available globally from these search/command dialogs.

## Signature
`appOption(app)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to hide the option. Returning a non-empty string can be used to customize the label shown for the option.

## Example
```javascript
appOption(app) {
  app.alert("hello");
}
```

## Related
- [noteOption](./noteOption.md)
- [dailyJotOption](./dailyJotOption.md)
- [taskOption](./taskOption.md)
