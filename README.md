# Inkling Flow

A simple but robust configuration management process using ZenHub.

## Flow

TL;DR:

- Create a milestone at the start of a new version of software.
- Assign all issues to milestones (assigned with descriptive titles).
- Tag. Manually release after writing release notes.

### Plan a Sprint/Milestone

Either this is a set period of time (as in Scrum) or a group of mandatory Issues. Either way, plan
by creating the Milestone first.

### Assign Issues to Milestones

Every Issue can only be worked on when it has both an Assignee and a Milestone. The titles should
be descriptive so the problem fixed is clearly understood from just the title.

### Pipeline Quality Checks

Pull Requests have quality checks. Every push to any branch checks the test suite and coverage.

### Release a Version

When the `main` branch is ready for deployment, it is tagged with `v1.0.5` (for example).
Maintainers write release notes and then hit "Publish Release" in GitHub Releases which triggers
a GitHub Action to perform common CI/CD tasks.

The version is figured out on each deployment. This is also how hotfixes are deployed (patch
versions for production).

## Specifics

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

Document your `README.md` file with build and deploy instructions.

### Extra Considerations

- Code qualimetry should run locally and in each pull request via Actions.
- Definitely try to follow Test-Driven Development/Behaviour-Driven Development.
- Set up code coverage at least before `1.0.0`.

[autosuite-organisation]: https://github.com/autosuite
[semver-link]: https://semver.org
