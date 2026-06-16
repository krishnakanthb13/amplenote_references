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

## Screenshots

![appOption — app-wide options invoked from the jump-to-note dialog](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/188f9755-da0e-470e-8d40-e111f45d1cdf.png)

![dailyJotOption — suggestion shown below today's daily jot](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/9da23331-2073-4ce7-8a01-0c515697142f.png)

![dailyJotOption — customized button text](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/d0d1f3ba-14bd-40cc-93c4-126473b31d01.png)

![imageOption — dropdown menu on a note image](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/99427c5b-e917-4372-b2e9-47d76ce75ae5.png)

![insertText — expression auto-complete menu](https://images.amplenote.com/2ae961e0-bc5d-11ed-808b-e21efa2d8566/011fd085-edee-4650-a24c-97278fcac158.png)

![insertText — custom keyword example](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/5001d613-ce83-4508-8040-e6bbba13ede1.png)

![linkOption — Rich Footnote popup button](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/deac9f00-e496-4420-a0b0-8397a29bc87b.png)

![linkTarget — plugin link triggered from note content](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/6aba51ee-90a7-436a-bdc1-214a8fb26af7.png)

![noteOption — per-note menu](https://images.amplenote.com/2ae961e0-bc5d-11ed-808b-e21efa2d8566/3ae0c6a7-1147-4453-afe9-303eb00613fb.png)

![renderEmbed — HTML embed rendered by a plugin](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/8dcb94e1-ca68-4c9f-af6e-a34708c1fb03.png)

![renderEmbed — embed with a button calling the host plugin](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/f2ff1507-0b95-436f-9fb1-3ec1d8e6667a.png)

![renderEmbed — prompt shown on embed button click](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/9cd1936e-5d0b-4732-ae88-aa309918ccdf.png)

![renderEmbed — result displayed after submission](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/3c9861e2-9fdf-4767-8220-1e36da4f2695.png)

![replaceText — text replacement selection menu](https://images.amplenote.com/2ae961e0-bc5d-11ed-808b-e21efa2d8566/06f99dcf-1a52-4093-9f7b-8ab762174e55.png)

![replaceText — custom keyword in the selection menu](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/9f580c1e-57f3-4ec5-b907-ff520f19f8de.png)

![suggestTaskTargetNotes — task target note suggestions](https://images.amplenote.com/4a2505be-dc5d-11f0-9fc3-f100570d5d30/8b4fe4b0-ae4a-40a0-b99f-0a1a2487298b.png)

![taskOption — task commands menu (typing !)](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/18f9018d-61d0-49fa-82cc-9abe417b377a.png)

![validateSettings — settings validation error message](https://images.amplenote.com/fae505fa-bd40-11ed-8e3b-9a67e5fef0db/eece4bf8-4a9b-4a7d-8982-bc562067fb11.png)
