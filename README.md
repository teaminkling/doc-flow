# Inkling Flow

A simple but robust configuration management process.

## Your Actions

In order to use Inkling Flow, you need to:

1. Add the `epic` and `breaking` labels to your organisation's default Issue labels.
2. Read through the rest of this file.

## Maintainer Documentation

1. Document your `README.md` file with build and deploy instructions.
2. Automate versioning in `package.json` and similar package metadata files.
    - Autoversion might help with this.

## Change Management

1. Prototype on `main` with no fear of breaking or Issues pre-`1.0.0`.
2. Changes after `1.0.0` should be associated to GitHub Issues.
   - Each has a mandatory Assignee and Milestone.
3. An assigned Issue should automatically create a branch, e.g., `i-512-short-description-here`.
    - Autobranch might help with this.
4. Available milestones are automated.
    - Automilestone might help with this.

## Release Documentation

1. Release by pushing a tag e.g., `pre-1.2.11`, `pre-0.18.0-rc2`.
2. Automate tagging of `1.2.11` and `pre-0.18.0-rc2` leading to GitHub Releases, artifact creation,
   and so on as required.
    - Autorelease might help with this.
3. `main` branch is stable; builds should succeed.

## Versioning and Branching

Just use [Semantic Versioning][semver-link]. Remember that `MAJOR` is only incremented from `0` to 
`1` on a first stable release; breaking changes before `1.0.0` are expected.

Branching is based on GitHub Flow and uses merge commits and encourages rebasing before pushes for
a semi-linear flow.

- `main` contains `dev` code.
  - `0.1.13-dev+2`
- Tags contain stable versions.
  - `0.1.13`
  - `3.11.0`
- `issue` branches (based on the issue number and description) are unstable.
  - They are never individually versioned.

## Extra Considerations

- Consider running some kind of code qualimetry on your codebase.
- Definitely try to follow Test-Driven Development/Behaviour-Driven Development.
- Set up code coverage at least before `1.0.0`.

[autosuite-organisation]: https://github.com/autosuite
