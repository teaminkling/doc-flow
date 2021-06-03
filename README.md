# Inkling Flow

A simple but robust configuration management process using ZenHub.

## Flow

TL;DR is that it's Scrum but easier and using just GitHub (and optionally ZenHub):

- Create a milestone/sprint for every upcoming version.
- Assign all issues to milestones.
- Tag with `vX.Y.Z` and manually release with your change notes.

### Planning a Milestone

Milestones are created manually when the need arises. Every two weeks, the minor or major version
goes up (see [specifics](#specifics) below) but sometimes hotfixes need to be applied.

These hotfixes often branch directly from the release and are cherrypicked from the issue branches
off the trunk. They are rare in software offering an API and non-existent in applications.

### Release a Version

When the `main` branch is ready for deployment, it is tagged with `v1.0.5` (for example). It must
have already passed quality checks for this.

After that, maintainers write release notes and then hit "Publish Release" in GitHub Releases.

## Specifics

### Versioning and Branching

We use [Semantic Versioning][semver-link]. Remember that `MAJOR` is only incremented from `0` to 
`1` on a first stable release; breaking changes before `1.0.0` are expected.

Branching is:

- Based on GitHub Flow (trunk).
- Uses merge commits on completion of a ticket.
- Encourages rebasing before merges.

Specifically:

- `main` contains `rc` code.
  - Deploys: `0.1.13-rc+2`.
- Tags contain production versions.
  - Deploys: `0.1.13`.
- `issue` branches (based on the issue number and description) are unstable.
  - Does not deploy/unversioned.

## Practices

### Maintainer Documentation

Document your `README.md` file with build and deploy instructions.

### Extra Considerations

- Code qualimetry should run locally and in each pull request via Actions.
- Try to follow Test-Driven Development/Behaviour-Driven Development.
- Set up code coverage at least before `1.0.0`.

[semver-link]: https://semver.org
