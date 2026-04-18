# Forge Drift Check

Run at the start of any review session and before closing any session that touched more than one file.

## Step 1: Vocabulary consistency

Open `_vocabulary/forge-context.jsonld`. Note the defined node types and edge types.

For any concept file touched this session: confirm it uses only vocabulary-defined types in its front matter. Flag any type not present in the vocabulary.

## Step 2: Citation completeness

Every concept file must have a `citation` field. Every parked concept must have a `trigger` field. Check any files created or modified this session for these required fields.

## Step 3: Status progression validity

Concept status must follow the defined progression. Check that no concept has been moved backward in status without an explicit reason recorded in the file.

## Step 4: Session record immutability

Confirm no files under `_sessions/` have been modified after their initial commit. If modifications are found, flag for amendment file creation.

## Output

- **Pass**: all checks clear, proceed
- **Drift found**: list item, affected file, required fix
- **Blocked**: do not add new content until drift is resolved
