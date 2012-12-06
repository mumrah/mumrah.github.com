---
layout: post
title: Speeding up Hadoop integration testing
published: false
---

## tl;dr

Lower the following configuration values in mapred-site.xml to lower the startup cost of a Hadoop job

    jobclient.completion.poll.interval=100
    jobclient.progress.monitor.poll.interval=50

## {{ page.title }}

When dealing with complex Hadoop workflows, and let's face it - they're all complex, it is often useful to test
the workflow from a very high level. Unit testing your Hadoop jobs is useful (see [MRUnit](http://mrunit.apache.org/)),
but narrowly focused testing like this fails to capture the interactions between Hadoop jobs.

So we write integration tests to make sure all the steps of the workflow play nice. That's all fine and well, 
but now we are faced with a new problem: Hadoop. Specifically, the slowness of Hadoop when it comes to starting 
jobs and reporting progress.

Consider a test case for a workflow with ten steps. Each step starts one or more map-reduce jobs. There might be 
many parameters with many permutations you want to test. If each Hadoop job incurs a five second lag in startup, 
and you have just ten test cases, then you are waiting around for eight minutes doing nothing.

I am a huge proponent of rapid iteration. To facilitate rapid iteration, you need fast tests. Eight minutes of idle
for a test cycle is pretty unacceptable (N.B., in practice this could be a much larger number). So, how can we speed
things up?

Hadoop has a configurable polling interval for job startup and job progress. The default values are 5000ms and 1000ms,
respectively, and are found in `mapred-site.xml`.

    jobclient.completion.poll.interval=100
    jobclient.progress.monitor.poll.interval=50

Lowering these too much in a production environment is a bad idea since it will increase the chattiness of your jobs,
and therefor increase load on your JobTracker.