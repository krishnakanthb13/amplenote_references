# `app.getTaskDomains`

> Part of [App Interface](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/app_interface)

**Category:** Tasks

## Description
Get the list of configured Task Domains for the user.

## Signature
`app.getTaskDomains() → Promise<taskDomain[]>`

## Parameters
None.

## Returns
`Promise<taskDomain[]>` — array of task domain objects, each containing:
- `name` (`string`) — display name
- `notes` (`noteHandle[]`) — noteHandles in the Task Domain
- `uuid` (`string`) — identifier

## Example
```javascript
appOption: async function(app) {
  const taskDomains = await app.getTaskDomains();
  const descriptions = taskDomains.map(({ name, notes }) => {
    return `${ name } - ${ notes.length } notes`;
  });
  app.alert(descriptions.join("\n"));
}
```

## Related
- [`app.getTaskDomainTasks`](./getTaskDomainTasks.md)
- [`app.addTaskDomainNote`](./addTaskDomainNote.md)
