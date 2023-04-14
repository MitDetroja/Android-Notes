<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.375 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:21:47 GMT-0700 (PDT)
* Source doc: ActivityResultContract
----->


**ActivityResultContract**

**What is ActivityResultContract or ActivityResultAPI?**

Till now, whenever we need to Transfer data between activities, We have used Intents, startActivityForResult() and onActivityResult() APIs. 

But This APIs has some coding cleanliness issues, Unwanted Null Pointer Exceptions due to minor typos and tight coupling because you can abstract that result code from Activity.

This can be overcome by the ActivityResultContract API introduced by Google.

**What can be done using ActivityResultContract ?**

The APIs provide[ default contracts](https://developer.android.com/reference/androidx/activity/result/contract/ActivityResultContracts) for basic intent actions like taking a picture, requesting permissions, and so on. You can also create custom contacts.

**How to Use ActivityResultContact in Activity or Fragment?**

There are three steps to use it:



* **Create Contract**: Create your custom contract based on Input and output you need by extending <code>[ActivityResultContract](https://developer.android.com/reference/androidx/activity/result/contract/ActivityResultContract)</code>&lt;I,O>() class.There are Many Default contacts available to perform some actions
* <strong>Register Contract</strong>: Register your custom or Predefined contract using <code>registerForActivityResult()</code>,It takes <code>[ActivityResultContract](https://developer.android.com/reference/androidx/activity/result/contract/ActivityResultContract)</code> and <code>[ActivityResultCallback](https://developer.android.com/reference/androidx/activity/result/ActivityResultCallback)</code>&lt;O> (it will receive the result)  as parameter and returns <code>[ActivityResultLauncher](https://developer.android.com/reference/androidx/activity/result/ActivityResultLauncher)</code>&lt;I> 
* <strong>Launch Contract</strong>: you can launch(I) your contact now by calling launch method on <code>[ActivityResultLauncher](https://developer.android.com/reference/androidx/activity/result/ActivityResultLauncher)</code>.It will start new activity and result will be received.

<strong>How to Register a Contract?</strong>

Contracts should be registered before activity is created because by any chance if activity gets destroyed and recreated to receive the result, Result callbacks must be available unconditionally. So you must call registerForActivtyResult() before activity or fragment is created.

registerForActivtyResult() takes two parameters:



    * ActivityResultContract that you have created or default contracts. 
    * ActivityResultCallback: it is a single method interface with onActivityResult() method   which takes output type of contract as parameter.

registerForActivtyResult() returns ActivityResultLauncher() object which can be used to launch contracts

Here is example: 


    **ActivityResultLauncher&lt;String> mGetContent = registerForActivityResult(new GetContent(),**


    **    new ActivityResultCallback&lt;Uri>() {**


    **        @Override**


    **        public void onActivityResult(Uri uri) {**


    **            // Handle the returned Uri**


    **        }**


    **});**

**How to register ActivityResultContract in a separate class?**

Activity and fragment classes by default implement ActivityResultCaller class that can be used to call registerForActivityResult(). But in other classes you can use ActivityResultRegistry.

Activity.getActivityResultRegistry() call will return the object of ActivityResultRegistry. By using this object you can call register() method.Which will take the key, ActivityResultContract and ActivityResultCallback as parameters and return ActivityResultLauncher object.

**How to Launch a Contract?**

You can launch a contract using the ActivityResultLauncher object using launch() method.It and can take parameters defined in Contract.

It can be called after Activity or Fragment is created.


    **mGetContent.launch("image/*");**

**How to create a custom Contract?**

Each ActivityResultContract Requires Predefined input and Output class if you don't require input then use void

It must implement these following methods:



* createIntent() :Takes context and defined input type as parameter and Returns the Intent
* parseResult(): It can produce output from resultcode and Intent

**What is a generic <code>[StartActivityForResult](https://developer.android.com/reference/androidx/activity/result/contract/ActivityResultContracts.StartActivityForResult)</code> contract?</strong>

This is a generic contract that takes any `Intent` as an input and returns an <code>[ActivityResult](https://developer.android.com/reference/androidx/activity/result/ActivityResult)</code>, letting you extract the <code>resultCode</code> and <code>Intent</code> as part of your callback

—

Ref:[https://wajahatkarim.com/2020/05/activity-results-api-onactivityresult/](https://wajahatkarim.com/2020/05/activity-results-api-onactivityresult/)
