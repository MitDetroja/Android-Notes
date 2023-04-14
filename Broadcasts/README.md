<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.466 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:09:48 GMT-0700 (PDT)
* Source doc: Broadcasts
----->


**Broadcasts**

**What are Broadcasts?**

Broadcasts are messages that an OS or App sends or receives.Message could be data or event.

Broadcasts are messaging component that is used for communicating across the apps when events of interest occur

**What are types of Broadcast?**

There are two types of broadcasts:



* _System broadcasts_ are delivered by the system.
* _Custom broadcasts_ are delivered by your app.

**What are System Broadcasts? Give Examples.**

A _system broadcast_ is a message that the Android system sends when a system event occurs.

Android sends broadcasts when system events occur such as system boots up, device starts charging, connectivity chaning, date changing, low battery.

The broadcast message itself is wrapped in an[ Intent](https://developer.android.com/reference/android/content/Intent) object whose action string identifies the event that occurred

**What are Custom broadcasts?**

Custom broadcasts are the broadcasts that an application sends.It can be used within an application or across the application to send custom messages.

**How can applications receive broadcasts?**

To enable an application from receiving broadcasts we need to register an app for that broadcast.

It can be done in two ways: Manifest-declared and Context-registered

**What is a Manifest-declared Receiver? **

In Manifest-declared Receiver, registration is done using manifest file statically.When it is registered using manifest System launches your app.

It is used when you want to perform some action even if the app is not running , It becomes a new entrypoint for the app.

**How to declare receivers using Manifest?**

Specify your &lt;action> that you want to receive using  that receiver within the Intent filter tag in receiver.


    **&lt;receiver android:name=".MyBroadcastReceiver" android:exported="false">**


    **    &lt;intent-filter>**


    **        &lt;action android:name="_APP_SPECIFIC_BROADCAST_" />**


    **    &lt;/intent-filter>**


    **&lt;/receiver>**

**What are the limitations applied on Manifest-declared receivers with android 8 (API26)?**

Beginning with android 8 and above , System imposes the restriction on Manifest-declared receivers.You can not use manifest to declare most of Implicit receivers ([Exception](https://developer.android.com/guide/components/broadcast-exceptions)).

Instead You can still use a[ context-registered receiver](https://developer.android.com/guide/components/broadcasts#context-registered-recievers) when the user is actively using your app.

**What is a Context-registered Receiver? **

In context-registered Receiver, registration is done dynamically with use of context.It is valid until context is valid.

It can not receive the message if the app is not running.

**How are Context-registered Receivers registered?**

It can be done as below


    **IntentFilter intentFilter = new IntentFilter();**


    **intentFilter.addAction(“YOUR_ACTION”);**


    **MyBroadcastReceiver myReceiver = new MyBroadcastReceiver();**


    **registerReceiver(myReceiver, filter);**

When you register dynamically it must be unregistered.

	**unregisterReceiver(myReceiver);**

**What needs to be taken care while registering and unregistering receivers dynamically?**

Be mindful of where you register and unregister the receiver, for example, if you register a receiver in[ onCreate(Bundle)](https://developer.android.com/reference/android/app/Activity#onCreate(android.os.Bundle)) using the activity's context, you should unregister it in[ onDestroy()](https://developer.android.com/reference/android/app/Activity#onDestroy()) to prevent leaking the receiver out of the activity context. If you register a receiver in[ onResume()](https://developer.android.com/reference/android/app/Activity#onResume()), you should unregister it in[ onPause()](https://developer.android.com/reference/android/app/Activity#onPause()) to prevent registering it multiple times (If you don't want to receive broadcasts when paused, and this can cut down on unnecessary system overhead). Do not unregister in[ onSaveInstanceState(Bundle)](https://developer.android.com/reference/android/app/Activity#onSaveInstanceState(android.os.Bundle)), because this isn't called if the user moves back in the history stack.

**How to enable Context-registered Receivers exported or visible to other apps?**

It can be done as follow:

**ContextCompat.registerReceiver(context, br, filter, receiverFlags);**

Here, **receiverFlags **could be set **ContextCompat.RECEIVER_EXPORTED**

Or **ContextCompat.RECEIVER_NOT_EXPORTED** at the time of registering.

**What is the risk when a  broadcast receiver is exported?**

If the broadcast receiver is exported, other apps could send unprotected broadcasts to your app.

** \
How can  applications send Broadcasts?**

Application can send broadcast in Three ways using:



* SendOrderedBroadcast
* SendBroadcast
* LocalBroadcastManager.sendBroadcast

**What is an ordered Broadcast?**

SendOrderedBroadcast() Method is used to send broadcasts in an ordered way to the one receiver at a time.

The order receivers run in can be controlled with the android:priority attribute of the matching intent-filter

**What is the advantage of ordered Broadcasts?**

As Receivers receive broadcast in synchronous manner It can propagate result to the next receiver, or can abort the broadcast so it is not passed ahead.

**What is a Normal Broadcast?**

Normal broadcast can be sent using sendBroadcast() method.It is sent to all the components who have registered for it at the same time.


```
sendBroadcast(Intent)
```


This is more efficient, but means that receivers cannot read results from other receivers, propagate data received from the broadcast, or abort the broadcast.

**How to Restrict broadcasts with permissions?**

Permissions allow you to restrict broadcasts to the set of apps that hold certain permissions. You can enforce restrictions on either the sender or receiver of a broadcast.

Sending Broadcast with permission:

If the sender application has added a permission while sending broadcast then the receiving app must have that particular permission granted to receive broadcast.

Receiving Broadcast with permission:

If the receiving app has mentioned permission in manifest or while registering the receiver, Then sender application must have that permission to send broadcasts to the receiving app.

**Why should we prefer context-registered over manifest declared receivers?**

First reason is that after android version 8 and above, Manifest declared receivers wont work for implicit broadcasts

Another reason is that when any receiver is declared in manifest by many apps then it can cause a system to launch many apps even though it is not required and it affects system performance and UX

**How to send sensitive information using broadcast?**

These points needs to be taken care:



* Do not use implicit intents , Instead use custom actions so that only the apps that know the action can register for your receiver.
* Specify permissions while sending broadcasts so that only apps that have permission can receive broadcast.
* You can also specify package of receiving app , using setPackage while sending broadcast 

**How to protect your app against receiving malicious broadcasts?**

Take care of following points:



* You can specify a **permission** when registering a broadcast receiver.
* For manifest-declared receivers, you can set the[ android:exported](https://developer.android.com/guide/topics/manifest/receiver-element#exported) attribute to "false" in the manifest. The receiver does not receive broadcasts from sources outside of the app.
* Use LocalBroadcastManager if within the app.

**What should be avoided in the onReceive() method?**



* Avoid long running task in onReceive() since it runs on the main thread, it should execute and return quickly 
* Avoid starting activity from here it can cause bad UX, instead display notification.

**What is localBroadcatmanager and how  is it used?**

LocalBroadcastManager is used to send and receive broadcasts within an application only.

To Send Broadcast:


```
LocalBroadcastManager.getInstance(MainActivity.this).sendBroadcast(intent);
```


To Receive Broadcast:


```
LocalBroadcastManager
    .getInstance(this)
        .registerReceiver(broadcastReceiver, 
                    new IntentFilter("custom-action-local-broadcast"));


```


**[Broadcast Receiver Android Tutorial | Medium](https://medium.com/@huseyinozkoc/android-broadcast-receiver-tutorial-with-example-230bea21e78)**

**[Broadcast Receiver in Android](https://vinodpattanshetti49.medium.com/broadcast-receiver-in-android-7790016ee15e) **
