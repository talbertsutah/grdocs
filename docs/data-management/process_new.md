---
title: "Uploading ApplyYourself Data to GradRecruit"
date: 2021-12-25T09:30:36-07:00
authors:
    - Tom Alberts
draft: false
---

## Overview

This explains how to process **new applicant** data that has been downloaded from ApplyYourself and uploaded to the webserver. It assumes that you have already [downloaded the data from ApplyYourself](download.md) and [uploaded the following to the webserver](upload.md):

* an XML file with data for new applicants
* an XML file with data for new letter writers
* one or more PDF files with data for applicants

**To complete the steps below you need to have access to the GradRecruit file system. Usually only one person has this access to this file system. Currently that person is Tom Alberts, but soon we will switch it to Paula Tooman.**

**If you don't have such access you need to contact Pieter Bowman, who can grant it to you. Show these instructions to him and he will know what needs to be done.**

**You also must have access to the Python scripts that process the data. See the Python page for how to get this access and do a one-time setup of the scripts.** 

## Quick Commands

The next section explains what each command does. You can copy and paste the following and enter it into your terminal to process the new data.

These commands assume that the XML file containing new applicant info is called **AppsNew.xml**, and the one containing new recommender info is called **RecsNew.xml**

    setenv PATH /usr/uumath/ashare/anaconda/anaconda3/bin:$PATH
    source /usr/uumath/ashare/anaconda/anaconda3/etc/profile.d/conda.csh
    conda activate py3
    python3 importApps.py ../../Files/New/AppsNew.xml -n newappid.txt  -m
    python3 importReccs.py ../../Files/New/RecsNew.xml -n newrecs.txt
    python3 mkappdir.py -f newappid.txt -s
    python3 pdfsplitter.py ../../Files/New/*.pdf
    python3 SoPscanner.py -f newappid.txt
    conda deactivate

**After you have successfully executed these commands you should delete the files in the /Files/New/ directory on the department server.**

You can then disconnect from the webserver, if finished updating files.

## Detailed Explanation

This section explains in depth what each of the commands above is doing.

1.  Accessing the department Python:

        setenv PATH /usr/uumath/ashare/anaconda/anaconda3/bin:$PATH
        source /usr/uumath/ashare/anaconda/anaconda3/etc/profile.d/conda.csh
    
    These commands activate anaconda, which is used by Python on the department webservers. If this ever doesn't work we need to contact Pieter Bowman.
    
2.  Activating the Python Environment:

        conda activate py3
    
    py3 is the environment used by our Python scripts. **This command will only work if this environment has already been installed for your user.**  
    
3.  Pushing data from applicant XML files to our database
    
        python3 importApps.py ../../Files/New/AppsNew.xml -n newappid.txt  -m      

    This cycles through the XML data obtained from ApplyYourself, and inserts the applicant data into our database. The *-n* option prints out a list of Application IDs for new applicants to the file *newappid.txt*. Subsequent steps use that file so this should not be deleted. The *-m* option emails statistics about the number of applications uploaded to a select list of people. To see more options for the importApps.py program use
    
        python3 importApps.py -h
        
4.  Pushing data from recommender XML files to our database
      
        python3 importReccs.py ../../Files/New/RecsNew.xml -n newrecs.txt
        
    This cycles through the XML data obtained from ApplyYourself, and inserts the recommender data into our database. The *-n* option prints out a list of Recommender IDs for new applicants to the file *newrecs.txt*. As of December 2021 that text file is not used in later steps so the *-n* option could probably be removed. To see more options for the importReccs.py program use
    
        python3 importReccs.py -h
        
5.  Make file directories for new applicants

        python3 mkappdir.py -f newappid.txt -s

    This program makes a new directory on the filesystem for each new applicant. It follows a standard naming convention that can be found in the source code of the program. The list of applicant IDs comes from the file *newappid.txt*. The *-s* option creates symlinks for alternative ways of accessing individual applications (other than AppIDs), although as of December 2021 it is not clear that these symlinks actually work.
    
6.  Split the downloaded pdf files into multiple pieces

        python3 pdfsplitter.py ../../Files/New/*.pdf
        
    This program takes the applicant PDF files and splits them into multiple pieces. This is what allows us to look at individual pieces of the application (letters, transcripts, etc) on the webpage. This program sorts the new PDF files into the directories created by *mkappdir.py* in the last step.
    
7.  Scan the statement of purpose for relevant information

        python3 SoPscanner.py -f newappid.txt
        
    This program scans each new applicant's statement of purpose, looking for relevant information. As of December 2021 it is searching for faculty names that the applicant may have mentioned. This information gets stored in our database.
    
8.  Deactivate the python environment

        conda deactivate    
