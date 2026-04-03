# Contributing and issue intake

This organization uses a shared agile issue model across repositories.

## Work item types

- **Epic** - a large body of work spanning multiple stories or tasks
- **Story** - a user-centric slice of value
- **Task** - a concrete implementation, operational, architecture, or documentation item
- **Bug** - a defect or regression
- **Sub-task** - a broken-down actionable step under a parent item

## Operating rules

1. Use the issue form that matches the work item type.
2. Every active item should have an owner, priority, and status.
3. Stories should normally belong to an Epic.
4. Sub-tasks must always have a parent item.
5. Bugs should include repro steps unless they are genuinely unknown.
6. Keep hierarchies shallow. Prefer Epic -> Story -> Sub-task, or Epic -> Task.

## Kanban statuses

- **Backlog** - captured but not yet ready to pull
- **Ready** - refined and ready for execution
- **In Progress** - actively being worked
- **Blocked** - cannot proceed due to a dependency or decision
- **In Review** - implementation complete and awaiting validation
- **Done** - accepted and complete

## Definition of ready

An item is Ready when:
- the work item type is correct
- the value or objective is clear
- the acceptance criteria or done criteria are clear enough to execute
- dependencies are identified
- the owning team is known

## Definition of done

An item is Done when:
- the agreed acceptance criteria or done criteria are met
- required tests are complete
- documentation is updated if needed
- downstream validation or review is complete
