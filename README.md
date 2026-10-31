# Herdr branch changes

A Changes panel for the [Herdr](https://herdr.dev) desktop app that can show everything on your branch, not only uncommitted work.

Herdr's own Changes panel shows uncommitted changes. Once an agent commits its work, the panel is empty. This panel adds a toggle in its header:

- **Uncommitted**: the same view as Herdr's panel.
- **Branch**: every change since the branch split from the default branch. That is committed work, uncommitted work and untracked files, against the merge base.

The default branch is `origin/HEAD`. If that isn't set, it tries `origin/main`, `origin/master`, `main` and `master`, in that order. The choice of view is remembered across restarts. The commit box works the same in both views.

## Install

Clone this repository and link the mod into Herdr's home, so a `git pull` updates it:

```sh
git clone https://github.com/stympy/herdr-branch-changes.git ~/Code/herdr-branch-changes
ln -s ~/Code/herdr-branch-changes/mods/branch-changes ~/.config/herdr-app/mods/branch-changes
cp ~/Code/herdr-branch-changes/layouts/main-branch.json ~/.config/herdr-app/layouts/
herdr-app do layout.switch '{"name":"main-branch"}'
```

`main-branch` is Herdr's own `main` layout (0.1.10) with the Changes block pointing at this mod. `ctrl-shift-l` cycles back to any other layout.

### Your own layout

Already have a layout of your own? Point its Changes block at this mod:

```json
{ "id": "changes", "type": "block", "content": { "mod": "branch-changes" } }
```

Keep the block id `changes` so the tab bar's Changes button still opens it.

## License

Apache-2.0. The mod is a modified copy of the `changes` mod that ships with Herdr (Apache-2.0, © the Herdr authors).
