# Things Restructure Design

## Goal

Restructure the user's live Things database into a clearer Dutch-language system with:

- action-oriented task titles
- stable area names
- result-oriented project names
- fewer orphaned items
- weak, duplicate, or bookmark-like items moved to Trash instead of deleted

## Scope

In scope:

- rename task titles using title + notes context
- rename project and area titles into clearer Dutch
- create new projects and areas where the current structure is too weak
- move tasks between projects/areas when intent is clear
- move low-value or duplicate items to Trash

Out of scope:

- editing completed/logbook items
- changing deadlines or schedule dates unless required by a move
- rewriting note bodies
- permanent deletion

## Constraints

- Prefer minimal semantic change.
- Do not invent intent when title and notes are still ambiguous.
- Use Trash as the safety net for anything removed from the active system.
- Keep genuine single actions outside projects only when a project would be artificial.

## Design Principles

### Areas

Areas should represent stable life domains in Dutch, not temporary contexts or catch-all buckets.

Target shape:

- Wonen
- Werk en inkomen
- Gezondheid
- Administratie
- Relaties
- Aankopen
- Producten en AI
- Reflectie en notities (only if needed)

### Projects

Projects should represent concrete outcomes, ongoing themes, or bounded collections of related work.

Examples:

- `Garage: Ombouwen` -> `Garage ombouwen tot kantoor`
- `Later` should be dismantled rather than preserved as a catch-all project

### Tasks

Tasks should be explicit next actions or deliberate intake/review actions.

Patterns:

- `Bel ...`
- `Plan ...`
- `Vraag offerte aan ...`
- `Lees ... en noteer ...`
- `Bekijk ...`
- `Onderzoek ...`
- `Vergelijk ...`

Raw URLs and vague labels should not remain as active task titles unless there is a clear reason.

## Migration Rules

1. Establish the target area structure first.
2. Rename or create projects so each cluster has a clear home.
3. Re-home loose tasks into projects when the connection is obvious.
4. Rewrite task titles based on title + note context.
5. Move weak, duplicate, stale, or bookmark-like items to Trash.
6. Leave genuinely ambiguous items untouched or move them to Trash rather than guessing.

## High-Risk Zones

- `Vibecoding`: many bookmark-like and research-heavy items
- `Later`: catch-all project that likely needs to be split apart
- `Notes`: contains mixed reflections, reference items, and possible actions
- old standalone tasks from 2024: likely stale, but still user-owned context

## Verification

Success means:

- the active system has clearer Dutch names
- vague task titles are reduced substantially
- orphaned tasks are reduced
- catch-all containers are reduced or removed
- all removed items are recoverable in Trash

## Execution Notes

Take a fresh snapshot before mutation, perform changes in batches, and verify each batch by re-reading the affected areas/projects from Things.
