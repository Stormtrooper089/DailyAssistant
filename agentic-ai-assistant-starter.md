# Agentic AI Assistant Starter

## Goal

Build a personal agentic AI assistant that helps with daily work by capturing tasks, clarifying intent, planning next actions, and executing safe workflows with user approval.

## First MVP

The first version should be a local daily-task copilot with four practical abilities:

1. Capture tasks from quick natural-language notes.
2. Turn vague requests into concrete next actions.
3. Maintain a prioritized daily plan.
4. Draft or execute simple follow-ups, with approval before external actions.

Example requests:

- "Remind me to send the invoice tomorrow."
- "Plan my day around these three meetings."
- "Summarize what I need to do from this note."
- "Draft a reply to this email."
- "Break this project into next actions."

## Agent Loop

The assistant should follow a small, predictable loop:

1. Understand the user request.
2. Decide whether it needs clarification, planning, memory lookup, or tool use.
3. Produce a short plan.
4. Execute safe local actions automatically.
5. Ask for approval before sending messages, changing calendars, spending money, deleting data, or contacting other services.
6. Record the result and any follow-up tasks.

## Suggested Components

- Chat interface: the main place the user talks to the assistant.
- Task store: simple local database or JSON file at first.
- Memory layer: preferences, recurring responsibilities, people, projects, and routines.
- Planner: converts goals into ordered steps.
- Tool registry: calendar, email, files, browser, reminders, and notes can be added one at a time.
- Approval system: explicit confirmations for risky actions.

## Data Model

Core entities:

- Task: title, status, priority, due date, project, source, notes.
- Project: name, outcome, status, related tasks.
- Person: name, relationship, contact context.
- Reminder: time, recurrence, message, linked task.
- Daily plan: date, commitments, focus blocks, carry-over tasks.

## Safety Rules

- Never send, delete, purchase, publish, or schedule externally without approval.
- Show the intended action before taking irreversible steps.
- Keep a local audit log of tool actions.
- Prefer asking one clear question over guessing when ambiguity changes the outcome.

## Build Milestones

### Milestone 1: Local Task Brain

- Chat-style CLI or lightweight web app.
- Add, list, update, and complete tasks.
- Parse due dates and priorities from natural language.
- Generate a daily plan from stored tasks.

### Milestone 2: Useful Agent Behavior

- Add task decomposition.
- Add clarification questions.
- Add memory for user preferences and routines.
- Add an action log.

### Milestone 3: Integrations

- Calendar read/write with approval.
- Email draft creation.
- File and note search.
- Browser-assisted research.

### Milestone 4: Proactive Assistance

- Morning planning prompt.
- End-of-day review.
- Follow-up detection.
- Recurring reminders and routines.

## Recommended First Build

Start with a small local web app:

- Frontend: task/chat interface.
- Backend: agent endpoint plus task APIs.
- Storage: SQLite.
- Model integration: one LLM call for intent parsing/planning, with deterministic local task operations.

The first satisfying demo should let the user type:

> I need to call Rahul tomorrow, finish the expense report by Friday, and block 2 hours for the AI assistant project.

The assistant should extract tasks, ask any needed clarifying question, save the tasks, and produce a daily plan.

## Immediate Next Decision

Choose the first interface:

1. CLI assistant: fastest to build and easy to iterate.
2. Local web app: better daily usability.
3. Mobile-first prototype: best long-term daily habit, slower to build.

Recommended: start with the local web app.
