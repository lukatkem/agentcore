# Design decisions

Why the wire format is fenced JSON blocks (and not function calling):
- **Observable**: every tool call is visible text in the transcript — debuggable with grep.
- **Portable**: works with any model that can emit text, including local 7B models.
- **Testable**: the parser is a pure function with 25 parametrized test cases.

Why the registry validates types eagerly: an agent that dispatches on bad
arguments produces confident nonsense; failing fast at the boundary keeps the
error message small enough for the model to correct itself in the next turn.
