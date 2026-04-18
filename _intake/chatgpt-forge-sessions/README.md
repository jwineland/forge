# ChatGPT Forge Sessions

This directory holds content from prior ChatGPT sessions where the Forge concept was developed. These sessions predate the current Forge repository and contain foundational work on:

- Completeness scoring methodology for concept formalization
- Human/AI prompted interchange design
- Concept lifecycle state machine (prior version)
- `forge this conversation` invocation design
- Concept registry structure (prior version)

## Expected content

Place the following here when available:

```
chatgpt-forge-sessions/
  README.md                          this file
  session-01/
    conversation.json                ChatGPT export (preferred) or
    conversation.md                  plain text
    artifacts/
      [any documents produced]
    intake-notes.md                  pre-annotation if known
  session-02/
    ...
```

If the sessions are in a single export file, place it at the top level:
```
  conversations.json                 full ChatGPT export containing all sessions
```

## Processing priority

Once content is placed here, the following parked concepts should be activated:

| Parked concept | File | Trigger condition |
|---|---|---|
| completeness-scoring-methodology | `_parked/completeness-scoring-methodology.md` | ChatGPT Forge session deposited |

Additionally, the following formalized concepts have open questions that the ChatGPT sessions may resolve:

- `human-ai-role-separation` — confidence threshold for autonomous vs. prompted classification
- `forge-concept-lifecycle` — fingerprinting algorithm for concept identity
- `challenge-loop-methodology` — integration with completeness scoring

## After processing

Once excavated:
- Session records land in `_sessions/YYYY-MM-DD-chatgpt-forge-[n]/`
- Activated concepts move from `_parked/` to `_concepts/`
- This directory can be cleared or moved to `_intake/_processed/`
