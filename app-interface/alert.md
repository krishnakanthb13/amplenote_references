# `app.alert`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Dialogs

## Description
Show the user a message. The name of the plugin is shown in the title of the dialog. Similar to `app.prompt`, except that this doesn't offer inputs, and instead offers "actions", which are buttons the user can pick at the bottom of the notification.

## Signature
`app.alert(message: string, options?: object) → Promise<number | null>`

## Parameters
- `message` (`string`) — the message, with optional `\n` for new lines
- `options` (`object`, optional):
  - `actions` (`array`) — action objects with `icon`, `label`, `value`
  - `preface` (`string`) — text shown before the main message
  - `primaryAction` (`object`) — object with `icon`, `label` for the rightmost button
  - `scrollToEnd` (`boolean`) — scroll long messages to the end

## Returns
`Promise<number | null>` — `null` if dismissed, `-1` if DONE pressed, or the action index/value if an action is selected.

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
