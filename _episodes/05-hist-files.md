---
title: "CESM Output Overview"
teaching: 0
exercises: 0 
questions:
- "What kinds of output do I get after the model runs?"
objectives:
keypoints:
---

### History Files
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

> ## Understanding history files
> 
> netcdf format
> named based on time frequency of data
> `h0/h` contain monthly averaged output
> `h1,h2` contain other time frequencies (e.g. daily)
> contain all variables for a given model component for a given time frequency and produced as the experiment runs
>
> Eventually, we want all timesteps for a specific variable from our model run.  These files are called `timeseries` files and they are 
> produced created using a postprocessing step after the model run is completed. We will learn how to create these in a future lesson.
>
{: .callout}
