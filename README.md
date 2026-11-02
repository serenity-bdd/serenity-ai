# Serenity BDD for AI coding assistants

A Claude Code plugin that helps an AI assistant write, fix and review [Serenity BDD](https://serenity-bdd.github.io) tests in Java. It describes **Serenity 5.4.2** (Playwright modules 5.3.11).

> **Generated.** This repository is built from [`docs/ai`](https://github.com/serenity-bdd/serenity-core/tree/main/docs/ai) in `serenity-core` by `skill/build-plugin.py`. Do not edit it here: open the issue or pull request against `serenity-core`.

## Install

```
/plugin marketplace add serenity-bdd/serenity-ai
/plugin install serenity-bdd@serenity
```

Then ask for Serenity work as usual ("add a Serenity test for the login page"). The skill loads when the request matches. To update later: `/plugin marketplace update serenity`.

## What is in it

| Part | What it does |
|---|---|
| `serenity-bdd` skill | Picks the style (Page Objects with `@Steps`, Screenplay, Cucumber; Selenium, Playwright or REST) or asks which one you want, then loads the reference for it: the exact packages, a mistakes table, compiling examples. Also covers `serenity.conf`, running tests, reading results from the JSON files, upgrading, and troubleshooting by symptom. |
| `serenity-test-reviewer` agent | Reads new tests and the report and checks that scenarios state their intent in business English, are grouped by function, and assert what their titles claim. It reports and does not edit. |
| `templates/agents-md/` | One `AGENTS.md` per style, to copy into a project so the assistant stays in that style. A plugin does not load these; copy the one you need to the project root as `AGENTS.md` (or `CLAUDE.md`). |

The skill never defaults to one style: Page Objects, Screenplay and Cucumber are all supported ways of working.

## How far to trust it

Every class and method named in the guidance is checked against the released jars, and the examples compile and their tests run, on each release (`skill/release-check.sh` in `serenity-core`). The pass rates measured so far, and the limits (Claude models and Claude Code only, live sample sites, 2 to 3 runs per case), are in the [evaluation write-up](https://github.com/serenity-bdd/serenity-core/blob/main/docs/ai/baseline-results.md). Treat the guidance as experimental.

Not covered: mobile (Appium), Spring and Guice object factories, cloud and grid capabilities, and Gradle beyond Cucumber.

## Licence

Apache 2.0, like Serenity BDD.
