# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a minimal educational project ("Intro-to-CICD") used to demonstrate a basic CI/CD pipeline with GitHub Actions. It is not a full application — just a single function with a test and a CI workflow scaffold.

## Commands

```bash
npm install     # install dependencies (jest) — node_modules/ is gitignored and not present after clone
npm test        # run the Jest test suite
npx jest src/index.test.js -t "Says 'Hello Mike'"   # run a single test by name
```

## Architecture

- `src/index.js` — exports a single function, `sayHi(name)`, via `module.exports`.
- `src/index.test.js` — Jest test for `sayHi`.
- `.github/workflows/main.yml` — GitHub Actions CI workflow with two placeholder jobs (`build`, `test`) that only echo strings; the `test` job does not actually invoke `npm test` yet. This file is the intended target for CI/CD exercises in this repo.

## Known issue

`sayHi('Mike')` currently returns `'Hello there Mike'`, but `src/index.test.js` asserts it equals `'Hello Mike'`. The test suite fails as-is — this mismatch is likely intentional as a starting point for the CI/CD exercise (i.e., wiring up CI to catch a failing test), not an accidental bug to silently fix.
