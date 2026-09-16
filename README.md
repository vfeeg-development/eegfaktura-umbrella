# eegfaktura-master

Umbrella repository. Every EEGFaktura project is included as a git submodule, each
pinned to an exact commit. A commit (or tag) in this repository therefore describes
one consistent set of versions across all projects.

## Clone

```sh
git clone --recurse-submodules <url-of-this-repo>
# already cloned without submodules:
git submodule update --init --recursive
```

## Create a version that belongs together

```sh
git submodule foreach 'git fetch --all'          # optional: see what is new
git submodule update --remote                    # move each submodule to its tracked branch tip
git add -A && git commit -m "release 2026.1"
git tag -a v2026.1 -m "release 2026.1"
git push --follow-tags
```

## Restore a version

```sh
git checkout v2026.1
git submodule update --init --recursive
```

Every project can also be moved individually: check out the wanted commit inside the
submodule directory, then `git add <project>` and commit here.

## Overview

```sh
git submodule status                             # pinned commit per project
git submodule foreach 'git log -1 --oneline'     # what each pin actually is
```

## Tracked branch per project

Each submodule records the branch it was added from (see `.gitmodules`), so
`git submodule update --remote` follows the right branch. Most projects track
`main` or `master`; these currently track a feature branch:


