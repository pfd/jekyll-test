---
layout: default
title: API Quickstart
permalink: /integration/api/quickstart
nav_order: 2
parent: REST API
grand_parent: Integration
---

# API Quickstart

[*Make sure you have your program ID before starting*]

{% include programs.md %}

## Retrive Theme (Optional)

If you would like to use the CSS and messaging that was configured in the self-service tool, then you will need to first fetch the 
[program theme](docs/rest/programTheme.md). To do this, make a `GET` request to `https://preview.sheerid.com/rest/v2/program/{programId}/theme`. 
See the [program theme docs](docs/rest/programTheme.md) for more information about what is contained in that payload. 

```json
{
    "intl": {
        "locale": "en-US",
        "messages": {
            "errorId": {
                "internalServerError": "Internal server error",
                "noProgram": "No program found",
                "noVerification": "No verification found",
                "invalidProgram": "Invalid program",
                "invalidStep": "Invalid step",
                "invalidOrganizationId": "Invalid organization",
                "invalidFirstName": "Invalid first name",
                "invalidLastName": "Invalid last name",
                "invalidBirthDate": "Invalid birthdate",
                "invalidEmail": "Invalid email",
                "underagePerson": "Underage",
                "outsideAgePerson": "Age outside allowed range",
                "futureBirthDate": "Future birthdate",
                "unsupportedDocMimeType": "One or more files is an unsupported format",
                "invalidFileSizeEmpty": "One or more files is empty",
                "invalidFileSizeMax": "One or more files is too large (max: 10MB)",
                "invalidNumberOfFiles": "Maximum number of files exceeded (max: 5)",
                "invalidDocUploadToken": "Provided document upload token is not valid",
                "verificationLimitExceeded": "Verification limit exceeded",
                "docReviewLimitExceeded": "Document review limit exceeded",
                "maxMetadataValuesExceeded": "Maximum number of metadata values exceeded",
                "maxMetadataLengthExceeded": "Maximum length of metadata value exceeded",
                "unknownError": "Unknown Error",
                "invalidRequest": "Invalid request"
            },
            "dateTime": {
                "january": "January",
                "february": "February",
                "march": "March",
                "april": "April",
                "may": "May",
                "june": "June",
                "july": "July",
                "august": "August",
                "september": "September",
                "october": "October",
                "november": "November",
                "december": "December",
                "month": "Month",
                "day": "Day",
                "year": "Year"
            },
            "schoolName": "School Name",
            "error": "Error",
            "sheerIdFaqs": "SheerID FAQs",
            "poweredBy": "Verification services powered by SheerID",
            "personalInformation": "Personal Information",
            "birthDate": "Birth Date",
            "school": "School",
            "verifyAndContinue": "Verify and continue",
            "studentInfoShared": "Information entered into this web form will be used for verification purposes. The information will be shared with Students.com.",
            "requiredFields": "All fields are required",
            "step": {
                "collectStudentPersonalInfo": {
                    "subtitle": "Confirm your eligibility by simply completing the form below.",
                    "title": "Verify your details",
                    "formTitle": "Personal information"
                },
                "docUpload": {
                    "acceptedTypes": "Acceptable file types: png, gif, jpg, bmp, pdf",
                    "title": "Documentation Needed",
                    "subtitle": "Please upload a document that clearly shows your first name, last name, valid dates and/or status.",
                    "footer": "Please omit, cover up or black out any sensitive information such as Social Security Number, bank information, etc.",
                    "submitButtonLabel": "Continue"
                },
                "pending": {
                    "subtitle": "The review process has now started. You will be contacted via email in less than 20 minutes with details regarding your verification request.",
                    "title": "Under Review",
                    "subtitle2": "NOTE: If you do not receive an email within the time shown above, you may want to check your junk/spam folder for the message."
                },
                "success": {
                    "title": "Congratulations!",
                    "subtitle": "Your status has been verified."
                }
            }
        }
    },
    "customCss": "/* \n\n**********************\nATTENTION - This configuration is written by sheerid-web-apps, my.sheerid.com\n**********************\n\n */\n        /* The following code is customer provided */\n        \n        .sid-text-input {\n background: pink; \n}\n\n        \n        "
}
```

## Retrieve Verification Segment

Now we need to begin a verification. This will retrieve what kind of segment you will be verifying against (Student, Active Military, Inactive Military, Teacher, etc.).

To retrieve the initial step for your [flow](docs/flows.md), make the following `POST` request:

URL: `https://preview.sheerid.com/rest/v2/verification`

Request Body:
```
{
    "programId": "YOUR PROGRAM ID HERE"
}
```
Response:
```
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "collectStudentPersonalInfo", // The step in the verification flow the current verification is on
    "submissionUrl": "https://preview.sheerid.com/rest/v2/verification/111111111111111111111111/step/collectStudentPersonalInfo" // The URL to hit for the current step
}
```

At this point a verification has begun and can be referenced with the `verificationId`, in the example case `111111111111111111111111`. This ID will be used for all
future interactions with this verification ID. 

## Verify a User

Now that we have our step (in our demo case we are verifying a student, so our step is `collectStudentPersonalInfo`), we can submit a verification subject to verify. 
We will be submitting a student for verification, so we will need to fill out this structure:

```
{
    "firstName": "",
    "lastName": "",
    "email": "",
    "birthDate": "YYYY-MM-DD",
    "universityId": 0
}
```
<a href="docs/generated/js-lib/modules/_types_.html" target="_blank">*Schemas for all verification subjects can be found here*</a>

Once all data has been collected, make a `POST` call to the URL collected in the previous step's `submissionUrl` response with the data, e.g.
```
{
    "firstName": "First",
    "lastName": "Last",
    "email": "demo@sheerid.com",
    "birthDate": "1980-01-01",
    "universityId": 1
}
```

This example will cause an instant success response because it uses an even birth year. To see comprehensive testing rules, see the [test rules](docs/testRules.md) 
documentations. 

### Success

If the verification was successful, then you will receive a response like this:
```
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "success", // The step in the verification flow the current verification is on
    "rewardCode": "REWARD" // The reward code that was configured in the self service tool
}
```

After providing the `rewardCode` to your user to be used in your system, you're done!

### Document Review

If the verification was unsuccessful, then you will need to collect document(s) that prove the user is part of the verification segment to be provided to SheerID 
for review. The document review response will be returned after submitting the personal info of the user if the user could not be verified instantly, and will look 
something like this:
```
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "docUpload", // The step in the verification flow the current verification is on
    "submissionUrl": "https://preview.sheerid.com/rest/v2/verification/111111111111111111111111/step/docUpload/1234" // The URL to hit for the current step
}
```

After collecting the documents, they should be submitted to SheerID by making a `POST` request to the `submissionUrl` provided in the doc upload response. This 
request must use the `multipart/form-data` `Content-Type` header, and should specify each file with a key beginning with `file` e.g.

```
file1=first file...
file2=second file...
file3=third file...
```

Once all files have been submitted, you will receive a `pending` response.

### Pending

If documents have been successfully uploaded to SheerID for review, then you will receive a response that looks like this:
```
{
    "verificationId": "111111111111111111111111", // Verification ID that should be used for all future calls
    "currentStep": "pending", // The step in the verification flow the current verification is on
    "statusUrl": "https://preview.sheerid.com/rest/v2/verification/111111111111111111111111" // The URL to poll for current status
}
```

The `statusUrl` is the URL used to retrieve the current status of the verification. This endpoint can be polled to watch for changes to the verification state. If 
a document review is completeled and marked successful (the document proved the user was associated with the segment), then you will receive the `success` response. 
If the document review was marked rejected (the document did not prove the user was associated with the segment), the you will receive the `docUpload` response so 
the user has a change to upload different documentation. The user has a limited number of times they can perform this operation. If the document review is still in 
progress, you will continue to get the `pending` response. 

### Getting Current Status

The current status of a verification can be retrieved at any time by making a `GET` request to `https://preview.sheerid.com/rest/v2/verification/{verificationId}`. The 
response from this endpoint will match the responses you get a various points through the flow (`success`, `docUpload`, `pending`, `error`, etc.). This endpoint can be 
used to continue a verificaiton that was halted at any point. 

### Errors

To see detailed descriptions of errors that could occur during the verification flow, see the [errors documentation](docs/rest/errors.md).