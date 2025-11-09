# web-main-frnd
Lets learn javascript

| Browser      | JS Engine      |
| ------------ | -------------- |
| Chrome, Edge | V8             |
| Firefox      | SpiderMonkey   |
| Safari       | JavaScriptCore |


The Execution Context
When the engine runs your code, it creates an Execution Context —
this is the environment where your code actually lives and runs.
=>its somehting like big box where whole js is excecutred

There are two kinds:
Global Execution Context (GEC) — created automatically when your file starts running.
Function Execution Context (FEC) — created each time you call a function.
So when the program starts, the first thing created is the Global Execution Context.

| Part                                  | Description                                                        | Example                           |
| ------------------------------------- | ------------------------------------------------------------------ | --------------------------------- |
| 🗂️ **Memory (Variable Environment)** | Where all variables and functions are stored as *key-value pairs*. | `a → undefined`, `add → function` |
| ⚡ **Code (Thread of Execution)**    | Where the code runs line by line.                                  | executes `a = 10`, calls `add()`  |

=>see when we run js code the GEC is pushed into the call stack or exceutable stack n inside trhe code if any function call is there 
then another context i.e FEC will be pushed into the call stack similarly to any function call.when function is done with the work its poped out from the stack 
and at the end GEC will be present which also will poped once the progrm ends.

====================================================================================================================================================================
js is synchronous single threaded lanaguage

A thread is like a path of execution — it’s how the computer runs your code, line by line.
When we say JavaScript is single-threaded, it means:
🟢 It can execute only one line of code at a time in a single main thread.
So if JS is doing one task, it cannot do another at the same moment.
syncronous means it follows a particular order
“Synchronous” means JavaScript executes code in the order it appears,
and each line waits for the previous one to finish before running.
====================================================================================================================================================================
wht happens when u run a js progrm behind the scene
see as soon as the progrm is runned the global exceution phase will be tehre which holds memory and code 
this exceution phase has 2 phases i.e creation phase (memory creation pahse-criticalpahse) next is code excecution phase)

====================================================================================================================================================================
What is Hoisting?
👉 Hoisting means JavaScript moves declarations (not initializations) to the top of their scope before the code actually runs.
In simple words:
You can use variables or functions before you actually write them in your code — because JavaScript sets them up in memory first.

Why does this happen?
Because when JavaScript runs your code, it does it in two phases inside the Execution Context:
🩵 1. Memory Creation Phase:
JS scans your code and allocates memory for all variables and functions.
Variables are stored as undefined initially.
Functions are fully stored in memory.
💚 2. Code Execution Phase:
JS executes your code line by line.
Now it assigns real values to variables and runs the functions.

====================================================================================================================================================================
1. How JavaScript Runs in the Browser

When you open a webpage in Chrome, Edge, or Firefox, each browser has a JavaScript engine inside it (like Chrome → V8 Engine).
When JS code runs:
The browser gives an environment to run the JS — this is called the Global Environment.
The JS Engine creates the Global Execution Context (GEC).
The GEC is linked to a big global object.
In browsers, that global object is called window.
In Node.js, it’s called global

🌐 2. The Window Object — The “Global King”
When JS starts in the browser, it automatically creates a window object.
The window object:
represents the global scope.
contains everything in the browser — variables, functions, and also browser features like:
alert()
setTimeout()
document (to access HTML)
location (URL info)
and more.

example 1:
console.log(window);
✅ This prints a huge object in your browser console with many properties and functions.

example 2:
var name = "Meghana";
console.log(window.name);
✅ Output:
Meghana

3. The Global Execution Context (GEC)
When your JS file starts running:
The engine creates a Global Execution Context.
This GEC has:
A Memory Component (also called the Variable Environment)
A Thread of Execution (where code runs line by line)
In the browser:
The global object (window) is created first.
The this keyword at the global level points to window.

example:
console.log(this === window);
true

4)The Call Stack

Whenever you call a function, JS creates a new Execution Context for it.
All execution contexts are managed using a Call Stack (like plates stacked on top of each other 🍽️).

example :
function first() {
  console.log("First");
  second();
}

function second() {
  console.log("Second");
}
first();

Behind the scenes:
JS creates Global Execution Context (GEC) → pushed to the call stack
Calls first() → new Function Execution Context → pushed
Calls second() → another Function Execution Context → pushed
second() finishes → popped out
first() finishes → popped out
Finally, the Global Execution Context is popped off when the program ends
===================================================================================================================================================================
What is undefined?
👉 undefined means:
The variable exists in memory, but no value has been assigned to it yet
JavaScript knows the variable, but doesn’t know its value.

What is not defined?
👉 not defined means:
The variable was never declared in the code at all.

TRICKY INTERVIEW QUESTION
example 1:
console.log(x);
var x = 5;
output:undefined

typeof
example 2:
The typeof operator never throws an error, even for undeclared variables.
var a;
console.log(typeof a); // undefined
console.log(typeof b); // undefined (even though b not declared)

<img width="1174" height="659" alt="image" src="https://github.com/user-attachments/assets/7ac0eacb-9841-4e67-b845-a3e39ef05e6f" />
