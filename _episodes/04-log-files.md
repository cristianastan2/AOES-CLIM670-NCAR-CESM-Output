---
title: "Log files"
teaching: 0
exercises: 0 
questions:
- "What do log files tell me?"
objectives:
keypoints:
---

### Log files
Each component of CESM produces a log file that contains output and errors related to the running of that component. If your model experiment ran successfully, then the log files are zipped and stored with the short-term archiving in `DOUT_S_ROOT/logs`.  If you have an error, then the logfiles will be located in `RUNDIR/*` 

Let's take a look at a log file:

~~~
$ ./xmlquery DOUT_S_ROOT
$ cd /glade/scratch/kpegion/archive/b.day1.0
$ ls
$ cd logs
$ gunzip cesm.log.8732081.chadmin1.ib0.cheyenne.ucar.edu.230225-190529.gz
$ more cesm.log.8732081.chadmin1.ib0.cheyenne.ucar.edu.230225-190529
$ tail cesm.log.8732081.chadmin1.ib0.cheyenne.ucar.edu.230225-190529
~~~
{: .language-bash}

Log files are very long and contain lots of information which may look like errors, but are usually just diagnostic information unless your run fails and there is a clear error. Useful error information is typically located at the end of the file

~~~
$ tail cesm.log.8732081.chadmin1.ib0.cheyenne.ucar.edu.230225-190529
~~~
{: .language-bash}
