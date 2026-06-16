# `app.updateMoodRating`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Mood Tracking

## Description
Update a single mood rating's properties.

## Signature
`app.updateMoodRating(moodRatingUUID: string, updates: object) → Promise<void>`

## Parameters
- `moodRatingUUID` (`String`) — `uuid` identifying the mood rating
- `updates` (`Object`) — writable [`moodRating`](../appendices/types.md#moodrating) fields:
  - `note` (`String`) — free-text note associated with the rating
  - `rating` (`Integer`) — an integer in the range -2 to +2 (inclusive)

## Returns
`Promise<void>`

## Types & references
- [`moodRating`](../appendices/types.md#moodrating) — writable fields accepted in `updates`
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const yesterday = Math.floor(Date.now() / 1000) - (60 * 60 * 24);
  const moodRatings = await app.getMoodRatings(yesterday);
  if (moodRatings.length < 1) return;
  const { uuid } = moodRatings[0];
  await app.updateMoodRating(uuid, { note: "this is a note" });
}
```

## Related
- [`app.recordMoodRating`](./recordMoodRating.md)
- [`app.getMoodRatings`](./getMoodRatings.md)
