# Inkling Flow

A simple but robust configuration management process.

## Your Actions

In order to use Inkling Flow, you need to:

1. Add the `epic` and `breaking` labels to your organisation's default Issue labels.
2. Read through the rest of this file.

## Flow

### Change Management

1. Prototype on `main` with no fear of breaking or Issues pre-`1.0.0`.
2. Changes after `1.0.0` should be associated to GitHub Issues.
   - Each has a mandatory Assignee and Milestone.
3. An assigned Issue should automatically create a branch, e.g., `i-512-short-description-here`.
4. Milestones are manually created and tracked.
    - Consider the user of a third party system such as ZenHub.

### Release Documentation

> `ink-release` performs automation for this.

1. Release by pushing a tag e.g., `pre-1.2.11`, `pre-0.18.0-rc2`.
2. Automate tagging of `1.2.11` and `pre-0.18.0-rc2` leading to GitHub Releases etc (as required).
3. `main` branch is stable; builds must succeed.

### Versioning and Branching

Just use [Semantic Versioning][semver-link]. Remember that `MAJOR` is only incremented from `0` to 
`1` on a first stable release; breaking changes before `1.0.0` are expected.

Branching is:

- Based on GitHub Flow (trunk).
- Uses merge commits on completion of a ticket.
- Encourages rebasing before merges.

Specifically:

- `main` contains `dev` code.
  - Deploys: `0.1.13-dev+2`.
- Tags contain production versions.
  - Deploys: `0.1.13`.
- `issue` branches (based on the issue number and description) are unstable.
  - Does not deploy/unversioned.

## Practices

### Maintainer Documentation

> `ink-version` helps with this.

1. Document your `README.md` file with build and deploy instructions.
2. Automate versioning in `package.json` and similar package metadata files.

### Extra Considerations

- Code qualimetry should run locally and in each pull request via Actions.
- Definitely try to follow Test-Driven Development/Behaviour-Driven Development.
- Set up code coverage at least before `1.0.0`.

[autosuite-organisation]: https://github.com/autosuite
