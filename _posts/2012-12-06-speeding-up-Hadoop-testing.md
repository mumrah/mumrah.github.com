---
layout: post
title: Speeding up Hadoop integration testing
published: true
---

## {{ page.title }}

### tl;dr

In Hadoop 0.21 or later (or 2.x), lower the following configuration values in mapred-site.xml to lower the startup cost 
of a Hadoop job:

    mapreduce.client.completion.pollinterval=100
    mapreduce.client.progressmonitor.pollinterval=50

<hr/>

When dealing with complex Hadoop workflows, and let's face it - they're all complex, it is often useful to test
the workflow from a very high level. Unit testing your Hadoop jobs is useful too (see [MRUnit](http://mrunit.apache.org/)),
but narrowly focused testing like this fails to capture the interactions between Hadoop jobs.

So we write integration tests to make sure all the steps of the workflow play nice. That's all fine and well, 
but now we are faced with a new problem: Hadoop overhead. Specifically, the slowness of Hadoop when it comes to 
starting jobs and reporting progress.

Consider a test case for a workflow with ten steps. Each step starts one or more map-reduce jobs. There might be 
many parameters with many permutations you want to test. If each Hadoop job incurs a five second lag in startup, 
and you have just ten test cases, then you are waiting around for eight minutes doing nothing (5s * test cases * workflow steps).

I am a huge proponent of rapid iteration. To facilitate rapid iteration, you need fast tests. Eight minutes of idle
for a test cycle is pretty unacceptable. So, how can we speed things up?

Starting in 0.21, Hadoop has a configurable polling interval for job startup and job progress. The default values 
are (in milliseconds) "5000" and "1000", respectively, and are found in `mapred-default.xml`.

    mapreduce.client.completion.pollinterval=100
    mapreduce.client.progressmonitor.pollinterval=50

Lowering these too much in a production environment is a bad idea since it will increase the chattiness of your jobs,
and therefor increase load on your JobTracker.

Normally, I would include some speedup claims here and maybe a pretty picture or two; unluky for us though, we
are on the 1.0.x branch where these values are hardcoded. Oh well.
