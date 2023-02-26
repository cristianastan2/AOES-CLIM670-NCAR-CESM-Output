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
2023-02-20 10:25:32: case.submit starting 
 ---------------------------------------------------
2023-02-20 10:25:40: case.submit success case.run:8671655.chadmin1.ib0.cheyenne.ucar.edu, case.st_archive:8671656.chadmin1.ib0.cheyenne.ucar.edu
 ---------------------------------------------------
2023-02-25 19:05:16: case.submit starting 
 ---------------------------------------------------
2023-02-25 19:05:25: case.submit success case.run:8732081.chadmin1.ib0.cheyenne.ucar.edu, case.st_archive:8732082.chadmin1.ib0.cheyenne.ucar.edu
 ---------------------------------------------------
2023-02-25 19:05:29: case.run starting 
 ---------------------------------------------------
2023-02-25 19:05:37: model execution starting 
 ---------------------------------------------------
2023-02-25 19:08:09: model execution success 
 ---------------------------------------------------
2023-02-25 19:08:09: case.run success 
 ---------------------------------------------------
2023-02-25 19:08:16: st_archive starting 
 ---------------------------------------------------
2023-02-25 19:08:24: st_archive success 
 ---------------------------------------------------
~~~
{: .output}

From this we can see `model execution success` indicates the model ran successfully and `st_archive_success` indicates that the archiving job ran successfully. Remember that when we submitted the model, two jobs were sent to the queue, the model run and the archive job.  Both appear to have run successfully.

> ## Troubleshooting
>
> Does anyone have a `CaseStatus` file that indicates the model did not run successfully? 
>
{: .challenge}

