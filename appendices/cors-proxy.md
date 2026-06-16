# Appendix V: CORS Proxy

> Part of [Appendices](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/notes/25184228-4b24-11f1-b1cd-dff3f15bb702)

> **Note:** The source for this appendix is a shared Amplenote note that was not publicly fetchable at generation time (it returned HTTP 403). This page is a faithful stub describing the topic. Consult the [source note ↗](https://www.amplenote.com/notes/25184228-4b24-11f1-b1cd-dff3f15bb702) for the authoritative, complete content.

## What this covers

Plugin code runs inside the browser (see [Appendix II: Plugin code execution environment](./execution-environment.md)), so any `fetch` it makes is subject to the browser's CORS (Cross-Origin Resource Sharing) policy. Many third-party APIs do not send permissive CORS headers, so a direct browser request to them fails — the response is blocked even though the server received the request.

This appendix describes how to work around that by routing the request through a **CORS proxy** that you control — most commonly a small **Cloudflare Worker** (or similar edge/serverless function). The proxy receives your plugin's request, makes the actual call to the external API server-to-server (where CORS does not apply), and returns the response with the `Access-Control-Allow-Origin` headers the browser requires.

## The pattern, in brief

1. Deploy a small proxy (e.g. a Cloudflare Worker) at a URL you own.
2. The proxy forwards the incoming request to the target external API, attaching any required secrets/headers (which also keeps API keys out of the plugin code shipped to users).
3. The proxy responds with permissive CORS headers (e.g. `Access-Control-Allow-Origin: *`) so the browser accepts the response.
4. Your plugin `fetch`es the proxy URL instead of the external API directly.

## Related

- For a concrete walkthrough of calling an external service from a plugin (including the proxy approach), see [examples/external-service-fetch.md](../examples/external-service-fetch.md).
- For loading external *code* libraries (as opposed to fetching data), see [Appendix IV: Loading external libraries](./external-libraries.md).
