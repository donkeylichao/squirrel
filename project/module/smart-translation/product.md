# Module Product: smart-translation

## Scope

- Module: Local Chinese-to-English assistance.
- User value: See an accurate translation and a natural spoken alternative after finishing Chinese input.
- Out of scope: Speech, favorites, history, cloud APIs, and model management.

## Functional Design

| Function | Description | Status | Notes |
| --- | --- | --- | --- |
| Detect completed Chinese | Read the active client's complete current text when translation starts | implemented | Also mirror directly inserted visible characters such as digits into fallback context |
| Trigger translation | Immediate at sentence punctuation, otherwise after 0.8s idle | implemented | Retry when the field changes while a response is in flight |
| Request Ollama | Call `qwen3.5:4b` on localhost | implemented | Structured JSON, thinking disabled, 200-token output budget |
| Present result | Show Chinese source, direct English, and natural English in a compact, movable result card | implemented | Native per-section copy buttons write directly to the pasteboard and show a checkmark on success |
| Handle unavailable Ollama | Keep normal input behavior without user-facing errors | implemented | Translation failures are silent |

## API / UI / Data Surface

| Surface | Direction | Parameters / Fields | Status |
| --- | --- | --- | --- |
| Ollama `/api/chat` | Outbound localhost | Chinese source, direct/natural schema | implemented |
| Candidate panel | User-facing | Source, direct, natural | implemented |
| `squirrel.yaml` | Configuration | enabled, model | implemented |

## Rules And States

- Never delay or consume additional key events while inference runs.
- Cancel pending or in-flight translation when new input begins.
- Do not display a response after focus changes or a newer request supersedes it.
- Retry against the newest complete field value when a response becomes stale without another committed-text event.
- Keep translated source as context until the input session is reset.
- Mirror an unhandled Backspace by removing the last committed character from translation context.
- Mirror visible unhandled characters, including digits, into translation context.
- Do not clear translation context for ordinary unhandled keys such as cursor movement.
- Prefer the current input field value only when InputMethodKit returns the complete document.
- Silently skip translation when Ollama is unavailable.
- Keep result cards temporary and movable so they do not obstruct editing.
- Allow result bodies to be selected and provide focus-independent copy actions; reserve section headings for dragging the card.

## Dependencies

- Ollama running at `127.0.0.1:11434`.
- Model `qwen3.5:4b` installed locally.

## Implementation Status

| Item | Status | Code / Doc Reference | Notes |
| --- | --- | --- | --- |
| MVP | implemented | `sources/SquirrelInputController.swift`, `sources/SquirrelPanel.swift`, `sources/SquirrelView.swift` | Built and installed with native copy controls |
