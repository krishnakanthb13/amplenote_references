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
**Type:** [`link`](../appendices/types.md#link) (conditional)

A [`link`](../appendices/types.md#link) object describing properties of the link the plugin action was invoked from (`description` markdown `String | null`, `href` `String | null`). Will be `undefined` if the plugin action was not invoked from a context where the selection is in a link. Use `app.context.updateLink` to modify it.

---

### `app.context.selectionContent`
**Type:** `String` (conditional)

When invoked from an editor context, the [markdown](../guides/markdown-reference.md) representation (`String`) of the content that is currently selected. Use `app.context.replaceSelection` to overwrite it.

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
**Signature:** `replaceSelection(markdown: String) → Promise<Boolean>`

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
**Signature:** `updateLink(updates: Object) → Promise<void>`

If the plugin action was invoked in a link, can be called to update [`link`](../appendices/types.md#link) properties (`description`, `href`).

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
**Signature:** `updateImage(updates: Object) → Promise<void>`

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

---

### `app.context.closeEmbed`
**Signature:** `closeEmbed() → Promise<void>`

Only present in `renderEmbed` and `onEmbedCall` action functions, when an embed is rendered from a note context (`app.context.renderEmbedTarget === "note"`). Calling this function will immediately close and remove the embed that is being rendered.

---

### `app.context.getStyleProperties`
**Signature:** `getStyleProperties() → Promise<String>`

Only present in `renderEmbed` and `onEmbedCall` action functions, returns a string of CSS containing the custom properties defining themed light/dark colors for the app. This string can be included in a `<style>` element to apply themed colors, which can then be referenced in CSS in the embed (e.g. `color: var(--color-text-high-contrast);`).

```javascript
async renderEmbed(app) {
  const styleProperties = await app.context.getStyleProperties();
  return `
    <style>
      :root { ${ styleProperties } }
    </style>
    <div style="padding: 16px; font-family: sans-serif; background: #d7e9fb;">
      <pre>${ styleProperties }</pre>
    </div>
  `;
}
```

---

### `app.context.refreshNotesList`
**Signature:** `refreshNotesList() → Promise<Boolean>`

Attempts to ensure the notes list is up to date. Returning `true` indicates the notes list is up to date to within approximately one minute, while a `false` return value indicates that the notes list could not be updated. Refreshing the notes list ensures metadata about notes is up to date — it does not indicate that content in updated notes has been retrieved and updated in the client's datastore.

```javascript
async appOption(app) {
  const wasRefreshed = await app.context.refreshNotesList();
  await app.alert("Notes list is (roughly) up to date: " + wasRefreshed);
}
```

---

### `app.context.refreshSettings`
**Signature:** `refreshSettings() → Promise<Object>`

`app.settings` is updated on a lower tier of sync urgency than most data. To ensure fresh settings are available (e.g. from other devices/clients that may be modifying the plugin's settings), `refreshSettings` can be used. Note this is likely to make a web request that can potentially take some time.

```javascript
async noteOption(app, noteUUID) {
  const latestSettings = await app.context.refreshSettings();
}
```

---

### `app.context.setEmbedHTML`
**Signature:** `setEmbedHTML(html: String) → void`

Only defined in `renderEmbed` action functions. Call with an HTML string to immediately render it in the embed — this allows for an initial loading screen to be placed in the embed while `renderEmbed` performs some longer work to produce the final embed content.

```javascript
async renderEmbed(app) {
  app.context.setEmbedHTML("<div>Loading...</div>");
  await new Promise(resolve => setTimeout(resolve, 5000));
  return "<div>Done</div>";
}
```

---

### `app.context.setScheduledTasks`
**Signature:** `setScheduledTasks(scheduledTasks: Array<Object>) → Promise<void>`

Only available in [`suggestScheduledTasks`](../actions/suggestScheduledTasks.md) — call to set initial or progressive suggestions before returning from the action. Useful if the calculation of suggested tasks is slow and there are initial suggestions that can be presented to the user while the final suggestions are being determined.

```javascript
async suggestScheduledTasks(app, { startAt, schedulableTasks }) {
  const schedulableTask = schedulableTasks[0];
  if (!schedulableTask) return [];

  const scheduledTasks = [
    { explanation: "Very basic scheduling", startAt, taskUUID: schedulableTask.uuid },
  ];

  await app.context.setScheduledTasks(scheduledTasks);
  await new Promise(resolve => setTimeout(resolve, 5000));
  return scheduledTasks;
}
```

---

### `app.context.setStatus`
**Signature:** `setStatus(status: String) → void`

Call with a string argument to set a status while the plugin is executing, which will be displayed to the user when listing running plugins.

```javascript
async appOption(app) {
  app.context.setStatus("Reticulating splines...");
  await new Promise(resolve => setTimeout(resolve, 5000));
}
```

---

### `app.context.setTaskTargetNotes`
**Signature:** `setTaskTargetNotes(suggestions: Array<noteHandle | String>) → Promise<void>`

Only available in [`suggestTaskTargetNotes`](../actions/suggestTaskTargetNotes.md) — call to set some results immediately before returning from the action with the final suggestions.

```javascript
async suggestTaskTargetNotes(app, task, suggestedNoteHandles) {
  const suggestions = suggestedNoteHandles.toReversed();
  await app.context.setTaskTargetNotes(suggestions);
  return suggestions;
}
```

## Types & references
- [`link`](../appendices/types.md#link) — shape of `app.context.link` (and `updates` for `updateLink`)
- [Markdown reference](../guides/markdown-reference.md) — format of `selectionContent` and `replaceSelection` arguments
- [Execution environment](../appendices/execution-environment.md) — embed contexts driving `renderEmbed`/`updateEmbedArgs`
- [App Interface index](./index.md)

## Related
- [`app.settings` & `app.setSetting`](./settings.md)
- [`app.navigate`](./navigate.md)
- [`app.openEmbed`](./openEmbed.md)
