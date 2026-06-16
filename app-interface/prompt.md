# `app.prompt`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Dialogs

## Description
Show the user a message and input fields — defaulting to a single text input — receiving the user-selected/user-entered value(s). Similar to `app.alert`, except that this allows options to be presented in a dialog.

## Signature
`app.prompt(message: string, options?: object) → Promise<string | Array | null>`

## Parameters
- `message` (`String`) — the message, with `\n` for new lines
- `options` (`Object`, optional):
  - `inputs` (`Array<Object>`) — input objects with properties:
    - `type` (`String`) — one of `"checkbox"`, `"date"`, `"note"`, `"radio"`, `"secureText"`, `"select"`, `"string"`, `"tags"`, `"text"`
    - `label` (`String`) — label for the input
    - `placeholder` (`String`) — placeholder (for text)
    - `value` (any) — initial value
    - `options` (`Array<Object>`) — `{ label, value }` entries (for select/radio)
    - `image` (`String`) — URL (radio only)
    - `limit` (`Integer`) — (tags only)
  - `actions` (`Array<Object>`) — action objects with `icon` (`String`), `label` (`String`), `value` (any)
  - `primaryAction` (`Object`) — object with `icon` (`String`), `label` (`String`)

## Returns
`Promise<String | Array | null>` — the user-entered value(s), action result, or `null` if canceled. A single input with no actions resolves to that input's value; when multiple inputs (and/or actions) are present, the result is an `Array` in input order, with the selected action's `value` appended last. A `"note"` input resolves to a [`noteHandle`](../appendices/types.md#notehandle).

## Types & references
- [`noteHandle`](../appendices/types.md#notehandle) — value returned by a `"note"` input
- [App Interface index](./index.md)

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
