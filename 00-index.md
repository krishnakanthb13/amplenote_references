# Amplenote Plugin API — Master Reference Index

A complete, navigable reference for the Amplenote plugin API. Every API option (each action, every `app.*` method, and every `note.*` member) lives in its own markdown file, grouped into folders, each folder with its own index, and all linked back here.

> **This is the master index — start here.** It is named `00-index.md` so it always sorts to the top of the folder.

---

## Source Documentation (reference points)

Everything in this reference was derived from the official Amplenote plugin documentation. Each generated file also links back to its specific source page in its breadcrumb. The canonical sources:

| # | Source page | Mirrored in |
|---|-------------|-------------|
| 1 | [Developing Amplenote Plugins (overview)](https://www.amplenote.com/help/developing_amplenote_plugins) | [`00-overview.md`](./00-overview.md) |
| 2 | [Plugin Creation](https://www.amplenote.com/help/developing_amplenote_plugins/plugin_creation) | [`01-plugin-creation.md`](./01-plugin-creation.md) |
| 3 | [Actions](https://www.amplenote.com/help/developing_amplenote_plugins/actions) | [`actions/`](./actions/index.md) |
| 4 | [App Interface](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface) | [`app-interface/`](./app-interface/index.md) |
| 5 | [Note Interface](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface) | [`note-interface/`](./note-interface/index.md) |
| 6 | [Examples](https://www.amplenote.com/help/developing_amplenote_plugins/examples) | [`examples/`](./examples/index.md) |

---

## How this reference is organized

```
amplenote_references/
├── 00-index.md            ← you are here (master index)
├── 00-overview.md         ← what plugins are; the big picture
├── 01-plugin-creation.md  ← the anatomy of a plugin note
├── actions/               ← 17 entry-point hooks (1 file each)
├── app-interface/         ← 55 `app.*` methods & properties (1 file each)
├── note-interface/        ← 21 `note.*` members (1 file each)
└── examples/              ← 4 worked patterns
```

Each option file follows the same template (Description · Signature · Parameters · Returns · Example · Related) and carries a breadcrumb linking back to its group index, this master index, and its original source page.

---

## 1. Getting Started

| Document | What it covers |
|----------|----------------|
| [Overview](./00-overview.md) | What plugins are, the five reference areas, supporting appendices, key capabilities, and community resources. |
| [Plugin Creation](./01-plugin-creation.md) | A plugin = a note with a metadata table + a first code block. Metadata fields, the three code-block forms, settings, state, and async. |

---

## 2. Actions — `actions/`

Entry-point hooks. The plugin object exposes a function whose **name matches the action type**. → **[Full Actions index](./actions/index.md)**

**Text Insertion / Replacement**
- [`insertText`](./actions/insertText.md) — insert text in place of an `{expression}`
- [`replaceText`](./actions/replaceText.md) — transform highlighted text from the selection menu

**Menu Options**
- [`noteOption`](./actions/noteOption.md) — option in a note's `...` menu
- [`appOption`](./actions/appOption.md) — app-wide option (jump-to-note / quick search)
- [`dailyJotOption`](./actions/dailyJotOption.md) — suggestion below today's daily jot
- [`taskOption`](./actions/taskOption.md) — option in the task commands menu (`!`)
- [`eventOption`](./actions/eventOption.md) — option on a calendar event popup
- [`imageOption`](./actions/imageOption.md) — option on an image's dropdown
- [`linkOption`](./actions/linkOption.md) — button in the Rich Footnote link popup
- [`linkTarget`](./actions/linkTarget.md) — handler for `plugin://<uuid>` link clicks

**Lifecycle & Navigation**
- [`onNavigate`](./actions/onNavigate.md) — fires on location change
- [`onNoteCreated`](./actions/onNoteCreated.md) — fires when a note is created

**Embeds**
- [`renderEmbed`](./actions/renderEmbed.md) — return HTML for an embed iFrame
- [`onEmbedCall`](./actions/onEmbedCall.md) — handle `window.callAmplenotePlugin` from an embed

**Plugin Communication**
- [`onPluginCall`](./actions/onPluginCall.md) — handle `app.callPlugin` from another plugin

**Tasks**
- [`suggestTaskTargetNotes`](./actions/suggestTaskTargetNotes.md) — suggest target notes for a task

**Settings**
- [`validateSettings`](./actions/validateSettings.md) — validate settings on save

---

## 3. App Interface — `app-interface/`

The `app` object, passed as the first argument to every action handler. Nearly all methods return Promises. → **[Full App Interface index](./app-interface/index.md)**

| Category | Options |
|----------|---------|
| **Note Management** | [createNote](./app-interface/createNote.md) · [findNote](./app-interface/findNote.md) · [deleteNote](./app-interface/deleteNote.md) · [getNoteContent](./app-interface/getNoteContent.md) · [setNoteName](./app-interface/setNoteName.md) · [insertNoteContent](./app-interface/insertNoteContent.md) · [replaceNoteContent](./app-interface/replaceNoteContent.md) · [app.notes object](./app-interface/notes-object.md) |
| **Filtering & Search** | [filterNotes](./app-interface/filterNotes.md) · [searchNotes](./app-interface/searchNotes.md) · [getNoteBacklinks](./app-interface/getNoteBacklinks.md) · [getNoteBacklinkContents](./app-interface/getNoteBacklinkContents.md) |
| **Tags & Organization** | [addNoteTag](./app-interface/addNoteTag.md) · [removeNoteTag](./app-interface/removeNoteTag.md) · [getTags](./app-interface/getTags.md) |
| **Tasks** | [getNoteTasks](./app-interface/getNoteTasks.md) · [insertTask](./app-interface/insertTask.md) · [getTask](./app-interface/getTask.md) · [updateTask](./app-interface/updateTask.md) · [getCompletedTasks](./app-interface/getCompletedTasks.md) · [getTaskDomains](./app-interface/getTaskDomains.md) · [getTaskDomainTasks](./app-interface/getTaskDomainTasks.md) · [addTaskDomainNote](./app-interface/addTaskDomainNote.md) |
| **Media & Attachments** | [attachNoteMedia](./app-interface/attachNoteMedia.md) · [getNoteAttachments](./app-interface/getNoteAttachments.md) · [getAttachmentURL](./app-interface/getAttachmentURL.md) · [getNoteImages](./app-interface/getNoteImages.md) · [updateNoteImage](./app-interface/updateNoteImage.md) |
| **Publishing** | [publishNote](./app-interface/publishNote.md) · [unpublishNote](./app-interface/unpublishNote.md) · [getNotePublicURL](./app-interface/getNotePublicURL.md) |
| **Note Metadata** | [getNoteOpenCounts](./app-interface/getNoteOpenCounts.md) · [getNoteSections](./app-interface/getNoteSections.md) · [getNoteSettings](./app-interface/getNoteSettings.md) · [setNoteSetting](./app-interface/setNoteSetting.md) · [getNoteURL](./app-interface/getNoteURL.md) |
| **Dialogs** | [alert](./app-interface/alert.md) · [prompt](./app-interface/prompt.md) |
| **Navigation** | [navigate](./app-interface/navigate.md) |
| **Shortcuts** | [addShortcut](./app-interface/addShortcut.md) · [getShortcuts](./app-interface/getShortcuts.md) · [removeShortcut](./app-interface/removeShortcut.md) |
| **Mood Tracking** | [recordMoodRating](./app-interface/recordMoodRating.md) · [getMoodRatings](./app-interface/getMoodRatings.md) · [updateMoodRating](./app-interface/updateMoodRating.md) |
| **Calendar** | [getExternalCalendarEvents](./app-interface/getExternalCalendarEvents.md) |
| **Plugin Communication** | [callPlugin](./app-interface/callPlugin.md) |
| **Embeds** | [openEmbed](./app-interface/openEmbed.md) · [openSidebarEmbed](./app-interface/openSidebarEmbed.md) |
| **Utilities** | [evaluateExpression](./app-interface/evaluateExpression.md) · [htmlFromContent](./app-interface/htmlFromContent.md) · [saveFile](./app-interface/saveFile.md) · [writeClipboardData](./app-interface/writeClipboardData.md) |
| **Settings & Context** | [app.settings & app.setSetting](./app-interface/settings.md) · [app.context](./app-interface/context.md) |

---

## 4. Note Interface — `note-interface/`

An object-oriented abstraction over a single note, obtained via `app.notes.find(handle)`. Many members mirror an `app.*` equivalent. → **[Full Note Interface index](./note-interface/index.md)**

| Category | Members |
|----------|---------|
| **Properties** | [name](./note-interface/name.md) · [tags](./note-interface/tags.md) |
| **Content** | [content](./note-interface/content.md) · [insertContent](./note-interface/insertContent.md) · [replaceContent](./note-interface/replaceContent.md) · [sections](./note-interface/sections.md) |
| **Tags** | [addTag](./note-interface/addTag.md) · [removeTag](./note-interface/removeTag.md) |
| **Tasks** | [tasks](./note-interface/tasks.md) · [insertTask](./note-interface/insertTask.md) |
| **Media** | [images](./note-interface/images.md) · [attachMedia](./note-interface/attachMedia.md) · [attachments](./note-interface/attachments.md) · [updateImage](./note-interface/updateImage.md) |
| **Backlinks** | [backlinks](./note-interface/backlinks.md) · [backlinkContents](./note-interface/backlinkContents.md) |
| **Publishing** | [publish](./note-interface/publish.md) · [publicURL](./note-interface/publicURL.md) |
| **Lifecycle / Metadata** | [setName](./note-interface/setName.md) · [url](./note-interface/url.md) · [delete](./note-interface/delete.md) |

---

## 5. Examples — `examples/`

Worked, end-to-end patterns. → **[Full Examples index](./examples/index.md)**

- [Task action via slash command](./examples/task-action-slash-command.md) — `appOption` + `check` scoped to task context
- [Parsing rich footnotes](./examples/parsing-rich-footnotes.md) — how images/links/connected tasks surface as markdown
- [External services & fetch](./examples/external-service-fetch.md) — `fetch()`, CORS, Cloudflare Worker proxy
- [LLM integration](./examples/llm-integration.md) — OpenAI / Gemini / Anthropic from a plugin
