# Project Overview

## Summary

- Project: Squirrel macOS input method
- Goal: Provide reliable Rime input with optional local AI-assisted translation.
- Main modules: Input handling, candidate panel, smart translation.

## Implemented

| Feature | Module | Status | Notes |
| --- | --- | --- | --- |
| Rime input and candidate UI | Core input method | implemented | Existing project behavior |
| Local Chinese-to-English suggestions | Smart translation | implemented | Async Ollama request and compact result card |

## Not Implemented

| Feature | Module | Status | Notes |
| --- | --- | --- | --- |

## Architecture Notes

- Input controllers own per-client sessions; the app delegate owns global Rime lifetime.
- Smart translation must never block key handling or send text outside localhost.

## Recent Updates

| Date | Module | Change | Verification |
| --- | --- | --- | --- |
| 2026-10-10 | Smart translation | Added buffered Chinese detection, async Ollama translation, and direct/natural result UI | `make debug ARCHS=arm64`; installed Debug app |
| 2026-10-10 | Smart translation | Capped result width and improved text hierarchy/spacing | `make install-debug ARCHS=arm64` |
| 2026-10-10 | Smart translation | Added movable, auto-dismissing result cards and stale-response retry | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` |
| 2026-10-10 | Smart translation | Restored Chinese source comparison and reduced result-card typography | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` |
| 2026-10-10 | Smart translation | Preserved directly inserted digits and extended result visibility to 30 seconds | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` |
| 2026-10-10 | Smart translation | Increased Ollama response budget from 80 to 200 tokens for longer text | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64` |
| 2026-10-11 | Smart translation | Replaced unreliable inline copy links with native icon buttons and success feedback | `make debug ARCHS=arm64`; `make install-debug ARCHS=arm64`; isolated pasteboard check |
