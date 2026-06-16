# `app.getMoodRatings`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Mood Tracking

## Description
Returns an array of mood rating objects filtered by timestamp range.

## Signature
`app.getMoodRatings(from: number, to?: number) → Promise<Array>`

## Parameters
- `from` (`number`) — integer unix timestamp (seconds); ratings on or after this time
- `to` (`number`, optional) — integer unix timestamp (seconds); ratings before this time

## Returns
`Promise<Array>` — array of moodRating objects.

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
