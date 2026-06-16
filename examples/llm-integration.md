# LLM Integration (OpenAI / Gemini / Anthropic)

> Part of [Examples](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/examples)

The **AmpleAI** plugin demonstrates calling large language models from OpenAI, Gemini,
and Anthropic. The same shape applies to all three providers — only the endpoint,
headers, request body, and API-key setting differ.

Key elements of the pattern:

- **API key from settings** — read the key from `app.settings["<Key Name>"]` so the user
  supplies their own credentials (configured via a `setting` row in the plugin metadata
  table).
- **Request body / model** — send the model name plus the messages, and (for structured
  output) a `response_format` such as `{ type: "json_object" }`.
- **Timeout via `Promise.race()`** — race the `fetch()` against a timer that rejects, so a
  hung request fails after `timeoutSeconds` instead of blocking forever.
- **Error handling** — check `fetchResponse.ok`; on failure throw an error that carries
  the response (and HTTP status) for the caller to inspect or retry.

```javascript
async function makeRequest(app, messages, model, {
  attemptNumber = 1,
  promptKey = null,
  stream = null,
  timeoutSeconds = 10
} = {}) {
  const apiKey = app.settings["OpenAI Key"];
  const body = { model: "gpt-5.2", messages: [...], response_format: { type: "json_object" }};
  const endpoint = "https://api.openai.com/v1/chat/completions";
  const headers = { "Content-Type": "application/json", "Authorization": `Bearer ${apiKey}` };

  const fetchResponse = await Promise.race([
    fetch(endpoint, { method: "POST", headers, body: JSON.stringify(body) }),
    new Promise((_, reject) =>
      setTimeout(() => reject(new Error('Timeout')), timeoutSeconds * 1000)
    )
  ]);

  if (!fetchResponse.ok) {
    const err = new Error(`Request failed with status ${fetchResponse.status}`);
    err.response = fetchResponse;
    throw err;
  }
  return fetchResponse;
}
```

To target **Gemini** or **Anthropic** instead, swap the endpoint, authentication header,
and body to match that provider's API (for example, Anthropic uses the
`https://api.anthropic.com/v1/messages` endpoint with an `x-api-key` header and an
`anthropic-version` header), while keeping the same `Promise.race()` timeout and
`fetchResponse.ok` error-handling structure shown above.

> Note: the `makeRequest` snippet is adapted from the AmpleAI example on the source page;
> the surrounding `messages` construction is abbreviated as `[...]` there.
