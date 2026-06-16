# Appendix I: Types

> Part of [Appendices](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/developing_amplenote_plugins/appendix_i)

This appendix documents the structured object types that the Amplenote plugin API passes to, and receives from, your plugin code. Each type below has its own heading (so it can be linked by anchor) followed by a table of its properties.

Types in this reference:
[attachment](#attachment) ·
[externalCalendarEvent](#externalcalendarevent) ·
[image](#image) ·
[link](#link) ·
[moodRating](#moodrating) ·
[noteHandle](#notehandle) ·
[section](#section) ·
[tag](#tag) ·
[task](#task)

---

### attachment

Describes a file attached to a note.

| Field | Type | Description |
|-------|------|-------------|
| `name` | String | The filename of the attachment. |
| `type` | String | The MIME type of the attachment (e.g. `application/pdf`, `image/png`). |
| `uuid` | String | Unique identifier for the attachment. |

---

### externalCalendarEvent

Describes an event sourced from an external calendar provider (e.g. Google Calendar, Apple Calendar, Outlook Calendar).

| Field | Type | Description |
|-------|------|-------------|
| `allDay` | Boolean | Whether the event spans the entire day rather than a specific time range. |
| `calendar` | Object | The calendar the event belongs to. See the nested fields below. |
| `calendar.color` | String | Hex color string of the source calendar. |
| `calendar.name` | String | Display name of the source calendar. |
| `calendar.provider` | String | The calendar provider, e.g. `google_calendar`, `apple_calendar`, or `outlook_calendar`. |
| `calendar.uuid` | String | Unique identifier of the source calendar. |
| `color` | String | Hex color string for the event itself. |
| `end` | Date | When the event ends. |
| `start` | Date | When the event starts. |
| `title` | String | The event's title. |

---

### image

Describes an inline image embedded in note content.

| Field | Type | Description |
|-------|------|-------------|
| `caption` | String | Markdown caption shown beneath the image. |
| `index` | Integer | Read-only. Disambiguates multiple images that share the same `src`. |
| `src` | String | The image source URL. |
| `text` | String | OCR text recognized within the image. |
| `width` | Integer | Optional. The rendered width in pixels; the height scales automatically to preserve the image's aspect ratio. |

---

### link

Describes a link, including the content of its associated Rich Footnote.

| Field | Type | Description |
|-------|------|-------------|
| `description` | String | Markdown describing the content of the link's Rich Footnote. This is a subset of the markdown supported in note content. |
| `href` | String | The target URL the link points to. |

> Any property of a `link` may be `null` if it has not been set.

---

### moodRating

Describes a user-recorded mood rating.

| Field | Type | Description |
|-------|------|-------------|
| `note` | String | A user-entered note accompanying the rating. |
| `rating` | Integer | The mood rating, from `-2` to `+2` inclusive. |
| `timestamp` | Integer | Unix timestamp (in seconds) of when the rating was recorded. |
| `uuid` | String | Unique identifier for the mood rating. |

---

### noteHandle

Identifies a note, whether it already exists or is yet to be created.

A `noteHandle` accepts a String `uuid` as shorthand — passing a bare uuid string is equivalent to passing an object with that `uuid`. For example, `someFn("123")` is equivalent to `someFn({ uuid: "123" })`.

> UUIDs prefixed with `local-` reference notes that have not yet been persisted to the server. Such handles are only valid on the client that originated them.

When returned from the API, a `noteHandle` may include the following properties:

| Field | Type | Description |
|-------|------|-------------|
| `changed` | String | ISO 8601 timestamp of the last user modification to the note. |
| `created` | String | ISO 8601 timestamp of when the note was created. |
| `name` | String or null | The note's title, or `null` if it has none. |
| `published` | Boolean | Present only when `true` — indicates the note is published. |
| `shared` | Boolean | Present only when `true` — indicates the note is shared. |
| `tags` | Array of String | The tags applied to the note. |
| `updated` | String | ISO 8601 timestamp of when the note was last updated. |
| `uuid` | String | The note's unique identifier. |
| `vault` | Boolean | Present only when `true` — indicates the note is in the vault. |

---

### section

Describes a section of a note — a chunk of content delimited by headings (or horizontal rules).

| Field | Type | Description |
|-------|------|-------------|
| `heading` | Object or null | The heading that begins the section, or `null` for content preceding the first heading. See the nested fields below. |
| `heading.anchor` | String | The anchor slug of the heading. |
| `heading.href` | String | A link URL targeting the heading. |
| `heading.level` | Integer | The heading level, from `1` to `3`. |
| `heading.text` | String | The heading's text content. |
| `index` | Integer | Disambiguates sections with identical or `null` headings. |

![Note structure with sections and headings](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/c553df7f-08ca-47f9-b2cd-dce6dc48668c.png)

![Note sectioning with multiple headings and horizontal rules](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/c4d34ddd-25b8-4e40-9ac4-0a698742f8dd.png)

---

### tag

Describes a tag in the user's account.

| Field | Type | Description |
|-------|------|-------------|
| `color` | String | Hex color string for the tag, without the leading `#`. |
| `noteCount` | Integer | The number of notes carrying this tag. For parent tags, this counts notes under child tags as well. |
| `text` | String | The tag's text. Composed of lowercase letters, dashes, and the parent-child delimiter `/`. |

---

### task

Describes a task. Timestamps are Unix timestamps in UTC seconds.

| Field | Type | Description |
|-------|------|-------------|
| `completedAt` | Integer | Unix UTC timestamp of completion. Present only if the task is completed. |
| `content` | String | The task's content as markdown. |
| `createdAt` | Integer | Read-only. Unix UTC timestamp of when the task was created. |
| `deadline` | Integer | Unix UTC timestamp of the task's deadline. |
| `dismissedAt` | Integer | Unix UTC timestamp of dismissal. Present only if the task is dismissed. |
| `endAt` | Integer | Unix UTC timestamp of the task's end. Must be after `startAt`, and requires `startAt` to be set. |
| `hideUntil` | Integer or null | Unix UTC timestamp before which the task is hidden, or `null`. |
| `important` | Boolean | Whether the task is flagged important. |
| `isParent` | Boolean | Whether the task has indented subtasks. |
| `isRepeating` | Boolean | Whether the task repeats. |
| `noteUUID` | String | The UUID of the note containing the task. Ignored when passed to app functions. |
| `repeat` | String or null | An RRULE string describing the repeat schedule, or `null`. |
| `score` | Number | The task's computed score. |
| `startAt` | Integer or null | Unix UTC timestamp of the task's start, or `null`. |
| `urgent` | Boolean | Whether the task is flagged urgent. |
| `uuid` | String | The task's unique identifier. |
