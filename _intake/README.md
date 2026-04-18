# Intake Staging Directory

This directory is a temporary staging area for raw session content awaiting excavation. Once processed, extracted concepts move to `_concepts/`, session records move to `_sessions/`, and the intake content may be cleared or archived.

## What belongs here

- Conversation exports (ChatGPT JSON export, Claude exports, or other platform formats)
- Supporting artifacts referenced in those conversations (documents, code, diagrams)
- Any supplementary context needed to process the session

## What does not belong here

- Formalized concepts (those go in `_concepts/`)
- Processed session records (those go in `_sessions/`)
- Long-term reference material (that belongs in the relevant project repo)

## Processing protocol

1. Create a subdirectory named `YYYY-MM-DD-PLATFORM-CONTEXT/` (matching the session ID that will be used in citation addresses)
2. Place the conversation export as `conversation.json` (ChatGPT) or `conversation.md` (plain text) in that directory
3. Place any supporting artifacts in `artifacts/` under the same directory
4. Open a session with the instruction: `forge this conversation` pointing to the intake directory
5. The AI will perform an excavation, propose concept classifications, and prompt for validation
6. Once excavation is complete and committed to `_sessions/` and `_concepts/`, the intake subdirectory may be deleted or moved to `_intake/_processed/`

## Supported conversation formats

### ChatGPT JSON export (preferred)

Export from ChatGPT via Settings → Data Controls → Export Data. The resulting `conversations.json` contains structured turn-by-turn message objects with IDs, timestamps, and threading. This format maps directly to the Session → Thread → Exchange → Emergence citation model and supports the most precise citation addresses.

### Shareable link

If a ChatGPT conversation has a shareable link, provide the URL and the AI can fetch it directly. No file needed.

### Plain text paste or export

Acceptable for shorter sessions. Loses message IDs and threading structure, so citation addresses will be approximate at the Exchange level. Note this limitation in the session excavation record.

### Claude conversation

Claude does not currently provide a structured JSON export. Use the conversation search tools available in the session, or paste the relevant content as plain text.

## Intake directory structure

```
_intake/
  README.md                          this file
  _processed/                        optional archive of processed intake
  YYYY-MM-DD-PLATFORM-CONTEXT/
    conversation.json                ChatGPT JSON export (preferred)
    conversation.md                  plain text alternative
    artifacts/
      document-name.md
      code-file.py
      other-artifact.ext
    intake-notes.md                  optional: notes for the excavation session
```

## Intake notes

An optional `intake-notes.md` file in each session directory can pre-identify:
- Known concepts the session contains (speeds up excavation)
- Known artifacts to prioritize
- Connections to existing concepts in `_concepts/`
- Specific threads or topics to focus on
- Items to park immediately without full excavation

This is the human pre-annotation path that reduces AI prompting during excavation.
