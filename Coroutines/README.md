<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.416 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Apr 14 2023 04:25:34 GMT-0700 (PDT)
* Source doc: Coroutines
* This is a partial selection. Check to make sure intra-doc links work.
----->


**Coroutines**


---

**What is Kotlin coroutine?**

Corouitnes is a framework to manage concurrency by taking advantage of cooperative nature of functions



* It can run parallel
* Wait for each other to communicate

It will enable writing asynchronous code in a synchronous way.

Coroutine is a lightweight thread, it is very cheap so it improves performance.

**Difference between Thread and coroutines?**

we can say that Coroutines and the threads both are multitasking. But the difference is that threads are managed by the OS and coroutines by the users as it can execute a few lines of function by taking advantage of the cooperation.

The biggest difference is that coroutines are very cheap, almost free: we can create thousands of them, and pay very little in terms of performance. True threads, on the other hand, are expensive to start and keep around. A thousand threads can be a serious challenge for a modern machine.


#### **What makes coroutines more efficient than threads?**

Coroutines are more efficient than threads because they are lightweight and can be suspended and resumed without incurring the overhead of a context switch. This means that they can be used to perform tasks that would otherwise block a thread, without incurring the same performance penalty.

This will be helpful when a thread is sitting idle and not doing anything, in that case, it can execute a few lines of another function. 

**What is the suspend function?**

The suspend function is a function which can be started, stopped and resumed.It is useful while Any long-running task might need to be interrupted.

Suspend function can be called only from another suspend function or coroutines.


#### **Are suspend functions executed by default on the main thread or some other one?**

By default, suspend functions are executed on a background thread.

**What is Launch()?**

launch() is a _coroutine builder_. It launches a new coroutine concurrently with the rest of the code, which continues to work independently. 

**What are Dispatchers in Coroutines?**

Dispatchers help coroutines in deciding on which thread task has to be done. There are Three types of Dispatchers:



* Dispatchers.IO: It is used to perform network and Disk-related work
* Dispatchers.Default: is used to do CPU intensive works
* Dispatchers.Main: Is used to perform UI related works

**What is delay()?**

Delay is a special suspend function, which is used to suspend a coroutine for a specific time.It does not mean blocking of thread , It allows other coroutines to run and use the thread.

**What is withContext()?**

withContext() is a suspend function which is used to shift the context to the thread where operation needs to be performed using Dispatchers.

**What is Scope in coroutines?**

Scope defines the restrictions within which coroutines are being executed.There is three scope in android kotlin coroutines



* GlobalScope: coroutines live as long as application.
* LifeCycleScope: coroutines lives Until the activity is not destroyed
* ViewModelScope: live as long the view model is alive

**How can we Start coroutines?**

Coroutines can be started using launch or Async with using the scope.

**Difference between launch vs Async?**

Launch does not return result while async returns result as Deferred&lt;T> which has await() which returns the result of the coroutine.

 

Async is used to perform tasks parallel.

**Difference between withContext and Async?**

WithContext and Async both return the result but Async is used to start Coroutine while withContext is only a suspend function to shift the thread.

WithContext acn not be used to perform task parallel.It will perform serially while async can perform task parallel.

**What is Async()?**

Async is simply used to start the coroutine and expect a result from a task. It will wait until the result is arrived using await().

Multiple async can execute parallel.

**How to handle Exceptions in coroutines when it is started using launch?**

While using launch to start the Coroutines you can directly use the try catch block to handle the exceptions based on your requirement whether to cover all cases in single or individual for each suspend function

You can also use CoroutineExceptionHandler to handle the exceptions as a global Exception handler for coroutine.

**How to handle Exceptions in coroutines when it is started using async?**

When coroutine is launched using the async we need to use either coroutineScope  or supervisorScope to handle the exception using try catch block.

coroutineScope: If any of the methods throw exceptions it will stop execution and move to catch blocks. With `async`, use `coroutineScope` with the top-level `try-catch`, when you do **NOT** want to continue with other tasks if any of them have failed.

   try {

        coroutineScope {

            //async one
            //async two
            //await one
            //await two
        }
      } catch (e: Exception) {
      }

supervisorScope: It will not stop execution of all the async, if any of them fails. With `async`, use `supervisorScope` with the individual `try-catch` for each task, when you want to continue with other tasks if one or some of them have failed.


    supervisorScope {
                	//async one
                  //async two
            	    try {
                    //await one
                  } catch (e: Exception) {
                  
                  }
                  try {
                    //await two
                  } catch (e: Exception) {
                  
                  }
      }

**REF:**

**[20 Kotlin Coroutines Interview Questions and Answers - CLIMB](https://climbtheladder.com/kotlin-coroutines-interview-questions/)**

**[Mastering Kotlin Coroutines](https://amitshekhar.me/blog/kotlin-coroutines)**

**[Exception Handling in Kotlin Coroutines](https://blog.mindorks.com/exception-handling-in-kotlin-coroutines/)**
