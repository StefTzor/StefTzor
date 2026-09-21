# StefTzor/StefTzor — the GitHub profile README

The fourth surface of the tzortzoglou.eu project, and the smallest. This repo renders as the
profile page at github.com/steftzor. Two files, both of them identity copy.

The others: `steftzor.github.io` (public site and signed-in app), `tzortzoglou-api` (private
backend), `portfolio-skill` (the knowledge base).

## Load first

**The `portfolio` skill** (`/portfolio`) — the canonical knowledge base for this project. It is
user-level, so it loads here as well. The two that matter for this repo:

- `references/identity-images.md` — how `banner.png` is made and why it is not drawn by hand.

The skill knows which of its own files is canonical for wording. Ask it rather than restating it
here: this repo is public.

## Do not hand-edit these two files

Both are generated in the **site repo** and copied here:

| File here | Source | Rebuild with |
|---|---|---|
| `README.md` | `scripts/cards/github-profile-README.md` | `npm run cards` |
| `banner.png` | `_data/identity.js` + `scripts/cards/card.html` | `npm run cards` |

`npm run cards` writes both into `steftzor.github.io/dist-cards/`, then they are copied here and
committed. Editing them here instead means the next `npm run cards` silently reverts your change.

**Why the indirection.** The banner used to be a `capsule-render.vercel.app` URL with its text in
the query string, so "Implementation Lead" lived here as `Implementation%20Lead` and survived a
`grep -rc "Implementation Lead"` that was run across every other repo and returned nothing. Text
inside a URL or a PNG cannot be checked. It lives in `_data/identity.js` now, and
`checks/surfaces.mjs` in the skill asserts this profile against it.

## Rules

1. **Run `/security-review` and wait for it before every `git push`.** Even here. It is a public
   repo and this is the most-read page of the four.
2. **Never `git add -A`.** Stage by path, read `git diff --cached --stat`.
3. **No Claude attribution** in commit messages.
4. **No availability signals.** No "open to work", no "hire me", and `hireable` stays unchecked
   in the profile settings. `checks/surfaces.mjs` asserts the flag stays off.
5. **After changing anything here**, run the checker:
   `node ~/.claude/skills/portfolio/checks/surfaces.mjs`
