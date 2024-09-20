ADR 003: Why Selenium Cucumber?

Date: 13/09/2024

Status: Approved

## Context
- Build a framework and use it are 2 separate topics.
- The question is, how easy is it to write a test case?

## Problem
- The people who write test cases don't have to understand how the framework has been built; they just need to know how to write and run them.
- People like Manual Tester and PO can write test cases with less training; there is no need to learn how to code.

## Options

Criteria | Cucumber (BDD) | Method Test Case (TestNG/JUnit)
-- | -- | --
Writing Style | Natural language (Gherkin) | Code written directly in methods
Readability | Easy to read for non-technical stakeholders | Suitable mainly for developers
Maintenance | Easier to maintain due to clear separation | Can be harder to maintain as test cases grow
Performance | May be slower due to translation between Gherkin and step definitions | Faster as there is no overhead
Scalability | Suitable for large projects with multiple stakeholders | Suitable for small projects
Collaboration | Better for cross-functional teams | Better for technical teams

## Decision
We choose Cucumber because:
- QA is not a big team, and we have many products to test, so we have to invoke as many people as possible, not just developers.

We still choose Method Test Case:
- But this is a second choice when we talk about writing test cases.

## Negative Consequences
- Build framework with Cucumber require high level of SDET.