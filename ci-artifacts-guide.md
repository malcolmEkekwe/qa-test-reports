# CI Artifacts Guide

The automated Playwright tests generate useful artifacts both locally and in the
continuous integration (CI) pipeline.  This document describes what to expect
and how to access these artefacts.

## HTML Report

Each test run produces an HTML report under the `playwright-report/` directory.
This report summarises passed and failed tests, screenshots and traces.  In CI,
the report is uploaded as an artifact named `playwright-report-<browser>` for
each browser in the matrix.

To view the report locally after a run:

```bash
npm run report
```

In GitHub Actions, navigate to the workflow run page, scroll to the
**Artifacts** section and download the report.  Extract the zip and open
`index.html` in your browser.

## Screenshots and Videos

Screenshots and videos are captured only on failures to keep runs lean.  They
are stored in `test-results/` during execution and are included inside the
HTML report.  On CI failures, they can be accessed via the same report.

## Traces

For the lean version, Playwright collects a trace on the first retry.  The
trace provides a full recording of the browser actions and network requests.
Traces are included in the HTML report and can also be viewed with
`npx playwright show-trace <path/to/trace.zip>` if downloaded separately.