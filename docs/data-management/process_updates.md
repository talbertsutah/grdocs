---
title: "Updating Letters for GradRecruit"
date: 2021-12-25T09:30:36-07:00
authors:
    - Tom Alberts
draft: false
---

## Overview

This explains how to upload data to the GradRecruit system. It assumes that you have already [downloaded the data from ApplyYourself](../download/download.md), and typically assumes that you have three types of data:

* an XML file with data for new applicants
* an XML file with data for new letter writers
* one or more PDF files with data for applicants
However these instructions work even if you have just one of these types of data.

**To complete the steps below you need to have access to the GradRecruit file system. Usually only one person has this access to this file system. Currently that person is Tom Alberts, but soon we will switch it to Paula Tooman.**

**If you don't have such access you need to contact Pieter Bowman, who can grant it to you. Show these instructions to him and he will know what needs to be done.**

## Quick Commands

These commands assume that the XML file containing updated applicant info is called **AppsUpdate.xml**

    setenv PATH /usr/uumath/ashare/anaconda/anaconda3/bin:$PATH
    source /usr/uumath/ashare/anaconda/anaconda3/etc/profile.d/conda.csh
    conda activate py3
    python3 importApps.py ../../Files/New/AppsUpdate.xml --DBupdate
    python3 pdfsplitter.py ../../Files/New/*.pdf
    conda deactivate

**After you have successfully executed these commands you should delete the files in the /Files/New/ directory on the department server.**

You can then disconnect from the webserver, if finished updating files.




