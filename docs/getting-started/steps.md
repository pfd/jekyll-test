---
layout: default
title: Steps
permalink: /getting-started/concepts/steps
nav_order: 2
parent: Concepts
grand_parent: Getting Started
---

# Steps
A SheerID verification happens one step at a time.
Steps combine together into a flow. Read more about [flows](./flows) here.

The REST API will return a step name for what it expects to receive next, to progress the Verification through its flow. You will only ever need to render one step at a time.

See the [JavaScript API](../../integration/sdk) docs for details about individual request and response objects.



### Collect Student Personal Info Step
<a href="http://localhost:4000/examples/entire-form.html?mockStep=collectStudentPersonalInfo" target="_blank">?mockStep=collectStudentPersonalInfo</a>


### Pending State
<a href="http://localhost:4000/examples/entire-form.html?mockStep=pending" target="_blank">?mockStep=pending</a>


### Success
<a href="http://localhost:4000/examples/entire-form.html?mockStep=success" target="_blank">?mockStep=success</a>


### Doc Upload
<a href="http://localhost:4000/examples/entire-form.html?mockStep=docUpload" target="_blank">?mockStep=docUpload</a>


### Doc Review Limit Exceeded
<a href="http://localhost:4000/examples/entire-form.html?mockStep=docReviewLimitExceeded" target="_blank">?mockStep=docReviewLimitExceeded</a>


### Error
<a href="http://localhost:4000/examples/entire-form.html?mockStep=error" target="_blank">?mockStep=error</a>

### Loading
This is a special case where we show the loading spinner so it can be styled. Program information is not available for this application state.
<a href="http://localhost:4000/examples/entire-form.html?mockStep=loading" target="_blank">?mockStep=loading</a>
