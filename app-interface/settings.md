# `app.settings` & `app.setSetting`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Settings & Context

This file documents the plugin settings property `app.settings` and the method `app.setSetting`.

---

## `app.settings` (property)

**Type:** `object`

### Description
An object containing the user-configured settings for the plugin. All values will be strings.

### Example
```javascript
insertText(app) {
  return app.settings["Some setting"];
}
```

---

## `app.setSetting`

### Description
Update the value of a single setting. The value will be synchronized to all of the user's devices. Note that the updated value is not guaranteed to be updated in `app.settings` before the next invocation of a plugin function.

### Signature
`app.setSetting(key: string, value: string) → Promise<void>`

### Parameters
- `key` (`string`) — the setting name to update or add
- `value` (`string`) — the new value for the setting (non-string values except `null` are converted to strings)

### Returns
`Promise<void>`

### Example
```javascript
async appOption(app) {
  const count = parseInt(app.settings["counter"] || "0", 10);
  await app.setSetting("counter", count + 1);
  app.alert("new value: " + count);
}
```

## Related
- [`app.context`](./context.md)
