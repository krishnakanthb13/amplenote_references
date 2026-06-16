# `app.context`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Settings & Context

`app.context` provides details about where the plugin action was invoked, and allows for interaction at that location. This file documents all `app.context.*` properties and methods.

---

## Properties

### `app.context.noteUUID`
**Type:** `string`

The UUID of the note the plugin action was invoked from. This will include the note UUID that a task is in when invoking an action.

---

### `app.context.taskUUID`
**Type:** `string` (conditional)

If the plugin action was invoked from a position in a task, this will be the UUID of the task in question.

```javascript
insertText(app) {
  return app.context.taskUUID || "not in a task";
}
```

---

### `app.context.pluginUUID`
**Type:** `string`

The UUID of the plugin itself — this is the note UUID of the plugin note.

---

### `app.context.url`
**Type:** `string` (URL)

A URL representing the current location in the app. Can be passed to `app.navigate` to return to the same location.

---

### `app.context.subscriptionLevel`
**Type:** `string`

A string describing the current subscription level of the user, one of: `personal`, `pro`, `unlimited`, or `founder`.

---

### `app.context.lightDarkMode`
**Type:** `string`

A string indicating which mode the app is currently in. Will be either `light` or `dark`.

---

### `app.context.link`
**Type:** `object` (conditional)

Link object describing properties of the link the plugin action was invoked from. Will be `undefined` if the plugin action was not invoked from a context where the selection is in a link.

---

### `app.context.selectionContent`
**Type:** `string` (conditional)

When invoked from an editor context, the markdown representation of the content that is currently selected.

---

### `app.context.embedArgs`
**Type:** `array` (conditional)

Only present in `onEmbedCall` action functions — the array of arguments used when rendering the embed.

---

### `app.context.renderEmbedTarget`
**Type:** `string` (conditional)

In `renderEmbed` and `onEmbedCall` action functions, will be set to a string representing where the embed is being rendered. One of: `note`, `notesDashboard`, `prompt`, `publicNote`, `peekViewer`, `section`.

---

### `app.context.checkForUpdates`
**Type:** function (conditional)

Only present when a plugin has been installed from a public note. Call to check if the plugin is out of date relative to the public note it was installed from.

---

## Methods

### `app.context.replaceSelection`
**Signature:** `replaceSelection(markdown: string) → Promise<boolean>`

Replaces the selection with markdown content. This function will not be present for plugin actions that are not invoked with a user selection/cursor placed in a note. Throws if the context in which the selection existed is no longer available.

Returns a boolean indicating if the given markdown content replaced the selection (`false` if the selection was removed or the markdown was invalid).

```javascript
async insertText(app) {
  const replacedSelection = await app.context.replaceSelection("**new content**");
  if (replacedSelection) {
    return null;
  } else {
    return "plain text";
  }
}
```

---

### `app.context.updateLink`
**Signature:** `updateLink(updates: object) → Promise<void>`

If the plugin action was invoked in a link, can be called to update link properties.

```javascript
async replaceText(app) {
  if (app.context.updateLink) {
    const newDescription = (app.context.link.description || "") + "\nmore";
    app.context.updateLink({ description: newDescription });
  }
  return null;
}
```

---

### `app.context.updateImage`
**Signature:** `updateImage(updates: object) → Promise<void>`

If the plugin action was invoked on an image (`imageOption` actions), can be called to update image properties.

```javascript
async imageOption(app, image) {
  await app.context.updateImage({ caption: "and " + image.caption.toString() });
}
```

---

### `app.context.renderEmbed`
**Signature:** `renderEmbed() → Promise<void>`

Only present when in an embed context, re-renders the embed. Note that the current embed args are used — this function does not take any arguments.

---

### `app.context.updateEmbedArgs`
**Signature:** `updateEmbedArgs(callback: function) → Promise<void>`

When invoked from an embed context, can be used to update the arguments passed to `renderEmbed`.

```javascript
async onEmbedCall(app, value) {
  await app.context.updateEmbedArgs((value || 0) + 1);
}
```

## Related
- [`app.settings` & `app.setSetting`](./settings.md)
- [`app.navigate`](./navigate.md)
- [`app.openEmbed`](./openEmbed.md)
