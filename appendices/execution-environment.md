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
