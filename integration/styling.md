---
layout: default
title: Styling
permalink: /integration/sdk/styling
nav_order: 1
parent: JavaScript SDK
grand_parent: Integration
---


# Styling

## SheerID Base Styles
We encourage you to include SheerID's stylesheet to provide basic style for the form.
```
<link rel="stylesheet" href="https://s3.amazonaws.com/com.sheerid.resources/common/kraken/0.0.2.sheerid.css" type="text/css" />
```

## Override CSS
You can override styles by including your own stylesheet after SheerID's.
View an example of overwritten styles on <a href="https://jsfiddle.net/AaronSheerID/n5h46dao/" target="_blank">JSFiddle here</a>


## Direct Step Access
When rendering the <a href="examples/entire-form.html" target="_blank">entire form</a>, you can directly access any step in the [verification flow](docs/flows) with a query parameter. This makes it easy to refresh the page and see your css changes, without having to fill out the form repeatedly.

We recommend styling each of these steps to suit your brand, since it's probable that some customers will reach any/all of them.

*Note: Submitting these mock steps won't work. To test the flow, see [test rules](docs/testRules)*

### Collect Student Personal Info Step
<a href="examples/entire-form.html?mockStep=collectStudentPersonalInfo" target="_blank">?mockStep=collectStudentPersonalInfo</a>


### Pending State
<a href="examples/entire-form.html?mockStep=pending" target="_blank">?mockStep=pending</a>


### Success
<a href="examples/entire-form.html?mockStep=success" target="_blank">?mockStep=success</a>


### Doc Upload
<a href="examples/entire-form.html?mockStep=docUpload" target="_blank">?mockStep=docUpload</a>


### Doc Review Limit Exceeded
<a href="examples/entire-form.html?mockStep=docReviewLimitExceeded" target="_blank">?mockStep=docReviewLimitExceeded</a>


### Error
<a href="examples/entire-form.html?mockStep=error" target="_blank">?mockStep=error</a>

### Loading
This is a special case where we show the loading spinner so it can be styled. Program information is not available for this application state.
<a href="examples/entire-form.html?mockStep=loading" target="_blank">?mockStep=loading</a>



