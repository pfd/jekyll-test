---
layout: default
title: SheerID Quickstart
permalink: /getting-started/quickstart
nav_order: 2
parent: Getting Started
description: Set up your first verification program with our easy-to-use campaign interface, and integrate a verification form into your site.
---

## Table of contents
{: .no_toc }

1. TOC
{:toc}

## Steps

In this Quickstart, we are going to create a Student verification program in the SheerID web app, and add a link
to your site that renders a student verification in a lightbox window. Next
we'll test the form for a successful verification using our
test methods.

1. Register SheerID account at my.sheerid.com.
1. Design a verification program.
1. Install the verification form on your site.
1. Test

## Create your account


## Create your first program

* Create a test verification program at <a href="https://my.sheerid.com" target="_blank">my.sheerid.com</a>.
* Install our JavaScript library and render a verification form for your test program.
* Simulate successful and failed outcomes for two verification [steps](./verification/steps): 1) Collecting
a student's personal information and 2) Document upload.

{% include note.html content="You can edit styles either directly on your site via css or via the web UI which passes the styles to your form, assuming you are using the custom one." %}

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
