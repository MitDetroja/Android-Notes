<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 1.291 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:08:06 GMT-0700 (PDT)
* Source doc: Intent and Intent Filter
----->


**Intent and Intent Filter**

**What is Intent?**

Intent is an abstract description of operation to be performed in other terms,a Messaging object that is used to request an action from another app component.

**What are the usages of Intent?**

Intent can be used in following cases:



* Start an Activity
* Start Service
* Delivering Broadcast
* Sending the User to Another App
* Sending a Result from to Activity
* Sending Simple Data to Other Apps

**What are the types of Intent?**

There are two types of Intent: Implicit and Explicit

**What is Implicit Intent?**

Implicit intents do not name a specific component, but instead declare a general action to perform, which allows a component from another app to handle it. For example, Capturing Image through camera.

**What are the usages of Implicit Intent?**

Implicit intent can be used to (Ref:[ Common Intents](https://developer.android.com/guide/components/intents-common))



* Create Alarm -[ ACTION_SET_ALARM](https://developer.android.com/reference/android/provider/AlarmClock#ACTION_SET_ALARM)
* Create a timer -[ ACTION_SET_TIMER](https://developer.android.com/reference/android/provider/AlarmClock#ACTION_SET_TIMER)
* Show Alarm  -[ ACTION_SHOW_ALARMS](https://developer.android.com/reference/android/provider/AlarmClock#ACTION_SHOW_ALARMS)
* Add a calendar event -[ ACTION_INSERT](https://developer.android.com/reference/android/content/Intent#ACTION_INSERT)
* Capture a picture or video [ ACTION_IMAGE_CAPTURE](https://developer.android.com/reference/android/provider/MediaStore#ACTION_IMAGE_CAPTURE) or[ACTION_VIDEO_CAPTURE](https://developer.android.com/reference/android/provider/MediaStore#ACTION_VIDEO_CAPTURE)
* Compose an email with optional attachments[ ACTION_SENDTO](https://developer.android.com/reference/android/content/Intent#ACTION_SENDTO) (for no attachment) or[ ACTION_SEND](https://developer.android.com/reference/android/content/Intent#ACTION_SEND) (for one attachment) or[ ACTION_SEND_MULTIPLE](https://developer.android.com/reference/android/content/Intent#ACTION_SEND_MULTIPLE) (for multiple attachments)
* Retrieve a specific type of file -[ ACTION_GET_CONTENT](https://developer.android.com/reference/android/content/Intent#ACTION_GET_CONTENT)
* Open or create a specific type of file -[ ACTION_OPEN_DOCUMENT](https://developer.android.com/reference/android/content/Intent#ACTION_OPEN_DOCUMENT) or[ ACTION_CREATE_DOCUMENT](https://developer.android.com/reference/android/content/Intent#ACTION_CREATE_DOCUMENT)
* Show a location on a map  -[ ACTION_VIEW](https://developer.android.com/reference/android/content/Intent#ACTION_VIEW)
* Play a media file -[ ACTION_VIEW](https://developer.android.com/reference/android/content/Intent#ACTION_VIEW)
* Initiate a phone call -[ACTION_DIAL](https://developer.android.com/reference/android/content/Intent#ACTION_DIAL) - Opens the dialer or phone app.[ ACTION_CALL](https://developer.android.com/reference/android/content/Intent#ACTION_CALL) - Places a phone call (requires the CALL_PHONE permission)
* Open a specific section of Settings -[ ACTION_SETTINGS](https://developer.android.com/reference/android/provider/Settings#ACTION_SETTINGS)
* Compose an SMS/MMS message with attachment- [ ACTION_SENDTO](https://developer.android.com/reference/android/content/Intent#ACTION_SENDTO) or[ACTION_SEND](https://developer.android.com/reference/android/content/Intent#ACTION_SEND) or[ACTION_SEND_MULTIPLE](https://developer.android.com/reference/android/content/Intent#ACTION_SEND_MULTIPLE)
* Load a web URL -[ ACTION_VIEW](https://developer.android.com/reference/android/content/Intent#ACTION_VIEW)
* Sharing data -[ ACTION_SEND](https://developer.android.com/reference/android/content/Intent#ACTION_SEND)

**What is the Diff between ACTION_GET_CONTENT and ACTION_OPEN_DOCUMNET?**

As per the documentation,

ACTION_GET_CONTENT is used to get a document and copy it in your app.

ACTION_OPEN_DOCUMNET is used when you want to read an existing file without making a copy into your app, or when you want to open and edit a file in place.

**Which Exception is thrown if No activity is found to handle your intent?**

Whenever you invoke an intent, be ready to catch an** ActivityNotFoundException**, which occurs if there's no other activity that can handle your app's intent.

**How to forcefully show a chooser for Implicit Intent?**

To show the chooser, create an **Intent **using **createChooser**() and pass it to **startActivity**().



* **Intent chooser = Intent.createChooser(myIntent, title);**

**What is Explicit Intent?**

Explicit intent is used to start a component in your own app,  by supplying the class name of the activity or service you want to start. For example, you might start a new activity within your app in response to a user action, or start a service to download a file in the background.

**What are the usages of Explicit Intent?**



* Start an Activity
* Start Service
* Delivering Broadcast

**What are the Building blocks of Intent?**

Intent can be created using Following:



* Component name
* Action
* Data
* Type
* Extras
* Flag

**What is the component name in Intent?**

It categories whether the Intent is Implicit or Explicit. It's the critical piece of information that makes an intent _explicit_, meaning that the intent should be delivered only to the app component defined by the component name. Without a component name, the intent is _implicit._

You can set the component name with[ setComponent()](https://developer.android.com/reference/android/content/Intent#setComponent(android.content.ComponentName)),[ setClass()](https://developer.android.com/reference/android/content/Intent#setClass(android.content.Context,%20java.lang.Class%3C?%3E)),[ setClassName()](https://developer.android.com/reference/android/content/Intent#setClassName(java.lang.String,%20java.lang.String)), or with the[ Intent](https://developer.android.com/reference/android/content/Intent) constructor.

**Why should we Always specify the Component name to start service?**

When starting a[ Service](https://developer.android.com/reference/android/app/Service), always specify the component name. Otherwise, you cannot be certain what service will respond to the intent, and the user cannot see which service starts.

Hence, Do not start service using Implicit Intent.

**What is Action in Intent?**

A string that specifies the generic action to perform (such as _view_ or _send, [ ACTION_VIEW](https://developer.android.com/reference/android/content/Intent#ACTION_VIEW) or[ ACTION_SEND](https://developer.android.com/reference/android/content/Intent#ACTION_SEND)_). It is mostly used with Implicit Intent.You can also specify your custom Action.

You can specify the action for an intent with[ setAction()](https://developer.android.com/reference/android/content/Intent#setAction(java.lang.String)) or with an[ Intent](https://developer.android.com/reference/android/content/Intent) constructor.

**How is Action used in Broadcast sending and receiving?**

In case of Broadcast action plays the main role, Actions are being performed while sending and reported while receiving. It can be systems action or customs actions too.

**What is data in Intent?**

The URI (a[ Uri](https://developer.android.com/reference/android/net/Uri) object) that references the data to be acted on and/or the MIME type of that data. The type of data supplied is generally dictated by the intent's action. For example, if the action is[ ACTION_EDIT](https://developer.android.com/reference/android/content/Intent#ACTION_EDIT), the data should contain the URI of the document to edit.

When creating an intent, it's often important to specify the type of data (its MIME type) in addition to its URI.However, the MIME type can sometimes be inferred from the URI—particularly when the data is a content: URI.

If you want to set both the URI and MIME type, _don't_ call[ setData()](https://developer.android.com/reference/android/content/Intent#setData(android.net.Uri)) and[ setType()](https://developer.android.com/reference/android/content/Intent#setType(java.lang.String)) because they each nullify the value of the other. Always use[ setDataAndType()](https://developer.android.com/reference/android/content/Intent#setDataAndType(android.net.Uri,%20java.lang.String)) to set both URI and MIME type.

**What is Category in Intent?**

A string containing additional information about the kind of component that should handle the intent.

**What are the key properties of intent?**

component name, action, data, and category represent the defining characteristics of an intent. By reading these properties, the Android system is able to resolve which app component it should start.

**What are the additional properties of intent that do not affect how it is resolved to an app component?**

Extras and Flags do not play a role in resolving which app component it should start.

**What is Extras in Intent?**

Key-value pairs that carry additional information required to accomplish the requested action.

You can add extra data with various[ putExtra()](https://developer.android.com/reference/android/content/Intent#putExtra(java.lang.String,%20android.os.Bundle)) methods, each accepting two parameters: the key name and the value. You can also create a[ Bundle](https://developer.android.com/reference/android/os/Bundle) object with all the extra data, then insert the[ Bundle](https://developer.android.com/reference/android/os/Bundle) in the[ Intent](https://developer.android.com/reference/android/content/Intent) with[ putExtras()](https://developer.android.com/reference/android/content/Intent#putExtras(android.content.Intent)).

**What Kind of data Should be avoided in Extras?**

Do not use[ Parcelable](https://developer.android.com/reference/android/os/Parcelable) or[ Serializable](https://developer.android.com/reference/java/io/Serializable) data when sending an intent that you expect another app to receive. If an app attempts to access data in a[ Bundle](https://developer.android.com/reference/android/os/Bundle) object but does not have access to the parceled or serialized class, the system raises a[ RuntimeException](https://developer.android.com/reference/java/lang/RuntimeException).

**What is Flag in Intent?**

Flags are defined in the[ Intent](https://developer.android.com/reference/android/content/Intent) class that function as metadata for the intent. The flags may instruct the Android system how to launch an activity (for example, which[ task](https://developer.android.com/guide/components/tasks-and-back-stack) the activity should belong to) and how to treat it after it's launched (for example, whether it belongs in the list of recent activities).

**What is the difference between addFlag vs SetFlag?**

When you use setFlags you are replacing the old flags. when you use addFlags you are appending new flags.

**What are the Flags used to Launch Activity / what are Activity launch Modes, List Them?**

Launch mode is an Android OS command that determines how the activity should be started. It specifies how every new action should be linked to the existing task.



* FLAG_ACTIVITY_NEW_TASK
* FLAG_ACTIVITY_CLEAR_TASK
* FLAG_ACTIVITY_SINGLE_TOP
* FLAG_ACTIVITY_CLEAR_TOP

**How Activity, Service or Broadcast is started?**

Activity can be started using startActivity() or startActivityForResult() 

Service can be started using startService()

Broadcast can be sent using sendBroadcast()

**What is the difference between start?**

if the intent that started your activity might expect a result. If the originating activity has been called[ startActivityForResult()](https://developer.android.com/reference/android/app/Activity#startActivityForResult(android.content.Intent, int)), then the system delivers the result otherwise, the result is ignored.

**How to enable your app to receive data from another application?**

Application can receive data using Implicit Intent

To advertise which implicit intents your app can receive, declare one or more intent filters for each of your app components with an[ &lt;intent-filter>](https://developer.android.com/guide/topics/manifest/intent-filter-element) element in your[ manifest file](https://developer.android.com/guide/topics/manifest/manifest-intro). Each intent filter specifies the type of intents it accepts based on the intent's action, data, and category. 

The system delivers an implicit intent to your app component only if the intent can pass through one of your intent filters.

**What is Intent Filter?**

Intent Filter is declaration in manifest file about your activity or service that which Intents it can handle or receive

Intent is received only if passes through the intent filter

**What are the main elements used to declare Intent Filter?**

Intent filter is declared in Manifest using Action, data and category tags.

Inside the[ &lt;intent-filter>](https://developer.android.com/guide/topics/manifest/intent-filter-element), you can specify the type of intents to accept using one or more of these three elements:

[&lt;action>](https://developer.android.com/guide/topics/manifest/action-element)

Declares the intent action accepted, in the name attribute. The value must be the literal string value of an action, not the class constant.

[&lt;data>](https://developer.android.com/guide/topics/manifest/data-element)

Declares the type of data accepted, using one or more attributes that specify various aspects of the data URI (scheme, host, port, path) and MIME type.

[&lt;category>](https://developer.android.com/guide/topics/manifest/category-element)

Declares the intent category accepted, in the name attribute. The value must be the literal string value of an action, not the class constant.

**Can Activity receive multiple types of intents? Or can we declare multiple Intent Filters for Single Activity?**

Yes.

You can create a filter that includes more than one instance of[ &lt;action>](https://developer.android.com/guide/topics/manifest/action-element),[ &lt;data>](https://developer.android.com/guide/topics/manifest/data-element), or[ &lt;category>](https://developer.android.com/guide/topics/manifest/category-element). If you do, you need to be certain that the component can handle any and all combinations of those filter elements.

When you want to handle multiple kinds of intents, but only in specific combinations of action, data, and category type, then you need to create multiple intent filters.

**How can we expose app Activity to other applications?**

explicitly set a value for[ android:exported](https://developer.android.com/guide/topics/manifest/activity-element#exported). This attribute indicates whether the app component is accessible to other apps. 

If an activity, service, or broadcast receiver in your app uses intent filters and doesn't explicitly set the value for android:exported, your app can't be installed on a device that runs Android 12 or higher.

**How to declare Intent Filter Dynamically?**

Filters for broadcast receivers can be registered dynamically by calling[ registerReceiver()](https://developer.android.com/reference/android/content/Context#registerReceiver(android.content.BroadcastReceiver, android.content.IntentFilter, java.lang.String, android.os.Handler)). You can then unregister the receiver with[ unregisterReceiver()](https://developer.android.com/reference/android/content/Context#unregisterReceiver(android.content.BroadcastReceiver)). Doing so allows your app to listen for specific broadcasts during only a specified period of time while your app is running.

**How is Intent Resolution done?**

For Action:



* An intent filter can declare zero or more[ &lt;action>](https://developer.android.com/guide/topics/manifest/action-element) elements
* The action specified in the[ Intent](https://developer.android.com/reference/android/content/Intent) must match one of the actions listed in the filter.
* If the filter does not list any actions, there is nothing for an intent to match, so all intents fail the test.
* if an[ Intent](https://developer.android.com/reference/android/content/Intent) does not specify an action, it passes the test as long as the filter contains at least one action.

For category: 



* An intent filter can declare zero or more[ &lt;category>](https://developer.android.com/guide/topics/manifest/category-element) elements
* What Intent have must be in Intent Filter , But what IntentFilter have should not be Mandatorily in Intent
* Every category in the[ Intent](https://developer.android.com/reference/android/content/Intent) must match a category in the filter
* The intent filter may declare more categories than are specified in the[ Intent](https://developer.android.com/reference/android/content/Intent) and the[ Intent](https://developer.android.com/reference/android/content/Intent) still passes
* An intent with no categories always passes this test, regardless of what categories are declared in the filter.

For data:



* TODO

**How can any Activity be started by another App using Implicit Intent?**

Any Activity that has declared Intent Filters can be started using its matching Intent filter by any other app if it is exported.

 

**How can any Component be started by another App using Explicit Intent?**

Before android 13:

Any Activity that is exported can be started using its component  Name by any other app.it does not have anything to do with Intent Filters.

On and After android 13: (Ref :[IntentFilter above 13](https://medium.com/androiddevelopers/making-sense-of-intent-filters-in-android-13-8f6656903dde))

If Component contains Intent Filter in its manifest declaration then to start it by another app it should also match its intent filter apart from Component name in Intent definition.

It Helps in avoiding vulnerability of components.

It should be exported in both cases above.

So regardless of intent type, if you are targeting a component from another app or any other app targeting your apps component it should always match the Intent Filter if it has been declared in android 13 and above version.

**How is Intent Filter used to define Apps entry point?**

app's main entry point—the activity that opens when the user initially launches the app with the launcher icon.

First of all set  android:exported flag true, then Action and category as follow:



* The[ ACTION_MAIN](https://developer.android.com/reference/android/content/Intent#ACTION_MAIN) action indicates this is the main entry point and does not expect any intent data.
* The[ CATEGORY_LAUNCHER](https://developer.android.com/reference/android/content/Intent#CATEGORY_LAUNCHER) category indicates that this activity's icon should be placed in the system's app launcher. If the[ &lt;activity>](https://developer.android.com/guide/topics/manifest/activity-element) element does not specify an icon with icon, then the system uses the icon from the[ &lt;application>](https://developer.android.com/guide/topics/manifest/application-element) element.

These two must be paired together in order for the activity to appear in the app launcher.

**Describe how broadcasts and intents work to be able to pass messages around your app?**

To send


    Intent i = new Intent("com.mycompany.myapp.SOME_MESSAGE");


    sendBroadcast(i);

To Receive


    registerReceiver(myReceiver, new IntentFilter("com.mycompany.myapp.SOME_MESSAGE"));

**Why should the category be DEFAULT to receive implicit Intent?**

To receive implicit intents, you _must include_ the[ CATEGORY_DEFAULT](https://developer.android.com/reference/android/content/Intent#CATEGORY_DEFAULT) category in the intent filter. The methods[ startActivity()](https://developer.android.com/reference/android/app/Activity#startActivity(android.content.Intent)) and[ startActivityForResult()](https://developer.android.com/reference/android/app/Activity#startActivityForResult(android.content.Intent, int)) treat all intents as if they declared the[ CATEGORY_DEFAULT](https://developer.android.com/reference/android/content/Intent#CATEGORY_DEFAULT) category. If you do not declare this category in your intent filter, no implicit intents will resolve to your activity.

**How intent is used to return a result?**

If you want to return a result to the activity that invoked yours, simply call[ setResult()](https://developer.android.com/reference/android/app/Activity#setResult(int, android.content.Intent)) to specify the result code and result[ Intent](https://developer.android.com/reference/android/content/Intent). When your operation is done and the user should return to the original activity, call[ finish()](https://developer.android.com/reference/android/app/Activity#finish()) to close (and destroy) your activity

You must always specify a result code with the result. Generally, it's either[ RESULT_OK](https://developer.android.com/reference/android/app/Activity#RESULT_OK) or[ RESULT_CANCELED](https://developer.android.com/reference/android/app/Activity#RESULT_CANCELED). You can then provide additional data with an[ Intent](https://developer.android.com/reference/android/content/Intent), as necessary.

The result is set to[ RESULT_CANCELED](https://developer.android.com/reference/android/app/Activity#RESULT_CANCELED) by default

**How to handle Incoming data from Intent?**

Application receives data in Two ways: First when our Intent Filter matches with broadcast and other when we perform any action through Intent to get data(ex. Capture Photo).

In the first case we receive data in onCreate() and in the other we get data in OnActivityResult() methods.

In Both cases by Using Intent , you can get type, action and data to perform any operation.

(Ref: [Receive Data](https://developer.android.com/training/sharing/receive))

**How can two distinct Android apps interact?**

Android applications can use an[ Intent](https://developer.android.com/reference/android/content/Intent) to perform some basic interactions with other apps, such as start another app, receive a result from that app, and make your app able to respond to intents from other apps.

(Ref: [Interacting with Other Apps](https://developer.android.com/training/basics/intents))

**What is Pending Intent?**

PendingIntent is an Intent wrapped with some additional information of action to perform action.

PendingIntent is a token that an app gives to another application to perform an action on behalf. It Also allows other applications to use host apps permission to perform particular pieces of code.

(Ref: [https://medium.com/androiddevelopers/all-about-pendingintents-748c8eb8619](https://medium.com/androiddevelopers/all-about-pendingintents-748c8eb8619) )

**What are the use cases of Pending Intent?**



* Declaring an intent to be executed when the user performs an action with your[ Notification](https://developer.android.com/develop/ui/views/notifications) (the Android system's[ NotificationManager](https://developer.android.com/reference/android/app/NotificationManager) executes the[ Intent](https://developer.android.com/reference/android/content/Intent)). 
* Declaring an intent to be executed at a specified future time (the Android system's[ AlarmManager](https://developer.android.com/reference/android/app/AlarmManager) executes the[ Intent](https://developer.android.com/reference/android/content/Intent)). 

**What are the components needed to create a Pending Intent?**

Method takes the current app[ Context](https://developer.android.com/reference/android/content/Context), the[ Intent](https://developer.android.com/reference/android/content/Intent) you want to wrap, and one or more flags that specify how the intent should be used (such as whether the intent can be used more than once).



* <code>[PendingIntent.getActivity()](https://developer.android.com/reference/android/app/PendingIntent#getActivity(android.content.Context, int, android.content.Intent, int))</code> for an[ Intent](https://developer.android.com/reference/android/content/Intent) that starts an[ Activity](https://developer.android.com/reference/android/app/Activity).
* <code>[PendingIntent.getService()](https://developer.android.com/reference/android/app/PendingIntent#getService(android.content.Context, int, android.content.Intent, int))</code> for an[ Intent](https://developer.android.com/reference/android/content/Intent) that starts a[ Service](https://developer.android.com/reference/android/app/Service).
* <code>[PendingIntent.getBroadcast()](https://developer.android.com/reference/android/app/PendingIntent#getBroadcast(android.content.Context, int, android.content.Intent, int))</code> for an[ Intent](https://developer.android.com/reference/android/content/Intent) that starts a[ BroadcastReceiver](https://developer.android.com/reference/android/content/BroadcastReceiver).

Intent Must be an explicit type to perform action within your app.

**What is PendingIntent Mutability?**

If your app targets Android 12 or higher, you must specify the mutability of each `PendingIntent` object that your app creates. To declare that a given `PendingIntent` object is mutable or immutable, use the[ PendingIntent.FLAG_MUTABLE](https://developer.android.com/reference/android/app/PendingIntent#FLAG_MUTABLE) or[ PendingIntent.FLAG_IMMUTABLE](https://developer.android.com/reference/android/app/PendingIntent#FLAG_IMMUTABLE) flag, respectively.

**What is <code>[FLAG_IMMUTABLE](https://developer.android.com/reference/kotlin/android/app/PendingIntent#FLAG_IMMUTABLE:kotlin.Int)</code> in Pending Intent?</strong>

<code>[FLAG_IMMUTABLE](https://developer.android.com/reference/kotlin/android/app/PendingIntent#FLAG_IMMUTABLE:kotlin.Int)</code>: Indicates the Intent inside the <code>PendingIntent</code> cannot be modified by other apps

**What is <code>[FLAG_MUTABLE](https://developer.android.com/reference/kotlin/android/app/PendingIntent#FLAG_MUTABLE:kotlin.Int)</code> in Pending Intent?</strong>

<code>[FLAG_MUTABLE](https://developer.android.com/reference/kotlin/android/app/PendingIntent#FLAG_MUTABLE:kotlin.Int)</code>: Indicates the Intent inside the <code>PendingIntent</code> should allow its contents to be updated by an app by merging values from the intent parameter of <code>PendingIntent.send()</code>.

**What is <code>[FLAG_UPDATE_CURRENT](https://developer.android.com/reference/kotlin/android/app/PendingIntent#flag_update_current)</code> in Pending Intent?</strong>

<code>[FLAG_UPDATE_CURRENT](https://developer.android.com/reference/kotlin/android/app/PendingIntent#flag_update_current)</code>: Requests that the system update the existing <code>PendingIntent</code> with the new extra data, rather than storing a new <code>PendingIntent</code>. If the <code>PendingIntent</code> isn’t registered, then this one will be.

If an application wants to update its own Pending intent then this flag is used.

**How to prevent Pending Intent from being vulnerable?**

We also talked about how a `PendingIntent`s should usually be immutable and that doing so prevents other apps from modifying it and doesn’t prevent the app from updating its own `PendingIntent` objects by using the `FLAG_UPDATE_CURRENT` flag in addition to `FLAG_IMMUTABLE`.

**What is package visibility?**

Your Application can get information about other applications installed on the device using Package manager class.But it was possible till android version 11, When you target android version 11 or above OS by default filters the visibility of other applications.

It was made a little harder process to retrieve this information by adding  a `&lt;queries>` entry to `AndroidManifest.xml`

You can do this by specifying  the other apps[ by package name](https://developer.android.com/training/package-visibility/declaring#package-name),[ by intent signature](https://developer.android.com/training/package-visibility/declaring#intent-filter-signature)` `in `&lt;queries> `tag.

**Why is resolveActivity() used?**

This is used to check if There is any Activity that can handle this Inten. By doing this we can avoid <code>[ActivityNotFoundException](https://developer.android.com/reference/kotlin/android/content/ActivityNotFoundException)</code> to be thrown.

So basically it is asking the OS to find the app to handle this Intent. It can be useful in cases like when some action needs to be disabled if in advance if there is no activity that can handle it

**Why should we avoid resolveActivity()?**

(Ref: [https://cketti.de/2020/09/03/avoid-intent-resolveactivity/](https://cketti.de/2020/09/03/avoid-intent-resolveactivity/))

After android version 11, Package visibility is restricted and hence using this method might return a null even though using `startActivity()` with the intent would work just fine.To make this work you could add a `&lt;queries>` entry to `AndroidManifest.xml`

In the past, using one method over the other was mostly a matter of taste. With the changes in Android 11 this method has the big advantage that you don’t have to add anything to `AndroidManifest.xml`
