# `app.getExternalCalendarEvents`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Calendar

## Description
Get events from the user's connected external calendars (e.g. Google Calendar, Apple Calendar, etc). Note this does not query external calendars directly, but rather cached calendar events for the next ~30 days.

## Signature
`app.getExternalCalendarEvents(options?: object) → Promise<Array>`

## Parameters
- `options` (`object`, optional):
  - `days` (`number`) — integer (1-30) days of events to return
  - `taskDomainUUID` (`string`) — UUID to filter results by task domain

## Returns
`Promise<Array>` — array of externalCalendarEvent objects.

## Example
```javascript
async appOption(app) {
  const externalCalendarEvents = await app.getExternalCalendarEvents({ days: 3 });
  await app.alert("External calendar events in next 3 days: " + externalCalendarEvents.length);
}
```

## Related
- [`app.getTaskDomains`](./getTaskDomains.md)
