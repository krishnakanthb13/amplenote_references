# `app.recordMoodRating`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Mood Tracking

## Description
Records a mood rating.

## Signature
`app.recordMoodRating(rating: number) → Promise<string>`

## Parameters
- `rating` (`Integer`) — the [`moodRating`](../appendices/types.md#moodrating) `rating` value, an integer in the range -2 to +2 (inclusive)

## Returns
`Promise<String>` — the `uuid` of the recorded [`moodRating`](../appendices/types.md#moodrating).

## Types & references
- [`moodRating`](../appendices/types.md#moodrating) — shape of a recorded mood rating
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const ratingUUID = await app.recordMoodRating(2);
  await app.alert("Rating: " + ratingUUID);
}
```

## Related
- [`app.getMoodRatings`](./getMoodRatings.md)
- [`app.updateMoodRating`](./updateMoodRating.md)
