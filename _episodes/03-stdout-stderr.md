---
title: "Standard error and standard out"
teaching: 0
exercises: 0 
questions:
- "What do the stderr and stdout files tell me?"
objectives:
keypoints:
---

### Standard error and standard out files

In your `CASEROOT` directory, your model produced files like `b.day1.0.run.o*` and `b.day1.0.st_archive.o*`.  These files produce output related to our submit script.  If the model and/or archiving did not run to completion, you will also have a `b.day1.0.run.e*` and/or `b.day1.0.st_archive.e*` file.  The ones with `*.o*' are called standard out (stdout) and the ones with `*.e*` are called standard error (stderr).  

The end of the file usually contains the most useful information, so you can use the Unix `tail` command to look at the end of the file:

~~~
$ tail b.day1.0.run.o7534849
~~~
{: .language-bash}

~~~
 - Case input data directory (DIN_LOC_ROOT) is /glade/campaign/cesm/cesmdata/inputdata 
 - Checking for required input datasets in DIN_LOC_ROOT
-------------------------------------------------------------------------
2025-01-20 17:23:52 MODEL EXECUTION BEGINS HERE
run command is mpiexec  --label  --line-buffer  -n 768 /glade/derecho/scratch/cstan/b.day1.0/bld/cesm.exe  >> cesm.log.$LID 2>&1  
2025-01-20 17:26:37 MODEL EXECUTION HAS FINISHED
check for resubmit
dout_s True 
mach derecho 
resubmit_num 0
~~~
{: .output}

> ## Troubleshooting
>
> Does anyone have a `stdout` file that does not indicate `MODEL EXECUTION HAS FINISHED`
>
{: .challenge}

