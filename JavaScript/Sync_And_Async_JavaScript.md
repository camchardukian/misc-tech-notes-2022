# Synchronous & Asynchronous JavaScript

## Synchronous Programming

With synchronous code, the code in a file will execute from top to bottom.

Generally speaking, synchronous code always runs in the same order.

### The Function Execution Stack/Call Stack

The _function execution stack_ or _call stack_ is a mechanism that helps the JavaScript interpreter keep track of the functions that a script calls.

[Felix Gerschau explains the call stack](https://felixgerschau.com/javascript-event-loop-call-stack/) like so:

> The call stack is a mechanism that helps the JavaScript interpreter to keep track of the functions that a script calls.  
> Every time a script or function calls a function, it's added to the top of the call stack.  
> Every time the function exits, the interpreter removes it from the call stack.  
> A function either exits through a return statement or by reaching the end of the scope.

For an alternate explanation, let's look at how FreeCodeCamp described the call stack in [this article](https://www.freecodecamp.org/news/synchronous-vs-asynchronous-in-javascript/):

> #1 -- When the JavaScript engine invokes a function, it adds it to the stack, and the execution starts.  
> #2 -- If the currently executed function calls another function, the engine adds the second function to the stack and starts executing it.  
> #3 -- Once it finishes executing the second function, the engine takes it out from the stack.  
> #4 -- The control goes back to resume the execution of the first function from the point it left it last time.  
> #5 -- Once the execution of the first function is over, the engine takes it out of the stack.  
> #6 -- Continue the same way until there is nothing to put into the stack.

## Asynchronous Programming

Like synchronous code, asynchronous code will start executing code at the top of the file until it gets to the bottom.

The difference is that with asynchronous code we will sometimes run into certain functions or code where the execution will split off and execute that async code separately.

This is usually the case when there is an operation that takes a long amount of time to execute or when we need to wait for a response.

Asynchronous code can sometimes run in different orders because of the different execution threads.

### Event Loop

The JavaScript engine creates a loop to periodically check the callback queue to see if there are any functions that need to run.

Whenever the call stack is empty, callbacks from the _callback queue_ will be pulled into the call stack and executed.

The exception to this, however, is if there are some tasks in the job queue (perhaps promise executor functions for example) that were added at the same time as the callbacks in the callback queue.

In this case, the tasks in the job queue will be prioritized over the functions in the callback queue.

Another difference between the callback queue and the _job queue_ is that when the loop comes to the job queue it will run all tasks in the job queue before continuing to loop whereas only one callback from the callback queue would be pulled at a time before looping back to the call stack.

Overall, this entire process is known as the _Event Loop_.

### Promises

[According to MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises):

> A promise is an object representing the eventual completion or failure of an asynchronous operation... Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.

Basically, a promise constructor takes a single argument which is a callback function with two parameters -- resolve and reject.

If everything in the promise went as expected or was otherwise successful, we resolve the promise. Otherwise, we can reject the promise and throw an error.

We can then take the results of our promise and then use the .then() function to do something else once our promise has resolved. Using .then() will return a new promise. Using the .then() multiple times consecutively is referred to as _promise chaining_.

If, however, our promise was rejected, we could use .catch() instead of .then() to handle the error, or tell our program how we would like to proceed.

### Async/Await

We can use _Async/Await_ to work with promises in a more comfortable fashion. The word _async_ before a function indicates that the return value of said function will be a resolved promise.

The _await_ keyword suspends the function execution until the promise settles.

If there is an error an exception is generated. Otherwise, the result of the settled promise will be returned.

A syntax error will be returned if we try to use the _await_ keyword outside of an async function.

## Resources

1. [Asynchronous Vs Synchronous Programming](https://www.youtube.com/watch?v=Kpn2ajSa92c)

1. [JavaScript Event Loop & Call Stack](https://felixgerschau.com/javascript-event-loop-call-stack/)

1. [What the heck is the event loop anyway](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

1. [Guide to Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

1. [Promises](https://web.dev/promises/)

1. [Async/Await](https://javascript.info/async-await)
