<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 1.21 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:01:05 GMT-0700 (PDT)
* Source doc: Activity
----->


**Activity**

**What is activity?**



* Activity is a screen that represents GUI with whom users interact.
* Single Mobile Application can contain multiple activities.For example LoginScreen,Home Screen, SettingsScreen.
* Here Each activity can start another activity to perform different actions, Still Each activity is independent and only loosely bound to another activity.Even apps from another activity can start your activity.

**How to Declare activities?**

To use activity by your application you need to declare activity in the manifest file with certain attributes, Only [android:name](https://developer.android.com/guide/topics/manifest/activity-element#nm) element is mandatory to be declared.

You can also add attributes that define activity characteristics such as label, icon, or UI theme etc.

contained in:


```
<application>
```


can contain:


```
    <intent-filter>
    <meta-data>
    <layout>
```


After you publish your app, you should not change activity names. If you do, you might break some functionality, such as app shortcuts.

**What is the advantage of declaring intent filters in the Activity tag in manifest?**

By Declaring Intent filters it provides the ability to launch an activity based not only on an _explicit_ request, but also an _implicit_ one.** **

Activities that you don't want to make available to other applications should have no intent filters, and you can start them yourself using explicit intents.

**What is the Activity lifeCycle?Explain each stage of the lifeCycle.	.**

When activity starts it goes through the different states and based on that it receives callbacks in the activity class.



* OnCreate(): You must implement this callback, which fires when the system first creates the activity. On activity creation, the activity enters the _Created_ state. In the[ onCreate()](https://developer.android.com/reference/android/app/Activity#onCreate(android.os.Bundle)) method, perform basic application startup logic that happens only once for the entire life of the activity.

    Most importantly, this is where you must call[ setContentView()](https://developer.android.com/reference/android/app/Activity#setContentView(android.view.View)) to define the layout for the activity's user interface.

* onStart():The activity enters the Started state, and the activity becomes **visible **to the user. This callback contains what amounts to the activity’s final preparations for coming to the foreground and becoming interactive. 

     	

* onResume():The system invokes this callback just before the activity starts interacting with the user. At this point, the activity is at the top of the activity stack, and captures all user input. Most of an app’s core functionality is implemented in the[ onResume()](https://developer.android.com/reference/android/app/Activity#onResume()) method. 
* onPause():The system calls[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) when the activity loses focus and enters a Paused state. This state occurs when, for example, the user taps the Back or Recents button. When the system calls[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) for your activity, it technically means your activity is still partially visible, but most often is an indication that the user is leaving the activity, and the activity will soon enter the Stopped or Resumed state. 

    Use the[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) method to pause or adjust operations that can't continue, or might continue in moderation, while the `Activity` is in the Paused state, and that you expect to resume shortly.


    You can also use the `onPause()` method to release system resources, handles to sensors (like GPS), or any resources that affect battery life while your activity is Paused and the user does not need them.

* onStop():When your activity is no longer visible to the user, it enters the _Stopped_ state, and the system invokes the[ onStop()](https://developer.android.com/reference/android/app/Activity#onStop()) callback. This can occur when a newly launched activity covers the entire screen. The system also calls `onStop()` when the activity finishes running and is about to be terminated. 

    use `onStop()` to perform relatively CPU-intensive shutdown operations. For example, if you can't find a better time to save information to a database, you might do so during `onStop()`.

* <code>[onDestroy()](https://developer.android.com/reference/android/app/Activity#onDestroy())</code> is called before the activity is destroyed. The system invokes this callback for one of two reasons:
1. The activity is finishing, due to the user completely dismissing the activity or due to[ finish()](https://developer.android.com/reference/android/app/Activity#finish()) being called on the activity.
2. The system is temporarily destroying the activity due to a configuration change, such as device rotation or entering multi-window mode.

    The <code>onDestroy()</code> callback releases all resources not released by earlier callbacks, such as[ onStop()](https://developer.android.com/reference/android/app/Activity#onStop()). 


**What is the difference between onCreate() and onStart()?**

OnCreate() Callback is received when Activity is launched by System while onStart() is called when activity is visible to the user and ready to interact.

**When only onDestroy is called for an activity without onPause() and onStop()?** 

When finish() is called from OnCreate() it will directly call onDestroy() since activity has not entered Start and Resume mode so no need to call onPause() and onStop().

**Why do we need to call setContentView() in onCreate() of Activity class?**

setContentView() set the UI that is visible to user and onCreate() method is the only method that is called only once during the lifecycle of the activity so to avoid setting up UI unnecessarily we call it in onCreate() 

**When onRestart() is called?**

When activity starts again after onStop() it will call onRestart() and the onStart().

**When activity is destroyed by the System?**

the system destroys the activity by default when such a configuration change occurs, wiping away any UI state stored in the activity instance.

**What is saving and restoring instance state?**

When activity is destroyed and recreated by OS,We need to provide a flawless experience to users while performing any operations, This can be achieved by Saving and restoring instance state.

**What is Instance state?**

State of Instances(views and variables) of Activity class is stored which is called Instance state.

**How state of view hierarchy is managed when activity is recreated?**

System save the State of view hierarchy by saving its Instance state in the form of Key value pair in Bundle object.Then retrieved on Activity creation.

The thing that needs to be taken care of is we need to assign a unique id in manifest  to each of the views to achieve this.

**When saving and restoring instance state is not performed?**

When activity is closed by the user using back press or Activity is finished by finish() call then this operation is not performed.

**How can variables be stored while Activity is recreated?**

Store only lightweight and simple data that dont need to be serialized in Bundle with key value pairs.

This can be done by saving that bundle while  onSaveInstanceState() is called.

**When onSaveInstanceState() is called?** \
This method is called by OS when activity is about to destroy.Specifically, After android P It is called after onStop() method and before that its been called before onStop() method (Not sure before or after onPause()).

**What should be avoided in onSaveInstanceState()?**

Storing persistent data that needs to be serialized should be avoided to store using a bundle. It should be done while the activity is running or onStop() method.

**What should be taken care of while using onSaveInstanceState()?**

Always call superclass implementation of this method because it is used to save the state of view hierarchy.

**How to restore Data when activity is recreated?**

When activity is recreated, The data can be restored from the saved Instance State Bundle. It can be done by two ways: Using savedInstanceState Bundle received in onCreate() and onRestoreInstanceState().

**How can we restore data in onCreate()?**

When onCreate() is called check for bundle if it is null then activity is newly created else it is recreated, Then you can restore data from that bundle.

**How can we restore data in onRestoreInstanceState()?**

This method is only called when we have saved an Instance state so we do not need to check for null. We can restore data using the bundle received in the argument.

**When onRestoreInstanceState() is called?**

This method is called after the onStart() method.

**What should be taken care of while using onRestoreInstanceState()?**

Always call superclass implementation of this method because it is used to restore the state of view hierarchy.

**How to start one activity from another?**

Depending on whether or not your activity wants a result back from the new activity it’s about to start, you start the new activity using either the[ startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent, android.os.Bundle)) method or the[ startActivityForResult()](https://developer.android.com/reference/android/app/Activity#startActivityForResult(android.content.Intent, int)) method. In either case, you pass in an[ Intent](https://developer.android.com/reference/android/content/Intent) object. 

**What does Intent specify while starting activity?**

The `Intent` object specifies either the exact activity you want to start(Explicit) or describes the type of action you want to perform(implicit).An `Intent` object can also carry small amounts of data to be used by the activity that is started.

**When and how <code>[startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent, android.os.Bundle))</code> should be used?</strong>

If the newly started activity does not need to return a result, the current activity can start it by calling the[ startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent, android.os.Bundle)) method. 

It can be used to start both implicit and explicit intents.

**When and how <code>[startActivityForResult(Intent, int)](https://developer.android.com/reference/android/app/Activity#startActivityForResult(android.content.Intent, int))</code> should be used?</strong>

Sometimes you want to get a result back from an activity when it ends. For example, you might start an activity that lets the user pick a person in a list of contacts. When it ends, it returns the person that was selected. To do this, you call the[ startActivityForResult(Intent, int)](https://developer.android.com/reference/android/app/Activity#startActivityForResult(android.content.Intent, int)) method, where the integer parameter identifies the call.The result comes back through your[ onActivityResult(int, int, Intent)](https://developer.android.com/reference/android/app/Activity#onActivityResult(int, int, android.content.Intent)) method. 

When a child activity exits, it can call `setResult(int)` to return data to its parent. The child activity must supply a result code, which can be the standard results <code>RESULT_CANCELED<strong>(Default)</strong></code>, <code>RESULT_OK</code>, or any custom values starting at <code>RESULT_FIRST_USER</code>.In addition, the child activity can optionally return an <code>Intent</code> object containing any additional data it wants

**What is the sequence of lifecycle callbacks when Activity starts another activity?**

For example , Here's the order of operations that occur when Activity A starts Activity B:



1. Activity A's[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) method executes.
2. Activity B's[ onCreate()](https://developer.android.com/reference/android/app/Activity#onCreate(android.os.Bundle)),[ onStart()](https://developer.android.com/reference/android/app/Activity#onStart()), and[ onResume()](https://developer.android.com/reference/android/app/Activity#onResume()) methods execute in sequence. Activity B now has user focus.
3. If Activity A is no longer visible on screen, its[ onStop()](https://developer.android.com/reference/android/app/Activity#onStop()) method executes.

This sequence of lifecycle callbacks lets you manage the transition of information from one activity to another.

**What is the sequence of lifecycle callbacks when configuration change happens?**

When a configuration change occurs, the activity is destroyed and recreated. The original activity instance will have the following callbacks triggered:



1. <code>[onPause()](https://developer.android.com/reference/android/app/Activity#onpause)</code>
2. <code>[onStop()](https://developer.android.com/reference/android/app/Activity#onstop)</code>
3. <code>[onDestroy()](https://developer.android.com/reference/android/app/Activity#ondestroy)</code>

A new instance of the activity will be created and have the following callbacks triggered:



1. <code>[onCreate()](https://developer.android.com/reference/android/app/Activity#onCreate(android.os.Bundle))</code>,
2. <code>[onStart()](https://developer.android.com/reference/android/app/Activity#onstart)</code>,
3. <code>[onResume()](https://developer.android.com/reference/android/app/Activity#onResume())</code>

<strong>What is the sequence of lifecycle callbacks when Activity or dialog appears in foreground and covers Activity partially?</strong>

If a new activity or dialog appears in the foreground, taking focus and partially covering the activity in progress, the covered activity loses focus and enters the Paused state. Then, the system calls[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) on it.

When the covered activity returns to the foreground and regains focus, it calls[ onResume()](https://developer.android.com/reference/android/app/Activity#onResume()).

**What is the sequence of lifecycle callbacks when Activity or dialog appears in foreground and covers Activity completely?**

If a new activity or dialog appears in the foreground, taking focus and completely covering the activity in progress, the covered activity loses focus and enters the Stopped state. The system then, in rapid succession, calls[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) and[ onStop()](https://developer.android.com/reference/android/app/Activity#onStop()).

When the same instance of the covered activity comes back to the foreground, the system calls[ onRestart()](https://developer.android.com/reference/android/app/Activity#onRestart()),[ onStart()](https://developer.android.com/reference/android/app/Activity#onStart()), and[ onResume()](https://developer.android.com/reference/android/app/Activity#onResume()) on the activity.

**What is the sequence of lifecycle callbacks when the user taps the Overview or Home button?**

the system behaves as if the current activity has been completely covered.

**What is the sequence of lifecycle callbacks when the User presses or gestures Back?**

If an activity is in the foreground, and the user presses or gestures Back, the activity transitions through the[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()),[ onStop()](https://developer.android.com/reference/android/app/Activity#onStop()), and[ onDestroy()](https://developer.android.com/reference/android/app/Activity#onDestroy()) callbacks. In addition to being destroyed, the activity is also removed from the back stack.

It is important to note that, by default, the[ onSaveInstanceState()](https://developer.android.com/reference/android/app/Activity#onSaveInstanceState(android.os.Bundle)) callback does not fire in this case.

**What is root launcher activity?**

Root launcher activities are activities that declare an[ Intent filter](https://developer.android.com/reference/android/content/IntentFilter) with both[ ACTION_MAIN](https://developer.android.com/reference/android/content/Intent#ACTION_MAIN) and[ CATEGORY_LAUNCHER](https://developer.android.com/reference/android/content/Intent#CATEGORY_LAUNCHER). These activities are unique because they act as entry points into your app from the app launcher.

**How is back pressed handled by root launcher activity?**

When a user presses or gestures Back from a root launcher activity, the system handles the event differently depending on the version of Android that the device is running.

System behavior on Android 11 and lower:

The system finishes the activity.

System behavior on Android 12 and higher:

The system moves the activity and its task to the background instead of finishing the activity. This behavior matches the default system behavior when navigating out of an app using the Home button or gesture.

**What is the task and the back stack?**

A _task_ is a collection of activities that users interact with when trying to do something in your app.

These activities are arranged in a stack—the _back stack_—in the order in which each activity is opened.

**What is the background and foreground task?**

Any application that has collection of activities is considered as a task , Now when this app or task goes in background by Pressing home screen or starting any other app , That app or task is considered as background task.While in the background, all the activities in the task are stopped, but the back stack for the task remains intact—the task has simply lost focus while another task takes place.

And the application which started its task is considered to be in Foreground.

When the previous task comes to the foreground—all the activities in its stack are intact and the activity at the top of the stack resumes.

**What is Launch Mode?**

Launch mode allows you to define how a new instance of an activity is associated with the current task.

You can define different launch modes in two ways:



* [Using the manifest file \
 \
](https://developer.android.com/guide/components/activities/tasks-and-back-stack#ManifestForTasks)When you declare an activity in your manifest file, you can specify how the activity should associate with tasks when it starts.
* [Using Intent flags \
 \
](https://developer.android.com/guide/components/activities/tasks-and-back-stack#IntentFlagsForTasks)When you call[ startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent)), you can include a flag in the[ Intent](https://developer.android.com/reference/android/content/Intent) that declares how (or whether) the new activity should associate with the current task.

**Which Type of Launch mode is preferred if defined in both?**

Launch mode defined in the Using Intent Flag is preferred over manifest.

**Note:** Some launch modes available for the manifest file are not available as flags for an intent and, likewise, some launch modes available as flags for an intent cannot be defined in the manifest.

**What are the Types of launch modes that can be defined using Manifest?**

There are five types of launch modes in Android:



1. `Standard`
2. `SingleTop`
3. `SingleTask`
4. `SingleInstance`
5. `SingleInstancePerTask`

**What is standard launch mode?**

The system always creates a new instance of the activity in the target task.

It is used to create multiple instances

**What is SingleTop launch mode?**

If an activity already exist on the top of stack then It will not create new instance but calls existing instance with onNewIntent() 

If Activity does not exist on the top of the stack then it will create activity as usual.

It can have multiple instances

**What is SingleTask launch mode?**

If Activity Does not exist on the task then it will create it as usual.

If it exists then it will be called by onNewIntent() and Activity above it in the stack will be popped out.

(Still confusing,  SingleInstance Needs to be learned)

**What launch modes need to be preferred?**

`standard` is the default mode and is appropriate for most types of activities. `SingleTop` is also a common and useful launch mode for many types of activities. The other modes — `singleTask` , `singleInstance`, and `singleInstancePerTask` — are not appropriate for most applications, since they result in an interaction model that is likely to be unfamiliar to users and is very different from most other applications. 

**What are the Types of launch modes that can be used with Intent as a Flag?**

When starting an activity, you can modify the default association of an activity to its task by including flags in the intent that you deliver to[ startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent)). The flags you can use to modify the default behavior are:



* <code>[FLAG_ACTIVITY_NEW_TASK](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_NEW_TASK)</code>
* <code>[FLAG_ACTIVITY_SINGLE_TOP](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_SINGLE_TOP)</code>
* <code>[FLAG_ACTIVITY_CLEAR_TOP](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_CLEAR_TOP)</code>

<strong>Explain <code>[FLAG_ACTIVITY_NEW_TASK](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_NEW_TASK)</code></strong>

Start the activity in a new task. If a task is already running for the activity you are now starting, that task is brought to the foreground with its last state restored and the activity receives the new intent in[ onNewIntent()](https://developer.android.com/reference/android/app/Activity#onNewIntent(android.content.Intent)).

This produces the same behavior as the <code>"singleTask"</code>[ launchMode](https://developer.android.com/guide/topics/manifest/activity-element#lmode) value

**Explain <code>[FLAG_ACTIVITY_SINGLE_TOP](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_SINGLE_TOP)</code></strong>

If the activity being started is the current activity (at the top of the back stack), then the existing instance receives a call to[ onNewIntent()](https://developer.android.com/reference/android/app/Activity#onNewIntent(android.content.Intent)), instead of creating a new instance of the activity.

This produces the same behavior as the <code>"singleTop"</code>[ launchMode](https://developer.android.com/guide/topics/manifest/activity-element#lmode) value

**Explain <code>[FLAG_ACTIVITY_CLEAR_TOP](https://developer.android.com/reference/android/content/Intent#FLAG_ACTIVITY_CLEAR_TOP)</code></strong>

If the activity being started is already running in the current task, then instead of launching a new instance of that activity, all of the other activities on top of it are destroyed and this intent is delivered to the resumed instance of the activity (now on top), through[ onNewIntent()](https://developer.android.com/reference/android/app/Activity#onNewIntent(android.content.%0AIntent))).

`FLAG_ACTIVITY_CLEAR_TOP` is most often used in conjunction with `FLAG_ACTIVITY_NEW_TASK`. When used together, these flags are a way of locating an existing activity in another task and putting it in a position where it can respond to the intent.

**How To send data between activities?**

Data can be sent between activities using Directly setting an Extra in Intent, Bundle, Serializable and Parcelable objects**.**

**How to add extra using Intent?**

When an app creates an[ Intent](https://developer.android.com/reference/android/content/Intent) object to use in[ startActivity(android.content.Intent)](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent)) in starting a new Activity, the app can pass in parameters using the[ putExtra(java.lang.String, java.lang.String)](https://developer.android.com/reference/android/content/Intent#putExtra(java.lang.String, java.lang.String)) method. 

**How Bundle is used to pass data in activity?**

We recommend that you use the[ Bundle](https://developer.android.com/reference/android/os/Bundle) class to set primitives known to the OS on[ Intent](https://developer.android.com/reference/android/content/Intent) objects. The[ Bundle](https://developer.android.com/reference/android/os/Bundle) class is highly optimized for marshaling and unmarshalling using parcels. 

**How can we pass objects to another activity?**

In Android we cannot just pass objects to activities. To do this the objects must either implement `Serializable` or `Parcelable` interface.

**How is Serializable used to send data?**

`Serializable` is a standard Java interface. You can just implement a Serializable interface and add override methods. The problem with this approach is that reflection is used and it is a slow process. This method creates a lot of temporary objects and causes quite a bit of garbage collection. However, `the Serializable` interface is easier to implement.


    **MyObjects mObjects = new MyObjects("name", "age", "Address array here");**


    **// Passing MyObjects instance via intent**


    **Intent mIntent = new Intent(FromActivity.this, ToActivity.class);**


    **mIntent.putExtra("UniqueKey", mObjects);**


    **startActivity(mIntent);**


    **// Getting MyObjects instance**


    **Intent mIntent = getIntent();**


    **MyObjects workorder = (MyObjects)    mIntent.getSerializableExtra("UniqueKey");**

**Parcelable**

Parcelable is a serialization mechanism provided by Android to pass complex data from one activity to another activity.In order to write an object to a Parcel, that object should implement the interface **“[Parcelable](https://developer.android.com/reference/android/os/Parcelable)“**.


    **// MyObjects instance**


    **MyObjects mObjects = new MyObjects("name", "age", "Address array here");**


    **// Passing MyOjects instance**


    **Intent mIntent = new Intent(FromActivity.this, ToActivity.class);**


    **mIntent.putExtra("UniqueKey", mObjects);**


    **startActivity(mIntent);**


    **// Getting MyObjects instance**


    **Intent mIntent = getIntent();**


    **MyObjects workorder = (MyObjects) mIntent.getParcelableExtra("UniqueKey");**

Here we need to implement (Still to learn)


    **describeContents() \
writeToParcel(Parcel dest, int flags)**

And We have to provide Parcelable. A creator that is used to create an instance of the class from the Parcel data.

**Differentiate Parcelable from Serialziable?**



1. `Parcelable` is faster than `Serializable` interface
2. `Parcelable` interface takes more time to implement compared to `Serializable` interface
3. `Parcelable` array can be passed via Intent in android
4. `Serializable` interface is easier to implement
5. `Serializable` interface creates a lot of temporary objects and causes quite a bit of garbage collection

**What happens when finish() is called?**

When finish() is called, activity gets destroyed and removed from the stack.It does not call for restoring Instance state.

**What is finishAffinity()?**

`finishAffinity()` is not used to "shutdown an application". It is used to remove a number of Activities belonging to a specific application from the current task (which may contain Activities belonging to multiple applications).

				

**Ref:**

[Android Application Class. While Starting App development, we tend… | by Balakrishnan | Droid Log | Medium](https://medium.com/droid-log/android-application-class-a8a1d64c82d1)

[The Android Lifecycle cheat sheet — part I: Single Activities | by Jose Alcérreca](https://medium.com/androiddevelopers/the-android-lifecycle-cheat-sheet-part-i-single-activities-e49fd3d202ab)

**Notes:**

Improve launchmode concepts

Learn Parcelable Implementation

Learn Affinity and clearing back stack

Learn about Lifecycle aware and LifecycleObserver
