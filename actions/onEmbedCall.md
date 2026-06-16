# `onEmbedCall`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Embeds

## Description
Called when code running in an embed that was rendered by this plugin calls `window.callAmplenotePlugin`. This is the host-side handler that responds to messages sent from the embed's isolated iFrame, enabling two-way communication between the embed and the plugin.

## Signature
`onEmbedCall(app, ...args)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `...args` — Any arguments passed to `window.callAmplenotePlugin` from within the embed.

## Returns
Any JavaScript value serializable as JSON. The value is returned to the calling code inside the embed (as the resolved value of the `window.callAmplenotePlugin` promise).

## The `check` function
The `check` function is not used for this action.

## Example
```javascript
onEmbedCall(app, ...args) {
  console.log("onembedcall", args)
  return 42;
}
```

Complete embed interaction (the embed calls back into the host, which prompts the user and returns the result):

```javascript
{
  renderEmbed(app, ...args) {
    return `
      <b>hello</b> from a plugin <button>call host</button>
      <script type="text/javascript">
      var button = document.querySelector("button");
      button.addEventListener("click", function() {
        window.callAmplenotePlugin().then(result => {
          button.textContent = "Got: " + result;
        })
      });
      </script>
    `;
  },
  async onEmbedCall(app, ...args) {
    return await app.prompt("enter something");
  }
}
```

## Types & references
- `...args` and the return value are any JSON-serializable values; takes no API object types.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md) — registering the action.

## Related
- [renderEmbed](./renderEmbed.md)
