ADR 002: Why Selenium Appium?

Date: 13/09/2024

Status: Approved

## Context
We need to find way to control Natice App build by Flutter.

## Problem
Flutter dont give developers full control of UI Element, so it's not easy to locate elements from E2E testing.

## Options
### 1. Espresso

Pros:
* Deep Android * integration: Officially supported by Google, ensuring compatibility and stability for Android apps.
* Fast performance: Runs tests efficiently as it operates directly in the app’s instrumentation.
* Simple API: Easy to use and read for writing UI tests.
* Automatic synchronization: Handles waiting for UI elements automatically.
* Supports various UI tests: Can test complex interactions, including RecyclerView.
* Strong community support: Well-documented with a large user base.

Cons:
* Android-only: Does * not support iOS or other platforms.
* Challenging for complex apps: May struggle with highly dynamic or complex screens.
* Limited WebView support: Difficult to test apps that heavily rely on WebView.
* Setup can be tricky: Initial configuration may be complex for beginners.

### 2. Robot 

Pros:
* Versatile: Can test web, desktop, mobile apps, and APIs with various libraries (e.g., Appium for mobile).
* Keyword-driven: Easy to write and understand test cases using keyword-based syntax.
* Cross-platform: Works across multiple platforms and environments.
* Extensible: Can be extended with custom libraries in Python or Java.
* Good reporting: Provides detailed reports and logs for test execution.

Cons:
* Steeper learning curve: The keyword-driven approach may require time to get used to.
* Not optimized for mobile: Requires additional libraries (like Appium) to test mobile apps, adding complexity.
* Slower execution: Due to its high-level nature, tests may run slower compared to native frameworks.

### 3. Appium

Pros:
* Cross-platform: Supports both Android and iOS, allowing testing for multiple platforms with one framework.
* Language flexibility: Supports various programming languages (Java, Python, JavaScript, C#).
* Open-source: Free and widely supported by a large community.
* No app modification: Does not require modifying the app code to run tests.
* Supports real devices and emulators: Can test on both actual devices and virtual environments.

Cons:
* Slower execution: Appium tests can be slower, especially on real devices.
* Complex setup: Initial configuration can be tricky, especially for cross-platform projects.
* Limited to functional testing: Not ideal for non-functional testing, such as performance or load testing.
* Less stable on iOS: May experience occasional issues or instability with iOS testing compared to Android.

## Decision
We choose Appium because:
- Because it has [Flutter Integration Driver](https://github.com/AppiumTestDistribution/appium-flutter-integration-driver), with this we can do cross platform scenarios from web to moblie.

We did not choose Espresso and Robot because:
- Some of their cons: not support iOS, community smaller compared with Appium.
- They also can't work with Selenium.

## Negative Consequences
- The Flutter Integration Driver is quite new, but its maintainers are very active.
- It require a build for testing only.
