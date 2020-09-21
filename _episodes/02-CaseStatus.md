---
title: "CaseStatus"
teaching: 0
exercises: 0 
questions:
- "What does the CaseStatus file tell me about my model experiment?"
objectives:
keypoints:
---

### The `CaseStatus` file

Let's start by going to the `CASEROOT` directory for your first experiment and looking at the `CaseStatus` file:

~~~
$ cd ~/cases/b.day1.0
$ cat CaseStatus
~~~
{: .language-bash}

~~~
 ---------------------------------------------------
2020-09-15 11:00:30: case.submit starting
 ---------------------------------------------------
2020-09-15 11:00:38: case.submit success case.run:4141153.chadmin1.ib0.cheyenne.ucar.edu, case.st_archive:4141154.chadmin1.ib0.cheyenne.ucar.edu
 ---------------------------------------------------
2020-09-15 11:21:16: case.run starting
 ---------------------------------------------------
2020-09-15 11:21:22: model execution starting
 ---------------------------------------------------
2020-09-15 11:23:58: model execution success
 ---------------------------------------------------
2020-09-15 11:23:58: case.run success
 ---------------------------------------------------
2020-09-15 11:24:10: st_archive starting
 ---------------------------------------------------
2020-09-15 11:24:18: st_archive success
 ---------------------------------------------------
~~~
{: .output}

From this we can see `model execution success` indicates the model ran successfully and `st_archive_success` indicates that the archiving job ran successfully. Remember that when we submitted the model, two jobs were sent to the queue, the model run and the archive job.  Both appear to have run successfully.

> ## Troubleshooting
>
> Does anyone have a `CaseStatus` file that indicates the model did not run successfully? 
>
{: .challenge}

