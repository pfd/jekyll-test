---
layout: default
title: Test Rules
permalink: /getting-started/verification/test-rules
nav_order: 5
parent: The Verification Process
grand_parent: Getting Started
---

# Test Rules
When a program is created at <a href="https://trial-preview.sheerid.com" target="_blank">trial-preview.sheerid.com</a>, it is in **test mode**.

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
