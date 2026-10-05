---
name: Readability Refactor
description: Remove demonstrable code clutter and improve readability and extensibility without changing intended behavior.
---

# Readability Refactor

Improve the code the user identifies by removing unnecessary complexity and making the result easier to understand and extend. Treat "slop" as code with a concrete problem, not code that merely differs from your preferred style.

## Working approach

1. Inspect the target code, its callers, tests, and nearby conventions before editing. For broad cleanup requests, map the project-owned source and test files first; exclude dependencies, generated output, build artifacts, and vendored code.
2. Identify specific problems such as duplicated logic, dead code, misleading names, needless indirection, oversized responsibilities, redundant state, or unclear control flow. Make changes only when the improvement is clear and supported by usage or test evidence.
3. Make cohesive, surgical changes. Prefer direct, well-named code and existing project patterns over new abstractions, configuration, dependencies, or architecture. Introduce an abstraction only when it removes real duplication or gives a coherent responsibility a clear home.
4. Preserve public APIs, user-visible behavior, error handling, accessibility, and compatibility unless the user explicitly asks to change them. Check call sites before changing or removing symbols. Do not delete code merely because it appears unused in a partial search.
5. Keep types precise, handle errors explicitly, and avoid catch-all fallbacks, unsafe casts, and comments that repeat what the code already says.
6. Update directly affected tests and documentation. Run the narrowest relevant existing checks, then report what changed and what could not be verified.

## Guardrails

- Do not reformat or rewrite unrelated files as part of a cleanup.
- Do not optimize performance without evidence of a meaningful bottleneck.
- Do not add speculative extension points or abstractions for hypothetical future requirements.
- Do not silently change behavior to make code shorter or more uniform.
- If a proposed cleanup has ambiguous behavior or meaningful product/design tradeoffs, ask before changing it.
- Preserve user changes already present in the worktree.
