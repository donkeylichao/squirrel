# Module Todo: smart-translation

## Current Focus

- Verify longer translation responses in target applications.

## In Progress

| Task | Status | Owner/Context | Next Step |
| --- | --- | --- | --- |

## Planned

| Task | Status | Priority | Notes |
| --- | --- | --- | --- |

## Blocked

| Task | Status | Blocker | Needed Decision |
| --- | --- | --- | --- |

## Implemented

| Date | Task | Verification | Notes |
| --- | --- | --- | --- |
| 2026-10-10 | Async translation request | Debug build; decoder self-check embedded | Cancellable request, structured response, stale-result guard |
| 2026-10-10 | Translation result panel | Debug build | Source plus direct and natural English sections |
| 2026-10-10 | Install Debug input method | `make install-debug ARCHS=arm64` | Registered successfully |
| 2026-10-10 | Live Ollama translation | User verification | Local translation confirmed working |
| 2026-10-10 | Compact translation result card | `make install-debug ARCHS=arm64` | 420pt width cap, semibold headings, tighter spacing |
| 2026-10-10 | Retain translated source in active session | `make install-debug ARCHS=arm64` | Idle-triggered requests no longer discard prior source |
| 2026-10-10 | Mirror committed-text Backspace | `make install-debug ARCHS=arm64` | Each ordinary Backspace removes one buffered character |
| 2026-10-10 | Synchronize from active text client | `make install-debug ARCHS=arm64` | Read field before request and reject results when field changes |
| 2026-10-10 | Suppress Ollama failure UI | `make install-debug ARCHS=arm64` | Network/model failures no longer show a panel or log message |
| 2026-10-10 | Preserve whole-field context across edits | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | Reject partial client text and retain context across ordinary unhandled keys |
| 2026-10-10 | Compact movable result card | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | 360pt cap, above-caret preference, drag support, typing dismissal, 12-second timeout |
| 2026-10-10 | Retry stale translation | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | Reschedule using newest complete client text when an in-flight result becomes stale |
| 2026-10-10 | Restore source/result comparison | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | Restored Chinese source; reduced headings from 16pt to 13pt and content from 16pt to 14pt |
| 2026-10-10 | Preserve directly inserted digits | `make debug ARCHS=arm64`; visibility self-check | Mirrors printable unhandled text and schedules translation when Chinese context exists |
| 2026-10-10 | Extend result timeout | `make install-debug ARCHS=arm64` | Translation card remains visible for 30 seconds |
| 2026-10-10 | Increase Ollama output budget to 200 tokens | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | Reduces structured JSON truncation for longer translations |
| 2026-10-11 | Make translation results selectable | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` | Result bodies allow selection; section headings remain window drag handles |
| 2026-10-11 | Add focus-independent copy actions | superseded | Inline text hit-testing was unreliable and replaced by native buttons |
| 2026-10-11 | Replace inline copy links with native icon buttons | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64`; isolated AppKit pasteboard read/write check; UI automation could not trigger the translation card | Top-level borderless SF Symbol buttons copy each section and change to a checkmark on success |

## Assumptions

- A pause of 0.8 seconds after a Chinese commit means the current phrase is complete.
- The first version uses `qwen3.5:4b` and a fixed localhost Ollama endpoint.
- When an app does not expose document text through InputMethodKit, buffered commits remain the fallback source.
