# Appendix IV: Loading external libraries

> Part of [Appendices](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/developing_amplenote_plugins/appendix_iv)

Because plugin code runs in a sandboxed context (see [Appendix II: Plugin code execution environment](./execution-environment.md)), there is no module bundler and no package manager available at runtime. To use a third-party library, you load it into the sandbox yourself at runtime. There are two common patterns.

> The plugin execution context is kept loaded, so a dependency does not need to be loaded on every call to the plugin — only on the first call. Cache the loaded library (for example on `window` or on your plugin object) and reuse it on subsequent invocations.

## Pattern 1: Append a `<script>` tag (browser builds)

For libraries that ship a browser build, you can dynamically append a `<script>` element. Once it loads, the library is available on the global `window` object. This example loads [RecordRTC](https://github.com/muaz-khan/RecordRTC):

```javascript
async _loadRecordRTC() {
  // Reuse the already-loaded library on subsequent calls.
  if (window.RecordRTC) return window.RecordRTC;

  await new Promise((resolve, reject) => {
    const script = document.createElement("script");
    script.src = "https://cdn.jsdelivr.net/npm/recordrtc@5.6.2/RecordRTC.min.js";
    script.onload = resolve;
    script.onerror = reject;
    document.head.appendChild(script);
  });

  // The library has now attached itself to the global scope.
  return window.RecordRTC;
}
```

Usage:

```javascript
const RecordRTC = await this._loadRecordRTC();
const recorder = new RecordRTC(stream, { type: "audio" });
```

## Pattern 2: Fetch and evaluate a UMD module

Dependencies that define a UMD (Universal Module Definition) build can be loaded with a small code shim: fetch the module's source text, then evaluate it inside a module context using the `Function` constructor, and return its exports.

```javascript
async _loadUmdModule(url) {
  // Fetch the raw source of the UMD build.
  const response = await fetch(url);
  const source = await response.text();

  // Provide a CommonJS-style module context for the UMD wrapper to populate.
  const module = { exports: {} };
  const factory = new Function("module", "exports", source);
  factory(module, module.exports);

  // Return whatever the UMD build assigned to module.exports.
  return module.exports;
}
```

Usage:

```javascript
const someLib = await this._loadUmdModule("https://cdn.jsdelivr.net/npm/some-lib/dist/some-lib.umd.js");
```

Both approaches let a sandboxed plugin pull in third-party libraries that are not otherwise available in the host application environment. For fetching data (rather than code) from external services that block browser CORS, see [Appendix V: CORS Proxy](./cors-proxy.md).
