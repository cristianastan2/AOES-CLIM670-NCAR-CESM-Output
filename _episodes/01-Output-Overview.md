---
title: "CESM Output Overview"
teaching: 0
exercises: 0 
questions:
- "What kinds of output do I get after the model runs?"
objectives:
keypoints:
---

Last week we setup and ran our first CESM experiment. What did it do? How do I find and interpret the output from it?
There are several types of output form our model simulation:

1. Information in the `CaseStatus` file
2. Standard error and standard out
3. Log files
4. Model output data

In this episode, we will take a look at each of these and understand what they tell us.

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

### Standard error and standard out files

In your `CASEROOT` directory, your model produced files like `b.day1.0.run.o*` and `b.day1.0.st_archive.o*`.  These files produce output related to our submit script.  If the model and/or archiving did not run to completion, you will also have a `b.day1.0.run.e*` and/or `b.day1.0.st_archive.e*` file.  The ones with `*.o* are called standard out (stdout) and the ones with `*.e* are called standard error (stderr).  The end of the file usually contains the most useful information, so you can use the Unix `tail` command to look at the end of the file:

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

### Log files
Each component of CESM produces a log file that contains output and errors related to the running of that component. If your model experiment ran successfully, then the log files are tarred and stored with the short-term archiving in `DOUT_S_ROOT/logs`.  If you have an error, then the logfiles will be located in `RUNDIR/*` 
### Model Output Data!
This is of course why we run the model experiment in the first place.  We want to see the model output from our experiment. Where does it go? If the experiment an the archiving ran successfully, model output is located in `DOUT_S_ROOT`. Where is that?

~~~
$ ./xmlquery DOUT_S_ROOT 
~~~
{: .language-bash}

~~~
	DOUT_S_ROOT: /glade/scratch/kpegion/archive/b.day1.0
~~~
{: .output}

Let's go to this directory and see what is there:

~~~
$ cd /glade/scratch/kpegion/archive/b.day1.0
$ ls
~~~
{: .language-bash}

~~~
atm  cpl  esp  glc  ice  lnd  logs  ocn  rest  rof  wav
~~~
{: .output}

There are sub-directories for each of the component models and the output, called `history` files are located in each component sub-directory.

Let's go look at output files form the ocn model:

~~~
$ cd ocn/hist
$ ls
~~~
{: .language-bash}

~~~
ocn/hist> ls
b.day1.0.pop.dd.0001-01-01-03600  b.day1.0.pop.dv.0001-01-01-03600           b.day1.0.pop.h.once.nc
b.day1.0.pop.do.0001-01-01-03600  b.day1.0.pop.h.ecosys.nday1.0001-01-01.nc  b.day1.0.pop.hv.nc
b.day1.0.pop.dt.0001-01-01-03600  b.day1.0.pop.h.nday1.0001-01-01.nc
~~~
{: .output}

We can do a quick look at the ocean model output file `b.day1.0.pop.h.nday1.0001-01-01.nc` 
~~~
$ module load ncview
$ ncview b.day1.0.pop.h.nday1.0001-01-01.nc
~~~
{: .language-bash}

It make take a few seconds, but a viewer will appear on your screen.  If you select `SST`, then a small map of SST will appear. You can advance through all 5-times in this file using the arrows. You can advance through all 5-times in this file using the arrows.

Let's look at the atmosphere history files:
~~~
$ cd ../atm
$ ls 
~~~
{: .language-bash}

There are no history files for the atmosphere.  Why?  We ran our first experiment for 5-days.  The atmosphere is set to only provide monthly mean history files as its default.  Since we did not run a full month, there are no atmosphere history files available. That configuration is set in the `user_nl_cam` file and we will learn how to change it later in class.

#### History file nameing convenctions
