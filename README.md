# .github

The GitHub defaults shared by [regulad](https://github.com/regulad)'s
repositories.

## Repository settings

[`.github/settings.yml`](.github/settings.yml) holds the settings every
repository has in common: merge options, features, security alerts and the
standard labels. The [Settings app](https://github.com/repository-settings/app)
applies it. A repository's own `.github/settings.yml` inherits it and adds
only what is that repository's own:

```yaml
_extends: .github

repository:
  name: example
  description: >-
    One line on what the repository is
  homepage: ""
  private: false
  # Comma-and-space separated string, not a YAML list.
  topics: rust, windows
  default_branch: master
```

The repository's own values win. A label it lists under one of the shared
names replaces that label's colour or description, and a label it lists
under a new name is added. Any label listed in neither file is deleted.

A repository created without a settings file gets the shared file as it is,
so the shared file never names, describes, publishes or hides a repository.

A change to the shared file reaches a repository only when that repository's
own settings file is next pushed to its default branch.

Environments and secrets aren't set here or in any repository's settings file.
[regulad/homelab](https://github.com/regulad/homelab) manages them.

## Licence

Free software, under the GNU Affero General Public License, version 3 or (at
your option) any later version ([`LICENSE.md`](LICENSE.md)).
