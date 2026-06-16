# `onNavigate`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Lifecycle & Navigation

## Description
Called when the user changes locations in the app, e.g. when opening a note, jots, etc.

## Signature
`onNavigate(app, url)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `url` (`String`) — The URL being navigated to (e.g. the location of the note or jots view just opened).

## Returns
Nothing.

## The `check` function
The check function is not called for this action.

## Example
```javascript
onNavigate(app, url) {
  console.log("new location: " + url);
}
```

## Types & references
- `url` is a plain `String`; this action takes no API object types.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action.

## Related
- [onNoteCreated](./onNoteCreated.md)
- [linkTarget](./linkTarget.md)
