# ISSUES_README

This repository uses a shared issue workflow based on **GitHub Issues** and a **master GitHub Project** (.github).

The goal is to make work easy to understand across teams and repositories, while still keeping day-to-day execution close to the code.

This document explains how developers and project managers should use the workflow.

## Overview

We use five issue types:

- **Epic** – a large body of work or initiative
- **Story** – a user-centric feature or outcome
- **Task** – a concrete technical or operational work item
- **Bug** – a defect or regression
- **Sub-task** – a smaller actionable step under another issue

Issues are typically created in the repository where the work belongs, then added to the shared Project for planning, tracking, and rollup.

## Core principles

1. **Create issues in the repo where the work lives**
   - If the work belongs to a specific codebase, create the issue in that repo.
   - Use the shared Project to manage prioritization and visibility across repos.

2. **Use the correct issue type**
   - Do not use Tasks for Bugs.
   - Do not use Stories for large multi-part initiatives.
   - Do not use Sub-tasks as standalone planning items.

3. **Keep hierarchy shallow**
   - Prefer:
     - Epic → Story → Sub-task
     - Epic → Task
     - Bug → Sub-task
   - Avoid deep nesting unless absolutely necessary.

4. **Use the Project for workflow state**
   - The Project is the source of truth for execution status and planning views.
   - The issue body is the source of truth for the work description and acceptance details.

## Issue type definitions

### Epic

Use an **Epic** for a large initiative, outcome area, or major body of work.

Examples:
- Introduce SSO across all internal tools
- Migrate service platform to a new cloud architecture
- Launch customer self-service onboarding

An Epic should usually:
- span multiple Stories and/or Tasks
- represent meaningful business or product value
- live for more than a few days
- provide context and goals, not implementation details

Use an Epic when the work is too large to deliver as a single Story or Task.

### Story

Use a **Story** for a user-centric feature or outcome.

A Story should answer:
- who needs something
- what they need
- why it matters

Typical format:
> As a \<user/persona\>, I want \<capability\>, so that \<value/outcome\>.

Examples:
- As an admin, I want to assign roles to users so that access can be managed without engineering support.
- As a customer, I want to reset my password so that I can regain access without contacting support.

A Story should usually:
- belong to an Epic
- include acceptance criteria
- be deliverable in a reasonable time window
- focus on user value, not low-level implementation

### Task

Use a **Task** for concrete work that is not best framed as a Story.

Examples:
- Add audit logging for role changes
- Upgrade dependency set for auth service
- Write deployment runbook
- Add CI validation for issue templates

A Task is appropriate for:
- engineering work
- operations work
- documentation work
- architecture work
- maintenance work

Tasks may belong to an Epic directly, or support a Story.

### Bug

Use a **Bug** for a defect, regression, broken behavior, or mismatch between expected and actual behavior.

Examples:
- Password reset link expires immediately after creation
- Role assignment silently fails for some users
- UI displays duplicate records after refresh

A Bug should include:
- expected behavior
- actual behavior
- steps to reproduce
- severity
- environment details if relevant

Use a Bug only for defects. Do not use Bug for feature requests or cleanup work.

### Sub-task

Use a **Sub-task** for a smaller actionable step under another issue.

Examples:
- Add backend validation for role payload
- Update user settings page copy
- Write regression test for permission inheritance
- Verify deployment in staging

A Sub-task should:
- have a clear parent issue
- be small and actionable
- help break down a Story, Task, or Bug into manageable pieces

Do not create standalone Sub-tasks unless there is a temporary workflow reason to do so.

## Recommended hierarchy

Use these patterns:

- **Epic**
  - Story
    - Sub-task
    - Sub-task
  - Story
    - Sub-task
  - Task

- **Bug**
  - Sub-task

Preferred rules:
- Stories should usually belong to an Epic.
- Sub-tasks should always have a parent.
- Tasks can belong to an Epic or stand on their own if the work is small and well-scoped.
- Bugs can be standalone or linked to a Story/Epic if relevant.

## Where to create issues

Create issues in the repository where the work belongs.

After creating the issue:
1. assign the correct issue type
2. add it to the shared Project
3. populate the required Project fields

## Required Project fields

Every active work item should have the relevant Project fields set.

Typical fields include:

- **Status**
- **Priority**
- **Team**
- **Area**
- **Effort**
- **Quarter**
- **Customer impact**
- **Risk**
- **Target date**
- **Iteration**
- **Blocked reason** when blocked

At a minimum, items that are being worked on should have:
- **Status**
- **Priority**
- **Team**

## Status workflow
Use the following statuses consistently.

### Backlog
The issue is captured but not ready to start.

### Ready
The issue has enough detail and can be picked up.

### In Progress
Work is actively underway.

### Blocked
Work cannot continue because of a dependency, decision, access problem, or other blocker.

When using **Blocked**, add a clear **Blocked reason**.

### In Review
Implementation is complete and is awaiting review, validation, QA, or approval.

### Done
The work is complete and accepted.


## How developers should use this workflow

### 1. Create work in the right repo

When you identify work:
- create the issue in the relevant repository
- choose the right issue form
- fill in the required fields clearly

### 2. Use the right level of detail

- Use **Story** for user-facing outcomes
- Use **Task** for concrete engineering or operational work
- Use **Bug** for broken behavior
- Use **Sub-task** to break a larger issue into smaller steps

### 3. Keep issues actionable

A good issue should make it obvious:
- what needs to be done
- how success will be judged
- whether dependencies exist
- who owns it

### 4. Update status as work moves

Do not leave items in outdated statuses.

Move items through the workflow:
- Backlog → Ready → In Progress → In Review → Done

Use **Blocked** when necessary, and explain why.

### 5. Link related work

Developers should maintain issue relationships where helpful:
- Stories under Epics
- Sub-tasks under Stories, Tasks, or Bugs
- Bugs linked to related work if they affect a larger initiative

### 6. Keep issue bodies useful

Issue bodies should contain enduring context:
- problem statement
- acceptance criteria
- repro steps
- dependencies
- key technical notes

Avoid burying important information only in comments.

## How project managers should use this workflow

### 1. Use Epics for planning and rollup

Project managers should use **Epics** to represent larger initiatives and group related work.

An Epic should communicate:
- the goal
- business value
- scope
- dependencies
- success measures

### 2. Drive execution through Stories and Tasks

Break Epics into:
- **Stories** for user-centric deliverables
- **Tasks** for concrete implementation or support work

### 3. Use the master Project as the portfolio view

The Project is the main place to:
- review progress across repositories
- prioritize work
- identify blocked items
- manage roadmap visibility
- inspect bugs across teams

### 4. Keep field values current

Project managers should ensure key fields are maintained, especially:
- Status
- Priority
- Team
- Target date
- Quarter
- Risk
- Customer impact

### 5. Use views intentionally

Use different Project views for different purposes, for example:

- **Portfolio Board** – high-level tracking of Epics and Stories
- **Delivery Board** – execution tracking for Stories, Tasks, Bugs, and Sub-tasks
- **Backlog Table** – prioritization and grooming
- **Roadmap** – time-based planning for major work
- **Bugs view** – defect review and triage
- **Blocked view** – issue escalation and unblock management

### 6. Do not overload issue types

Project managers should avoid:
- using Epic for every large task
- writing Stories that are really implementation tasks
- tracking defects as Tasks just to fit a plan

Good classification improves reporting and planning.

## Triage guidance

When a new issue is created, ask:

### Is it a large initiative with multiple parts?
Use **Epic**.

### Is it a user-facing feature or outcome?
Use **Story**.

### Is it concrete work that is mainly technical, operational, or documentation-related?
Use **Task**.

### Is something broken?
Use **Bug**.

### Is it a smaller step under another issue?
Use **Sub-task**.

## Suggested working agreements

These are the recommended working rules for the team:

- Every Story should usually belong to an Epic.
- Every Sub-task should have a parent.
- Every Bug should include repro steps or clearly state why they are unknown.
- Every item in active execution should have Status, Priority, and Team filled in.
- Every blocked item should include a Blocked reason.
- Every issue should be understandable without needing a meeting to decode it.

## Common mistakes to avoid

### Using Tasks instead of Stories
If the work is fundamentally about user value, use a Story.

### Using Stories for technical chores
If the item is engineering work without a direct user-centric framing, use a Task.

### Creating vague Epics
An Epic should describe the initiative clearly, not just act as a bucket with no purpose.

### Leaving issues unclassified
Type, Status, and ownership should be clear.

### Using Sub-tasks as standalone planning items
Sub-tasks are meant to support parent issues.

### Letting the Project drift from reality
The Project is only useful if statuses and fields are updated regularly.

## Example workflow

### Example 1: Feature delivery

- Create **Epic**: Introduce self-service user administration
- Create **Story**: As an admin, I want to assign roles to users so that access can be managed without engineering support
- Create **Sub-tasks**:
  - Add backend endpoint for role assignment
  - Add frontend admin UI
  - Add audit logging
  - Add tests

Track all of them in the Project and update Status as work progresses.

### Example 2: Technical work

- Create **Task**: Add structured logging for auth failures
- Add to Project
- Assign Team, Priority, and Status
- Move from Ready to In Progress to Done

### Example 3: Defect handling

- Create **Bug**: Password reset link fails after redirect
- Add repro steps and severity
- Add to Project
- If needed, create Sub-tasks:
  - Identify root cause
  - Add regression test
  - Verify fix in staging

## Practical usage summary

### Developers
- create issues in the correct repo
- use the correct issue type
- keep issue content actionable
- update Status as work moves
- use Sub-tasks to break down larger work

### Project managers
- organize work through Epics and Stories
- maintain prioritization and rollup in the Project
- keep fields current
- use views for planning, tracking, and escalation
- ensure issue quality is high enough for execution

## Final note

This workflow is meant to improve clarity, prioritization, and visibility across repositories.

Keep it simple:
- create the right issue type
- put it in the right repo
- add it to the Project
- keep the fields and status current
- use hierarchy to clarify work, not complicate it