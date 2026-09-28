# FYP Ideas

A shared idea board for the team. Everyone brings project ideas, drops them here, and we
compare, narrow down, and pick what we actually build.

**This is not a codebase.** There is no application here, no build step, no dependencies.
It is Markdown and opinions.

---

## Structure

One directory per person, named after them:

```
ideas/
├── abdullah/       # ideas added by abdullah
│   └── .gitkeep
├── akash/          # ideas added by akash
│   ├── A8.md
│   └── A22.md
├── behzad/         # ideas added by behzad
│   └── .gitkeep
├── umair/          # ideas added by umair
│   └── .gitkeep
└── TEMPLATE.md     # standard idea template (copy this, never edit in place)
```

At the repo root, `IDEAS_INDEX.json` is the machine-readable registry: one row per
idea with a stable `IDEA-NNN` id, owner, path, status. The fyp-service flow and the
contribution tracker reference ideas by these ids, so every idea file gets a row.

---

## The one rule

**You write in your own directory. That is it.**

- Add as many idea files as you want — one file per idea, or one giant file, whatever works.
- Name your files however you like. `A8.md`, `escrow.md`, `notes-2026-09-28.md` are all fine.
- **Never** edit, rename, move, or delete another person's files.
- **Never** create a directory for someone else. You make yours; they make theirs.
- If you want to build on someone else's idea, write a new file in *your* directory and
  reference theirs.

This keeps authorship obvious and makes it impossible to accidentally clobber someone's work.

---

## Joining the repo

A directory may already exist for you — check the tree above first. If it is there, skip
straight to [Adding an idea](#adding-an-idea).

If it is not there yet, you need write access or a fork.

1. Fork this repo to your own GitHub account.
2. Create your directory: `ideas/<your-name>/` — your name, all lowercase.
3. Your directory will start empty. Git does not track empty folders, so add a `.gitkeep`
   file inside it. (The file has no content — it just makes the folder exist.)
4. Add at least one real idea file so the folder is not just a placeholder.
5. Open a pull request. A repo maintainer reviews and merges.

Once your directory exists on `main`, future PRs only touch your files.

---

## Adding an idea

1. `git checkout main && git pull`
2. `git checkout -b <your-name>/<short-description>`
3. Add your file(s) under `ideas/<your-name>/`.
4. `git add` only your own files — check with `git status` before committing.
5. Commit, push, open a PR.

**One idea per PR.** It keeps review trivial and keeps the history readable.

---

## File format

Write plain Markdown, however you like. Structure it so someone else could pick it up
and understand the idea without asking you questions.

Strong ideas tend to answer: what problem, who has it, what you would build, how hard is
it, and how you would know it worked.

### Optional frontmatter

If you want to record where an idea came from, start the file with this block:

```yaml
---
source: Q8.txt
date: 2026-09-26
model: big-pickle
agent: opencode
---
```

- `source` — the prompt or input the idea came from
- `date` — when it was written
- `model` — the model that helped generate it
- `agent` — the tool you ran it through

This is entirely optional. Add it when it is useful, skip it when it is not. See
`ideas/akash/A8.md` and `ideas/akash/A22.md` for the format in practice.

---

## Idea registry (IDEAS_INDEX.json)

Every idea gets a row in the root `IDEAS_INDEX.json` — one row per idea, in the
SAME PR as the idea file:

- `id` — `IDEA-NNN`, zero-padded, never reused. Take the next free number.
- `title` — short human-readable name of the idea.
- `owner` — your lower-case name; must match `ideas/<owner>/`.
- `path` — exact path of the idea file inside this repo.
- `status` — `proposed` until the team selects it for a deal; then `selected`.
- `source` / `date` — where and when the idea came from (same values as frontmatter).

One rule, same as the repo itself: you append only your own rows. Never edit,
rename, or delete another person's row. The `selected` status is set by the team
lead when a deal is signed on that idea.

Copy `ideas/TEMPLATE.md` for every new idea — it keeps the sections consistent
(problem, who has it, what we build, how hard, success check) so proposals can be
drafted from any idea without chasing the author.
