---
layout: default
title: Quickstart
permalink: /getting-started/quickstart
nav_order: 1
parent: Getting Started
---

# Quickstart
{: .no_toc }

In this quickstart you will:


* Create a test verification program at <a href="https://trial-preview.sheerid.com" target="_blank">trial-preview.sheerid.com</a>.
* Install our JavaScript library and render a verification form for your test program.
* Simulate successful and failed outcomes for two verification [steps](./verification/steps): 1) Collecting
a student's personal information and 2) Document upload.



## Create a Verification Program

Let's begin by creating a program at <a href="https://trial-preview.sheerid.com" target="_blank">trial-preview.sheerid.com</a>. Programs created at the `trial-preview` site are in **test mode**
and do not access our production databases. We provide **test rules** to simulate successful
and failed outcomes in the verification workflow.

To test the [flow](./verification/flows), you can use the following rules:

### Test collectStudentPersonalInfo step
* Use an **even birth year** to simulate instant success.
* Use an **odd birth year** to simulate instant failure.

### Test docUpload step
After simulating instant failure (see above), you can simulate outcomes for the `docUpload` step as well.
* Upload a file with the name **SandboxTesting-ACCEPTED.png** to simulate a review with a successful outcome.
    * <a href="/assets/img/SandboxTesting-ACCEPTED.png" target="_blank">Download SandboxTesting-ACCEPTED.png</a>
* Upload a file with the name **SandboxTesting-REJECTED.png** to simulate a review with a rejected outcome.
    * <a href="/assets/img/SandboxTesting-REJECTED.png" target="_blank">Download SandboxTesting-REJECTED.png</a>

## Installation

Add css to the `<head>` of your html file.
```html
<link rel="stylesheet" href="https://preview.sheerid.com/docs/sheerid.css" type="text/css" />
```


Add the SheerID js library in the `<body>`.
```js
<script src="https://preview.sheerid.com/docs/sheerid.js"></script>
```

Render the verification form in a `div`.
```html
<div id="my-form"></div>
<script>
    var sheerid = window.sheerid;
    sheerId.setOptions({logLevel: 'info'});

    // Create a program at trial-preview.sheerid.com
    var myProgramId = '5bbd127d9781852f68e14ddc';
    var myDiv = document.getElementById('my-form');
    var myForm = new sheerId.VerificationForm(myDiv, myProgramId);
</script>
```

[*How to find my program's id*](docs/programs?id=programid)
