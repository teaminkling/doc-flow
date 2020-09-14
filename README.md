# Inkling Flow

A simple but robust configuration management process.

## Your Actions

In order to use Inkling Flow, you need to:

1. Add the `epic` and `breaking` labels to your organisation's default Issue labels.
2. Read through the rest of this file.
3. Browse the GitHub Actions in the [Autosuite][autosuite-organisation] organisation.

## Maintainer Documentation

1. Maintain your `README.md` file with build and deploy instructions.
2. Automate versioning in `package.json` and similar package metadata files.
    - Autoversion might help with this.

## Change Management

> Obviously, write concise and good commit messages even with ticketing.

1. Prototype on `main` with no fear of breaking or Issues.
2. Any change after `1.0.0` should be guided by a GitHub Issue.
3. Each GitHub Issue needs an Assignee and Milestone.
4. An assigned Issue should automatically create a branch, e.g., `i-512-short-description-here`.
    - Autobranch might help with this.
5. Milestones are automated.
    - Automilestone might help with this.
6. GitHub Projects are associated 1-to-1 with Milestones.
    - Autoproject might help with this.

## Release Documentation

1. Release by pushing a tag e.g., `pre-1.2.11`, `pre-0.18.0-rc2`.
2. Automate tagging of `1.2.11` and `pre-0.18.0-rc2` leading to GitHub Releases, artifact creation,
   and so on as required.
    - Autorelease might help with this.
3. `main` branch is stable; builds should succeed, tests should pass.

## Versioning and Branching

Just use [Semantic Versioning][semver-link]. Remember that `MAJOR` is only incremented from `0` to 
`1` on a first stable release, and breaking changes before `1.0.0` are expected.

Branching is based on GitHub Flow and uses merge commits and encourages rebasing before pushes for a semi-linear flow.

- `master` contains `rc` code.
  - `0.1.13-rc+2`
- Tags can deploy stable or `pre-release` code depending on the major version.
  - `0.1.13-pre-release`
  - `3.11.0`
- `issue` branches (based on the issue number and description) are unstable and tested on PR.

## Extra Considerations

- Consider running some kind of code qualimetry on your codebase.
- Definitely try to follow Test-Driven Development/Behaviour-Driven Development.
- Set up code coverage before `1.0.0`.

[autosuite-organisation]: https://github.com/autosuite
