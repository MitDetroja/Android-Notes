<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.331 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:19:31 GMT-0700 (PDT)
* Source doc: Job Scheduler
----->


**Job Scheduler**


---

**What is a Job Scheduler?**

Whenever we want to schedule some future task whenever certain system conditions match then we can use Job Scheduler to achieve this functionality

So we prepare a contract what needs to be done and under what condition it will execute and then we hand it over to android framework to perform the task using job Scheduler

**What is the difference between AlarmManager and Job Scheduler?**

Using the Alarm Manager You can perform the task on exact time but it does not give an option to set conditions while using Job Scheduler You can not perform task on Exact Time but it Gives you option to set the conditions when task should be executed.

Setting an Alarm manager for an exact time might lead to battery drainage which can be avoided by the Job Scheduler.

Alarm manage is available for almost all the SDK versions while Job Scheduler is available only adobe SDK version 21, 

Both can be set to use periodic tasks.

**What classes are required to schedule the Job?**

To Schedule a Job we need JobScheduler, JobInfo , JobInfo.Builder, JobService classes

JobInfo : Defines in which conditions job needs to be run

JobService: Implementation of Job that needs to be done

**How to create JobService?**

To create a Service for a scheduler we have to extend the JobService class.You have to implement two methods,onStartJob() and onStopJob().

And then add service in manifest and add permission for bind job service.android:permission="android.permission.BIND_JOB_SERVICE" in service tag.It is must to do otherwise the system will ignore this service.

**When  onStartJob() is called?**

This callback is called when System determines that now the task should be executed. You should implement a job to be done here.By default this method runs on a main thread , if you want to perform long-running tasks then move them to another thread.

**What does a Boolean returned from onStartJob() indicate?**

If its returns true means job is still running on another thread and in that case you have to explicitly call the jobFinished() to indicate the job is finished,

If it returns false then it means that the job is completed and the system calls jobFinished() on your behalf

.

Note:(It returns the answer of , Is Your job still running?)

**When onStopJob() is called?**

When the condition described in JobInfo does not match, Job must be stopped, at that time onStopJob() is called.

**What does a Boolean returned from onStopJob() indicate?**

It returns the answer of should we reschedule the job if it is not finished, true means that yes reschedule the job again and false means drop the job no need to reschedule.

True: Reschedule the job

False: Don't Reschedule, Drop the Job

**How to create JobInfo?**

JobInfo class is an abstraction that hides the task that needs to be done and under which condition it needs to be done. To create JobInfo you need to Use JobInfo.Builder  which returns JobInfo by calling build() on the Builder.

**How to create JobInfo.Builder?**

JobInfo.Builder has a Constructor which takes JobID and ComponentName as a parameter.

Here ComponentName can be created using the context and the JobService class that you want to execute.

Now that constructor returns the builder object which can be used to set the conditions.

**What conditions can be set in JobInfo.Builder?**



* `setRequiresCharging()`
* `setMinimumLatency()`
* `setRequiredNetworkType()`
* `setOverrideDeadline()`
* `setPeriodic()`
* `setRequiresDeviceIdle()`

**What is <code>setOverrideDeadline()</code> constraint?</strong>

By using other constraints there is no way to know precisely when your task will be executed.It will all up to the system resources availability.To override all constraints and give a hard deadline it is used.

**How to schedule a Job?**

The Job can be scheduled using JobScheduler. JobScheduler object is get from getSystemService(JOB_SCHEDULER_SERVICE)

Then call JobScheduler.schedule() which takes JobInfo as a parameter.

**Can I call the API in JobService and keep it running in the background?**

**REF:**

[CodeLabs](https://developer.android.com/codelabs/android-training-job-scheduler?index=..%2F..%2Fandroid-training#0)

[Android JobScheduler — Medium](https://medium.com/@kiitvishal89/android-jobscheduler-schedule-your-jobs-like-a-master-cfa0d80e5f10)
