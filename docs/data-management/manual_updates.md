---
title: "Manual Data Uploads"
date: 2021-12-25T09:30:36-07:00
authors:
    - Tom Alberts
draft: false
---

## Overview

Sometimes students send us updates to their application *after* they have submitted it through ApplyYourself. They typically do this by e-mailing the file directly to Paula Tooman. Typical updates are:

* updated transcripts, when they weren't available at the time of submission
* updated CVs or statements of purpose
* updated papers or other supplementary documents
* updated letters of reference, although generally these should **not** be submitted by the applicant


**To complete the steps below you need to have access to the GradRecruit file system. Usually only one person has this access to this file system. Currently that person is Tom Alberts, but soon we will switch it to Paula Tooman.**

**If you don't have such access you need to contact Pieter Bowman, who can grant it to you. Show these instructions to him and he will know what needs to be done.**

## Uploading Data to GradRecruit

1. Run the command that you use to access the file system. This will vary depending on the system that Pieter Bowman has set up for you. Its purpose is to mount the department webserver onto your local computer, so that you can drag and drop files that you've downloaded to the department server. You need to be able to mount the directory **/home/www/htdocs/gradrecruit/** to your computer.
2. Once you have that mounted onto your file system, in the gradrecruit directory look for the **/Files/byAppID/** directory. It contains a large number of folders, named after the Application ID of each applicant. Each Application ID is a 7 digit number in the current system.
3. Look for the Application ID of the student who wants their file uploaded. Hopefully the student included that with their email. If not, you can go to the [GradRecruit main page](https://www.math.utah.edu/gradrecruit/) and click on **All applicants**. A list of all submitted applications (for that term) comes up, and you can sort it by last name to find the Application ID of whoever you are looking for.
4. Each applicant's folder contains a subdirectory called **Standard**. Typically updated files should **NOT** go inside the "Standard" subdirectory. Instead place them alongside the "Standard" subdirectory. Then when you go to the applicant's webpage by visiting

        https://www.math.utah.edu/gradrecruit/applicant.php?ID=XXXXXXX
    where 'XXXXXXX' is replaced by their Application ID, the file should appear in the section called "Supplementary Files". **You should give the file a descriptive name so that people viewing the webpage have a good idea of what it is.**

5. If the file is a transcript, CV, statement of purpose, or letter of recommendation, you *may* want to put it in the "Standard" subdirectory. **If you do this the filename must follow the format of the files in that subdirectory.** Otherwise our webpages won't know what to do with the file and it will never be displayed. The filename formats are:

    * 'Transcripts': Transcript-XXXXXXX-Y, where XXXXXXX is the 7 digit Application ID and Y is the number of the transcript in the order that schools were inputted by the applicant
    * 'CV': CV-XXXXXXX.pdf, where XXXXXXX is the 7 digit Application ID
    * 'Statement of Purpose': SoP-XXXXXXXX.pdf, where XXXXXXX is the 7 digit Application ID
    * 'Recommendation Letter': Letter-XXXXXXX-YYYYYYY.pdf, where XXXXXXX is the 7 digit Application ID and YYYYYYY is the 7 digit Recommender ID
    * 'Full Application File': Full-XXXXXXX.pdf, where XXXXXXX is the 7 digit Application ID


