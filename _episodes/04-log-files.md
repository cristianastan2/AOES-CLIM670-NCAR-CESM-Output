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
$ cd /glade/derecho/scratch/cstan/archive/b.day1.0
$ ls
$ cd logs
$ gunzip cesm.log.7534849.desched1.250120-172344.gz
$ more cesm.log.7534849.desched1.250120-172344.gz
$ tail cesm.log.7534849.desched1.250120-172344.gz
~~~
{: .language-bash}

Log files are very long and contain lots of information which may look like errors, but are usually just diagnostic information unless your run fails and there is a clear error. Useful error information is typically located at the end of the file

~~~
$ tail cesm.log.7534849.desched1.250120-172344.gz
~~~
{: .language-bash}
