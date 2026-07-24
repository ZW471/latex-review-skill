# Reviewer memory (agents: maintain this)

Agents that review the paper or resolve review comments must maintain a
persistent, **git-ignored** preference memory at `review/memory/`. The goal:
a preference the author states once — in a `\cans` answer, a declined
proposal, or chat — is never asked about or violated again in a later
session.

## Location and lifecycle

- The folder is `review/memory/`, next to this file. It is listed in this
  repo's `.gitignore` and must **never be committed or pushed** — it is
  local, per-author state, and may contain informal remarks not meant for
  collaborators.
- Create it on first use; its absence simply means no preferences have been
  recorded yet.
- **Before inserting, answering, or applying any comment**, read
  `review/memory/index.md` (if present) and every memory file relevant to
  the task at hand.
- **During and at the end of every review/resolution session**, record each
  new durable preference you observed. Update or delete entries the author
  has since contradicted — a stale memory is worse than none.
- Memory fills gaps; it never overrides an explicit instruction from the
  current session or a convention documented in the host repo.

## Format

One file per preference, plus an index that is the only file read
unconditionally:

```
review/memory/
  index.md          # one bullet per memory: - [title](file.md) — one-line hook
  <topic-slug>.md   # a single preference
```

Each `<topic-slug>.md`:

```markdown
# <short title>

- **Preference:** what the author wants (or wants avoided).
- **Evidence:** where it was learned — comment slug, the `\cans` text, or a
  chat instruction — with the date.
- **How to apply:** the concrete behavior change for future review and
  resolution passes.
```

Keep entries short (a few lines). Merge into an existing file rather than
creating a near-duplicate; keep `index.md` in sync with every add, merge, or
delete.

## What to record

- **Accept/decline patterns** — e.g. the author consistently declines
  `\csub` proposals that shorten the introduction, or always accepts
  hedging-removal edits. Record the pattern, not each instance.
- **Style and wording preferences** — voice, tense, hedging level,
  British vs. American spelling, formality, sentence-length taste.
- **Terminology and notation rulings** — decisions made in `\cans` answers
  that are not (yet) codified in the paper's own conventions.
- **Comment-workflow preferences** — desired comment density, which comment
  types the author finds useful or noisy, whether they want `\capplied`
  audit trails or direct replacement, preferred report format.
- **Standing scope rules** — sections the author considers frozen, topics
  they own and don't want proposals on.

## What NOT to record

- Anything already codified in the host repo (its `CLAUDE.md`, skill files,
  or notation tables) — that is the authoritative home; suggest updating it
  instead of shadowing it here.
- One-off decisions that apply to a single comment only — the comment
  thread itself (and git history) is that record.
- Paper content, results, or facts derivable from the sources.
- Secrets, credentials, or personal data.
