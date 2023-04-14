<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.7 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:12:49 GMT-0700 (PDT)
* Source doc: Services
----->


**Services**

**What is service?**

Service is an application component that is used to perform long-running operations in the background without user interaction.

Service can run in the background even if the app is not running in foreground.

**Does Service have a separate thread?**

Service does not create a separate thread, it runs on Main UI Thread so you should avoid any blocking operation to avoid ANR errors. For that You can create a separate thread within service

**How to choose between Service and Thread?**

When you want the task to run in the background you can choose between Service and Thread. So whenever you need to perform operation only while the app is running and on the new Thread other than UI Thread you should go with the Thread. When  You need the operation to be continued even after the app stops you should choose Service

**What are the types of services?**

There is Three kind of services:



* Foreground:Foreground service performs operations that are noticeable to the user.It shows Notification while running.The notification can not be removed until the service is stopped.
* Background: Background service is not noticeable to the user whether it is running or not.There are many restrictions on it after android API level 26
* Bound:Bound service is the service that is bound to the component it's been started by. It creates client server relations to send requests and receive results. It can also be used for IPC.

**Can service be started by another app?**

Service can be started using another app as other components like activity are started using Intent.

**What is the Difference between Foreground and Background service?**

A Background Service is a service that runs only when the app is running so it'll get terminated when the app is terminated. A Foreground Service is a service that stays alive even when the app is terminated.

[Understanding and Using Services in Android: Background & Foreground Services || Medium](https://medium.com/@Codeible/understanding-and-using-services-in-android-background-foreground-services-8130f6bbf2a5)

**How to Declare a Service component?**

Every Service component should be declared in the Manifest File.It can be done using  &lt;service> tag in the &lt;application>.The[ android:name](https://developer.android.com/guide/topics/manifest/service-element#nm) attribute is the only required attribute—it specifies the class name of the service. 

You can ensure that your service is available to only your app by including the[ android:exported](https://developer.android.com/guide/topics/manifest/service-element#exported) attribute and setting it to `false`. This effectively stops other apps from starting your service, even when using an explicit intent.

**How to Stop service from being vulnerable?**

If you want to use service within your app only then set <code>[android:exported](https://developer.android.com/guide/topics/manifest/service-element#exported)</code> attribute to <code>false.</code>

If you want to allow your service to be used by other apps then, Do not declare intent filters and always start service by using Explicit intents.Starting a bound service using implicit intent will throw an exception after android version 8.

**What is the starting service and the bound Service?**

A Service component can be started by passing explicit Intent using startService() or bindService() method based on foreground service or Bound service respectively. Based on the type they are started, they are called Started service and bound service also.

 ** **

**How can we start the Started service?**

You can start a service from an activity or other application component by passing an[ Intent](https://developer.android.com/reference/android/content/Intent) to[ startService()](https://developer.android.com/reference/android/content/Context#startService(android.content.Intent)) or[ startForegroundService()](https://developer.android.com/reference/android/content/Context#startForegroundService(android.content.Intent))

Both are the same but <code>[startForegroundService()](https://developer.android.com/reference/android/content/Context#startForegroundService(android.content.Intent))</code> gives the implicit promise that service will be foreground in nature.

Multiple requests to start the service result in multiple corresponding calls to the service's[ onStartCommand()](https://developer.android.com/reference/android/app/Service#onStartCommand(android.content.Intent, int, int)). 

With android API level 26, You can not start background service when the app is not in foreground.If an app needs to create a foreground service, the app should call[ startForegroundService()](https://developer.android.com/reference/android/content/Context#startForegroundService(android.content.Intent)).Once the service has been created, the service must call its[ startForeground()](https://developer.android.com/reference/android/app/Service#startForeground(int, android.app.Notification)) method within five seconds. 

**What is the restriction on starting foreground service from android 12**

With Android 12 (API level 31) or higher can't start foreground services while running in the background

**How can we stop the service?**

Services which are started using startService continue to run after it has been started. So it needs to be stopped itself by calling stopSelf() or another component by stopService().

Multiple requests to start the service result in multiple corresponding calls to the service's[ onStartCommand()](https://developer.android.com/reference/android/app/Service#onStartCommand(android.content.Intent, int, int)). However, only one request to stop the service (with[ stopSelf()](https://developer.android.com/reference/android/app/Service#stopSelf()) or[ stopService()](https://developer.android.com/reference/android/content/Context#stopService(android.content.Intent))) is required to stop it.

**How to stop bind service?**

Multiple clients can bind to the service simultaneously. When a client is done interacting with the service, it calls[ unbindService()](https://developer.android.com/reference/android/content/Context#unbindService(android.content.ServiceConnection)) to unbind. When there are no clients bound to the service, the system destroys the service.

**Explain Service Lifecycle**

Based on the way they are started,It follows two paths:

Started Service lifecycle callbacks:

	



* onCreate(): called when service is started first time , setup vars.if service is already running already then it is skipped
* onStartCommand(): When service is started and can run in the background indefinitely.
* onBind(): it should return null if no binding , It is must to implement
* onDestroy(): when service is being destroyed

Bound service lifecycle callbacks:



* onCreate(): called when service is started first time , setup vars.if service is already running already then it is skipped
* onBind(): It returns IBinder object of interface by which user will communicate using it
* onUnbind():when all the clients are unbound to service
* onDestroy():when service is destroyed

**How to create a Started service?**

Started service could be either foreground or background. following needs to be done for oth

You can extend the[ Service](https://developer.android.com/reference/android/app/Service) class to handle each incoming intent. It initially calls onCreate() and then for each start request it will call onStartCommand() if service is already running.It is preferred to use Thread within the service

For Foreground service you need to promote your service to foreground using startForeground within 5 seconds of service started. It needs to display Notification to the user that the service is running.

**From which Android API level do you need permission for Foreground service?**

If an app that targets API level 28 or higher attempts to create a foreground service without requesting the `FOREGROUND_SERVICE` permission, the system throws a[ SecurityException](https://developer.android.com/reference/java/lang/SecurityException).

**What onStartCommand() method returns?**

It should always return the integer value and It means that when the system kills the service how it should continue the service.It should be from following constants:



* <code>[START_NOT_STICKY](https://developer.android.com/reference/android/app/Service#START_NOT_STICKY)</code>: Do not create service if there is no pending intent to deliver
* <code>[START_STICKY](https://developer.android.com/reference/android/app/Service#START_STICKY)</code>: recreate the service by calling onStartCommand() but does not deliver the last Intent.
* <code>[START_REDELIVER_INTENT](https://developer.android.com/reference/android/app/Service#START_REDELIVER_INTENT)</code>: recreate the service by calling onStartCommand() with r the last Intent.

<strong>How Notification behavior is changed based on android versions for foreground service?</strong>

When you start foreground service you have to mandatorily show the notification about service is running and that notification can not be dismissed by the user until the service is finished. 

From android version 13 and above there are two changes has been appeared:First that if the user doesn’t allow the notification permission then it will not be seen and other is that user can dismiss the notification by swiping

Another Thing that changed with android 12 and above is that Notification is not shown directly , It is shown after 10 seconds of service has started to provide streamlined performance to short running services.

**How to declare foreground service type?**

From android version 10 and above when you access location in foreground service you need to declare android:foregroundServiceType with location in service component

From android version 11 and above you also need to mention the above while using camera and microphone in service

From android version 14 and above you have to mandatorily mention the service type

You can also add multiple type and use any of them while making service foreground using startForeground()


## **What are the Restrictions to access to location, camera, and microphone?**

From android version 11 and above you can not start foreground service if app is in background if service contains any of the mentioned service type,location can be used if background location permission is granted

From android version 12 and above you can not start any foreground service if the app is in the background.

**How to create a bound service and bind with Client?**

 



* Create a Service 
    * Create  class that extends Binder class
        * It has one method which returns Service
    * Create IBinder object of that class
    * Service has one method which is public and can be accessed using the service object
    * Return the Ibinder object from onBind() callback
* Create a Activity (any client)
    * Create a object of ServiceConnection which overrides methods
        * onServiceConnected() and onServiceDisconnected()
    * Pass the object with  Explicit intent to bindService()

Here, When Service starts it receives call in onBind() which returns the IBinder and it is received in client in onServiceConnected() callback , You can get service using the that Binder class method which returns service

Now you have service and you can access that public method of service class and get data.

**How to detect if service is running or not?**

You can call Context.getSystemService(ACTIVITY_SERVICE) which will return object cast it to ActivityManager

Using ActivtyManager, You can call getRunningServices and get RunningServiceInfo and using it you can get name and other details.
