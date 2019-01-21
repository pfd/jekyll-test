---
layout: default
title: REST API
permalink: /integration/api
nav_order: 3
parent: Integration
has_children: true
---

# API Overview
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

The SheerID API is organized around REST.

## Base URL

```
https://preview.sheerid.com/rest/v2/
```

## Authentication

Requests use bearer auth.

```http
GET /rest/v2/info HTTP/1.1
Content-Type: application/json
Authorization: Bearer <YOUR_ACCESS_TOKEN>
```

Get your access token from the SheerID web application under _Settings_ »» _Access Tokens_.

## Errors 

Any response while interacting with the API could be an error response. There are two types of possible erros: one that can be recovered from and one that is fatal. 

### Recoverable Errors

A recoverable error will include the step the verification was on before the error occurred. So if I was attempting to submit a student subject for the `collectStudentPersonalInfo` step, I could receive this response:
```json
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "programConfig": {
        // See program config docs for description of contents
    },
    "currentStep": "collectStudentPersonalInfo", // The step in the verification flow the current verification is on
    "errorIds": [
        // The errors that occurred when attempting the step
    ]
}
```

The `errorIds` will indicate what went wrong, but since the `currentStep` is not `error` it means the issue could be corrected. These errors occur when bad data was
supplied, e.g. an invalid birth date, invalid email, invalid organization, etc. 

#### Messages

Recoverable errors can be caused by invalid entries from the user, so the messaging that should be shown can be found in the [program theme](docs/rest/programTheme.md) 
of the response that was returned. The messaging found in the `errorId` section of the messages should be appropriate to show users. 

#### Example

When submitting a student subject for the `collectStudentPersonalInfo` step, I sent this request:
```json
{
    "firstName": "First",
    "lastName": "Last",
    "birthDate": "1-1-1",
    "email": "notValidEmail,com",
    "universityId": 1
}
```

And this is the response:
```json
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "collectStudentPersonalInfo", // The step in the verification flow the current verification is on
    "errorIds": [
        "invalidBirthDate",
        "invalidEmail"
    ]
}
```

This lets me know I need to perform the `collectStudentPersonalInfo` step again, and I should find the `invalidBirthDate` and `invalidEmail` messages in the 
[program theme](docs/rest/programTheme.md) to find the message I should display to the user. 

### Non Recoverable Errors

A non recoverable error will have `error` as the `currentStep` and will provide both a list of `errorIds` as well as a `systemErrorMessage` that can be used to determine
what caused the failure to assist with debugging. An example error response would look like this:
```json
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "error", // The step in the verification flow the current verification is on
    "errorIds": [
        // The errors that occurred when attempting the step
    ],
    "systemErrorMessage": "Debugging message" // A description of the cause for the error to aid with debugging
}
```

These errors occur when programs or verifications are not found, when internal SheerID errors occur, or when a step can not be completed for a non-user related reason. 

#### Messages 

The supplied `errorIds` can be used to look up the user facing messages in the [program theme](docs/rest/programTheme.md) just like for recoverable errors, however
these can potentially be much more generic messages and difficult to understand. So to provide feedback for the integrator, the `systemErrorMessage` property can be used
to understand what went wrong. These messages are NOT intended to be displayed to users, they are only for the integrators benefit. 

#### Example

When submitting a student subject for the `collectStudentPersonalInfo` step, I sent this request:
```json
{
    "firstName": "First",
    "lastName": "Last",
    "birthDate": "1-1-1",
    "email": "notValidEmail,com",
    "invalidKey": "something"
}
```

And this is the response:
```json
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "error", // The step in the verification flow the current verification is on
    "errorIds": [
        "invalidRequest"
    ],
    "systemErrorMessage": "Unexpected property 'invalidKey', expected one of: firstName, lastName, birthDate, email, universityId, metadata"
}
```

This lets me know I need to change the structure of my student subject request, and I can look up the `invalidRequest` error in the 
[program theme](docs/rest/programTheme.md) to find the message I can show to the user. The `systemErrorMessage` tells me I need to remove the `invalidKey` property
and only use the provided allowed keys. 
