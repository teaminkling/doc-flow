# Inkling Flow

Supplementary tools - especially GitHub Actions - used to support the simple-as-cake Inkling Flow workflow.

## Maintainer Documentation

For us, this is the `README.md` file and package metadata files (e.g.: `Cargo.toml`). Any supplementary files required should be linked from the `README.md` file. Anything a new developer with zero prior visibility of the project should be able to start contributing after reading `README.md`.

### `FEATURES.md` file

I believe in the inclusion of a `FEATURES.md` file in all repositories that warrant it (sorry, not this one). This file should simply be updated every time a GitHub Issue tagged `epic` 

## Release Documentation

This is the `CHANGELOG.md` file, GitHub Releases descriptions, and any blog posts or release documentation accompanied with an artifact. Inkling Flow suggests that GitHub Releases should be based on `CHANGELOG.md` which in turn should be based on GitHub Issues and Milestones. This entire process is automated:

## CI/CD Definition

- On a merge or a push to `master`, a script runs. It may automatically commit to `master` by updating certain files.
  - Versions are incremented in supported package metadata files.
  - `CHANGELOG.md` is updated with most recent changes. Human-readable changes are retained, if present.
  - `FEATURES.md` is updated.
- On any push to `master` or to an open pull request:
  - Compile/test as usual.
  - Publish release candidate version.
  - Run any code quality tools available for the framework/language.
  - Generate code documentation and publish to appropriate location.
- On any `git tag`.
  - Package and publish release version.
  - Update the GitHub Release that was created with the tag action.
  - Deploy to environments (if applicable).

## Versioning Definition

A major difference between this an [SemVer](https://semver.org/) is that `PATCH` and `MINOR` are incremented even when backwards incompatible changes are made before version 1.0.0.

> MAJOR.MINOR.PATCH-extra_info+details

- **PATCH** is incremented when a bug or a group of bugs have been fixed.
- **MINOR** is incremented when a feature has been introduced.
- **MAJOR**...
  - ...from 0 to 1 is incremented when a game product leaves `beta`.
  - ...in any other circumstances is incremented when the product has changed in such a way that the user needs to change how they use the product or needs to change the environment around it (i.e.: backwards incompatible).
    - But not before the "first stable release." If anybody is using the tool before then, they accept liability for the application changing whenever the maintainer wants.

Branching is based on GitHub Flow and uses merge commits with semi-linear flow (requiring rebasing):

- `master` contains `rc` code.
  - `0.1.13-rc+2`
- Tags can deploy `release` or `alpha`/`beta` code.
  - If the project has a `major` version > 0, it is `release`, otherwise it is `pr` (pre-release).
  - `0.1.13-pr` or `3.11.0`
- `feature` branches (based on the issue number and description) contain `feature` code.
  - Such code is not automatically tested nor deployed until a pull request is opened.
  - If a version is created and deployed, it is deployed as `feature` with reference to the issue number.
  - `0.5.13-feature+21`
