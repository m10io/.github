# GitHub agile rollout guide

This package gives you the shared files for an organization-wide agile issue setup on GitHub.

## What is in this package

- `.github/ISSUE_TEMPLATE/config.yml`
- `.github/ISSUE_TEMPLATE/epic.yml`
- `.github/ISSUE_TEMPLATE/story.yml`
- `.github/ISSUE_TEMPLATE/task.yml`
- `.github/ISSUE_TEMPLATE/bug.yml`
- `.github/ISSUE_TEMPLATE/subtask.yml`
- `CONTRIBUTING.md`
- `PULL_REQUEST_TEMPLATE.md`

## Recommended implementation order

1. Create or update the organization `.github` repository.
2. Add the issue forms and shared community-health files from this package.
3. Create the organization issue types.
4. Create the organization issue fields.
5. Pin the most relevant issue fields to each issue type.
6. Create the master organization Project.
7. Add the project views and automations.
8. Pilot with 2 to 3 repositories.
9. Roll out to the rest of the organization.

## 1. Create the shared `.github` repository

In your GitHub organization, create a repository literally named `.github` if you do not already have one.

Then copy these files into that repo:

- `.github/ISSUE_TEMPLATE/*`
- `CONTRIBUTING.md`
- `PULL_REQUEST_TEMPLATE.md`

GitHub will use these as default templates and default community health files for repositories that do not define their own local versions.

## 2. Create organization issue types

In GitHub:

- Open your organization
- Go to **Settings**
- Under **Planning**, open **Issue types**
- Ensure the following types exist and are enabled:
  - Epic
  - Story
  - Task
  - Bug
  - Sub-task

Notes:
- GitHub includes default issue types such as Task, Bug, and Feature.
- You can keep Feature disabled if you want to standardize on Story instead.
- If your organization does not yet have `Epic`, `Story`, or `Sub-task`, create them before you rely on the `type:` lines in the issue forms.

Suggested descriptions:
- **Epic** - Large initiative spanning multiple stories or tasks
- **Story** - User-centric slice of value
- **Task** - Concrete implementation or operational work item
- **Bug** - Defect or regression
- **Sub-task** - Broken-down actionable step under a parent item

## 3. Create organization issue fields

In GitHub:

- Open your organization
- Go to **Settings**
- Under **Planning**, open **Issue fields**
- Create or rename fields to the following set

Recommended fields:

### Single-select
- **Priority**: P0, P1, P2, P3
- **Effort**: XS, S, M, L, XL
- **Team**: create options for each team
- **Area**: Platform, API, Frontend, Data, Infra, Docs, Security, Compliance, Other
- **Customer impact**: None, Low, Medium, High
- **Risk**: Low, Medium, High
- **Quarter**: 2026-Q1, 2026-Q2, 2026-Q3, 2026-Q4, then extend each year

### Date
- **Target date**
- Optional: **Start date**

### Text
- Optional: **Blocked reason**

Notes:
- GitHub creates default issue fields for Priority, Effort, Start date, and Target date when issue fields are enabled.
- You can rename or customize them.

## 4. Pin fields to issue types

For each issue type, pin the most relevant fields.

Recommended field pinning:

### Epic
- Priority
- Team
- Area
- Quarter
- Target date
- Customer impact
- Risk

### Story
- Priority
- Team
- Area
- Effort
- Quarter
- Target date
- Customer impact

### Task
- Priority
- Team
- Area
- Effort
- Target date

### Bug
- Priority
- Team
- Area
- Target date
- Risk

### Sub-task
- Team
- Area
- Effort
- Target date

## 5. Set up labels

Use labels for cross-cutting signals, not for work-item type.

Recommended labels:
- `needs-triage`
- `state:blocked`
- `kind:tech-debt`
- `kind:security`
- `kind:compliance`
- `area:platform`
- `area:api`
- `area:frontend`
- `area:data`
- `area:infra`
- `area:docs`

Do not use labels like `epic`, `story`, `task`, or `bug` when you already have issue types.

## 6. Create the master organization Project

In GitHub:

- Go to your organization
- Open **Projects**
- Create a new organization Project called something like **Master Delivery Overview**

Add these fields to the project if they are not already available from issue fields:
- Status
- Type
- Priority
- Team
- Area
- Iteration
- Quarter
- Effort
- Target date
- Repository
- Parent issue
- Blocked reason
- Customer impact
- Risk

Recommended `Status` options:
- Backlog
- Ready
- In Progress
- Blocked
- In Review
- Done

Recommended `Iteration` cadence:
- 2 weeks for product/engineering teams, with breaks configured as needed

## 7. Create project views

Create these views in the master Project.

### Portfolio Board
- Layout: Board
- Group by: Status
- Filter: `type:Epic OR type:Story`

### Delivery Board
- Layout: Board
- Group by: Status
- Filter: `type:Story OR type:Task OR type:Bug OR type:"Sub-task"`

### Backlog Table
- Layout: Table
- Filter: `-status:Done`
- Sort: Priority ascending, Target date ascending

### Roadmap
- Layout: Roadmap
- Filter: `type:Epic OR type:Story`
- Date field: Target date

### Bugs
- Layout: Table or Board
- Filter: `type:Bug`

### Blocked Work
- Layout: Table
- Filter: `status:Blocked OR label:"state:blocked"`

## 8. Add project automation

In the master Project, configure built-in workflows as appropriate.

Recommended automations:
- Auto-add items from selected repositories
- Set `Status = Backlog` when an item is added
- Archive items automatically when closed or when `Status = Done`

If you want tighter control, only auto-add issues whose type is one of your five standard types.

## 9. Repository-level rollout rules

For each participating repository:

- Remove local issue templates unless the repo needs an exception
- Keep local templates only when a repo truly needs special intake
- Encourage linking all PRs to an issue
- Add repository items to the master Project automatically or through triage

## 10. Suggested governance rules

- Epics may contain Stories and Tasks
- Stories usually belong to an Epic
- Stories may contain Sub-tasks
- Bugs may contain Sub-tasks
- Sub-tasks must have a parent
- Avoid nesting deeper than 3 levels

## 11. Pilot plan

Pilot in 2 to 3 repos first.

Suggested pilot checks:
- Are teams choosing the correct work item type?
- Are the forms collecting the right amount of detail?
- Do the project views feel useful without being noisy?
- Are hierarchy links being maintained consistently?
- Are labels and issue fields duplicating each other anywhere?

## 12. Known caveats

- Issue forms and issue fields are documented by GitHub as public preview features and may change.
- If a custom issue form fails validation, compare it against GitHub's issue form syntax docs and remove any unsupported keys.
- If the `type:` value in a form does not work in your org, first confirm the organization issue type exists with the exact intended name.

## 13. Rollout checklist

- [ ] `.github` repository created or updated
- [ ] Shared issue forms committed
- [ ] CONTRIBUTING and PR template committed
- [ ] Organization issue types created
- [ ] Organization issue fields created
- [ ] Fields pinned to issue types
- [ ] Master Project created
- [ ] Project views created
- [ ] Built-in automations configured
- [ ] Pilot repos onboarded
- [ ] Org-wide rollout completed
