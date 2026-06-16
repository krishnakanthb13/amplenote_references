# `onNavigate`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Lifecycle & Navigation

## Description
Called when the user changes locations in the app, e.g. when opening a note, jots, etc.

## Signature
`onNavigate(app, url)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `url` (`String`) — The URL being navigated to.

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

## Related
- [onNoteCreated](./onNoteCreated.md)
- [linkTarget](./linkTarget.md)
