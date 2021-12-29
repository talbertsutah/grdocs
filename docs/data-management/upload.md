---
title: "Uploading ApplyYourself Data to GradRecruit"
date: 2021-12-25T09:30:36-07:00
authors:
    - Tom Alberts
draft: false
---

## Overview

This explains how to upload data to the GradRecruit system. It assumes that you have already [downloaded the data from ApplyYourself](download.md), and typically assumes that you have three types of data:

* an XML file with data for new applicants
* an XML file with data for new letter writers
* one or more PDF files with data for applicants
However these instructions work even if you have just one of these types of data.

**To complete the steps below you need to have access to the GradRecruit file system. Usually only one person has this access to this file system. Currently that person is Tom Alberts, but soon we will switch it to Paula Tooman.**

**If you don't have such access you need to contact Pieter Bowman, who can grant it to you. Show these instructions to him and he will know what needs to be done.**

## Uploading Data to GradRecruit

1. Run the command that you use to access the file system. This will vary depending on the system that Pieter Bowman has set up for you. Its purpose is to mount the department webserver onto your local computer, so that you can drag and drop files that you've downloaded to the department server. You need to be able to mount the directory **/home/www/htdocs/gradrecruit/** to your computer.
2. Once you have that mounted onto your file system, in the gradrecruit directory look for the **/Files/New/** directory. It should be empty, and if not you can likely delete what is in there. **Usually this directory should be kept empty, except for when adding files.**
3. Drag and drop the files you wish to upload into the **/Files/New/** directory. It may take a few seconds for them to fully upload.



