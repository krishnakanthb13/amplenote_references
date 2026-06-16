# Amplenote Plugin App Interface

> [← API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

The `app` object is passed as the first argument to every action handler. Nearly all of its methods return Promises and should be `await`ed. This index groups every documented method and property by category.

## Note Management
- [`app.createNote`](./createNote.md) — create a new note, optionally with a name and tags
- [`app.findNote`](./findNote.md) — find a noteHandle with metadata for an extant note
- [`app.deleteNote`](./deleteNote.md) — delete a note (restorable for 30 days)
- [`app.getNoteContent`](./getNoteContent.md) — get a note's content as markdown
- [`app.setNoteName`](./setNoteName.md) — set a new name for a note
- [`app.insertNoteContent`](./insertNoteContent.md) — insert markdown content into a note
- [`app.replaceNoteContent`](./replaceNoteContent.md) — replace a note's content or a single section
- [`app.notes` object](./notes-object.md) — concise note-interface helpers (`find`, `filter`, `create`, `dailyJot`)

## Filtering & Search
- [`app.filterNotes`](./filterNotes.md) — find noteHandles matching filter criteria
- [`app.searchNotes`](./searchNotes.md) — full-text search of note content
- [`app.getNoteBacklinks`](./getNoteBacklinks.md) — list notes that link to a note
- [`app.getNoteBacklinkContents`](./getNoteBacklinkContents.md) — get backlink content with context

## Tags & Organization
- [`app.addNoteTag`](./addNoteTag.md) — add a tag to a note
- [`app.removeNoteTag`](./removeNoteTag.md) — remove a tag from a note
- [`app.getTags`](./getTags.md) — get the tags in the user's account

## Tasks
- [`app.getNoteTasks`](./getNoteTasks.md) — get tasks present in a note
- [`app.insertTask`](./insertTask.md) — insert a new task at the start of a note
- [`app.getTask`](./getTask.md) — get the details of a single task
- [`app.updateTask`](./updateTask.md) — update a task's properties or content
- [`app.getCompletedTasks`](./getCompletedTasks.md) — get tasks completed in a time range
- [`app.getTaskDomains`](./getTaskDomains.md) — get the user's configured Task Domains
- [`app.getTaskDomainTasks`](./getTaskDomainTasks.md) — get tasks in a task domain (async iterable)
- [`app.addTaskDomainNote`](./addTaskDomainNote.md) — add a note to a task domain

## Media & Attachments
- [`app.attachNoteMedia`](./attachNoteMedia.md) — upload media and attach it to a note
- [`app.getNoteAttachments`](./getNoteAttachments.md) — list a note's referenced attachments
- [`app.getAttachmentURL`](./getAttachmentURL.md) — get a temporary URL for an attachment
- [`app.getNoteImages`](./getNoteImages.md) — get a note's inline images
- [`app.updateNoteImage`](./updateNoteImage.md) — update an image in a note

## Publishing
- [`app.publishNote`](./publishNote.md) — publish a note to a public URL
- [`app.unpublishNote`](./unpublishNote.md) — unpublish a published note
- [`app.getNotePublicURL`](./getNotePublicURL.md) — get a published note's public URL

## Note Metadata
- [`app.getNoteOpenCounts`](./getNoteOpenCounts.md) — get note open counts by rollup period
- [`app.getNoteSections`](./getNoteSections.md) — list a note's sections
- [`app.getNoteSettings`](./getNoteSettings.md) — get note-specific styling settings
- [`app.setNoteSetting`](./setNoteSetting.md) — set a note setting
- [`app.getNoteURL`](./getNoteURL.md) — get a note's full app URL

## Dialogs
- [`app.alert`](./alert.md) — show a message with optional action buttons
- [`app.prompt`](./prompt.md) — show a message with input fields

## Navigation
- [`app.navigate`](./navigate.md) — open the app to a given Amplenote URL

## Shortcuts
- [`app.addShortcut`](./addShortcut.md) — add a sidebar shortcut
- [`app.getShortcuts`](./getShortcuts.md) — list shortcuts in an area
- [`app.removeShortcut`](./removeShortcut.md) — remove a shortcut from an area

## Mood Tracking
- [`app.recordMoodRating`](./recordMoodRating.md) — record a mood rating
- [`app.getMoodRatings`](./getMoodRatings.md) — get mood ratings in a time range
- [`app.updateMoodRating`](./updateMoodRating.md) — update a mood rating's properties

## Calendar
- [`app.getExternalCalendarEvents`](./getExternalCalendarEvents.md) — get cached external calendar events

## Plugin Communication
- [`app.callPlugin`](./callPlugin.md) — call another plugin's `onPluginCall`

## Embeds
- [`app.openEmbed`](./openEmbed.md) — add a full-screen embed section to the sidebar
- [`app.openSidebarEmbed`](./openSidebarEmbed.md) — open a Peek Viewer embed

## Utilities
- [`app.evaluateExpression`](./evaluateExpression.md) — evaluate an in-editor-style expression
- [`app.htmlFromContent`](./htmlFromContent.md) — render markdown to Amplenote editor HTML
- [`app.saveFile`](./saveFile.md) — save a file
- [`app.writeClipboardData`](./writeClipboardData.md) — write to the clipboard cross-platform

## Settings & Context
- [`app.settings` & `app.setSetting`](./settings.md) — read and update plugin settings
- [`app.context`](./context.md) — invocation context properties and interaction methods
