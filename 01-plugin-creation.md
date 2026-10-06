# Plugin Creation

> [← API Reference Index](./00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/plugin_creation)

A plugin is an ordinary Amplenote note that contains two things:

1. A **metadata table** describing the plugin (its name, icon, description, and any
   user-configurable settings).
2. A **first code block** containing a single JavaScript object. The functions on that
   object — whose names match Amplenote **action** types — are the handlers the client
   invokes.

The client reads the note, parses the metadata table and the first code block, and
registers the plugin. The note updates the plugin dynamically as it changes.

## Metadata Table Fields

![Metadata table example](https://images.amplenote.com/2ae961e0-bc5d-11ed-808b-e21efa2d8566/c7582134-fdf7-431e-9f7d-85d8f73c01dd.png)

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | The name the user will see when invoking the plugin. |
| `icon` | No | A [Material Design Icon](https://pictogrammers.com/library/mdi/) identifier. Defaults to a generic extension icon if omitted. |
| `description` | No | A short description shown when installing or configuring the plugin. |
| `instructions` | No | More detailed information about using the plugin, surfaced for published plugins. |
| `setting` | No | A user-configurable string value. **Repeatable** — add one `setting` row per setting your plugin needs. |

## Code Block Structure

The first code block in the note is a JavaScript object. Each property whose name
matches an **action type** registers a handler for that action. There are three forms,
from simplest to most advanced.

### Single Action as a Function

The simplest plugin: one action implemented directly as a function. The function's
return value is used by the action (here, the text to insert).

```javascript
{
  insertText(app) {
    return "Hello World!"
  }
}
```

### Multiple Named Actions

A single action type can expose multiple named sub-actions. The user picks which named
variant to invoke; each name maps to its own function.

```javascript
{
  insertText: {
    "one word": function(app) {
      return "hello";
    },
    "two words": function(app) {
      return "hello world";
    }
  }
}
```

### Advanced `check` / `run` Form

Instead of a plain function, an action (or a named sub-action) can be an object with a
`check` and a `run` function. `check` decides whether the action should be offered/run
(return a truthy value to enable it, falsy to hide it); `run` performs the work. Both
receive the same arguments as the underlying action.

```javascript
{
  insertText: {
    check(app) {
      return true;
    },
    run(app) {
      return "Hello World!";
    }
  }
}
```

The `check`/`run` form can be mixed with named actions — each named variant may itself be
a plain function or a `check`/`run` object:

```javascript
{
  insertText: {
    "one word": {
      check(app) { return true; },
      run(app) { return "hello"; }
    },
    "two words": {
      check(app) { return true; },
      run(app) { return "hello world"; }
    }
  }
}
```

> Note: the source page shows the second variant written inline; the corrected,
> runnable form is the `check`/`run` object shown above.

## Settings, State, Async

### Settings

Each `setting` row in the metadata table is exposed to your code via
`app.settings["<Setting Name>"]`, keyed by the exact setting name. For example, with a
metadata entry `setting: API Key`:

```javascript
{
  insertText(app) {
    return app.settings["API Key"];
  }
}
```

### State Persistence

Properties on the plugin object are instantiated when the plugin is installed in the
client and retain their state until the plugin is reloaded. This lets a plugin keep
state across invocations:

```javascript
{
  insertText(app) {
    this._counter++;
    return "hello " + this._counter;
  },
  _counter: 0,
}
```

Inside action functions the plugin object is available as `this`, so you can call helper
methods defined on the same object:

```javascript
{
  insertText(app) {
    return this._text();
  },
  _text() {
    return "hello world";
  }
}
```

### Promises / async-await

Both `check` and `run` (and plain action functions) may return promises, so plugins can
perform asynchronous work. Either return a promise directly:

```javascript
{
  insertText: {
    check(app) {
      return new Promise(function(resolve) {
        setTimeout(resolve, 2000);
      }).then(function() {
        return true;
      });
    },
    run(app) {
      return new Promise(function(resolve) {
        setTimeout(resolve, 2000);
      }).then(function() {
        return "hello world, eventually";
      });
    }
  }
}
```

…or use `async` / `await`:

```javascript
{
  insertText: {
    async check(app) {
      await new Promise(function(resolve) { setTimeout(resolve, 2000); });
      return true;
    },
    async run(app) {
      await new Promise(function(resolve) { setTimeout(resolve, 2000); });
      return "hello world, eventually";
    }
  }
}
```

### Action Function Arguments

`app` is always the **first** argument passed to a plugin action function. Any
action-specific arguments follow it. For example, `replaceText` receives the selected
text as a second argument:

```javascript
{
  replaceText(app, text) {
    return text + " more";
  }
}
```

For the `check` / `run` form, both functions receive identical arguments to the
underlying action (so `check` sees the same `app` and action-specific parameters that
`run` will).

## Large plugins: keeping the payload out of the code block

The rule above doesn't change: the first code block in the note is still the plugin's actions, and that's still required. But if your plugin needs to ship a large payload — a compiled embed document, a client bundle, a big data file — you don't have to inline it into that code block. You can upload it as an attachment on the plugin note instead, and fetch it at render time.

**Why this matters:** a multi-hundred-KB code block makes the plugin note itself slow to open, in every client, for every user, whether or not the plugin is actually being used. Keeping the code block lean and shipping the bulk of the payload as an attachment avoids that cost.

> **Note:** this is a delivery mechanism for the payload your actions load, not a substitute for the actions themselves. The code block is still required, and it's still where your plugin's action functions live.

Here's the pattern, based on the published tldraw plugin and the official embed starter repo:

```javascript
async renderEmbed(app) {
  if (app.context.setEmbedHTML) {
    app.context.setEmbedHTML(`<!-- spinner markup -->`); // paint before awaiting the network
  }
  try {
    const attachments = await app.getNoteAttachments(app.context.pluginUUID);
    const attachment = attachments.find(attachment => attachment.name === "build.html.json");
    if (!attachment) throw new Error("build.html.json attachment not found");
    return this._getAttachmentContent(app, attachment.uuid);
  } catch (error) {
    return `<div><em>renderEmbed error:</em> ${ error.toString() }</div>`;
  }
},

async _getAttachmentContent(app, attachmentUUID) {
  const url = await app.getAttachmentURL(attachmentUUID);
  const proxyURL = new URL("https://plugins.amplenote.com/cors-proxy");
  proxyURL.searchParams.set("apiurl", url);
  const response = await fetch(proxyURL);
  return response.text();
}
```

`app.context.pluginUUID` is the plugin note's own UUID, so `getNoteAttachments` here lists attachments on the plugin note itself rather than some other note. See [`app.getNoteAttachments`](./app-interface/getNoteAttachments.md), [`app.getAttachmentURL`](./app-interface/getAttachmentURL.md), and [Appendix V: CORS proxy](./appendices/cors-proxy.md) for the full API.

**Two constraints worth knowing before choosing this approach:**
1. **Requires an online client.** `getAttachmentURL` mints a temporary URL and fails offline, so a plugin using this pattern can't render its payload offline — a plugin with a fully self-contained code block can.
2. **The attachment reference must stay in the note body.** `getNoteAttachments` only returns attachments that are still referenced in the note, so removing the visible link from the note body hides the file from this lookup even though the file itself remains uploaded.

Each render is also an extra network round trip, which is why the example above paints a loading state with `app.context.setEmbedHTML` before awaiting the fetch.

## Execution Environment

Plugin code runs in a **sandboxed iFrame** on web/desktop and in a **WebView** on
mobile. The sandbox runs your code as-is: **no polyfills or transpilation are applied**,
so use language and browser features supported by the host runtime (or load them
yourself). See [Execution environment](./appendices/execution-environment.md) for
details.

## Related references

- [Getting started](./guides/getting-started.md) — a step-by-step guide to writing your
  first plugin.
- [Execution environment](./appendices/execution-environment.md) — the sandboxed
  iFrame/WebView in which plugin code runs (no polyfills or transpilation applied).
- [External library loading](./appendices/external-libraries.md) — how to load
  third-party libraries from within a plugin.
- [Types](./appendices/types.md) — the type definitions used throughout the API.
