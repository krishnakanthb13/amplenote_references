# `suggestScheduledTasks`

> Part of [Actions](./index.md) · [API Reference Index](../00-index.md) | [Source &#8599;](https://www.amplenote.com/help/developing_amplenote_plugins/actions)

**Category:** Tasks

## Description
Propose scheduling for one or more tasks, which the user can accept or dismiss on a per-task basis. [`app.context.setScheduledTasks`](../app-interface/context.md#appcontextsetscheduledtasks) is defined when this action is invoked to allow progressive display of suggestions.

## Signature
`async suggestScheduledTasks(app, { endAt, schedulableTasks, scheduledTasks, startAt, taskDomain })`

## Parameters
- `app` — App Interface object. See [App Interface](../app-interface/index.md).
- `arguments` (`Object`) in the shape of:
  - `endAt` (`Integer`) — Unix timestamp (seconds) representing the last day currently being shown by the calendar view.
  - `schedulableTasks` (`Array` of [task](../appendices/types.md#task)) — Array of `task` objects representing the tasks in the current task domain that are not scheduled, or are overdue.
  - `scheduledTasks` (`Array` of [task](../appendices/types.md#task)) — Array of `task` objects representing the tasks in the current task domain that are scheduled in the currently shown calendar view.
  - `startAt` (`Integer`) — Unix timestamp (seconds) representing the first day currently being shown by the calendar view.
  - `taskDomain` ([taskDomain](../appendices/types.md#taskdomain)) — The `taskDomain` object representing the currently selected task domain.

## Returns
`Array` of suggested task schedule objects, each with the following properties:
- `endAt` (`Integer`, optional) — Unix timestamp (seconds) describing the suggested end time for the task (controlling duration).
- `explanation` (`String`, optional) — Description explaining why the scheduling is being suggested for this task.
- `startAt` (`Integer`, required) — Unix timestamp (seconds) describing the suggested start time for the task.
- `task` ([task](../appendices/types.md#task), optional) — Represents a *new* task that should be scheduled. Ignored if `taskUUID` is provided. The `task` object must contain at least a valid `noteUUID` attribute indicating the target note to add the task to. The user will not be informed if the target note is not in the current task domain (in which case adding the task may not show it on the calendar view, depending on user settings).
- `taskUUID` (`String`, optional) — UUID string describing an *existing* task that should be scheduled.

## The `check` function
Standard check behavior — return falsy to skip suggesting. The check function receives the same `(app, { endAt, schedulableTasks, scheduledTasks, startAt, taskDomain })` arguments as `run`.

## Example
```javascript
{
  async suggestScheduledTasks(app, { startAt, schedulableTasks }) {
    const schedulableTask = schedulableTasks[0];
    if (!schedulableTask) return [];

    return [
      { explanation: "Very basic scheduling", startAt, taskUUID: schedulableTask.uuid },
    ];
  }
}
```

## Progressive Suggestions with `app.context.setScheduledTasks`
If the calculation of suggested tasks is slow (e.g., waiting on an LLM inference call), call `app.context.setScheduledTasks` to display progressive suggestions to the user immediately:

```javascript
{
  async suggestScheduledTasks(app, { startAt, schedulableTasks }) {
    const schedulableTask = schedulableTasks[0];
    if (!schedulableTask) return [];

    const scheduledTasks = [
      { explanation: "Initial quick schedule", startAt, taskUUID: schedulableTask.uuid }
    ];

    await app.context.setScheduledTasks(scheduledTasks);
    // Continue computing additional suggestions...
    return scheduledTasks;
  }
}
```

## Types & references
- [task](../appendices/types.md#task) — shape of task objects in `schedulableTasks`, `scheduledTasks`, and the return schedule.
- [taskDomain](../appendices/types.md#taskdomain) — shape of `taskDomain`.
- [`app.context.setScheduledTasks`](../app-interface/context.md#appcontextsetscheduledtasks) — context method available during this action.
- [Actions index](./index.md)
- [Plugin Creation](../01-plugin-creation.md)

## Related
- [suggestTaskTargetNotes](./suggestTaskTargetNotes.md)
- [eventOption](./eventOption.md)
- [taskOption](./taskOption.md)
- [Calendar Task Suggestions help guide](../../amplenote_help_docs/04-calendars-scheduling/calendar_auto_suggest_goal_aligned_tasks.md)
