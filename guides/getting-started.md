# Guide to Getting Started Writing Plugins

> Part of [Guides](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/guide_to_developing_amplenote_plugins)

This guide walks through getting started writing Amplenote plugins — from editing code directly inside a note, through installing/testing and debugging, up to an IDE-based development workflow, learning from example plugins, and letting AI help author plugin code.

---

## 🐣 The Beginner's Path: Write and Edit Basic Code in the Note

Amplenote supports plugin development directly through a note that contains a code block. As the guide puts it, **plugins are just a normal note, with a code block in a specific format.** You don't need any external tooling to get started — you can write and iterate on plugin code right inside Amplenote.

There are three ways to start.

### Starting option: Copy a working example

The recommended starting point is to **duplicate the Example AI plugin**. If you have Amplecap installed, visit the published plugin note and choose **"Duplicate note"** to copy it into your own account, then start editing.

![Duplicate note option in Amplenote](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/bd3c348e-bf39-4cd9-8eb8-701ce2891540.png)

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

![Add plugin selection list in Settings](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/81fc498e-e2ab-4281-a2fc-ee8499cbce28.png)

![Plugin settings gear icon](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/91599d8e-703d-4865-b7b1-241aa9c9c641.png)

![Active (green) plugin icon indicator](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/97d25a35-9042-4995-b75b-b5c2edc64661.png)

![Red plugin compilation error icon](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/aa3011fc-875f-40a9-b23b-ba48e3c25117.png)

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

![Red plugin compilation error indicator](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/5750d8a6-93e6-406c-81a1-6b74e93bd976.png)

![Accessing DevTools via the browser View menu](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/16d5b882-d944-4fb2-87b8-f4a4a966839c.png)

![DevTools Console error output](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/291e1f7c-9eb6-4fb6-9803-af3f71a4bb46.png)

![Note version history access menu](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/cb2932c9-92c6-4f9c-8ebc-2bf5cb6bc3db.png)

![Missing comma syntax error example](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/dae6b674-9143-4ea5-8a66-77048978c620.png)

---

## 🤓 Intermediate-to-Advanced Plugin Development

### Getting started: the example repo

For IDE-based development, use the **Amplenote Plugin Template repository**. It lets you create test files such as `plugin.test.js` that mock the `plugin` and `app` objects so you can exercise your code outside of Amplenote.

![IDE syntax error highlighting](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/f7c28bee-2cbf-4a0d-bcd6-7c9d1d8363da.png)

![Plugin test file example in an IDE](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/9556ee86-e888-43e9-bf57-0303bc86ed08.png)

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

![Readwise plugin table results](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/14d3df44-5320-4592-865b-59a4d20c4794.png)

---

## 🤖 Let AI Write Your Plugin Code

Using **phind.com** with GPT-4 lets you reference Amplenote's plugin API documentation directly while generating code. Tips:

- Enable the **"expert"** toggle for GPT-4.
- Open **"Advanced"** mode and paste the plugin docs URL so the model can reference it:

  ```
  https://www.amplenote.com/help/developing_amplenote_plugins
  ```

- Identify the target **action** you need — typically `insertText`, `noteOption`, or `replaceText`.

![Phind.com AI code generation interface](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/b5b81595-4d8d-4fc6-8fd3-09400161d585.png)

![Phind-generated rhyming plugin output](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/9e5405e8-eb76-41dc-a085-6f15840bbe01.png)

### Example: building the Note2PDF plugin

The guide describes building **Note2PDF** primarily through AI assistance. The workflow:

1. Initial query: *"Example convert markdown text to download PDF in Javascript"*
2. First follow-up: *"Rewrite … to use libraries … loaded by browser dynamically, by fetching scripts from a CDN"*
3. Second iteration: replaced the `marked` library when it failed.
4. Third iteration: replaced the `pdfkit` library with `js2pdf` when errors occurred.

**Debugging approach:** the developer used the Chrome Web Inspector to identify library errors, added `console.log` statements to inspect returned objects, and verified each conversion step worked (markdown → HTML → PDF → download) before consulting the Plugin API documentation for the final download implementation.

> Note: in the source page, the Note2PDF `console.log` debugging steps are shown via screenshots rather than reproduced as verbatim text, so the exact inspection code is not transcribed here.

![Phind follow-up question interface](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/50a1c807-c14d-4f75-9389-37a1383ed9aa.png)

![First version of Note2PDF plugin code generated by AI](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/fb4858b5-b953-4697-bbc6-9973f058b7fb.png)

![Plugin code methods structure](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/2484108f-07cf-498c-a2f1-79bf94a83fe9.png)

![Testing the plugin in Chrome Inspector](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/8341d764-8cc1-44f1-977a-619c5b3f81be.png)

![JavaScript errors shown in Chrome Inspector](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/97033a72-fcf1-4136-ade2-966b318eac9a.png)

![Viewing console.log output in the Console tab](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/869e1257-e2d0-4102-a420-156603be757c.png)

![Viewing JavaScript variables revealed by console.log](https://images.amplenote.com/b456a2e4-d93b-11ed-b6ce-f2e3384d8128/3055bd72-c48a-4246-a65a-6768de65fc81.png)
