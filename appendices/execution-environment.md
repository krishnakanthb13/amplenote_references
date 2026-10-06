# Appendix II: Plugin code execution environment

> Part of [Appendices](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/developing_amplenote_plugins/appendix_ii)

This appendix describes the technical environment in which Amplenote plugin code runs.

## Sandboxed execution

Plugin code is executed inside a sandboxed iframe, which prevents the plugin from directly accessing the outer page or the host application. On mobile devices, plugins run in isolated WebViews, with separation maintained between each plugin instance.

This isolation architecture exists so that a plugin cannot interfere with the main application or with other plugins.

## Runtime

The execution environment is the user's browser when running on the web, or the system WebView when running on mobile.

> **No polyfills or processing.** There are no polyfills applied within the plugin code sandbox, nor is any processing (transpilation, bundling, minification, etc.) performed on plugin code before it runs. The code you provide is the code that executes.

## Implications for plugin authors

- You are responsible for browser compatibility. Because no compatibility layer or code transformation is applied, you must write code that runs directly in the target browser/WebView, or include your own polyfills.
- The plugin execution context is kept loaded between calls, so any state or dependencies you set up (for example, a library loaded into the sandbox) persist across subsequent invocations of the plugin rather than being re-initialized on every call. See [Appendix IV: Loading external libraries](./external-libraries.md).
- Code running in this sandbox doesn't have to originate entirely from the note's code block: a plugin can fetch additional payload (an embed document, a compiled bundle) from an attachment on its own note at render time. See [Large plugins: keeping the payload out of the code block](../01-plugin-creation.md#large-plugins-keeping-the-payload-out-of-the-code-block).

## Embed environment

Embeds operate in further separated iFrames, with additional functions defined on `window`:

### `window.callAmplenotePlugin`
Calls the [`onEmbedCall`](../actions/onEmbedCall.md) action in the host plugin, passing the arguments provided to `callAmplenotePlugin`. Returns a Promise that resolves to whatever is returned by the plugin's `onEmbedCall` function, or `undefined` if nothing is returned.

```javascript
// Inside the embed iframe HTML/JS
const result = await window.callAmplenotePlugin("getCustomData", { id: 123 });
```

### `window.setAmplenoteEmbedHeight`
Sets a pixel-based height for the embed iframe. This overrides the aspect-ratio based height, keeping the iframe at 100% width and this fixed pixel height. Can be called repeatedly, and must be called with a number greater than zero.

```javascript
// Resize embed iframe dynamically to fit content
window.setAmplenoteEmbedHeight(document.body.scrollHeight);
```

## Related
- [`renderEmbed`](../actions/renderEmbed.md)
- [`onEmbedCall`](../actions/onEmbedCall.md)
- [`app.openEmbed`](../app-interface/openEmbed.md)
- [`app.openSidebarEmbed`](../app-interface/openSidebarEmbed.md)
- [`app.context.setEmbedHTML`](../app-interface/context.md#appcontextsetembedhtml)
- [`app.context.closeEmbed`](../app-interface/context.md#appcontextcloseembed)
- [`app.context.getStyleProperties`](../app-interface/context.md#appcontextgetstyleproperties)

