# Plugin API Markdown Reference

> Part of [Guides](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/plugin_api_markdown_reference_parse_markdown)

This reference explains how Amplenote markdown works for plugins — the markdown that flows in and out of the Plugin API when you read or write note content.

---

## Where this markdown is used

The Plugin API exchanges note content as markdown through several methods. You receive markdown from, and pass markdown to, methods including:

- `app.getNoteContent`
- `app.getNoteSections`
- `app.insertTask`
- `app.replaceNoteContent`
- `app.updateTask`

…plus the equivalent members on the Note Interface (`note.content`, `note.insertContent`, `note.replaceContent`, etc.).

## Markdown standard

> "Amplenote markdown support follows the [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)."

On top of GFM, Amplenote layers a set of **HTML-comment annotations** (`<!-- {...} -->`) that carry extra properties — colors, task metadata, cell widths, collapse state, and so on. The patterns below show those extensions.

---

## Colored Text and Colored Backgrounds

Colors are expressed on `==highlighted text==` elements, with an HTML-comment annotation that specifies a color index.

**Text (foreground) color** — `cycleColor`:

```
==Red text<!-- {"cycleColor": "23"} -->==
```

**Background color (with a foreground color)** — `backgroundCycleColor` plus `cycleColor`:

```
==green background<!-- {"backgroundCycleColor": "37","cycleColor":"0" } -->==
```

**Combined with other formatting** (e.g. bold), wrap the highlight in the usual markdown emphasis markers:

```
**==bold blue on golden background<!-- {"backgroundCycleColor":"25","cycleColor":"29"} -->==**
```

**Critical spacing rule:** highlight formatting will *not* be applied if there are any spaces between the end of the opening `==` block and the text itself. Keep the text flush against the `==`.

### Color index charts

The source page provides color-index charts for both **light mode** and **dark mode**, documenting **60 supported colors** for text and 60 for backgrounds, each mapped to an index number used in `cycleColor` / `backgroundCycleColor`. In the source, these name-to-index mappings are presented only as images, so the full numeric table is not transcribable here — refer to the [source page ↗](https://www.amplenote.com/help/plugin_api_markdown_reference_parse_markdown) for the exact index for each color.

---

## Plain Highlights

A plain highlight (no color annotation) uses the standard double-equals syntax:

```
==highlighted text==
```

The same spacing rule applies: no space between `==` and the text.

---

## Working with Tasks

You can read and write task data by setting **task properties as HTML comments** on a checkbox list item. Properties include `uuid`, `completedAt`, `startAt`, `hideUntil`, `victoryValue`, and more.

```
- [x] Completed task <!-- {"uuid": ${uuidv4()}, "completedAt": ${Date.now()}, "victoryValue": 1} -->
```

- `- [ ]` is an open task; `- [x]` is a completed task.
- The HTML comment carries the structured task metadata. (The `${uuidv4()}` / `${Date.now()}` shown above are template placeholders from the source — substitute real values such as a generated UUID and a Unix timestamp.)

---

## Inserting a Rich Footnote

Rich Footnotes use standard markdown footnote syntax. The footnote reference sits inline; the footnote body (which may contain a link description and/or an image) is defined separately.

```
[Rich Footnote on a new line after bold bullet title][^1]

[^1]: [Rich Footnote description text]()

![](image-url)
```

- `[label][^1]` places the footnote reference inline.
- `[^1]: ...` defines the footnote body, which can include a link (`[text](url)`) and an image (`![](image-url)`).

---

## Inserting a Markdown Table

Tables use standard GFM table syntax. Per-cell properties (such as column width) are attached with an HTML comment inside the cell.

```
|name|Bullet Journal<!-- {"cell":{"colwidth":350}} -->|
|icon|thermostat<!-- {"cell":{"colwidth":350}} -->|
```

- `{"cell":{"colwidth":350}}` sets that cell/column's width.

A fuller GFM table also includes the header separator row, e.g.:

```
| Column |
|--------|
| Content<!-- {"cell":{"colwidth":350}} --> |
```

---

## Images

Images use standard markdown image syntax:

```
![](image-url)
```

Images also appear inside Rich Footnote bodies (see above). Alt text goes inside the brackets: `![alt text](image-url)`.

---

## Links

Links use standard markdown link syntax:

```
[link text](url)
```

Links also appear inside Rich Footnote descriptions, e.g. `[Rich Footnote description text]()`.

---

## Code

Inline code and fenced code blocks follow standard GFM:

> *Illustrative (standard GFM, shown for completeness):*

```
Inline `code` uses single backticks.

```language
fenced code blocks use triple backticks
```
```

---

## Line Breaks in Markdown

Extra vertical spacing is produced with backslashes on otherwise-empty lines between blocks of text:

```
Two blank lines follow:

\\

\\

And then text resumes
```

Each `\` on its own line inserts an additional blank line of spacing.

---

## Collapsing Headings

A heading can be marked as collapsed with a `collapsed` HTML-comment annotation:

```
# Heading 1 <!-- {"collapsed": true} -->
```

When `"collapsed": true` is present, the section under that heading is rendered collapsed.
