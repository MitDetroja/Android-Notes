<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.501 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:35:23 GMT-0700 (PDT)
* Source doc: DataBinding
----->


**DataBinding**


---

**What is View Binding?**

ViewBinding is to bind views to code(Activity/Fragment). 

By Doing View Binding You can directly access the views in the layout in the code  by binding objects, it eliminates the use of  findViewById() method.

**What are the advantages of ViewBinding?**



* Easy to use
* It removes boilerplate code
* It is null safe and typesafe
* Faster compilation

**How to enable viewBinding?**

ViewBinding can be enabled for the module from gradle file of each Module by adding following options:


    **android {**


    **    ...**


    **    buildFeatures {**


    **        viewBinding true**


    **    }**


    **}**

When you enable a module for ViewBinding in gradle it enables all the layout in that module for binding.

**How to use viewBinding in Activity?**

You can access the view using binding. To Get the binding object in Activity use the inflate() method of the generated binding class and It will return the object of the binding class.

Get the root view of  binding and then set it in the setContentView()

Now you can use a binding class object to get reference of any view.

**How to use viewBinding in Fragment?**

To get the Binding class object you have to use inflator() that takes layoutInflator, ViewGroup and flag as a parameter and returns the binding object

Get the root of binding and return it

Now you can use a binding class object to get reference of any view.

**What are the options of ViewBinding ?**

Kotlin synthetics can be used to directly access the view from Layout

**Why has the kotlin synthetic been replaced by ViewBinding?**

Kotlin android extension is deprecated, that's why it is preferred to use View Binding over kotlin synthetics.

**What is DataBinding?**

DataBinding is a Library that is used to Bind UI component with the Data Sources of your app in a declarative way rather than Programmatically

Data Binding is Data to View Binding, It enables you to create Layout variables and Expressions

**What is the difference between DataBinding vs ViewBinding?**



* ViewBinding is view to code binding and DataBinding is View to Data binding. 
* ViewBinding is only used to access UI components and DataBindin is used to Dynamically Update View and Data by Declaring Variables in Layout File.
* When you do DataBinding There is no need to perform viewBinding as it  can be considered as done by default.
* ViewBinding has better performance and is easy to use

**What are the Types of Data Binding?**

Data Binding can be One-Way or Two-Way.



* One-Way: It only updates UI based on the changes in the Data  **@{}**
* Two-way: It changes the Data Based on change in UI component value and vice-versa **@={}**

**How to enable DataBinding?**


     **android {**


    **    ...**


    **    buildFeatures {**


    **        dataBinding true**


    **    }**


    **}**

**What are the steps for DataBinding?**



* Create a class with variable
* Use that class with &lt;data> in Layout File and enable Layout for Binding
* Get a binding object
* Set a value for variable in layout for that class

**How to enable Layout for DataBinding?**

To enable Layout for binding and create and use the Layout variables, You need to:



* Add &lt;data> tag within &lt;layout> tag in Layout file. &lt;data> tag must contain &lt;variable> which has a name and type that defines the variable name and Class.
* Now You can use a variables define in that class directly using name.var with any UI component by @{yourVarName.ClassVarName} 

**How to get a DataBinding object in Activity?**

To get a DataBinding object in Activity use  setContentView() of DataBindingUtil class. It will Give you  ActivityYournameBinding** **object

**How to get a DataBinding object in Fragment?**

If you are using data binding items inside a[ Fragment](https://developer.android.com/reference/android/app/Fragment),[ ListView](https://developer.android.com/reference/android/widget/ListView), or[ RecyclerView](https://developer.android.com/reference/androidx/recyclerview/widget/RecyclerView) adapter, you may prefer to use the[ inflate()](https://developer.android.com/reference/androidx/databinding/DataBindingUtil#inflate(android.view.LayoutInflater,%20int,%20android.view.ViewGroup,%20boolean,%20android.databinding.DataBindingComponent)) methods of the bindings classes or the[ DataBindingUtil](https://developer.android.com/reference/androidx/databinding/DataBindingUtil) class, as shown in the following code example:


    **val listItemBinding = ListItemBinding.inflate(layoutInflater, viewGroup, false)**


    **// or**


    **val listItemBinding = DataBindingUtil.inflate(layoutInflater, R.layout.list_item, vg, false)**

**How to set the Binding variable of Layout?**

binding.yourvarnameinlayout = class

**Is it Mandatory to use DataBiding with Observable Data types?**

No , it is not mandatory but in this case you have to update class var in layout manually.

**How to make data observable for data binding?**

It can be done by:



* extending your class with BaseObservable class in this case you have to use annotation @get:Bindable and notify property changed on setting up value
* Using LiveData or ObservableFiled&lt;>, In this case No additional things to be done


---

**TODO:**

Learn by Practice

For which component it can be used and not?

Handle Events

**REF:**

[How to Bind Data in Android](https://www.freecodecamp.org/news/how-to-bind-data-in-android/)

[Android 2-Way Data Binding With MVVM | by Siva Ganesh Kantamani | Better Programming](https://betterprogramming.pub/android-2-way-data-binding-with-mvvm-c13022a2f04a)
