# Things User Story Design

## Goal

Restructure the user's Things projects so that each project uses one primary user-story heading as the organizing frame for its actions.

## Decision

The previous workflow-phase model (`Refine`, `Plan`, `Voer uit`, `Afronden`) is removed.

The new model is:

- `Area` = stable life/work domain
- `Project` = concrete outcome or work container
- `Heading` = one primary user story
- `Tasks` = concrete actions under that user story

## User Story Rule

Each project should usually have one primary user story in this form:

`Als Ernst wil ik [gewenste situatie] zodat ik [waarde/resultaat] heb.`

This story should describe the human need or desired end state, not a process step.

Bad example:

- `Als Ernst wil ik de beste verbouwoptie kiezen zodat ik geen verkeerde investering doe.`

Better example:

- `Als Ernst wil ik een rustige werkplek in de garage hebben zodat ik gefocust kan werken en ongestoord kan bellen.`

## Structure Rules

- Keep project titles short and scan-friendly.
- Keep only one primary user-story heading per project unless there is a clear second human need.
- Keep tasks action-oriented under the story heading.
- Preserve project notes, tags, area, and schedule state where possible.

## Migration Strategy

Because Things does not reliably support inserting headings into existing projects through the available automation path, migrate by replacement:

1. Create a new project with the same title, area, notes, tags, and schedule state.
2. Create a single user-story heading in that new project.
3. Move the old project's tasks under that heading.
4. Cancel the old project.
5. Keep the replacement project under the original title.

## Safety Rules

- Do not delete projects permanently.
- Preserve all open tasks.
- Use conservative user-story wording derived from project title, notes, and tasks.
- If intent is weak, still prefer one simple user story over reusing workflow phases.

## Verification

Success means:

- every visible project has exactly one heading
- that heading is a user story
- the project's existing tasks sit under that heading
- no temporary replacement project names remain
