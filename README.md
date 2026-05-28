# Skill Manager

A Raycast extension to browse and health-check the skills installed for
Claude Code and Codex.

## Commands

- **Search Skills** — fuzzy-search every installed skill by name, purpose, or
  trigger phrase; preview its `SKILL.md`; copy its name / `/command` / trigger;
  open it in your editor.
- **Skill Doctor** — list health issues (broken symlinks, missing/unparseable
  `SKILL.md`, name/directory mismatch, Claude↔Codex drift, stale plugin cache)
  and copy a suggested fix command to your clipboard.

This extension never writes to or deletes from the filesystem. All fixes are
copied to the clipboard for you to review and run in your own terminal.

## Development

    npm install
    npm run dev      # run in Raycast
    npm test         # run unit tests
    npm run lint     # lint

## Status

v1. The extension icon (`assets/icon.png`) is a placeholder; replace it with a
real 512x512 PNG before submitting to the Raycast Store.
