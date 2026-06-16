# `app.getExternalCalendarEvents`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Calendar

## Description
Get events from the user's connected external calendars (e.g. Google Calendar, Apple Calendar, etc). Note this does not query external calendars directly, but rather cached calendar events for the next ~30 days.

## Signature
`app.getExternalCalendarEvents(options?: object) → Promise<Array>`

## Parameters
- `options` (`Object`, optional):
  - `days` (`Integer`) — number of days of events to return (1-30)
  - `taskDomainUUID` (`String`) — `uuid` to filter results by task domain

## Returns
`Promise<Array<`[`externalCalendarEvent`](../appendices/types.md#externalcalendarevent)`>>` — array of [`externalCalendarEvent`](../appendices/types.md#externalcalendarevent) objects (from cached events for roughly the next 30 days).

## Types & references
- [`externalCalendarEvent`](../appendices/types.md#externalcalendarevent) — shape of each returned event
- [App Interface index](./index.md)

## Example
```javascript
async appOption(app) {
  const externalCalendarEvents = await app.getExternalCalendarEvents({ days: 3 });
  await app.alert("External calendar events in next 3 days: " + externalCalendarEvents.length);
}
```

## Related
- [`app.getTaskDomains`](./getTaskDomains.md)
