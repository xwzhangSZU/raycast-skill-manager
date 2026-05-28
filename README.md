# Curator

**Your skills, curated.** A Raycast extension that gives you a fast, searchable
view of every skill installed for Claude Code and Codex — and quietly tells you
which ones are broken.

You have dozens of skills spread across user directories, plugin marketplaces,
and version caches, named in a mix of conventions you can never quite remember.
Curator turns that sprawl into one keystroke: open it, type what you're trying
to do, and grab the skill you forgot you had.

## Commands

### Search Skills

The launcher. Fuzzy-search every installed skill by name, purpose, or trigger
phrase — `scrape a webpage`, `firecrawl`, `superpowers` all land on the right
result. Then:

- `⏎` — copy the skill name
- `⌘⏎` — copy it as a `/command`
- `⌘⇧T` — copy a trigger phrase
- `⌘D` — preview the full `SKILL.md` in a side panel
- `⌘O` — open `SKILL.md` in your editor
- `⌘R` — rescan

Skills shared across Claude and Codex are merged into one row with surface
badges; plugin and user skills are grouped by source.

### Skill Doctor

The check-up. Surfaces health issues across your skill tree:

| Check | What it catches |
| --- | --- |
| Broken symlink | a linked skill whose target is gone |
| Missing / unparseable `SKILL.md` | empty or malformed skill folders |
| Name ≠ directory | `frontmatter.name` that disagrees with the folder |
| Cross-surface drift | a skill present for Claude but not Codex (or vice versa) |
| Stale cache | older plugin versions lingering in the cache |

Each issue comes with a one-keystroke **Copy Fix Command**.

## Safe by design

Curator **never writes to or deletes from your filesystem.** Every fix is a
shell command copied to your clipboard, for you to review and run yourself. The
only process it ever launches is your editor (via `execFile`, no shell).

## Development

    npm install
    npm run dev      # run in Raycast
    npm test         # run unit tests
    npm run lint     # lint

The core lives in `src/lib/` as pure, dependency-light modules (scan → parse →
aggregate → health → fix-command) with a full unit-test suite. The Raycast UI is
two thin `view` commands on top.

## Status

v1. Before submitting to the Raycast Store: replace the placeholder
`assets/icon.png` with a real 512×512 PNG, and set `author` in `package.json` to
your Raycast Store handle.

Roadmap (v2): natural-language skill recommendation — the full `SKILL.md`
frontmatter is already preserved in the cache as the hook.
