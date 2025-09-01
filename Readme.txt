 Overview

This project automates posting tweets with images stored in a Google Drive folder.
Captions are pulled from a companion Google Sheet (matched by filename), and each post is logged for tracking.

The workflow is built using **n8n** and integrates with **Google Drive, Google Sheets, and Twitter API**.



 Workflow

1. Google Drive Trigger → Watches a folder for new images
2. Get Row(s) in Sheet → Finds the caption for the image (matched by filename)
3. Download File → Gets the image file from Google Drive
4. HTTP Request → Uploads the image to Twitter (media endpoint)
5. Create Tweet → Posts the image + caption
6. Append Row in Sheet → Logs the post (time, file, caption, tweet ID, status)
7. Update Row in Sheet → Marks the caption entry as `done`

 Project Files

 `workflow.json` → Exported n8n workflow
 `README.md` → Documentation
 


 Requirements

 n8n (Cloud or Self-hosted)
 Google Drive API credentials
 Google Sheets API credentials
 Twitter API v2 credentials


Credentials Setup

Google Drive + Google Sheets

 Create a Google Cloud project
 Enable Google Drive API and Google Sheets API
 Create OAuth Client ID & Secret
 Share your Google Sheet with the service account email
 Add the credentials to n8n

 Twitter API

 Create a project in [Twitter Developer Portal](https://developer.twitter.com/)
Generate API keys & tokens
 Add credentials to n8n



  Google Sheet Setup

Captions Sheet

| Filename | Caption                        | ImageURL | Status  |
| -------- | ------------------------------ | -------- | ------- |
| sunset01 | Incredible sunset at the shore | ...      | done    |
| moonset  | asdasdasd                      | ...      | done    |
| earthset | asdawfertent                   | ...      | pending |



| Time | FileID | Filename | CaptionUsed | TweetID | Status |
| ---- | ------ | -------- | ----------- | ------- | ------ |



 Error Handling

 If caption is missing → Posts only the image
 If FileID already logged → Skips (deduplication)
 Errors are written to the PostLog with status = failed


 How to Run

1. Import `workflow.json` into n8n
2. Configure Google Drive, Google Sheets, and Twitter credentials
3. Update your Drive folder ID and Sheet ID inside the workflow
4. Activate workflow
5. Upload images to Drive → Tweets will be posted automatically



📸 Screenshots & Demo

Workflow (n8n editor)
Google Drive folder (X images)
Captions sheet
PostLog sheet
Video demo: `Automation Done.mp4`

