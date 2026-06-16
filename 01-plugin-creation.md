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
