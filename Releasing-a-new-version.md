## Checklist for releasing a new version

- [ ] Create a branch, **based on `develop`**, named: `release/release-X.Y.Z` - replacing `X.Y.Z` with the version being released (for example, `release/release-0.2.11`). The branch must start with the `release/` prefix, anything after that is acceptable.
- [ ] In the `themes-default/slim` folder, run `yarn install --prod false --check-files && yarn build` to build the themes for production.
- [ ] Bump the application version in `medusa/common.py` (look for the `VERSION` variable).
- [ ] Update the `CHANGELOG.md` file:
	- Change the `Unreleased` title to the new version with the UTC date of the release (for example, `## 0.2.11 (2018-10-29)`).
	- Remove empty sections under it (if there weren't any new features this release, for example).
- [ ] Open the PR from the release branch onto the `master` branch, assign to the version milestone.
- [ ] [Draft a new release](https://github.com/pymedusa/Medusa/releases/new) (don't publish yet):
	- **Tag version:** `vX.Y.Z` - Be sure to prefix the version with `v`! (for example, `v0.2.11`)
	- **Target:** `master`
	- **Release title:** `Release X.Y.Z` (for example, `Release 0.2.11`)
	- **Description:** Copy the changelog from `CHANGELOG.md`, without the version title.
- [ ] Get PR approved and merged - **don't** squash-merge, use merge-commit.
- [ ] Publish the drafted release [from the releases page](https://github.com/pymedusa/Medusa/releases).
- [ ] Close the version milestone.


### After releasing - Syncing `develop` with `master`

- [ ] Create a branch **based on the new `master`**.
- [ ] In the `themes-default/slim` folder, run `yarn dev` to build the themes for development.
- [ ] Update the `CHANGELOG.md` file - Add an `Unreleased` section to the top of the file:
```md
## Unreleased

#### New Features

#### Improvements

#### Fixes

-----

## 0.2.11 (2018-10-29)
[...]
```
- [ ] Open the PR from the sync branch onto the `develop` branch.
- [ ] Get PR approved and merged - **don't** squash-merge, use merge-commit.
- [ ] Resume normal development.