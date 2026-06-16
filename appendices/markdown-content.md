# Appendix III: Markdown content

> Part of [Appendices](./index.md) · [API Reference Index](../00-index.md) | [Source ↗](https://www.amplenote.com/help/developing_amplenote_plugins/appendix_iii)

This appendix describes the markdown that plugins exchange with the Amplenote app.

## Baseline: GitHub Flavored Markdown

Markdown support in the plugin API generally follows the [GitHub Flavored Markdown](https://github.github.com/gfm/) specification. Standard GFM constructs — headings, lists, tables, code blocks, links, emphasis, task list items, and so on — are supported.

## Current limitations

> As of July 2024, the markdown that plugins can pass to the app is somewhat limited relative to the full set of features available in the Amplenote editor. The platform plans to expand this support over time to cover additional Amplenote-specific features.

In practice this means some rich Amplenote editor features may not yet be expressible (or fully round-trippable) through plugin-supplied markdown, even though they exist in the app's own editing surface.

## Amplenote markdown features

Beyond the GFM baseline, the dedicated Plugin API Markdown reference page covers Amplenote-specific formatting, including:

- Applying foreground and background color to text.
- Creating Rich Footnotes.
- Tables.
- Other Amplenote formatting features.

For the authoritative and most current details of supported markdown, consult the dedicated Plugin API Markdown reference page in the Amplenote help documentation.
