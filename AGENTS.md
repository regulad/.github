# Agent notes for `regulad/.github`

This repository holds the GitHub defaults shared by regulad's repositories.
Today that is the Settings app's base file, `.github/settings.yml`, which
other repositories inherit with `_extends: .github`. [README.md](README.md)
explains how a repository extends it.

## The shared settings file

- `.github/settings.yml` is both this repository's own settings and the base
  for every other repository. The app also applies it, unchanged, to every
  repository created without a settings file. So it never carries a
  repository's identity (`name`, `description`, `homepage`, `topics`,
  `private`, `visibility`, `archived`, `is_template`, `default_branch`) or
  an `environments` key. The `repository-identity` pre-commit hook refuses
  them. This repository's own description and topics are set with
  `gh repo edit`, with Parker's approval.
- Put a setting here only when every repository should have it. A setting
  only some repositories share belongs in each of those repositories' files.
- Labels and branches merge by `name`, and any other key merges key by key,
  with the repository's own value winning. The app deletes every label that
  neither the shared file nor the repository's file lists. Removing a label
  here deletes it from every repository that syncs afterwards, unless that
  repository lists it itself.
- Environments and secrets belong to `regulad/homelab` (`tofu/github`). Never
  declare them here.
- A change here takes effect in a repository only when that repository syncs
  again, which happens on a push that touches its own settings file. Nothing
  re-syncs them all. Say so whenever you change this file, and list the
  repositories the change matters for.

## Commits

- Conventional commits: `<type>(<scope>): <summary>`. The scope is the file
  or area changed: `settings`, `labels`, `pre-commit`, `dependabot`,
  `agents` for this file, or `readme`.
