# `validateSettings`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Settings

## Description
When plugin settings are saved, this presents an opportunity to ensure that the settings are correctly set up. Returning errors signals to the user that the saved settings are invalid.

## Signature
`validateSettings(app, settings)`

## Parameters
- `app` — App Interface object (a limited version). See [App Interface](../app-interface/index.md).
- `settings` (`Object`) — The settings object that has been saved.

## Returns
`Array` of error strings, or a falsy value if the settings are valid.

## The `check` function
Not applicable — `validateSettings` is itself a validation function and does not use the `check`/`run` pattern.

## Example
```javascript
validateSettings(app, settings) {
  return [ "Settings are not valid" ];
}
```

## Types & references
- `settings` is a plain `Object`; the return value is an `Array` of error `String`s (or a falsy value when valid).
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — defining plugin settings.

## Related
- [onPluginCall](./onPluginCall.md)
