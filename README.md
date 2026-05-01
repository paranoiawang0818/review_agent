
# Review Agent System

A local Markdown-based personal review system powered by Claude Code subagents.

This project helps transform daily schedules, weekly plans, monthly summaries, and specific events into structured reviews with concrete next actions. It is designed to keep personal reflection aligned with a long-term academic and research direction: maintaining a high GPA while building AI/MLLM research ability, project experience, portfolio evidence, and competitiveness for QS Top 20 graduate applications in related fields.

## Overview

The Review Agent System is not a generic journal or note-taking template. It is a structured review workflow that uses specialized Claude Code subagents to analyze different types of reflection tasks.

The system supports four review modes:

- Daily Review
- Weekly Review
- Monthly Review
- Event Review

Each review mode has a dedicated subagent, input template, and output folder. Reviews are generated in Markdown format and saved locally.

## Core Purpose

The system is built around one central question:

> Are my actions actually helping me move closer to my long-term academic, research, and graduate application goals?

Instead of producing vague summaries or motivational comments, the system focuses on:

- identifying what actually happened;
- comparing actions against plans and priorities;
- detecting deviations from the main direction;
- separating high-value work from low-value busyness;
- converting reflection into concrete next actions.

## Long-Term Direction

The system is designed around the following long-term direction:

> As a student, I need to maintain a high GPA while building AI/MLLM research ability, project experience, portfolio evidence, and competitiveness for QS Top 20 graduate applications in related fields.

This direction is used as the main reference point when evaluating tasks, plans, progress, and trade-offs.

## Features

### 1. Daily Review

The daily review uses the KISS framework:

- Keep
- Improve
- Start
- Stop

It is used to analyze one day’s schedule, core tasks, completion status, problems, and useful behaviors.

The goal of the daily review is simple:

> Make tomorrow better than today.

Typical output includes:

- a factual summary of the day;
- key deviations from the daily plan;
- KISS analysis;
- a tomorrow action card;
- the most important reminder for the next day.

### 2. Weekly Review

The weekly review compares the original weekly plan with actual execution.

It focuses on:

- weekly plan completion;
- unfinished tasks;
- deviation causes;
- useful patterns;
- next week’s priorities.

The output organizes next week’s plan into:

- main-direction tasks;
- maintenance tasks;
- exploration tasks;
- tasks to pause or drop.

### 3. Monthly Review

The monthly review evaluates whether the month’s actions were aligned with the long-term direction.

It focuses on:

- academic performance;
- research learning;
- project or portfolio development;
- personal expression;
- life state;
- any custom monthly dimensions.

The monthly review helps decide:

- whether the month moved closer to the main direction;
- which investments were effective;
- which activities consumed time without enough long-term value;
- what the next month’s strategic focus should be.

### 4. Event Review

The event review is used for reviewing a specific matter, such as:

- an exam;
- a project;
- a competition;
- a communication issue;
- a delay or procrastination event;
- a content publishing attempt;
- a decision;
- a success or failure.

It analyzes:

- the original goal;
- the actual result;
- the gap between plan and execution;
- root causes;
- reusable lessons;
- next actions.

## Project Structure

```text
review-agent-system/
├── .claude/
│   └── agents/
│       ├── main-review-coordinator.md
│       ├── daily-review-agent.md
│       ├── weekly-review-agent.md
│       ├── monthly-review-agent.md
│       └── event-review-agent.md
│
├── docs/
│   ├── long-term-direction.md
│   ├── review-dimensions.md
│   └── review-rules.md
│
├── templates/
│   ├── daily-input.md
│   ├── weekly-input.md
│   ├── monthly-input.md
│   └── event-input.md
│
├── outputs/
│   ├── daily/
│   ├── weekly/
│   ├── monthly/
│   └── event/
│
├── CLAUDE.md
├── PLAN.md
└── README.md
````

## Subagents

### main-review-coordinator

The main coordinator routes the user’s input to the correct review agent.

It is responsible for:

* identifying the review type;
* selecting the correct subagent;
* checking whether the final output is specific and actionable;
* ensuring that every review stays aligned with the long-term direction.

### daily-review-agent

Handles daily reviews.

Main responsibilities:

* analyze the daily schedule;
* compare planned and completed tasks;
* apply the KISS framework;
* generate tomorrow’s action card.

### weekly-review-agent

Handles weekly reviews.

Main responsibilities:

* compare weekly plans with actual completion;
* identify key execution problems;
* extract useful patterns;
* create next week’s task list and priorities.

### monthly-review-agent

Handles monthly reviews.

Main responsibilities:

* evaluate monthly alignment with the long-term direction;
* analyze effective and low-value investments;
* identify capability changes;
* define next month’s strategic focus.

### event-review-agent

Handles specific event reviews.

Main responsibilities:

* analyze a specific event or task;
* judge whether the result was successful, partially successful, failed, or unclear;
* identify causes and lessons;
* generate concrete next actions.

## Output Rules

All review outputs should be written in Markdown.

Each saved review file should include YAML frontmatter:

```yaml
---
type: daily / weekly / monthly / event
date: YYYY-MM-DD
title: Review Title
main_direction: High GPA + AI/MLLM research development + QS Top 20 graduate application preparation
created_by: Claude Code Review Agent
---
```

Each review should include:

* clear headings;
* structured analysis;
* tables where useful;
* concrete action items;
* checkboxes for next steps.

Example action format:

```markdown
- [ ] Complete MTH008 9.2 revision
- [ ] Write one MLLM reading note
- [ ] Test the review agent with real daily data
```

## Output Folders

Reviews should be saved into the corresponding folders:

```text
outputs/daily/
outputs/weekly/
outputs/monthly/
outputs/event/
```

Recommended file naming rules:

```text
YYYY-MM-DD-daily-review.md
YYYY-WW-weekly-review.md
YYYY-MM-monthly-review.md
YYYY-MM-DD-event-event-name.md
```

Examples:

```text
outputs/daily/2026-05-01-daily-review.md
outputs/weekly/2026-W18-weekly-review.md
outputs/monthly/2026-05-monthly-review.md
outputs/event/2026-05-01-event-review-agent-system.md
```

## Input Templates

Input templates are stored in the `templates/` folder.

Use these templates when preparing review materials:

```text
templates/daily-input.md
templates/weekly-input.md
templates/monthly-input.md
templates/event-input.md
```

These templates help keep review inputs consistent and easier for Claude Code to process.

## How to Use

### 1. Open the project in VS Code

Open the project folder in VS Code with Claude Code enabled.

### 2. Choose a review type

Select one of the following review types:

* Daily Review
* Weekly Review
* Monthly Review
* Event Review

### 3. Fill in the corresponding input template

For example, for a daily review, use:

```text
templates/daily-input.md
```

Fill in your schedule, core tasks, actual completion, problems, useful behaviors, and next-day constraints.

### 4. Ask Claude Code to run the review

Example prompt:

```text
Please use daily-review-agent to generate a daily review based on the following input. Save the result as a Markdown file in outputs/daily/.
```

For weekly review:

```text
Please use weekly-review-agent to generate a weekly review based on the following weekly plan and actual completion. Save the result as a Markdown file in outputs/weekly/.
```

For monthly review:

```text
Please use monthly-review-agent to generate a monthly review and save the result in outputs/monthly/.
```

For event review:

```text
Please use event-review-agent to review this specific event and save the result in outputs/event/.
```

## Review Principles

The system follows these principles:

1. Reflection must serve action.
2. Every review must produce concrete next steps.
3. Plans should be reduced if they are overloaded.
4. Maintenance tasks should not be disguised as main-direction progress.
5. Difficult but high-value tasks should not be avoided.
6. Short-term failure should not be treated as a personal flaw.
7. Reviews should focus on systems, priorities, methods, and execution.
8. Empty encouragement should be avoided.
9. If information is insufficient, the agent should ask questions before reviewing.
10. The final output should help improve the next day, week, month, or similar event.

## Anti-Fluff Rules

The system should avoid vague advice such as:

* improve efficiency;
* stay focused;
* work harder;
* manage time better;
* keep learning;
* be more disciplined;
* adjust mindset.

These statements are only allowed when followed by a specific action, minimum completion standard, and checking time.

Bad example:

```text
Improve your MLLM learning efficiency.
```

Better example:

```text
Read one MLLM introductory article and write a 300-word note containing three key concepts, one confusion, and one possible demo idea before Friday 22:00.
```

## Privacy Note

The `outputs/` folder may contain personal schedules, reflections, failures, plans, and private information.

If this project is uploaded to a public GitHub repository, consider excluding real review outputs.

Recommended approach:

* keep the folder structure;
* avoid uploading real personal review files;
* use `.gitkeep` files if empty folders need to be preserved.

Example:

```text
outputs/daily/.gitkeep
outputs/weekly/.gitkeep
outputs/monthly/.gitkeep
outputs/event/.gitkeep
```

## Recommended Workflow

A practical workflow:

1. Fill in the appropriate input template.
2. Ask Claude Code to run the corresponding review agent.
3. Save the output into the correct folder.
4. Read only the action section first.
5. Move the next actions into the next day, week, or month plan.
6. Review whether previous action items were completed in the next cycle.

## Future Improvements

Possible future improvements include:

* connecting the system to Obsidian;
* adding weekly and monthly summary dashboards;
* creating review indexes;
* automatically linking daily reviews to weekly reviews;
* adding a project-progress tracking layer;
* integrating calendar or task-manager data;
* adding a lightweight web interface.

These improvements should only be added after the basic Markdown workflow is stable.

## Status

Current version:


Version: 1.0
Type: Local Markdown + Claude Code subagents
Status: Initial working structure


## License

This project is for personal learning, reflection, and productivity system design.

Add a license file if you plan to publish or share the project publicly.

```
```
