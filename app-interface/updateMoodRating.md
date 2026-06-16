# `app.updateMoodRating`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Mood Tracking

## Description
Update a single mood rating's properties.

## Signature
`app.updateMoodRating(moodRatingUUID: string, updates: object) → Promise<void>`

## Parameters
- `moodRatingUUID` (`string`) — identifies the mood rating
- `updates` (`object`) — allowed properties: `note`, `rating`

## Returns
`Promise<void>`

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
