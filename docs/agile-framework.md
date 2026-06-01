# Agile Framework

## Overview

Each project in this portfolio is delivered using a lightweight
Agile framework modeled on professional software and data operations
delivery. The goal is not to add overhead to learning — the goal is
to build disciplined habits in planning, delivery, testing,
documentation, review, and continuous improvement.

These habits map directly to the work expected in a Python Developer
/ Data Operations Analyst role: prioritization, SLAs, operational
controls, stakeholder communication, issue escalation, auditability,
UAT, parallel runs, sign-offs, and process improvement.

---

## Sprint structure

Each project spans one or two one-week sprints.

| Activity | When | What to produce |
|----------|------|----------------|
| Sprint planning | Start of sprint (Monday) | Sprint goal, selected Issues, branch created |
| Daily coding | Tuesday–Thursday | Feature implementation, tests, docs updates |
| Git day | Friday | Commit, push, open pull request |
| Sprint review | Saturday | Test outputs, review notes, README updated |
| Retrospective | Sunday | Improvement notes, carry-over items |

---

## Definition of Ready

A backlog item is ready to start when:

- [ ] The goal is clear
- [ ] The input data is known
- [ ] The expected output is defined
- [ ] The required libraries and tools are identified
- [ ] The task is small enough to complete within the sprint
- [ ] Any assumptions or constraints are documented
- [ ] The business value is clear
- [ ] Acceptance criteria are written

Do not start a task that does not meet the Definition of Ready.
Clarify first, then start.

---

## Definition of Done

A task is done when:

- [ ] The code works as expected
- [ ] The code is readable and maintainable
- [ ] Tests pass
- [ ] Errors are handled clearly with descriptive messages
- [ ] Logging is added where useful
- [ ] The README or documentation is updated
- [ ] Only synthetic data is used
- [ ] No secrets or credentials are committed
- [ ] The change is committed to Git with a clear message
- [ ] A pull request is created and reviewed against this checklist
- [ ] A short review note is written
- [ ] The work satisfies the acceptance criteria

Do not merge a pull request unless every item is checked.

---

## User story format

As a [role], I want [capability], so that [business value].

### Example

As a data operations analyst, I want to validate incoming synthetic
loan files, so that missing fields, duplicate loan IDs, and invalid
records can be identified before downstream processing.

---

## Acceptance criteria format

The task is complete when:

- The expected input is defined
- The expected output is defined
- The code runs successfully
- The feature handles common edge cases
- Tests are included where appropriate
- Logs or error messages are clear
- Documentation is updated
- The work is committed to Git
- The README explains the feature clearly
- No real data or secrets are used

---

## Kanban board columns

| Column | Meaning |
|--------|---------|
| Backlog | All project ideas and user stories not yet started |
| Ready | Items that meet the Definition of Ready and are selected for this sprint |
| In Progress | Currently being coded on a feature branch |
| Review | Pull request is open; checking against Definition of Done |
| Done | Merged, documented, README updated, Issues closed |

---

## GitHub Issues format

### Issue title

Use a clear, action-oriented title:

- Add CSV ingestion with pandas
- Implement duplicate loan ID detection
- Write pytest tests for validation functions
- Generate exception report as Excel output

### Issue body template

```
## User story
As a [role], I want [capability], so that [business value].

## Acceptance criteria
- [ ] ...
- [ ] ...
- [ ] ...

## Definition of Ready
- [ ] Goal is clear
- [ ] Input and output are defined
- [ ] Libraries are identified
- [ ] Task fits within the sprint

## Notes and assumptions
...
```

---

## Sprint planning template

```
## Sprint [N] — [Project Name]

**Sprint goal:** [One sentence — what will be working by end of sprint]
**Dates:** [Start date] to [End date]
**Branch:** feature/[branch-name]

### Selected backlog items
| Issue | Summary | Story points |
|-------|---------|-------------|
| #1    | ...     | 3           |
| #2    | ...     | 2           |

### Acceptance criteria for this sprint
The sprint is complete when:
- [ ] ...
- [ ] ...

### Technical task breakdown
- [ ] Create feature branch
- [ ] Implement [feature]
- [ ] Write tests
- [ ] Update README
- [ ] Open pull request
```

---

## Sprint review template

```
## Sprint [N] Review — [Project Name]

**Date:** [Date]
**Sprint goal achieved:** Yes / Partial / No

### What was completed
- [Feature / deliverable]

### What was NOT completed and why
- [Item] — [reason]

### Demo notes
- [What you ran, what the output showed]

### Metrics
- Tests passing: [count]
- PR merged: Yes / No
- README updated: Yes / No

### Stakeholder update (plain language)
[2–3 sentences as if explaining to a non-technical manager]
```

---

## Sprint retrospective template

```
## Sprint [N] Retrospective — [Project Name]

**Date:** [Date]

### What went well
- ...

### What could be improved
- ...

### What I will do differently next sprint
- ...

### Learning highlight
- ...

### Carry-over items
- ...
```

---

## Sprint review questions

Use these to evaluate each project before closing the sprint:

1. Did the sprint goal get achieved? If not, why?
2. Did the code pass all tests?
3. Is the README clear enough for someone new to understand and run the project?
4. Was error handling thorough — did I think about edge cases?
5. Is the logging useful — would it help me debug a failure at 3 AM?
6. Is the output auditable — can a reviewer trace how each result was produced?
7. Did I commit with clear messages that explain what changed and why?
8. Did I use only synthetic data and avoid committing any secrets?
9. Can I explain every function in plain language to a non-technical stakeholder?
10. What is the one thing I would do differently if I built this again?

---

## Sprint retrospective questions

Use these to reflect and improve after each sprint:

1. What habit did I build this sprint that I want to keep?
2. What slowed me down the most — and how can I prevent it next sprint?
3. Did I write tests before or after the code — and which felt better?
4. Was my sprint goal realistic, or did I over- or under-commit?
5. Did I update the README as I went, or leave it to the end?
6. What is one thing I learned that surprised me?
7. If a colleague had to pick up this project tomorrow with no help from me, could they?
