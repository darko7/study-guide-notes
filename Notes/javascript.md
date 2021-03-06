 Give a high level overview of what an object's prototype represents -->
 Go here https://javascript.info/function-prototype

 What are the differences between the __proto__ and prototype attributes?
 prototype is a property of a Function object. It is the prototype of objects constructed by that function.
__proto__ is internal property of an object, pointing to its prototype.

What happens when we do or don't explicity set an object's prototype?
If we do set it, it's gonna overwrite the existing one, if not it's gonna point to an object with the only property constructor that points back to the function itself.

What is an object's default prototype?
The default "prototype" is an object with the only property constructor that points back to the function itself.

What is data encapsulation?
Data encapsulation refers to the idea that some data should not be directly exposed

Formally define a Javascript closure
A closure is the combination of a function and the environment from which it was declared. Closure allows a function to access variables from an enclosing scope — environment — even after it leaves the scope in which it was declared.

 What are the benefits of a Javascript closure?
 One of the main benefits of closures is that it allows data encapsulation. This refers to the idea that some data should not be directly exposed. Also, It can refer to outer scope variables even after the outer function has returned.

 Give an example of a closure
One of the most common interview problems on this subject:
What is wrong with the following code and how would you fix it?

const arr = [10, 12, 15, 21];
for (var i = 0; i < arr.length; i++) {
  setTimeout(function() {
    console.log(`The value ${arr[i]} is at index: ${i}`);
  }, (i+1) * 1000);
}
In this example the console will display four identical messages "The value undefined is at index: 4". This happens because each function executed within the loop will be executed after the whole loop has completed, referencing to the last value stored in i, which was 4.
One solution would be declaring the i variable with let, which creates a unique scope for each iteration and storing each value within its scope.

for (let i = 0; i < arr.length; i++) {
  setTimeout(function() {
    console.log(`The value ${arr[i]} is at index: ${i}`);
   }, (i) * 1000);
}

 What is the difference between the memory heap and call stack in javascript?
 1. Stack is used for static memory allocation and Heap for dynamic memory allocation, both stored in the computer's RAM .
2. Variables allocated on the stack are stored directly to the memory and access to this memory is very fast. When a function or a method calls another function which in turns calls another function etc., the execution of all those functions remains suspended until the very last function returns its value. Variables allocated on the heap have their memory allocated at run time and accessing this memory is a bit slower
3. The stack is always reserved in a LIFO order, the most recently reserved block is always the next block to be freed. This makes it really simple to keep track of the stack, freeing a block from the stack is nothing more than adjusting one pointer.Element of the heap have no dependencies with each other and can always be accessed randomly at any time. You can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time.

When to use stack and when to use heap?
You can use the stack if you know exactly how much data you need to allocate before compile time and it is not too big. You can use heap if you don't know exactly how much data you will need at runtime or if you need to allocate a lot of data.

 What is one problem with programming languages that a fully single-threaded?
 They can execute only one thread (the smallest sequence of programmed instructions that can be managed by the language) at a time

 Is Javascript a single-threaded language? Explain (Hint: This may not be a yes or no question)
 Javscript is single-threaded. Each browser window has only one Javascript thread running inside them. What makes the asynchronous events possible is the browser’s Event Loop and the associated Event Queue.

  When is using an Immediate Invoked Function Expression (IIFE)
 necessary?
  - Enables you to attach private data to a function
  - Creates fresh environments
  - Avoids polluting the global namespace.

  IIFE example
  var result = [];
  for (var i=0; i < 5; i++) {
    result.push( function() { return i } );
  }
  console.log( result[1]() ); // 5
  console.log( result[3]() ); // 5

  result = [];
  for (var i=0; i < 5; i++) {
    (function () {
      var j = i; // copy current value of i
      result.push( function() { return j } );
    })();
  }
  console.log( result[1]() ); // 1
  console.log( result[3]() ); // 3

 What is the syntax for an IIFE?
 The (surrounding parenthesis) prevents from treating it as a function declaration.
 The final parenthesis() are executing the function expression.

 What's hoisting?
 The behavior of “moving” var and function declarations to the top of their respective scopes during the compilation phase is called hoisting.
Function declarations are completely hoisted. This means that a declared function can be called before it is defined.
Variables are partially hoisted. var declarations are hoisted but not its assignments.
let and const are not hoisted.

What is a pure function? Impure function?
An impure function is a function that mutates variables/state/data outside of it’s lexical scope, thus deeming it “impure” for this reason. A pure function is much easier to comprehend, especially as our codebase may scale, as well as role-based functions that do one job and do it well. Pure functions don’t modify external variables/state/data outside of the scope, and returns the same output given the same input. Therefore it is deemed “pure”.

What is jQuery?
jQuery is a lightweight, "write less, do more", JavaScript library.
The purpose of jQuery is to make it much easier to use JavaScript on your website.
jQuery takes a lot of common tasks that require many lines of JavaScript code to accomplish, and wraps them into methods that you can call with a single line of code.
jQuery also simplifies a lot of the complicated things from JavaScript, like AJAX calls and DOM manipulation.
The jQuery library contains the following features:
 - HTML/DOM manipulation
 - CSS manipulation
 - HTML event methods
 - Effects and animations
 - AJAX
 - Utilities

  What does the new keyword do in Javascript?
  The new keyword invokes a function in a special way. Functions invoked using the new keyword are called constructor functions.
  So what does the new keyword actually do?
 - Creates a new object.
 - Sets the object’s prototype to be the prototype of the constructor function.
 - Executes the constructor function with this as the newly created object.
 - Returns the created object. If the constructor returns an object, this object is returned.

 Whats event bubling in JS?
 When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.

  How can you stop event bubbling?
  A bubbling event goes from the target element straight up. Normally it goes upwards till <html>, and then to documentobject, and some events even reach window, calling all handlers on the path.
But any handler may decide that the event has been fully processed and stop the bubbling.
The method for it is event.stopPropagation().

What is the difference between event.target and event.currentTarget?
event.target is the deepest element that originated the event.
event.currentTarget (=this) is the current element that handles the event (the one that has the handler on it)

 What does stopImmediatePropagation do?
If an element has multiple event handlers on a single event, then even if one of them stops the bubbling, the other ones still execute.
In other words, event.stopPropagation() stops the move upwards, but on the current element all other handlers will run.
To stop the bubbling and prevent handlers on the current element from running, there’s a method event.stopImmediatePropagation(). After it no other handlers execute.

What is JSON.stringify() and when to use it?
A common use of JSON is to exchange data to/from a web server.
When sending data to a web server, the data has to be a string.
Convert a JavaScript object into a string with JSON.stringify().
var obj = { name: "John", age: 30, city: "New York" };
var myJSON = JSON.stringify(obj);
myJSON => {"name":"John","age":30,"city":"New York"}

How to test JS Class?
You can test it with creating html file, opening it from the terminal and then opening the dev tools.
If there is no html file, you can type in node in the terminal and then paste the whole class.

 What is event delegation?
 Capturing and bubbling allow us to implement one of most powerful event handling patterns called event delegation.
The idea is that if we have a lot of elements handled in a similar way, then instead of assigning a handler to each of them – we put a single handler on their common ancestor.
In the handler we get event.target, see where the event actually happened and handle it.

How do you get user input in JS?
Ruby has the methods puts and gets. JavaScript has console.log as an analogue to puts, but it doesn't have an exact analogue for gets.
In a web browser, you may use the prompt method to pop up a message box to ask for input from the user. When running server-side code in the node.js environment, prompt is not available (because node is not a graphical environment).
Instead, you must use the readline library when writing server-side node.js programs.

                                const readline = require('readline');

                                const reader = readline.createInterface({
                                  input: process.stdin,
                                  output: process.stdout
                                });

                                reader.question("What is your name?", function (answer) {
                                  console.log(`Hello ${answer}!`);
                                });

                                console.log("Last program line");

                                <!--
                                What is your name?
                                Last program line
                                Uroshima
                                Hello Uroshima!
                                -->

 Discuss 4 differences between ES5 and ES6 that you find important
 1. Block Scope
ES5 only had “function-level scope” (i.e. you wrap code in functions to create scope) and caused a lot of issues. ES6 provides “block”-level scoping(i.e curly-braces to scope) when we use “let” or “const” instead of “var”.
2. Lexical “this” (via Arrow Functions)
In ES5, “this” can vary based on “where” it is called and even “how” it is called and has caused all sorts of pains for JS developers. ES6 eliminates this major issue by “lexical” this.
Lexical “this” a feature that forces the variable “this” to always point to the object where it is physically located within.
3. Dealing With “arguments”
In ES5, “arguments” acts like an Array (i.e. we can loop over it), but is not an Array. So, all the Array functions like sort, slice and so on are not available.
In ES6, we can use a new feature called “Rest” parameters. It’s represented with 3 dots and a name like …args. Rest parameters is an Array and so we can use all the Array functions.
4. Classes
Conceptually, there is no such thing as a “Class”(i.e. blueprint) in JS like it is in other OO languages like Java. But people for a long time have treated the “function” (aka “function constructors”) that creates Objects when we use the “new” keyword as Classes.
And since JS doesn’t support the “Classes” and just simulates it via “prototypes”, it’s syntax has been very confusing for both existing JS developers and new comers who wants to use it in a traditional OO fashion. This is especially true for things like: creating subclasses, calling functions in parent class and so on.
ES6 brings a new syntax that’s common in various programming languages and makes the whole thing simple.

 What are the steps of a try..catch block in Javascript?
 - First, the code in try {...} is executed.
- If there were no errors, then catch(err) is ignored: the execution reaches the end of try and then jumps over catch.
- If an error occurs, then try execution is stopped, and the control flows to the beginning of catch(err). The err variable (can use any name for it) contains an error object with details about what’s happened.

 When creating a custom error, what attributes should it have?
 Our errors should support basic error properties like message, name and, preferably, stack.
