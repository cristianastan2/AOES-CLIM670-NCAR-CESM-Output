---
title: "CESM Output Overview"
teaching: 0
exercises: 0 
questions:
- "What kinds of output do I get after the model runs?"
objectives:
keypoints:
---

### Log files
Each component of CESM produces a log file that contains output and errors related to the running of that component. If your model experiment ran successfully, then the log files are tarred and stored with the short-term archiving in `DOUT_S_ROOT/logs`.  If you have an error, then the logfiles will be located in `RUNDIR/*` 