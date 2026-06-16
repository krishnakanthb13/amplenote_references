# `app.notes`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Note Management

The `app.notes` object provides an alternative, more concise interface for working with notes. Its methods build a `Note` interface object that lets you call note-specific functions more concisely than the top-level `app.*` equivalents. This file documents all `app.notes.*` methods.

---

## `app.notes.find`
**Signature:** `find(identifier: string | object) → Promise<Note | null>`

Builds an object that allows you to more concisely call `app.*` functions for a specific note.

**Parameters:**
- `identifier` — either a `uuid` (string UUID identifying the note) or a `noteHandle`

**Returns:** A `Note` interface object for the note, or `null` if the note doesn't exist or is deleted.

```javascript
async noteOption(app, noteUUID) {
  const note = await app.notes.find(noteUUID);
  app.alert(note.name);
}

async noteOption(app) {
  const note = await app.notes.find({ name: "some note" });
  app.alert(note ? "Note exists" : "Note doesn't exist");
}
```

---

## `app.notes.filter`
**Signature:** `filter(params?: object) → Promise<noteHandle[]>`

Find noteHandles for all notes matching a set of filter criteria. This is an alternative interface to [`app.filterNotes`](./filterNotes.md).

**Parameters (optional):**
- `group` — filter group (string, can use comma separator for multiple)
- `tag` — tag filter (string, comma-separated for multiple, prefix with `^` to negate)

**Returns:** An array of noteHandles matching the filter parameters.

```javascript
async insertText(app) {
  const noteHandles = await app.notes.filter({ tag: "daily-jots" });
  return `note count: ${noteHandles.length}`;
}

async insertText(app) {
  const noteHandles = await app.notes.filter({ tag: "daily-jots,^todo/next" });
  return `note count: ${noteHandles.length}`;
}
```

---

## `app.notes.create`
**Signature:** `create(name: string, tags: string[]) → Promise<Note>`

Create a new note. This is an alternative interface to [`app.createNote`](./createNote.md).

**Parameters:**
- `name` — string to use as the new note's name
- `tags` — array of string tag names to apply

**Returns:** A `Note` interface object for the newly created note.

```javascript
async noteOption(app, noteUUID) {
  const note = await app.notes.create("some new note", ["some-tag"]);
  app.alert(note.uuid);
}
```

---

## `app.notes.dailyJot`
**Signature:** `dailyJot(timestamp: number) → Promise<Note>`

Gets a note interface for the daily jot note on the day corresponding to the given timestamp.

**Parameters:**
- `timestamp` — unix timestamp number (seconds) indicating any time on the day

**Returns:** A `Note` interface object for the daily jot note.

```javascript
async noteOption(app, noteUUID) {
  const tomorrowTimestamp = Math.floor(Date.now() / 1000) + 60 * 60 * 24;
  const note = await app.notes.dailyJot(tomorrowTimestamp);
  app.alert(note.name);
}
```

## Related
- [`app.createNote`](./createNote.md)
- [`app.filterNotes`](./filterNotes.md)
- [`app.findNote`](./findNote.md)
