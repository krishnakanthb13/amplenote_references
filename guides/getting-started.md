# Guide to Getting Started Writing Plugins

> Part of [Guides](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/guide_to_developing_amplenote_plugins)

This guide walks through getting started writing Amplenote plugins — from editing code directly inside a note, through installing/testing and debugging, up to an IDE-based development workflow, learning from example plugins, and letting AI help author plugin code.

---

## 🐣 The Beginner's Path: Write and Edit Basic Code in the Note

Amplenote supports plugin development directly through a note that contains a code block. As the guide puts it, **plugins are just a normal note, with a code block in a specific format.** You don't need any external tooling to get started — you can write and iterate on plugin code right inside Amplenote.

There are three ways to start.

### Starting option: Copy a working example

The recommended starting point is to **duplicate the Example AI plugin**. If you have Amplecap installed, visit the published plugin note and choose **"Duplicate note"** to copy it into your own account, then start editing.

### Starting option: Use the embed repo

If you want to render React components or arbitrary JavaScript, you can **fork the `amplenote-embed-starter` project** to leverage Amplenote's embedding framework.

### Starting option: From scratch

Any note can become a plugin as long as it contains **a table and a code block that validly define a plugin.** The minimal requirement is a configuration/metadata table plus a JavaScript code block below it.

> Reference note linked from this section: `https://public.amplenote.com/bz3BbmEWyVevW6LDDuPJDHBJ`

---

## Iterating on Your Plugin

Once your note defines a plugin, install and test it:

1. Visit **Settings → Plugins**.
2. Search for and select your plugin note from the list.
3. Click **"Add Plugin"**.
4. If the plugin has settings, click the **gear icon** to configure them.

The plugin icon appears **green when the plugin is valid** and **red when compilation fails**. As you edit the note, re-checking the icon color is the fastest way to know whether your latest change still compiles.

---

## Something Is Broken — How Do I Debug This?

### Problem: the plugin isn't doing what you want

Three debugging techniques are recommended:

- **Use `console.log`** to inspect values, then view results in the browser's Developer / Inspector tools. For example:

  ```javascript
  console.log("The app interface is", app, "as of", new Date())
  ```

- **Invoke `debugger`** inside your code to pause execution with full context so you can inspect state in DevTools.

- **Wrap risky code in `try...catch`** so failures surface as readable errors instead of silently breaking:

  ```javascript
  try { dodgyCode() } catch(error) { alert("There was an error attempting to call dodgyCode: " + error); console.log(error); console.trace(); }
  ```

### Problem: the plugin won't compile

A **red plugin icon** indicates a compilation error. Ways to track it down:

- **Undo until working:** press `Ctrl-Z` repeatedly to return to the last working state.
- **Check the DevTools Console:** open it via the browser's View menu to read the error message.
- **Paste into an IDE:** drop the code into Visual Studio Code (or similar) to spot syntax errors.
- **Check version history:** compare the current note version against a past working version.
- **Look for missing commas:** the single most common error is a missing comma between methods in the plugin's JavaScript object.

---

## 🤓 Intermediate-to-Advanced Plugin Development

### Getting started: the example repo

For IDE-based development, use the **Amplenote Plugin Template repository**. It lets you create test files such as `plugin.test.js` that mock the `plugin` and `app` objects so you can exercise your code outside of Amplenote.

### Running tests with breakpoints

IDEs like **WebStorm** let you set breakpoints inside your tests, so you can inspect plugin state during execution.

### Moving back to Amplenote

Use the **"Github → Amplenote plugin"** tooling to automatically bundle source files from a GitHub repository into a note's code block — eliminating manual copy-pasting when you're ready to ship from your repo back into Amplenote.

---

## 🧑‍🏫 Learn by Example

The guide highlights several example plugins, each demonstrating key patterns:

- **AI Plugin** — Calls OpenAI's API with configurable settings for GPT-3.5 or GPT-4; presents 10 radio options (e.g. for rhyming words); implements timeout and retry logic.
- **Readwise Plugin** — Calls a third-party REST API with rate limiting; progressively builds table rows across multiple invocations; formats JSON objects into note sections.
- **Image Generation Plugin** — Uses images as radio selection options; uploads the chosen image to Amplenote's servers; grabs note content preceding the cursor position.
- **Thesaurus Plugin** — Renders 10 selections as radio inputs with a "show 10 more" option; makes simpler OpenAI calls than the AI plugin.
- **Amplequery Plugin** — Queries all available notes; filters and displays results in tables; converts Markdown tables to JavaScript dictionaries.

---

## 🤖 Let AI Write Your Plugin Code

Using **phind.com** with GPT-4 lets you reference Amplenote's plugin API documentation directly while generating code. Tips:

- Enable the **"expert"** toggle for GPT-4.
- Open **"Advanced"** mode and paste the plugin docs URL so the model can reference it:

  ```
  https://www.amplenote.com/help/developing_amplenote_plugins
  ```

- Identify the target **action** you need — typically `insertText`, `noteOption`, or `replaceText`.

### Example: building the Note2PDF plugin

The guide describes building **Note2PDF** primarily through AI assistance. The workflow:

1. Initial query: *"Example convert markdown text to download PDF in Javascript"*
2. First follow-up: *"Rewrite … to use libraries … loaded by browser dynamically, by fetching scripts from a CDN"*
3. Second iteration: replaced the `marked` library when it failed.
4. Third iteration: replaced the `pdfkit` library with `js2pdf` when errors occurred.

**Debugging approach:** the developer used the Chrome Web Inspector to identify library errors, added `console.log` statements to inspect returned objects, and verified each conversion step worked (markdown → HTML → PDF → download) before consulting the Plugin API documentation for the final download implementation.

> Note: in the source page, the Note2PDF `console.log` debugging steps are shown via screenshots rather than reproduced as verbatim text, so the exact inspection code is not transcribed here.
