---
layout: default
title: JavaScript SDK
permalink: /integration/sdk
nav_order: 2
parent: Integration
has_children: true
---


# SheerID JavaScript Library
{: .no_toc }

Integrating SheerID verification forms into your site comes in 3 forms:

[Easy](/getting-started){: .btn .btn-green .fs-5 .mb-4 .mb-md-0 .mr-2 } [Intermediate](/integration/js-sdk){: .btn .btn-blue .fs-5 .mr-2 }[Advanced](/integration/api){: .btn .fs-5 .btn-black }



## Easy

[Easy](/getting-started){: .btn .btn-green .fs-5 .mb-4 .mb-md-0 .mr-2 }

**`MyStore.html`**
```html
<script>
var myForm = new sheerID.VerificationForm(
    document.getElementById('my-form'),
    '5bbd127d9781852f68e14ddc'
    );
</script>
```



## Intermediate

[Intermediate](/integration/js-sdk){: .btn .btn-blue .fs-5 .mr-2 }

You can use your own forms and scripts to gather user information, and call the SheerID functions directly, and handle responses
directly using our REST API.

**`MyStore.html`**
```html
<script>
// This object is built with MyStore's forms/scripts:
var formData = {
    firstName: 'John',
    lastName: 'Doe',
    email: 'j@d.com',
    birthDate: '2000-01-01',
    universityId: 231
}
sheerid.submitVerification(formData)
    .then(response => {
        MyStore.handleResponse(response);
    });
</script>
```

## Advanced

[Advanced](/integration/api){: .btn .fs-5 .btn-black }

Or you can use a combination of the two.

```html
<div id="my-form">
    <div id="my-fields">
        <input type="text" name="firstName" />
    </div>
    <div id= "sheerid-fields"><!-- Built with JS --></div>
</div>

<script>
    var currentChoice = 3;
    function onChange( newChoice ) {
        myStore.handleNewChoice(newChoice);
    }

sheerid.renderFormFieldUniversity('#sheerid-fields', currentChoice, onChange);

sheerid.submitVerification(formData)
    .then(response => {
        MyStore.handleResponse(response);
    });
</script>
```

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Introduction 

The SheerID JavaScript Library helps customers of SheerID quickly integrate gated offer programs (e.g. Student Verification) with their website and e-commerce workflows. 

We offer three levels of integration, depending on your need for customization. 

- **Drop-in Form** - the JavaScript Library renders the entire multi-step verification form for you in a lightbox overlay. 
- **Custom Form** - you render your own form, but interact with SheerID through the JavaScript Library, for greater control over the user experience. 
- **REST API** - you can bypass the JavaScript Library and interact with a REST API directly (typically for backend integrations). 

## Intended Audience

This document is for developers responsible for integrating a SheerID gated offer programs with their systems. The SheerID Javascript Library was designed for anyone with basic HTML/JavaScript skills. We support customization of look and feel through standard CSS hooks in the HTML (see [Styling](./styling)). The <a href="http://developer.sheerid.com" target="_blank">REST API</a> is still available for more complex use cases.

## This Document
For installation instructions, and to get started with the code, see our [quick start](../../getting-started/quickstart). 

See [flows](docs/flows) for an overview of how Gated Offer programs work.
 
Need Help? 
Contact <a href="mailto:helpdesk@sheerid.com">helpdesk@sheerid.com</a> if you have any integration questions. 


## Customization Options

You can totally customize.

* Styling
* Field Layout
* Internationalization

Here's an example of a new form method

```js
new 
window.sheerId.VerificationForm(document.getElementById('my-form'), '5bb2a0747f31442f3dd8e4be');
```

[Customize](/getting-started){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [Customize](/integration/js-sdk){: .btn .btn-blue .fs-5 .mr-2 }[REST API](/integration/api){: .btn .fs-5 .btn-green }