ADR 004: Why not choose Testcontainers for Java?

Date: 16/09/2024

Status: Proposed 

## Context
We need a testing environment that isolates with another environment, and Testcontainers is the solution the dev team has chosen.

## Problem
New QA member doesn't think it's a good idea.

## Options

### Testcontainers for Java
Advantages of Testcontainers:
* Easy integration with tests: Automatically manages Docker containers within the test code.
* Isolated environments: Ensures a fresh environment for each test run.
* Efficient resource usage: Containers start and stop as needed, saving resources.
* Good CI/CD integration: Works well in automated pipelines for reliable tests.

Disadvantages of Testcontainers:
* Complex setup for large systems: Managing multiple services can be cumbersome.
* Slower startup for multiple containers: Initializing many services can take time.
* Requires programming knowledge: Not as user-friendly for non-developers.

### Local Docker Compose
Docker Compose Advantages over Testcontainers:
* Simple configuration: Easy to set up and manage multiple services using a single YAML file.
* User-friendly: Accessible to both developers and non-developers through a straightforward configuration file.
* Good for integration tests: Ideal for complex scenarios requiring multiple interdependent services.

Docker Compose Disadvantages compared to Testcontainers:
* Manual management: Containers need to be started and stopped manually or through additional scripts.
* Slower startup: May take longer to initialize all services at once.
* Less integration with test code: Does not provide automatic management of container lifecycle within test code.

### Separate Test Environment
Advantages of a Separate Test Environment for Selenium:
* Dedicated resources: Isolates testing environment from development and production, reducing interference.
* Consistent environment: Ensures tests run in a stable and controlled setup, minimizing external factors.
* Easier debugging: Dedicated environment can simplify troubleshooting and reproducing issues.

Disadvantages compared to Testcontainers:
* Resource overhead: Requires maintaining and managing a separate environment, which can be resource-intensive.
* Manual setup: Initial setup and configuration of the environment can be complex and time-consuming.
* Less flexibility: Does not offer the dynamic, on-the-fly container management that Testcontainers provides.

## Decision
- Testcontainers doesn't support rollback test data; we have to write a script for that.
- Testcontainers has one advantage: it manages Docker containers within the test code, which the QA team will not use because it slows down the test run.
- Testcontainers make the framework more complicated but don't bring enough benefit to the team.
- So, we chose Separate Test Environment auto-deployed by using Docker Compose.
- Separate Test Environment can be use for local and CI/CD test run.
- About isolates test data for each run; the pre-condition of E2E testing will handle that.

## Negative Consequences
- None