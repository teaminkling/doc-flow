# Inkling Flow

A process document on the (relatively) simple Inkling Flow.

## Your Actions

In order to use Inkling Flow, you need to:

1. Read through this entire file.
2. Use [Autosuite](https://github.com/autosuite). Check out [teaminkling/base](https://github.com/teaminkling/base) for a template that uses all it has to offer!
3. Add the `epic` and `breaking` labels to your organisation's default Issue labels.

## Maintainer Documentation

For us, "maintainer documentation" refers to the `README.md` file and package metadata files (e.g.: `Cargo.toml`). Any supplementary files required should be linked from the `README.md` file. A new developer should be able to read `README.md` and know everything they need to know to be useful.

`README.md` cannot be automated (except maybe through badges) but package metadata can: versions are automatically dealt with.

### `FEATURES.md` file

I believe in the inclusion of a `FEATURES.md` file in all repositories that warrant it. This file theoretically can be used by a marketing team to advertise a product.

Inkling Flow suggests that any issue marked `epic` should be included in a list (including contents) before any release. They can be organised by open and closed statuses.

These features will not be added to the list until they are closed.

Using the `epic` tag (case-insensitive) allows it to integrate nicely into tools like ZenHub, but the use of such tools is optional.

> NOTE: This isn't true right now.

## Release Documentation

This is the `CHANGELOG.md` file, GitHub Releases descriptions, and any blog posts or release documentation accompanied with an artifact. Inkling Flow suggests:

- You work normally with GitHub Issues, making sure everything has a milestone.
- You prepare a release candidate.
- You release a new version.
- `CHANGELOG.md` is automatically changed.
- A GitHub Release is automatically made.

## CI/CD Definition

In **bold**, we have steps you must define per type of framework.

- On a merge or a push to `master`, a script runs. It may automatically commit to `master` by updating certain files.
  - Versions are incremented in supported package metadata files.
  - `CHANGELOG.md` is updated with most recent changes. Human-readable changes are retained, if present.
  - `FEATURES.md` is updated.
  - Milestones are updated automatically.
- On any push to `master` or to an open pull request:
  - **Compile/test as usual.**
  - **Store any applicable artifacts in GitHub Registry.**
  - **Run any code quality tools available for the framework/language.**
- On any `git tag`.
  - **Package and publish release version.**
  - **Deploy to environments (if applicable).**

## Versioning Definition

A major difference between this an [SemVer](https://semver.org/) is that `PATCH` and `MINOR` are incremented even when backwards incompatible changes are made _before version `1.0.0`_.

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
  - If the project has a `major` version > 0, it is `release`, otherwise it is `pre-release`.
  - `0.1.13-pre-release` or `3.11.0`
- `feature` branches (based on the issue number and description) contain `feature` code.
  - Such code is not automatically tested nor deployed until a pull request is opened.
  - If a version is created and deployed, it is deployed as `feature` with reference to the issue number.
    - `0.5.13-feature+21`
    - This should rarely - if ever - happen.
