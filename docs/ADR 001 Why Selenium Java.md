ADR 001: Why Selenium Java?

Date: 2024-09-12

Status: Approved


## Context
- We need to build framework to test all Linagora products.

## Problem
- The team behind this framework is about 2 or 3 SDET.
- We don't know how complex the eco will become in feature.

## Options

### Playwright
1. Pros:
* Cross-browser support: Runs on Chrome, Firefox, and WebKit (Safari) with a single API.
* Multi-language support: Includes JavaScript, Python, C#, and Java.
* Auto-waiting mechanism: Reduces flaky tests by waiting for elements to be ready.
* Browser context isolation: Allows parallel test execution without interference.
* Headless and headful execution: Suitable for both speed and debugging.
* Network mocking and interception: Easy to simulate network conditions and application behavior.
* Device emulation: Supports mobile device emulation and responsive design testing.
* Detailed tracing and debugging: Provides video, screenshots, and trace files for troubleshooting.

2. Cons:
* Smaller community and ecosystem: Fewer tutorials and third-party tools compared to Selenium or Cypress.
* Resource-intensive: Running multiple browser contexts or tests can consume significant resources.
* Limited real-device support: Only emulates mobile devices, no support for actual devices.
* Challenging integration with Selenium Grid: Requires additional setup for distributed testing.
* Limited support for older browsers: Not ideal for testing on outdated browsers like Internet Explorer.


### Cypress
1. Pros:
* Easy setup and use: Cypress is straightforward to install and configure, with a user-friendly API.
* Real-time browser preview: Provides a real-time view of test execution, which helps in debugging.
* Automatic waiting: Handles asynchronous operations and waits for elements automatically, reducing flaky tests.
* Built-in assertion library: Includes built-in assertions, reducing the need for additional libraries.
* Time-travel debugging: Allows you to inspect the state of your application at each step of the test.
* Network stubbing: Easily mock and intercept network requests for more controlled testing environments.
* Comprehensive documentation: Offers extensive documentation and examples to help with testing setup and best practices.

2. Cons:
* Limited browser support: Primarily supports Chrome and Chromium-based browsers, with limited support for Firefox and no support for Safari.
* No support for multiple tabs or windows: Cannot handle tests that require interaction across multiple tabs or browser windows.
* Resource-intensive: Can consume significant system resources, especially with a large number of tests or complex scenarios.
* Not ideal for legacy browsers: Lacks support for older browsers like Internet Explorer.
* Limited to JavaScript: Focuses solely on JavaScript, so it's not suitable for projects using other languages.

### Selenium
1. Pros:
* Broad browser support: Selenium works with major browsers like Chrome, Firefox, Safari, and Edge, allowing cross-browser testing.
* Tool integration: It integrates well with TestNG, JUnit, Cucumber, and Maven, creating a complete test framework.
* Large community: Selenium has extensive documentation and a large support community.
* Rich libraries: Offers robust libraries for interacting with web UI components.
* Scalability: Easily extendable for complex testing like performance (JMeter), API (RestAssured), and mobile (Appium).
* Flexibility: Supports various test levels (UI, integration, unit) and integrates smoothly with CI/CD pipelines.
* Remote control: Selenium Grid allows remote browser control and parallel testing across environments.

2. Cons:
* Complex setup: Requires more configuration and setup compared to Cypress or Playwright.
* Slower execution: Can be slower due to the need for WebDriver interactions and communication.
* Flaky tests: More prone to flaky tests compared to Playwright and Cypress due to timing issues.
* Limited real-time feedback: Doesn’t offer real-time test previews or time-travel debugging.

## Decision

We choose selenium because:
- It is the most powerful tool. If we only have a small product, Selenium may be too powerful to use, but we are big.
- We need it in Java because our developers feel comfortable with it. The dev team and QA team will work together on this framework.

We not choose playright and cypress because:
- They can't control native app, they support Web Platform only.

## Negative Consequences
- The core of this framework will be more complicated than a normal framework that has been built with Selenium.