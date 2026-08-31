# `app.getPeople`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** People & Contacts

## Description
List the people known to the current user.

## Signature
`app.getPeople() → Promise<person[]>`

## Parameters
None.

## Returns
`Promise<Array<`[person](../appendices/types.md#person)`>>` — array of person objects.

## Example
```javascript
async appOption(app) {
  const people = await app.getPeople();
  await app.alert("People: " + JSON.stringify(people, null, 2));
}
```

## Types & references
- [person](../appendices/types.md#person) — the returned array elements.
- [App Interface index](./index.md)

## Related
- [`app.filterNotes`](./filterNotes.md) — filter notes by various criteria
