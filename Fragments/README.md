<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.787 seconds.


Using this HTML file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:11:19 GMT-0700 (PDT)
* Source doc: Fragments
----->


<p>
<strong>Fragments</strong>
</p>
<p>
<strong>What is Fragment?</strong>
</p>
<p>
A<a href="https://developer.android.com/reference/androidx/fragment/app/Fragment"> Fragment</a> represents a modular and  reusable portion of your app's UI.
</p>
<p>
Fragment has its own layout , Lifecycle and manages its own input events
</p>
<p>
Fragment cant live on their own they must be hosted  by activity or fragment and its view hierarchy becomes the past of its host’s view hierarchy
</p>
<p>
<strong>How is Fragment Modular and Reusable? </strong>
</p>
<p>
Fragment is Modular because the UI can be divided into chunks and Dividing your UI into fragments makes it easier to modify your activity's appearance at runtime. While your activity is in the <code>STARTED</code><a href="https://developer.android.com/guide/components/activities/activity-lifecycle"> lifecycle state</a> or higher, fragments can be added, replaced, or removed

<p>
Fragment is reusable because you can use multiple instances of the same fragment class within the same activity, in multiple activities, or even as a child of another fragment. 
</p>
<p>
<strong>How can fragments be used?</strong>
</p>
<p>
Fragments can be used with directly Activity or other Fragments, You can define a Fragment tag in xml of host and inflate it statically or dynamically.Fragment is also used with BottomNavigationView and Viewpager. You can also use it in Drawerlayout.
</p>
<p>
<strong>How can we Add a fragment in Activity?</strong>
</p>
<p>
Fragment can be added to activity in two ways:
</p>
<ul>

<li>By adding fragment in XML file directly

<li>By defining Fragment tag  in XML Layout file and adding Fragment dynamically
</li>
</ul>
<p>
<strong>How to add a fragment using XML?</strong>
</p>
<p>
To add a fragment using XML layout, Use an &lt;fragment> or &lt;FragmentContainerView> tag in the XML file and mention your Fragment class name in  android:name or android:class  element.
</p>
<p>
<strong>How to add a fragment programmatically?</strong>
</p>
<p>
To add a fragment programmatically , Use an &lt;FrameLayout> or &lt;FragmentContainerView> tag in an XML file, Then use FragmentManager Class to perform FragmentTransaction.
</p>
<p>
<strong>Why is it preferred to use &lt;FragmentContainerView> instead of &lt;Fragment> and &lt;FrameLayout>?</strong>
</p>
<p>
It is preferred to use &lt;FragmentContainerView> because it provides fixes related to fragments that &lt;FrameLayout> and &lt;Fragment> is missing.
</p>
<p>
&lt;Fragment> tag is used when you want to add a fragment statically using XML But you can not use fragmentmanager to perform any transaction on It.Fragment can not be changed.
</p>
<p>
&lt;FrameLayout> tag is used when you want to add fragment dynamically and fragment transactions can be done.
</p>
<p>
&lt;FragmentContainerView> can be used in replacement of the both above. We can use fragment instead of fragment and it will allow us to perform transactions even if added using  XML. It also eliminates the drawbacks related to animation in FrameLayout.
</p>
<p>
(Ref: <a href="https://stackoverflow.com/questions/19453530/android-when-why-should-i-use-framelayout-instead-of-fragment">Android: when / why should I use FrameLayout instead of Fragment? - Stack Overflow</a>)
</p>
<p>
<strong>Why should we check for savedInstance before adding a fragment in Activity?</strong>
</p>
<p>
When we add a fragment in onCreate() method of activity check for savedInstanceState is null or not. And only add if it is null. Because while recreating activity the fragment does not need to be added a second time, as the fragment is automatically restored from the <code>savedInstanceState</code>.
</p>
<p>
<strong>How to pass an argument to a fragment while adding it?</strong>
</p>
<p>
We can pass a bundle object to an add() method while adding it and it can be retrieved using requireArguments() function  in fragment class. We have used the class&lt;Fragment> argument and Bundle in the add() method.
</p>
<p>
<strong>What is fragment Manager?</strong>
</p>
<p>
Fragment manager is a class responsible for performing actions on your fragment such as Add, Remove or replace them, And adding them to backstack.
</p>
<p>
	
</p>
<p>
<strong>How to access FragmentManager?</strong>
</p>
<p>
To access FagmentManager in Activity:
</p>



<pre class="prettyprint">getSupportFragmentManager()
</pre>


<p>
To access FragmentManager in Fragment:
</p>
<p>
	To manage childs: <code><a href="https://developer.android.com/reference/androidx/fragment/app/Fragment#getChildFragmentManager()">getChildFragmentManager()</a></code>

<p>
	To get Host’s Fragmentmanager: <code><a href="https://developer.android.com/reference/androidx/fragment/app/Fragment#getParentFragmentManager()">getParentFragmentManager()</a></code>

<p>
<strong>What is FragmentTransaction?</strong>
</p>
<p>
Fragment manager can perform back stack operations like Adding, Removing and Replacing based on user's interaction. Each set is committed as a single unit called FragmentTransaction.
</p>
<p>
You can group multiple actions into a single transaction—for example, a transaction can add or replace multiple fragments.
</p>
<p>
<strong>How can we perform transaction of fragment?</strong>
</p>
<p>
You can get an instance of <code>FragmentTransaction</code> from the <code>FragmentManager</code> by calling <code>beginTransaction()</code>
</p>
<p>
The final call on each <code>FragmentTransaction</code> must commit the transaction. The <code>commit()</code> call signals to the <code>FragmentManager</code> that all operations have been added to the transaction.
</p>
<p>
<strong>What are the operations that can be performed on Fragment?</strong>
</p>
<p>
add(), remove and replace() transactions can be performed on Fragments using Fragment manager and FragmentTransaction.
</p>
<p>
<strong>What is an add() transaction?</strong>
</p>
<p>
add() is used to add a fragment in the same root.
</p>
<p>
<strong>What is the remove() transaction?</strong>
</p>
<p>
remove() is used to fragment from the  host.
</p>
<p>
<strong>What is replace() transaction?</strong>
</p>
<p>
Replace is used to replace an current fragment in a container with a new Instance of fragment you provide. It is equivalent to removing existing and  adding a new fragment.
</p>
<p>
<strong>Why is it recommended to <code>setReorderingAllowed(true) </code>should be set to true?</strong>

<p>
When this flag is enabled it ensures that<strong> </strong>if multiple transactions are executed together, then any intermediate fragment does not go through lifeCycle or animation or transition phase.
</p>
<p>
<strong>What is addTobackStack() ?</strong>
</p>
<p>
If you have added or replaced many Fragments on a Fragment container. There is no way to go back to the previous Fragment on a Back Button Pressed.This transactions can be stored in the  back stack using addToBackStack() call.
</p>
<p>
<code>addToBackStack()</code> = save reverse of the action
</p>
<p>
If you added or removed multiple fragments within a single transaction, all of those operations are undone when the back stack is popped. 
</p>
<p>
If you don’t call this method transactions are not saved and fragments are destroyed after the transaction is finished so you can not get back to that fragment.
</p>
<p>
(Ref: <a href="https://stackoverflow.com/questions/25932761/fragment-popbackstack">Fragment addToBackStack- Stack Overflow</a>)
</p>
<p>
<a href="https://stackoverflow.com/questions/22984950/what-is-the-meaning-of-addtobackstack-with-null-parameter">What is the meaning of addToBackStack with null parameter? - Stack Overflow</a>)
</p>
<p>
<strong>What is the difference between commit() and commitNow()?</strong>
</p>
<p>
commit() is asynchronous, It does not perform transactions immediately, It schedules transactions on the UI main thread to perform as soon as possible.
</p>
<p>
commotNow() is synchronous, It performs transactions immediately on the UI main thread.But it is not compatible with addToBackStack().
</p>
<p>
<strong>What is <code><a href="https://developer.android.com/reference/androidx/fragment/app/FragmentManager#executePendingTransactions()">executePendingTransactions()</a></code> used for?</strong>

<p>
This method is called when you want to perform all transaction immediately scheduled by commit()
</p>
<p>
<strong>How to show and hide the fragment without affecting the Lifecycle of fragment?</strong>
</p>
<p>
Use the <code>FragmentTransaction</code> methods<a href="https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#show(androidx.fragment.app.Fragment)"> show()</a> and<a href="https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#hide(androidx.fragment.app.Fragment)"> hide()</a> to show and hide the view of fragments that have been added to a container. These methods set the visibility of the fragment's views <em>without</em> affecting the lifecycle of the fragment.
</p>
<p>
<strong>How is FragmentManager used to get Fragment?</strong>
</p>
<p>
You can get existing fragment using two ways:
</p>
<ul>

<li>Using Container ID: To get the current fragment assigned in the container by passing an id to the given method.<code>findFragmentById()</code>
</li>
</ul>
<p>
 
</p>
<ul>

<li>Using tag: To get any fragment that is added or replaced can be obtained using <code><a href="https://developer.android.com/reference/androidx/fragment/app/FragmentManager#findFragmentByTag(java.lang.String)">findFragmentByTag()</a></code> method by passing a tag declared in xml or while transaction.
</li>
</ul>
<p>
<strong>What is popBackStack() used for?</strong>
</p>
<p>
It is the method of FragmentManager used to pop the back stack. You can also pass a transaction key that is used while adding a transaction in backstack.
</p>
<p>
<strong>Why should Fragment be preferred over activity?</strong>
</p>
<p>
Fragment provide modularity and reusability of UI
</p>
<p>
Fragment can be used with viewPager so it can be used in BottomNavigationView and Tabbed Layout
</p>
<p>
<strong>How would you communicate between two Fragments?</strong>
</p>
<p>
The communication between fragments should not be done directly. There are three ways of doing so.
</p>
<ol>

<li>With the help of ViewModel

<li>With the help of Interface

<li>using the Fragment Result API
</li>
</ol>
<p>
<strong>What is and How to use the Fragment Result API?</strong>
</p>
<p>
When you want to share one time data between two fragments or between fragment and its host It can be done using the Fragment Result API which is introduced in Fragment version 1.3.0.
</p>
<p>
It’s lifecycle-safe — when receiving a result, you can work with the fragment view
</p>
<p>
For that the fragment which sends data should set Fragment Result and the fragment or host which wants to receive data should set Fragment Result Listener.Bundle is the object that is set and retrieved with the key.
</p>
<p>
The thing that must need to be taken care of here is to choose the FragmentManager.when:
</p>
<ul>

<li>Between two fragments: Use Parent Fragment Manager in both the fragment

<li>Between Host and child Fragment: Use parent Fragment Manager in child and use Child fragment manager in Host
</li>
</ul>
<p>
(<strong>Ref</strong>:<a href="https://medium.com/e-legion/getting-the-result-right-part-2-fragment-result-api-1a17f99490dc">Fragment Result API | Medium</a> )
</p>
<p>
<strong>Explain Fragment Lifecycle?</strong>
</p>
<p>

    onAttach()
</p>
<p>

    onCreate()
</p>
<p>

    onCreateView()
</p>
<p>

    onViewCreated()
</p>
<p>

    onViewStateRestored()
</p>
<p>

    onStart()
</p>
<p>

    onResume()
</p>
<p>

    onPause()
</p>
<p>

    onStop()
</p>
<p>

    onSaveInstanceState()
</p>
<p>

    onDestroyView()
</p>
<p>

    onDestroy()
</p>
<p>

    onDetach()
</p>
<p>
<strong>How to use a Fragment with ViewPager?</strong>
</p>
<p>
Viewpager is a layout Manager that can be added in any Layout File.It is mostly used with Fragments and FragmentPagerAdapter or FragmentStatepagerAdapter.
</p>
<ul>

<li>Create Fragments that you need.

<li>Create an adapter that extends either FragmentPagerAdapter or FragmentStatePagerAdapter 
<ul>
 
<li>It overrides: getCount(), getItem(), getPageTitle() methods.
 
<li>getItem method returns the fragment that needs to be shown on current position
</li> 
</ul>

<li>Add a ViewPager in Layout XML

<li>In the Host that contain ViewPager(Activity or Fragment) 
<ul>
 
<li>Get a viewPager by ID
 
<li>Create an Adapter and initialize it
 
<li>Set Adapter in ViewPager
</li> 
</ul>
</li> 
</ul>
<p>
ViewPagercan also be used with the conjunction of Tab layout and Bottom navigation View.
</p>
<p>
(Ref:<a href="https://developer.android.com/develop/ui/views/animations/screen-slide">https://developer.android.com/develop/ui/views/animations/screen-slide</a>)
</p>
<p>
<strong>What is the difference between FragmentPagerAdapter vs FragmentStatePagerAdapter?</strong>
</p>
<p>
FragmentPagerAdapter stores each fragment visited by the user in Memory.Only view is destroyed while out of focus,So when Fragment is revisited only view needs to be recreated.
</p>
<p>
FragmentStatePagerAdapter does not save the fragment in memory , It is destroyed when not visible to the user. It is useful to enhance performance when there are too many fragments.You have to recreate the Fragment each time.
</p>
<p>
<strong>How to use a ViewPager withTabbedLayout?</strong>
</p>
<ul>

<li>Create the viewPager as mentioned above.

<li>Add TabLayout in XML Layout File.

<li>Get TabLayout using ID

<li>Set Up tabLayout with ViewPager using TabLayout.setupWithViewPager(viewPager)
</li>
</ul>
<p>
(Ref:<a href="https://www.geeksforgeeks.org/viewpager-using-fragments-in-android-with-example/">https://www.geeksforgeeks.org/viewpager-using-fragments-in-android-with-example/</a>)
</p>
<p>
<strong>	</strong>
</p>
<p>
<strong>How to use a fragment with BottomNavigationView? </strong>
</p>
<p>
Bottom navigation bars make it easy for users to explore and switch between top-level views in a single tap. They should be used when an application has three to five top-level destinations. 
</p>
<p>
We can directly use fragments with BottomNavigationView by Performing fragment Transactions.To Do So we need to perform following steps:
</p>
<ul>

<li>Create a Menu XML resource File

<li>Add a frame Layout in XML

<li>Add a <code>BottomNavigationView </code>In Layout XML and add created XML menu file with menu tag

<li>Get BottomNavigationView Object using Find by ID

<li>Set onNavigationItemSelectedListener for BottomNavigationView

<li>Based on the selected Item in Navigation choose the fragment and perform fragment transaction (Replace) in the Frame Layout Container
</li>
</ul>
<p>
(Ref:<a href="https://www.geeksforgeeks.org/bottomnavigationview-inandroid/">https://www.geeksforgeeks.org/bottomnavigationview-inandroid/</a>)
</p>
<p>
<strong>How to use a ViewPager with BottomNavigationView? </strong>
</p>
<p>
We can use Fragment using ViewPager and BottomNavigationView as follow:
</p>
<ul>

<li>Create a Menu XML resource File

<li>Add a <code>BottomNavigationView </code>In Layout XML and add created XML menu file with menu tag

<li>Create and setup ViewPager as above

<li>Get BottomNavigationView Object using Find by ID

<li>Set onNavigationItemSelectedListener for BottomNavigationView

<li>Based on the selected Item in Navigation setCurrentItem in Viewpager

<li>Set OnPageChangeListener and override onPageSelected() in this and check the menu option 
</li>
</ul>
<p>
(Ref:<a href="https://droidmentor.com/bottomnavigationview-with-viewpager-android/">https://droidmentor.com/bottomnavigationview-with-viewpager-android/</a>)
</p>
<p>
<strong>Why is it recommended to use only the default constructor to create a <code>Fragment</code>?</strong>

<p>
Whenever Fragment is recreated after configuration change, OS calls the no-argument constructor of the fragment because it has no idea with what argument we have created a fragment so it is preferred to use only the default constructor.
</p>
