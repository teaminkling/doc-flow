# Testing Guidelines

The development life cycle is:

1. Identify the problem.
2. Design a solution.
3. Write tests.
4. Implement.
5. Ensure quality.
6. Deploy.

## Contract-Based Testing

- Client services must create a contract for what it produces and expects to consume from producer services.
  - This is applicable for each service (including frontend applications).
  - This tests the entire system without needing to package and run every service in an entire application.

### Acceptance Tests

- For each service, software requirements (defined as Epics in GitHub Issues) tie to acceptance criteria.
- Such tests may need to test third party integrations (network-enabled calls) or I/O (database or file).

### Unit Tests

- Unitary tests must be written for "complex" functions/methods to ensure correctness.

## Notes

- We do not write integration tests.
- We write our code to be multi-paradigm but mostly functional.
- Quality Assurance (QA) is run separate to production versions and various forms of testing deployments.
  - A/B Testing.
  - Canary Deployments.
