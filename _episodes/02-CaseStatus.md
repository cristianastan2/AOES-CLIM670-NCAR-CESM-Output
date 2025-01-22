---
title: "CaseStatus"
teaching: 0
exercises: 0 
questions:
- "What does the CaseStatus file tell me about my model experiment?"
objectives:
- "Learn how to check the status of an experiment"
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
 2025-01-17 17:31:25: case.build success 
 ---------------------------------------------------
2025-01-20 17:23:14: case.submit starting 
 ---------------------------------------------------
2025-01-20 17:23:28: case.submit success case.run:7534849.desched1, case.st_archive:7534850.desched1
 ---------------------------------------------------
2025-01-20 17:23:44: case.run starting 
 ---------------------------------------------------
2025-01-20 17:23:52: model execution starting 
 ---------------------------------------------------
2025-01-20 17:26:37: model execution success 
 ---------------------------------------------------
2025-01-20 17:26:37: case.run success 
 ---------------------------------------------------
2025-01-20 17:26:52: st_archive starting 
 ---------------------------------------------------
2025-01-20 17:27:17: st_archive success 
 ---------------------------------------------------
~~~
{: .output}

From this we can see `model execution success` indicates the model ran successfully and `st_archive_success` indicates that the archiving job ran successfully. Remember that when we submitted the model, two jobs were sent to the queue, the model run and the archive job.  Both appear to have run successfully.

> ## Troubleshooting
>
> Does anyone have a `CaseStatus` file that indicates the model did not run successfully? 
>
{: .challenge}

