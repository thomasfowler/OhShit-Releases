# OhShit-Releases — agent guide

This is the **public distribution point** for OhShit, a closed-source SimHub plugin for
iRacing. The source lives in the private repo `thomasfowler/OhShit`; this repo exists so the
binaries, release notes and issue tracker have a public home — and so a future in-plugin
version checker has a stable, unauthenticated endpoint
(`api.github.com/repos/thomasfowler/OhShit-Releases/releases/latest`).

## What lives where

- **Git** holds only docs and assets: README, this file, LICENSE, issue templates, logos.
  No binaries in git, ever — they're release assets only.
- **Releases** are created by CI, not by hand. When a release is published in the private
  repo, its `release.yml` workflow builds the tagged source and mirrors the release here:
  same tag, same title, notes copied **verbatim**, plus `OhShit-Setup-<version>.exe` and its
  `.sha256`.

## Rules

- **Never hand-author or hand-edit a release here.** To fix one, fix it at the source and
  re-run the private repo's release workflow (Actions → release → Run workflow → existing
  tag). The mirror is idempotent: it re-edits notes and re-uploads assets with `--clobber`.
- **The version checker's contract** (do not break): tags are `v<major>.<minor>.<patch>`,
  the installer asset is named `OhShit-Setup-<version>.exe`, and this repo stays public.
- **Release notes are public.** They're copied verbatim from the private release, so notes
  must be written without private-repo commit/PR links ("Generate release notes" output needs
  editing before publish). If a private link ships in public notes, fix the private release
  body and re-run the mirror.

## Issues

Issues here are the public bug tracker. The bug template asks for OhShit version, SimHub
version, and the `[OhShit]` lines from the SimHub log — those lines record every warning
raised and every reason detection stayed idle, and most bugs are diagnosable from them alone.
General questions and discussion belong on the [JT-Racing Discord](https://discord.gg/BKCMK9fWxE);
the issue-template chooser points there too.
