# `note.sections`

> Part of [Note Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/note_interface)

**Type:** Method
**Category:** Content

## Description
Gets the sections in the note. See `app.getNoteSections` for more details.

## Signature
`note.sections()`

## Parameters
None.

## Returns
`Promise<section[]>` — an array of section objects describing the note's heading-delimited sections.

## Equivalent `app` method
`app.getNoteSections(noteHandle)`

## Example
```javascript
const sections = await note.sections();
app.alert(`Note has ${sections.length} sections.`);
```

## Related
- [`note.content`](./content.md)
- [`note.replaceContent`](./replaceContent.md)
