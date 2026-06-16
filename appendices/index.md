# Amplenote Plugin API — Appendices

> [← API Reference Index](../00-index.md)

Lower-level technical references for the plugin API.

1. [Appendix I: Types](./types.md) — structured object types exchanged with the API (`attachment`, `externalCalendarEvent`, `image`, `link`, `moodRating`, `noteHandle`, `section`, `tag`, `task`), each with a properties table.
2. [Appendix II: Plugin code execution environment](./execution-environment.md) — the sandboxed iframe/WebView runtime, browser compatibility, and the no-polyfills/no-processing model.
3. [Appendix III: Markdown content](./markdown-content.md) — the GitHub Flavored Markdown baseline, Amplenote-specific formatting, and current limitations on plugin-supplied markdown.
4. [Appendix IV: Loading external libraries](./external-libraries.md) — loading third-party code at runtime via the `<script>`-append pattern (RecordRTC) and the UMD fetch-and-eval helper.
5. [Appendix V: CORS Proxy](./cors-proxy.md) — using a CORS proxy / Cloudflare Worker to call external APIs that block browser CORS.
