# Valenzano Lab Website

<img src="https://raw.githubusercontent.com/valenzano-lab/labsite/quarto-redesign/files/pictures/dvlablogo_bl2.png" width="18%"></img>

Source for the [Valenzano Lab website](https://valenzano-lab.github.io/labsite/) at the [Leibniz Institute on Aging](https://www.leibniz-fli.de/).

The site is built with [Quarto](https://quarto.org/) and deployed to GitHub Pages via the `gh-pages` branch.

## Branches

| Branch | Purpose |
|---|---|
| `quarto-redesign` | Active development — all edits go here |
| `gh-pages` | Auto-managed by `quarto publish`, never hand-edited |
| `main` | Receives merge from `quarto-redesign` when ready to release |
| `legacy-html-site` | Frozen original Distill site, never touched |

## Contributing

1. Get a [GitHub](https://github.com/) account.
2. Familiarize yourself with [git](https://ryoaxton.medium.com/familiarize-yourself-with-git-fadcc125dbb9) and [Quarto](https://quarto.org/docs/websites/).
3. Ask Dario to add you as a [collaborator](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-teams-and-people-with-access-to-your-repository) on this repo.

## Day-to-day workflow

All commands run from inside the `_site/` directory (the Quarto project root).

**Edit source files, then commit and push:**

```bash
git add -u                        # stage modifications to tracked files
git add <any-new-files>           # stage genuinely new files explicitly
git commit -m "description"
git push origin quarto-redesign
```

**Deploy the live site:**

```bash
quarto publish gh-pages
```

This renders the site and pushes the output to `gh-pages` in one step. No need to run `quarto render` separately.

**Preview locally before publishing:**

```bash
quarto preview
```

## Adding a blog post

Create a new folder under `posts/` and add an `index.qmd`:

```
posts/
└── YYYY-MM-DD-short-title/
    └── index.qmd
```

Front matter template:

```yaml
---
title: "Post title"
date: YYYY-MM-DD
author: "Dario Valenzano"
categories: [field-work, killifish]
description: "One sentence summary shown in the listing."
---
```

## Notes

- Use `git add -u` rather than `git add .` to avoid committing `.DS_Store` and other junk.
- Stay on `quarto-redesign` for all development. Do not push to `main` until ready to formally release.
- Never edit the `gh-pages` branch directly.
