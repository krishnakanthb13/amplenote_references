# `app.getMoodRatings`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Mood Tracking

## Description
Returns an array of mood rating objects filtered by timestamp range.

## Signature
`app.getMoodRatings(from: number, to?: number) → Promise<Array>`

## Parameters
- `from` (`Integer`) — Unix timestamp (UTC seconds); ratings on or after this time
- `to` (`Integer`, optional) — Unix timestamp (UTC seconds); ratings before this time

## Returns
`Promise<Array<`[`moodRating`](../appendices/types.md#moodrating)`>>` — array of [`moodRating`](../appendices/types.md#moodrating) objects.

## Types & references
- [`moodRating`](../appendices/types.md#moodrating) — shape of each returned rating
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const from = Math.floor(Date.now() / 1000) - (60 * 60 * 24);
  const moodRatings = await app.getMoodRatings(from);
  await app.alert("Mood ratings: " + JSON.stringify(moodRatings));
}
```

## Related
- [`app.recordMoodRating`](./recordMoodRating.md)
- [`app.updateMoodRating`](./updateMoodRating.md)
