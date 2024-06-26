<!-----



Conversion time: 0.65 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β36
* Wed Jun 26 2024 09:07:50 GMT-0700 (PDT)
* Source doc: ViewModel
----->


**ViewModel**


---

**What is viewModel?**

ViewModel is designed to hold and manage UI related data in a Lifecycle conscious way.It contains Business logic and UI state Data.

Primary Object of ViewModel is to caching the data and persist through the configuration change.

**What are the advantages of using ViewModel?**



* Persist data though configuration changes
* Keep UI and logic separate and give access to business logic
* It improves testability 
* Reusable

**What are the steps of setting up and using ViewModel?**



* Create a separate class that extends ViewModel
* Setup communication between ViewModel and View
* Use ViewModel in View 

**How to create a ViewModel?**

It is created by extending the ViewModel class

**Can we create a common ViewModel for Multiple Views?**

Yes, Multiple Views can share common ViewModel

**What are the thumb rules while creating a ViewModel?**



* ViewModel should not know anything about Android Framework
* Avoid reference of Views in ViewModel

**Why Should  ViewModel not hold a reference to a View?**

A[ ViewModel](https://developer.android.com/reference/androidx/lifecycle/ViewModel) usually shouldn't reference a view.

In a configuration change (e.g., screen rotation, multi window, keyboard availability), the activity and all of its UI elements (fragments, views, etc.) get recreated. The `ViewModel` does _not_. Instead, the re-created activity gets the same `ViewModel` as the original instance had.

If that `ViewModel` contains references back to the old activity (directly or indirectly), you have at least two problems:



1. You have a memory leak, as the old activity (and all that it references) cannot be garbage-collected while the `ViewModel` is outstanding
2. Anything you try to do with the old activity instance is likely to crash, as that activity has been destroyed

Ref: [Why view model should never reference a view? - Stack Overflow](https://stackoverflow.com/questions/56692318/why-view-model-should-never-reference-a-view-is-it-only-the-design-like-socs)

**How to get ViewModel in View?**

Your view should know about the viewModel. To get an object of ViewModel You can use the ViewModelProviders class.

**ViewModelProvider(&lt;Your View>).get(&lt;Your ViewModel>.class)**

It will return the object of ViewModel that can be used to perform actions.

**What should be taken care While Using View with ViewModel?**

When you use viewModel you should keep View As clean as possible, Avoid complex logic and operations. It should only Display data and send events to the ViewModel.

**How is the Data State persisted in ViewModel?**

Whenever onCreate Method is called for the first time it returns the new Instance of the ViewModel , Then When it is recreated after configuration changes It will return the pre-existing ViewModel associated to that View.

**How to share ViewModel between Fragments in Android?**

ViewModel is used to share data between fragments by sharing a single ViewModel between them. You have to use LiveData with ViewModel

**What is ViewModelProvider.Factory?**

ViewModel instances can not be created directly, You have to use ViewModelProvider for that so you can not pass value in constructor of the viewModel directly.To Use dependency and pass it into constructor you have to Use **ViewModelProvider.Factory**

Ref:[ViewModel with ViewModelProvider.Factory |Medium](https://medium.com/koderlabs/viewmodel-with-viewmodelprovider-factory-the-creator-of-viewmodel-8fabfec1aa4f)

**How to use ViewModelProvider.Factory for passing data to the constructor?**

To Use ViewModelProvider.Factory:



* Create your factory by Extending the ViewModelProvider.Factory class
* Override the create() method and return your ViewModel 
* Use ViewModelProvider() and pass the context and factory and apply get() method with class name

Ref: **[Android Quicky: ViewModelProvider.Factory in Kotlin - DEV Community](https://dev.to/theplebdev/android-quicky-viewmodelproviderfactory-in-kotlin-191a)**

**How ViewModel Survives Configuration Changes?**

**[The Curious Case of Survival of Android ViewModel | by Abhilash Das | Geek Culture | Medium](https://medium.com/geekculture/the-curious-case-of-survival-of-viewmodel-afe074992fbc)**

**What happens if you create an instance of a ViewModel class without ViewModelProvider?**

ViewModelProvider helps in Managing the property of being LifeCycle Aware of its view and Also Helps in Survive the configuration changes. If it is done directly both of the above can not be done.


---

**TODO:**

ViewModelFactory

**REF:**

[MVVM with Kotlin Coroutines and Retrofit [Example] | by Velmurugan Murugesan | Howtodoandroid | Medium](https://medium.com/android-beginners/mvvm-with-kotlin-coroutines-and-retrofit-example-d3f5f3b09050)

[ViewModels : A Simple Example. Introduction | by Lyla Fujiwara | Android Developers | Medium](https://medium.com/androiddevelopers/viewmodels-a-simple-example-ed5ac416317e)

[https://www.freecodecamp.org/news/model-view-viewmodel-android-tutorial/](https://www.freecodecamp.org/news/model-view-viewmodel-android-tutorial/)
