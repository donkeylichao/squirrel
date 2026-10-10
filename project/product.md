# Product Plan

## Product Direction

- Target users: macOS users composing Chinese with Squirrel.
- Core value: Fast, private Chinese input with optional local English suggestions.
- Product boundaries: Input-method UI and local inference; no cloud translation service.

## Feature Modules

| Module | Product Scope | Status | Notes |
| --- | --- | --- | --- |
| Smart translation | Show and copy accurate and natural English after Chinese input ends | implemented | Uses local Ollama and a compact, movable result card with native copy icon buttons |

## Status Values

- `planned`: planned but not started
- `in_progress`: currently being implemented
- `implemented`: implemented and verified or verification noted
- `blocked`: blocked by missing decision, dependency, or external condition
- `deferred`: intentionally postponed

## Cross-Module Requirements

| Requirement | Modules | Status | Notes |
| --- | --- | --- | --- |
| Translation must not block typing | Input handling, smart translation | implemented | Cancellable async localhost request |

## Open Questions

- Whether later versions should add speech, favorites, or translation history.
