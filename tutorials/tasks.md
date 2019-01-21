---
layout: default
title: Tasks
parent: Tutorials
permalink: /tutorials/tasks
nav_order: 2
---

# Tasks WIP

Just going to put as many discrete tasks in here as possible, and
group them later.


## Self-Service App (my.sheerid.com)

* Create a program

* Find your program ID

* Customize

## JavaScript Library

* do some methods

## REST API

* make some calls




Sheer ID

Getting Started

I. So you want to do a verification. If you want to verify people's shit, then you have come
to the right place. We give you the tools to expose a verification utility on your website,
confirm a user's eligbility for an offer, and move on 



UI:
    browser
        render form
        render fields


Sheer ID: GETTING STARTED

* Installation

# Do stuff on your website
    * Add css to the <head> of your html file.
    * Add the SheerID js library in the <body>.
    * Render the verification form in a div.

# Do stuff on my.sheerid



When you do a verification tied to a program, you enter into the flow, starting with step 1. the current state of your flow will always be available usin the get state endpoint.



Example: Do a new verification using an odd birth year

1. POST https://preview.sheerid.com/rest/v2/verification
2. Response  "verificationId": "5c16e63955f50131bc52eaeb"
3. POST https://preview.sheerid.com/rest/v2/verification/5c16e63955f50131bc52eaeb/step/collectStudentPersonalInfo using odd year

{
  "firstName": "Pete",
  "lastName": "Davis",
  "email": "davispete@gmail.com",
  "birthDate": "1997-01-01",
  "universityId": 3499,
  "metadata": {
    "mascot": "Bruins"
  }

4. "currentStep": "docUpload"
5. POST https://preview.sheerid.com/rest/v2/verification/5c16e63955f50131bc52eaeb/step/docUpload/2a08cf47a1f344d2b218f33b40ae8a92

^^ docUpload step using the docupload token given in the previous response


curl -X POST https://preview.sheerid.com/rest/v2/verification/5c16e63955f50131bc52eaeb/step/docUpload/2a08cf47a1f344d2b218f33b40ae8a92 -H "Content-Type: multipart/form-data" -F "file=[~/Desktop/SandboxTesting-ACCEPTED.png]"

Success!! 

7. "currentStep": "success"
