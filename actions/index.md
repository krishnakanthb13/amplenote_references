# Amplenote Plugin Actions

> [← API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

Actions are the entry points that define how a plugin's code gets called. Each action registers a handler in the plugin object, and the **function name in the plugin object must exactly match the action type** (e.g. an `insertText` action is registered as a function named `insertText`). Every action receives the [App Interface](../app-interface/index.md) object as its first argument, and may return a value directly or as a `Promise`.

Many actions also support an optional `check` function. Define the action as an object with both `check` and `run` properties: `check` receives the same arguments as `run` and runs first to decide whether (and how) the action is shown. Returning a falsy value (`false`, `null`, empty string) hides the action; returning a non-empty string can be used to customize the displayed label or keyword for actions that support it.

## Text Insertion / Replacement
- [`insertText`](./insertText.md) — Insert text in place of an `{expression}` in a note or title.
- [`replaceText`](./replaceText.md) — Replace highlighted text, invoked from the selection menu.

## Menu Options
- [`noteOption`](./noteOption.md) — Add options to the per-note menu when editing a note.
- [`appOption`](./appOption.md) — Add app-wide options invokable from "jump to note" / quick search.
- [`dailyJotOption`](./dailyJotOption.md) — Add a suggestion with a run button below today's daily jot.
- [`taskOption`](./taskOption.md) — Add options to the task commands menu (typing `!` in a task).
- [`eventOption`](./eventOption.md) — Add an option to the calendar event (task/scheduled bullet) popup.
- [`imageOption`](./imageOption.md) — Add an option to the drop-down menu on each image.
- [`linkOption`](./linkOption.md) — Add a button to the Rich Footnote popup for a link.
- [`linkTarget`](./linkTarget.md) — Handle clicks on a plugin link (`plugin://<plugin UUID>`).

## Lifecycle & Navigation
- [`onNavigate`](./onNavigate.md) — Called when the user changes locations in the app.
- [`onNoteCreated`](./onNoteCreated.md) — Called when a note is created on the current client.

## Embeds
- [`renderEmbed`](./renderEmbed.md) — Return HTML to render in an isolated embed iFrame.
- [`onEmbedCall`](./onEmbedCall.md) — Handle `window.callAmplenotePlugin` calls from an embed.

## Plugin Communication
- [`onPluginCall`](./onPluginCall.md) — Handle calls from another plugin via `app.callPlugin`.

## Tasks
- [`suggestTaskTargetNotes`](./suggestTaskTargetNotes.md) — Suggest an ordered set of notes a task could be added to.

## Settings
- [`validateSettings`](./validateSettings.md) — Validate plugin settings when they are saved.
