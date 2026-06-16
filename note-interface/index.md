# Amplenote Plugin Note Interface

> [← API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

The **Note interface** is an object-oriented abstraction over a single Amplenote note. Instead of repeatedly passing a `noteHandle` to `app.*` functions, you obtain a `note` object bound to one specific note and call methods directly on it.

A note object is obtained via `app.notes.find(handle)` (for example `app.notes.find(noteUUID)`). The note returned may not yet exist on disk — calling functions that modify the note content will create the note if it doesn't already exist.

Many of the methods on this interface mirror their `app.*` equivalents (for example `note.content()` corresponds to `app.getNoteContent(handle)`, and `note.addTag(name)` corresponds to `app.addNoteTag(handle, name)`). Each member page below lists the equivalent `app` method where one exists.

## Properties
- [`note.name`](./name.md) — Get the title of the note (`String`).
- [`note.tags`](./tags.md) — An `Array` of tags applied to the note.

## Content
- [`note.content`](./content.md) — Get the note's content as markdown.
- [`note.insertContent`](./insertContent.md) — Insert markdown at the beginning of the note.
- [`note.replaceContent`](./replaceContent.md) — Replace the whole note, or a single section, with new content.
- [`note.sections`](./sections.md) — Get the sections in the note.

## Tags
- [`note.addTag`](./addTag.md) — Add a tag to the note.
- [`note.removeTag`](./removeTag.md) — Remove a tag from the note.

## Tasks
- [`note.tasks`](./tasks.md) — Get the tasks in the note.
- [`note.insertTask`](./insertTask.md) — Insert a new task at the beginning of the note.

## Media
- [`note.images`](./images.md) — Get all inline images in the note.
- [`note.attachMedia`](./attachMedia.md) — Attach an image or video media file to the note.
- [`note.attachments`](./attachments.md) — Get the list of attachments in the note.
- [`note.updateImage`](./updateImage.md) — Update a specific image in the note.

## Backlinks
- [`note.backlinks`](./backlinks.md) — Async-iterate the notes that link to this note.
- [`note.backlinkContents`](./backlinkContents.md) — Get the referencing content from a specific source note.

## Publishing
- [`note.publish`](./publish.md) — Publish the note and return its public URL.
- [`note.publicURL`](./publicURL.md) — Get the published URL of the note, if published.

## Lifecycle / Metadata
- [`note.setName`](./setName.md) — Set a new title for the note.
- [`note.url`](./url.md) — Get the String URL of the note.
- [`note.delete`](./delete.md) — Delete the note.
