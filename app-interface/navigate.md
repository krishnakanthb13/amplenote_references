# `app.navigate`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Navigation

## Description
Opens the app to the location corresponding to the given Amplenote app URL. Amplenote app URLs start with `https://www.amplenote.com/notes`.

URL examples:
- Jots area: `"https://www.amplenote.com/notes/jots"`
- Notes area: `"https://www.amplenote.com/notes"`
- Notes filtered by tag: `"https://www.amplenote.com/notes?tag=some-tag"`
- Specific note: `"https://www.amplenote.com/notes/NOTE_UUID"`
- Note section: `"https://www.amplenote.com/notes/NOTE_UUID#Section_name"`
- Specific task in note: `"https://www.amplenote.com/notes/NOTE_UUID?highlightTaskUUID=TASK_UUID"`
- Dedicated task page: `"https://www.amplenote.com/notes/tasks/TASK_UUID"`

## Signature
`app.navigate(url: string) → Promise<boolean>`

## Parameters
- `url` (`String`) — the Amplenote app URL to navigate to (must start with `https://www.amplenote.com/notes`)

## Returns
`Promise<Boolean>` — `true` if a valid URL was navigated to, `false` otherwise.

## Types & references
- [App Interface index](./index.md)

## Example
```javascript
noteOption(app) {
  app.navigate("https://www.amplenote.com/notes/jots");
}
```

## Related
- [`app.getNoteURL`](./getNoteURL.md)
- [`app.openEmbed`](./openEmbed.md)
