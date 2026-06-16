# `onNoteCreated`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Lifecycle & Navigation

## Description
Called when a note has been created _on the current client_.

## Signature
`async onNoteCreated(app, noteHandle)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `noteHandle` ([noteHandle](../appendices/types.md#notehandle)) — Describes the newly created note. Exposes props such as `uuid`, `name`, `tags`, `created`, `updated`, `published`, `shared` and `vault`.

## Returns
Nothing.

## The `check` function
Standard check behavior — return falsy to skip handling. The check function receives the same `(app, noteHandle)` arguments as `run`.

## Example
```javascript
async onNoteCreated(app, noteHandle) {
  await app.alert("note created: " + JSON.stringify(noteHandle));
}
```

## Types & references
- [noteHandle](../appendices/types.md#notehandle) — the object passed as `noteHandle`.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action and its optional `check`/`run` form.

## Related
- [onNavigate](./onNavigate.md)
