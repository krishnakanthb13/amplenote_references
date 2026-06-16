# `dailyJotOption`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Menu Options

## Description
Adds an option to the suggestions shown below today's daily jot note in jots mode, with a button to run the plugin action.

## Signature
`dailyJotOption(app, noteHandle)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — The note handle of the daily jot note. Exposes props such as `uuid`, `name`, `tags`, `created`, `updated`, `published`, `shared` and `vault`.

## Returns
Nothing.

## The `check` function
To customize the text shown on the "Run" button, return a non-empty string from the plugin action's `check` function. Returning `null`, `false`, or an empty string hides the option.

## Example
```javascript
dailyJotOption: {
  check(app, noteHandle) {
    return "Do something";
  },
  run(app, noteHandle) {
    app.alert("Hello");
  }
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the object passed as `noteHandle`.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its `check`/`run` form.

## Related
- [appOption](./appOption.md)
- [noteOption](./noteOption.md)
