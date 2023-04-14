<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.567 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:33:36 GMT-0700 (PDT)
* Source doc: LiveData
----->


**LiveData**


---

**What is LiveData?**

LiveData is an observable data holder class,Apart from other observables it is lifecycle aware.It means LiveData only updates the observers that are in active lifecycle.

**What are the advantages of being lifecycle aware?**

It avoids the unnecessary call to observers that are not active.

It avoids memory leak since it cleans up object references when lifecycle is destroyed

**What are the advantages of using LiveData?**

No memory leaks, No More manual handling of lifecycle and No Crashes due to stopped activity because it is life cycle aware.

Always up to date data , get immediate data on Activity or Fragment recreation because It is observable

**How can we use LiveData?**

To Use liveData we have to follow these steps:



* Create LiveData instance that can hold certain type of data
* Create an observer Using Observer and override onChanged() method
* Attach observer with LiveData using observe() method
* Update value using setValue or 

**What is observeForever()?**

To register an observer without lifeCycleOwner you can use obserForever() method.In this case Observer is considered as always active. 

This can be used When data needs to be provided or updated  throughout the application using singleton or application class

**What happens when multiple observers are registered for a single LiveData object?**

All the Observes get Notified when change occurs in the data, if the observer is in the Active state.

**How to create a LiveData object?**

LiveData is a wrapper that can be used with any data type to make it observable.Generally,  It is best practice to create and Update it from ViewModel.

**Why is it good practice to Create and update LiveData from ViewModel?**



* To avoid Bloated Views, They are used for displaying data not holding them
* To decouple it from View so it can survive configuration changes.

**How to observe LiveData objects?**

LiveData can be observed using Observer Class and overriding the onChange() method. And then passing the observer to observe() method of LiveData.

Generally It is good practice to begin observing  data in the onCreate() method.

**Why is it good practice to begin observing  data in the onCreate() method?**



* To ensure that system doesn't make redundant call
* To make sure that data is available when activity becomes visible to user

**When is the LiveData observer triggered?**



* When value changes
* When It comes to active state for the first time
* When it comes to active state for the second time, Only triggered if value has been changed from last time it was active

**How to update a LiveData object?**

LiveData does not have publicly available methods to update data.MutableLiveData provides setValue() and postValue() methods to edit LiveData value.

**What is the difference between setValue() and postValue()?**

sertValue() is used to update the value from the main thread while postValue() is used to update value from worker thread.



* If you are working on the main thread, then both `setValue `and `postValue `will work in the same manner i.e. they will update the value and notify the observers.
* If working in some background thread, then you can't use `setValue `. You have to use `postValue `here with some observer. But the interesting thing about `postValue `is that the value will be change immediately but the notification that is to be sent to observers will be scheduled to execute on the main thread via the event loop with the handler.

Ref: [https://blog.mindorks.com/livedata-setvalue-vs-postvalue-in-android/](https://blog.mindorks.com/livedata-setvalue-vs-postvalue-in-android/)

**What is the difference between LiveData and MutableLiveData?**

LiveData does not provide any public methods to update value but MutableLiveData does.

MutableLiveData is extended from LiveData class to make it mutable in case of updating values. Generally, ViewModel has an object of MutableLiveData and it only exposes the immutable LiveData to observers.

** **

**What is Transformations in LiveData?**

When you want to change the value of LiveData before dispatching to an observer or You want to return another LiveData based on the value of another one. Transformations class is used to perform this operations

** **

**What are the methods provided by Transformation?**

Transformation class provides map() and switchMap() methods to perform any operation on LiveData

**Explain Transformations.map()**

This function allows you to apply it to the output of LiveData and then propagates the result downstream. It can return any type of datatype.

You can use this function whenever you want to add or change in data  before returning the data to the observer.Whenever data is available or changed it takes the data, applies the map function and returns it to the observer.

Example: 



* Sort Users List before sending it to observer
* Return only userName from User Model to show snackbar

**Explain Transformations.switchMap()**

This function allows you to apply it to the output of LiveData and then propagates the new LiveData object as a downstream.It is same as map() but returns the LiveData object.

You can use this function when you want to return a liveData object to the observer based on the changes in the other LiveData object.

If this thing is done using the map() , It returns the new instance of LiveData and the UI subscribes to the new Instance and maintains the previous one also, In that case It will have the Multiple LiveData instance. And  we have to manually unregister the previous LiveData object.

switchMap() function Internally handle this problem and unregister the previous LiveData object

Example:



* When you enter the Address and get Postal code as a Result
* Searching User from the List 
* Have Category as CHIPS UI and show based result based on selected category

**TODO:**

Where have you used liveData?

Extend LiveData

MediatorLiveData

LiveData with coroutines

**REF:**

[LiveData transformations](https://proandroiddev.com/livedata-transformations-4f120ac046fc)

[Transform and Combine Android LiveData using LiveData Transformations and MediatorLiveData | Medium](https://medium.com/@pramahalqavi/transform-and-combine-android-livedata-using-livedata-transformations-and-mediatorlivedata-c48eaeb526e7)

[Android LiveData Transformation With Example | Map And SwicthMap](https://codinginfinite.com/android-livedata-transformation-example/)

[ViewModels and LiveData: Patterns + AntiPatterns  | Medium](https://medium.com/androiddevelopers/viewmodels-and-livedata-patterns-antipatterns-21efaef74a54)

[20 Android LiveData Interview Questions and Answers - CLIMB](https://climbtheladder.com/android-livedata-interview-questions/)
