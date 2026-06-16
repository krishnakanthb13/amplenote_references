# External Services & fetch

> Part of [Examples](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/examples)

Plugins run client-side and can call external services using the standard `fetch()` API.

```javascript
{
  async insertText(app) {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    return data.value;
  }
}
```

## CORS Restrictions

Because plugin code runs in the browser, network requests are subject to **CORS**. If the
external service does not return permissive CORS headers, the browser will block the
request. For services you do not control, Amplenote suggests signing up for Cloudflare and
setting up a **Cloudflare Worker** to act as a proxy: the plugin calls your Worker (which
returns the appropriate CORS headers), and the Worker forwards the request to the target
API.

```
Plugin (browser)  ──▶  Cloudflare Worker (adds CORS headers)  ──▶  Target API
```

## Reporting Progress on Long-Running Operations

For operations that take a while, use `app.openEmbed()` to write your progress to an
ephemeral section that is available to users on desktop or mobile. This gives the user
visible feedback while the plugin works, instead of leaving the UI appearing frozen.

```javascript
{
  async run(app) {
    await app.openEmbed("Working… 0%");
    // … perform long-running work, updating progress as you go …
    await app.openEmbed("Working… 100% — done");
  }
}
```
