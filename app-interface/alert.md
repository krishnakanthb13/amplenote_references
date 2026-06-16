# `app.alert`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Dialogs

## Description
Show the user a message. The name of the plugin is shown in the title of the dialog. Similar to `app.prompt`, except that this doesn't offer inputs, and instead offers "actions", which are buttons the user can pick at the bottom of the notification.

## Signature
`app.alert(message: string, options?: object) → Promise<number | null>`

## Parameters
- `message` (`String`) — the message, with optional `\n` for new lines
- `options` (`Object`, optional):
  - `actions` (`Array<Object>`) — action objects with `icon` (`String`), `label` (`String`), `value` (any)
  - `preface` (`String`) — text shown before the main message
  - `primaryAction` (`Object`) — object with `icon` (`String`), `label` (`String`) for the rightmost button
  - `scrollToEnd` (`Boolean`) — scroll long messages to the end

## Returns
`Promise<Integer | any | null>` — `null` if dismissed, `-1` if DONE/the primary action is pressed, or the selected action's `value` (when provided) otherwise its zero-based index.

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
async noteOption(app, noteUUID) {
  const actionIndex = await app.alert("This is an alert", {
    actions: [
      { icon: "post_add", label: "Insert in note" }
    ]
  });
  if (actionIndex === 0) {
    // "Insert in note"
  }
}
```

## Related
- [`app.prompt`](./prompt.md)
