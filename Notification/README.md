<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.717 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:17:02 GMT-0700 (PDT)
* Source doc: Notification
* Tables are currently converted to HTML tables.
----->


***Notification***


---

**What is Notification?**

A notification is a message that is used to Provide information and information about apps outside of app lifecycle.

You can use Notification to take some action using tap on Notification

**Where is Notification Displayed?**

Notification is Displayed in status bar, Notification Drawer, Heads-Up Notification and Lock Screen.

In Status bar and Notification Drawer Notification is displayed by default.

If you want to show Heads-up Notification It should be Important by nature

**What are the Parts of Notification UI?**



* Small Icon : Required , setSmallIcon()
* App Name: provided by system
* Time Stamp: setWhen(), setShowwhen(false) to hide
* Large Icon: optional, setLargeIcon()
* Title: optional, setContentTitle()
* Text: optional, setContentText()

**What permission is required for showing Notification?**

Android 13 (API level 33) and higher supports a[ runtime permission](https://developer.android.com/guide/topics/permissions/overview#runtime) for sending[ non-exempt](https://developer.android.com/develop/ui/views/notifications/notification-permission#exemptions) (including Foreground Services (FGS)) notifications from an app:[ POST_NOTIFICATIONS](https://developer.android.com/reference/android/Manifest.permission#POST_NOTIFICATIONS).

**What classes are Required for Notification?**

You need Notification , NotificationCompat.Builder, NotificationChannel(above android API 26 (8)), NotificationManager for creating and showing Notification. 

**What is a Notification Channel?**

Notification Channel is basically a category which represents the type of Notification. You can add several notifications in Single channel.You can set the behavior of the notification channel which is applied to all the notification in that channel

**When is the Notification Channel introduced?**

It is introduced in android API version 26 and above (android version 8)

** **

**How to Create a  Notification Channel?**

To create Notification Channel you have to add create a Object of NotificationChannel and then create channel using NotificationManager

**What parameters does NotificationChannel require?**

NotificationChannel requires Channel ID, Channel Name and Importance of Channel

**How to set the Importance of Notification Channel?**

To set the importance , NotificationChannel Constructor is used , It can be set from IMPORTANCE_NONE(0) to IMPORTNCE_HIGH(4)


<table>
  <tr>
   <td><strong>Urgent</strong> Notifications make a sound and appear as heads-up notifications.
   </td>
   <td><code><a href="https://developer.android.com/reference/android/app/NotificationManager.html#IMPORTANCE_HIGH">IMPORTANCE_HIGH</a></code>
   </td>
  </tr>
  <tr>
   <td><strong>High</strong> Notifications make a sound.
   </td>
   <td><code><a href="https://developer.android.com/reference/android/app/NotificationManager.html#IMPORTANCE_DEFAULT">IMPORTANCE_DEFAULT</a></code>
   </td>
  </tr>
  <tr>
   <td><strong>Medium</strong> Notifications make no sound.
   </td>
   <td><code><a href="https://developer.android.com/reference/android/app/NotificationManager.html#IMPORTANCE_LOW">IMPORTANCE_LOW</a></code>
   </td>
  </tr>
  <tr>
   <td><strong>Low</strong> Notifications make no sound and do not appear in the status bar.
   </td>
   <td><code><a href="https://developer.android.com/reference/android/app/NotificationManager.html#IMPORTANCE_MIN">IMPORTANCE_MIN</a></code>
   </td>
  </tr>
</table>


**How to set the behavior of NotificationChannel?**

You can set Behavior like Enable light, Light color, Vibration and Channel description,

It can be done using this methods:



* enableLight(bool)
* setLightColor(int_color)
* enableVibration(bool)
* setDescription(string)

**How to create a Notification Channel?**

It can be created using createNotificationChannel(NotificationChannel) of NotificationManager class.


    **if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {**


        **NotificationManager mNotificationManager =**


        **        (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);**


        **mNotifyManager.createNotificationChannel(notificationChannel);**


    **}**

You can use this only above android version 8 and above , So mention condition always

Once you create a notification and notification channel and submit it to the[ NotificationManager](https://developer.android.com/reference/android/app/NotificationManager.html), you cannot change the importance level using code. 

**How to create a Notification?**

The NotificationCompat.Builder class is used to create Notification.

**How to use NotificationCompat.Builder ?**

The NotificationCompat.Builder constructor takes context and Notification channel id and returns its object, Now You can set notification properties like small icon,large icon,text,title etc using Builder object.

NotificationComapt.Builder.build() will return  a Notification

**What is the priority for Notification?**

Priority can be set using setPriority() before android 7.1 and below 

**What does setAutoCancel() use for?**

setAllowCancel() will automatically remove the notification when the user taps it.

**How to set the intent for the notification's tap action?**

Notification’s tap action can be defined by setting Content Intent using setContentIntent() on NotificationCompat Builder class.

This method takes the Pending Intent as a parameter.Here PendingIntent contains the Intent and action whatever you want to perform

**How to Show the notification?**

To make the notification appear, call[ NotificationManagerCompat.notify()](https://developer.android.com/reference/androidx/core/app/NotificationManagerCompat#notify(int, android.app.Notification))  or <code>[NotificationManager](https://developer.android.com/reference/android/app/NotificationManager.html)</code>.<code>notify() , </code>passing it a unique ID for the notification and the result of[ NotificationCompat.Builder.build()](https://developer.android.com/reference/androidx/core/app/NotificationCompat.Builder#build()).



* To create an instance of `NotificationManager`, call `getSystemService()`, passing in the[ NOTIFICATION_SERVICE](https://developer.android.com/reference/android/content/Context.html#NOTIFICATION_SERVICE) constant.
* To create an instance of [ NotificationManagerCompat](https://developer.android.com/reference/androidx/core/app/NotificationManagerCompat#notify(int, android.app.Notification)), call `NotificationManagerCompat.from(this)`

**How to add action buttons in Notification?**

You can use addAction() method to add action button in Notification.An action button needs the following components:



* An icon, to be placed in the notification.
* A label string, to be placed next to the icon.
* A `PendingIntent`, to be sent when the user taps the notification action.


#### **What are Ongoing notifications?**

_Ongoing notifications_ are notifications that the user can't dismiss. To make a notification ongoing, set[ setOngoing()](https://developer.android.com/reference/android/app/Notification.Builder.html#setOngoing(boolean)) to `true`.

Your app must explicitly cancel ongoing notifications by calling `cancel()` or `cancelAll()`.

**Can I start Foreground service from Notification even after the restriction on foreground service after android 12?**

Yes. It is included in following exception cases:



* The user performs an action on a UI element related to your app. For example, they might interact with a[ bubble](https://developer.android.com/guide/topics/ui/bubbles),[ notification](https://developer.android.com/develop/ui/views/notifications),[ widget](https://developer.android.com/guide/topics/appwidgets/overview), or activity.


---

**TODO:**



* **Custom Notification**: allowed in content area only , set RemoteView in setCustomContentView, SetStyle with DecoratedCustomView , Android 12 and above don't allow full custom Notification layout. Ref: [Create a Custom Notification Layout | Android Developers](https://developer.android.com/develop/ui/views/notifications/custom-notification)
* Expandable Notification
* Start an Activity from Notification

**REF:**

[Notifications overview | Android Developers](https://developer.android.com/develop/ui/views/notifications)

[CodeLab Notification](https://developer.android.com/codelabs/android-training-notifications?index=..%2F..%2Fandroid-training#0)

[8.1: Notifications · GitBook](https://google-developer-training.github.io/android-developer-fundamentals-course-concepts-v2/unit-3-working-in-the-background/lesson-8-alarms-and-schedulers/8-1-c-notifications/8-1-c-notifications.html#compatibility)
