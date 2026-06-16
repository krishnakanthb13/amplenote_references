# `app.getTags`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tags & Organization

## Description
Get the tags in the user's account.

## Signature
`app.getTags() → Promise<tag[]>`

## Parameters
None.

## Returns
`Promise<tag[]>` — array of tag objects.

## Example
```javascript
async appOption(app) {
  const tags = await app.getTags();
  await app.alert("Tag count: " + tags.length);
}
```

## Related
- [`app.addNoteTag`](./addNoteTag.md)
- [`app.removeNoteTag`](./removeNoteTag.md)
