---
title: /info
position: 1.0
type: get
description: Retrieve theme
parameters:
  - name: name
    content: The name of the university you wish to verify
content_markdown: |-
  Get the theme data (messages and CSS) for a program
  {: .info }

left_code_blocks:
  - code_block: |-
      GET /rest/v2/info HTTP/1.1
      Authorization: Bearer <YOUR_API_TOKEN>
    title: HTTP
    language: http
  - code_block: |-
      curl -X GET \
        https://preview.sheerid.com/rest/v2/info \
        -H 'Content-Type: application/json' \
        -d '{
          "programId": "YOUR_PROGRAM_ID"
        }'

    title: Curl
    language: bash
right_code_blocks:
  - code_block: |2-
      {
          "sheeridVersion": "1.3.23.a0c14d160a6de518591a19c75544bc0297a4da18-SNAPSHOT",
          "sheeridGitCommit": "a0c14d160a6de518591a19c75544bc0297a4da18",
          "puppetGitCommit": "df47102b39f033007a0647f2dcaa1a40bb609ff3-dirty",
          "buildTimestamp": "2019-01-04T17:34:25Z"
      }
    title: Response
    language: json
  - code_block: |2-
      {
        "error": true,
        "message": "Bad request"
      }
    title: Error
    language: json
---