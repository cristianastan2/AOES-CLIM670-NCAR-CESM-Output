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
$ tail b.day1.0.run.o4141153
~~~
{: .language-bash}

~~~
 - Case input data directory (DIN_LOC_ROOT) is /glade/p/cesmdata/cseg/inputdata
 - Checking for required input datasets in DIN_LOC_ROOT
-------------------------------------------------------------------------
2020-09-15 11:21:22 MODEL EXECUTION BEGINS HERE
run command is mpiexec_mpt -p "%g:"  -np 576  omplace -tm open64  /glade/scratch/kpegion/b.day1.0/bld/cesm.exe  >> cesm.log.$LID 2>&1
2020-09-15 11:23:58 MODEL EXECUTION HAS FINISHED
check for resubmit
dout_s True
mach cheyenne
resubmit_num 0
~~~
{: .output}

> ## Troubleshooting
>
> Does anyone have a `stdout` file that does not indicate `MODEL EXECUTION HAS FINISHED`
>
{: .challenge}

