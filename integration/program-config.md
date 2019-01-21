---
layout: default
title: Program Config
permalink: /integration/api/program-config
nav_order: 3
parent: REST API
grand_parent: Integration
---

# Program Theme

The program theme object contains all theme and messaging information that was configured for a program in the self service tool. This includes a full CSS stylesheet
that can be included when rendering the form (as long as CSS selectors match), and any messaging that should be used throughout the verification process, including
field labels, success messages, etc. 

## Internationalization (i18n)

The program theme contains an `intl` property which is a structured JSON object containing translated messaging to use when rendering the forms to collect the data
necessary for the verification flow. This will also include custom messaging that was configured in the self service tool. 

### ErrorId

The `errorId` property under the `intl` property can be used to find error messaging to display to users when a given error is thrown. Any time a response has an 
`errorIds` property, it means an error occurred and appropriate messaging should be looked up here in the program theme based on the error ID that was returned. 

## Custom CSS

The `customCss` property on the program theme contains a CSS stylesheet as it was configured in the self service tool. This is heavily reliant on certain selectors
existing on the page, so it may or may not be useful when not using the JS client. 