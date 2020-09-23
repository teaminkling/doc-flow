# Testing Guidelines

Testing is vital to software development and should be written first after software design.

## Contract-Based Testing

Client services must create a contract for what it produces and expects to consume from producer services. This will
be tested for each service (including frontend applications).

This will test the entire system without needing to package and run every service in an entire application (e.g., an
entire Kubernetes cluster just to run tests on one acceptance criterion).

### Acceptance Tests

For each service, software requirements (defined as Epics in GitHub Issues) tie to acceptance criteria. Epics also
correspond to major features in the software.

### Unit Tests

Unitary tests must be written for "complex" functions/methods to ensure correctness.

## Notes

We do not write integration tests and write our code to be multi-paradigm but mostly functional. However, quality
assurance is run separate to production versions and various forms of testing deployments (A-B testing, canary
deployments etc) are used for safety.
