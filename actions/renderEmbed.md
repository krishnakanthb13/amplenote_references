# `renderEmbed`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Embeds

## Description
Called when an embed assigned to the plugin needs to render HTML. Embeds are HTML documents loaded in an isolated iFrame. The HTML returned by this action is loaded into that iFrame.

## Signature
`renderEmbed(app, ...args)`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `...args` — Additional arguments from `app.openSidebarEmbed` or inline embed parameters.

## Returns
`String` — the HTML to load in the embed.

## The `check` function
Standard check behavior — return falsy to make the embed unavailable. The check function receives the same `(app, ...args)` arguments as `run`.

## Example
```javascript
renderEmbed(app, ...args) {
  return "<b>hello</b> from a plugin";
}
```

Complete embed interaction example (embed that calls back into the host via `window.callAmplenotePlugin`):

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

## Related
- [onEmbedCall](./onEmbedCall.md)
