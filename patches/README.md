# Patches

Every `*.patch` file here is applied, in sorted order, to the upstream tmux
source by `scripts/build_tmux.sh` (`patch -p1`). A hunk that does not apply
fails the build.

A release tag of the form `v<upstream>-<suffix>` (for example
`v3.8-fix5776`) builds upstream tmux `<upstream>` plus these patches.

Delete a patch from this directory as soon as a released upstream tmux
version contains it.

| Patch | Upstream commit | Upstream issue |
| --- | --- | --- |
| `0001-select-layout-E-tiled-child-5776.patch` | [`67d1c4dc5dbc94ee5b8635f50af0d8b3b4a38fa3`](https://github.com/tmux/tmux/commit/67d1c4dc5dbc94ee5b8635f50af0d8b3b4a38fa3) "Check for tiled child cells as well for select-layout -E" | [tmux/tmux#5776](https://github.com/tmux/tmux/issues/5776) |

`0001` fixes a tmux 3.8 regression: `select-layout -E` counted only pane
children, so it did nothing for a parent whose children are all split cells,
and for a parent that mixes split cells and panes it made the layout larger
than the window, which put panes outside the visible area.
