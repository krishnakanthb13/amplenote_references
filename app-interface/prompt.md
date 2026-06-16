# `app.prompt`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Dialogs

## Description
Show the user a message and input fields — defaulting to a single text input — receiving the user-selected/user-entered value(s). Similar to `app.alert`, except that this allows options to be presented in a dialog.

## Signature
`app.prompt(message: string, options?: object) → Promise<string | Array | null>`

## Parameters
- `message` (`string`) — the message, with `\n` for new lines
- `options` (`object`, optional):
  - `inputs` (`array`) — input objects with properties:
    - `type` — one of `"checkbox"`, `"date"`, `"note"`, `"radio"`, `"secureText"`, `"select"`, `"string"`, `"tags"`, `"text"`
    - `label` (`string`) — label for the input
    - `placeholder` (`string`) — placeholder (for text)
    - `value` — initial value
    - `options` (`array`) — `{ label, value }` entries (for select/radio)
    - `image` (`string`) — URL (radio only)
    - `limit` (`number`) — (tags only)
  - `actions` (`array`) — action objects with `icon`, `label`, `value`
  - `primaryAction` (`object`) — object with `icon`, `label`

## Returns
`Promise<string | Array | null>` — the user-entered value(s), action result, or `null` if canceled. When multiple inputs (and/or actions) are present, the result is an array in input order, with the selected action value appended last.

## Example
```javascript
async noteOption(app, noteUUID) {
  const result = await app.prompt("This is the message", {
    inputs: [
      { label: "This is the label", placeholder: "placeholder", type: "text" },
      { label: "This is the label", type: "checkbox" },
      { label: "This is the label", type: "select",
        options: [ { label: "something", value: 1 }, { label: "other", value: 2 } ] },
      { label: "This is the label", type: "radio",
        options: [ { label: "something", value: 1 }, { label: "other", value: 2 } ] },
    ]
  });
  if (result) {
    const [ textResult, checkboxResult, selectResult ] = result;
  } else {
    // User canceled
  }
}
```

## Related
- [`app.alert`](./alert.md)
