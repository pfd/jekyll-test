---
layout: default
title: Test Rules
permalink: /getting-started/test-rules
nav_order: 3
parent: Getting Started
description: This page is doomed. Doesn't need to be a standalone page. Thinking of adding "test mode" as a concept page, as well as a glossary definition, and add `test-rules.html` as an include, to be referenced in tutorials.
---

## Overview

When a program is created at <a href="https://my.sheerid.com" target="_blank">my.sheerid.com</a>, it is in **test mode**.

To test the [flow](./flows), you can use the following rules:

### Test collectStudentPersonalInfo step
* Use an **even birth year** to simulate instant success.
* Use an **odd birth year** to simulate instant failure.

### Test docUpload step
After simulating instant failure (see above), you can simulate outcomes for the `docUpload` step as well.
* Upload a file with the name **SandboxTesting-ACCEPTED.png** to simulate a review with a successful outcome.
    * <a href="/assets/img/SandboxTesting-ACCEPTED.png" target="_blank">Download SandboxTesting-ACCEPTED.png</a>
* Upload a file with the name **SandboxTesting-REJECTED.png** to simulate a review with a rejected outcome.
    * <a href="/assets/img/SandboxTesting-REJECTED.png" target="_blank">Download SandboxTesting-REJECTED.png</a>
