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

=========================================================================================================================
js is synchronous single threaded lanaguage

A thread is like a path of execution — it’s how the computer runs your code, line by line.
When we say JavaScript is single-threaded, it means:
🟢 It can execute only one line of code at a time in a single main thread.
So if JS is doing one task, it cannot do another at the same moment.
syncronous means it follows a particular order
“Synchronous” means JavaScript executes code in the order it appears,
and each line waits for the previous one to finish before running.
=============================================================================================================================
wht happens when u run a js progrm behind the scene
see as soon as the progrm is runned the global exceution phase will be tehre which holds memory and code 
this exceution phase has 2 phases i.e creation phase (memory creation pahse-criticalpahse) next is code excecution phase)

==============================================================================================================================
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

=================================================================================================================================
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
================================================================================================
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

===============================================================================================================
Background — What’s the Problem with var?
Before ES6 (2015), JavaScript only had var.
Example:

console.log(a); // undefined
var a = 10;
Even though we’re accessing a before it’s declared, we don’t get an error — we get undefined.
That’s because var is hoisted and initialized to undefined during the creation phase of the execution context.

ES6 Introduced let and const

To make things safer and more predictable, ES6 introduced:
let → for block-scoped, reassignable variables
const → for block-scoped, non-reassignable variables
But both of these come with a new concept:
Temporal Dead Zone (TDZ)


What is Temporal Dead Zone?

TDZ is the time between:
the start of the scope (when the variable is known to exist)
and the moment it’s actually declared in your code.
"In general its the time between the variable declared in the memory till the varible being initialized"
During this time, you cannot access the variable — if you try, you’ll get a ReferenceError.

example(same for both let and const):
When the JS engine executes your code:
It creates a memory space for all variables (hoisting).
For var, it sets the value to undefined immediately.
For let and const, it does not initialize them yet → they stay in TDZ.
Only after the line let x = 5; is executed does the variable become initialized.
{
  // TDZ starts for x
  console.log(x); // ❌ ReferenceError
  let x = 5;      // TDZ ends here
  console.log(x); // ✅ 5
}
"before the initialization of variable (let and const)u cant print it,it will throw u refernce errorin js if itslet or const
if its var then it will give u undefined
and if the variable is not at all defined then it will throw u refernce errror :not-defined
like the let and const variable will be stored in script area and the var will get stored in global area"

===========================================================================================================
1. What Happens When JavaScript Code Runs
When JS executes your code, it creates an Execution Context (we’ve seen this before).
Each Execution Context has two main parts:

1️⃣ Memory Component (Variable Environment + Lexical Environment)
2️⃣ Code Component (Thread of Execution)
Now, within the Global Execution Context (GEC) — which is created when your program starts — the JS engine allocates memory differently for var, let, and const.

2. Memory Creation Phase (Before Execution Starts)

When the JS engine parses your code, it creates a Global Object (like window in browsers) and a Global Memory Space.
It allocates memory for all declared variables before running any line.
Here’s the key difference 👇
| Type            | Memory Location                            | Initialization        | Accessible before Declaration |
| --------------- | ------------------------------------------ | --------------------- | ----------------------------- |
| `var`           | **Global / Variable Object (VO)**          | `undefined`           | ✅ Yes                         |
| `let` & `const` | **Script / Block Scope (Separate memory)** | *Uninitialized* (TDZ) | ❌ No                          |


3. How It Looks Visually
var a = 10;
let b = 20;
const c = 30;
During Memory Creation Phase:
| Variable | Memory Location            | Value           | Status       |
| -------- | -------------------------- | --------------- | ------------ |
| `a`      | Global Object (`window.a`) | `undefined`     | ✅ accessible |
| `b`      | Script Scope               | *uninitialized* | 🚫 TDZ       |
| `c`      | Script Scope               | *uninitialized* | 🚫 TDZ       |

During Execution Phase (line-by-line):
var a = 10 → a is updated to 10.
let b = 20 → b is initialized and updated to 20.
const c = 30 → c is initialized and set to 30 (can’t be changed later).

"Var will be stored in the global object(windows) and the let and const will in script area"

GLOBAL EXECUTION CONTEXT
------------------------------------
Memory Space (Environment Record)
| window (global object)
| var → stored in window (undefined initially)
| let → stored in script record (uninitialized → TDZ)
| const → stored in script record (uninitialized → TDZ)

Execution Thread (Code)
| Executes line by line
| Initializes let/const when their line is reached
------------------------------------

===================================================================================================================================================================
Var, Let & Const

| Feature                 | `var`         | `let`   | `const` |
| ----------------------- | ------------- | ------- | ------- |
| Scope                   | Function      | Block   | Block   |
| Hoisted                 | ✅ (undefined) | ✅ (TDZ) | ✅ (TDZ) |
| TDZ                     | ❌ No          | ✅ Yes   | ✅ Yes   |
| Redeclaration           | ✅ Yes         | ❌ No    | ❌ No    |
| Reassignment            | ✅ Yes         | ✅ Yes   | ❌ No    |
| Initialization required | ❌ No          | ❌ No    | ✅ Yes   |
| Added to `window`       | ✅ Yes         | ❌ No    | ❌ No    |

// Hoisting test
console.log(a); // undefined
// console.log(b); // ReferenceError
// console.log(c); // ReferenceError

var a = 10;
// Redeclaration
var a = 40; // ✅
console.log(a); // 40

let b = 20;
// let b = 50; ❌ SyntaxError (redeclared)
b = 50; // ✅ reassignment allowed
console.log(b); // 50

const c = 30;
// c = 60; ❌ TypeError (cannot reassign const)

const a;
a=10;//Syntax error:missing initializer in const declaration

===================================================================================================================================================================
1. What is a Block?
In JavaScript, a block is anything inside curly braces {}.

2. What is Block Scope?
➡️ Block scope means that variables declared inside {} using let or const
are accessible only inside that block — not outside it.

{
  let a = 10;
  const b = 20;
  var c = 30;
}
console.log(c); // ✅ 30 (var is NOT block scoped)
console.log(a); // ❌ ReferenceError
console.log(b); // ❌ ReferenceError

✅ var is function-scoped (or global if outside a function).
❌ let and const are block-scoped

3. Nested Scopes & Scope Chain
Variables in inner blocks can access variables from outer blocks,
but not the other way around.

let x = 10;
{
  let y = 20;
  console.log(x); // ✅ can access outer variable
  console.log(y); // ✅ 20
}
console.log(y); // ❌ ReferenceError
✅ This is because of Lexical Scoping (the inner scope has access to outer scope).

SHADOWING

block shadowing
var a=100
let b=200;
const c=300;
{
  var a=10;
  let b = 20;
  const c=30;
  console.log(a); //10
  console.log(b);// 20 (inner b)
  console.log(c);// 30
  
}
console.log(a); // 10
console.log(b); // 200
console.log(c); //300


illegal shadowing
->u cannot shadow let usign var
let a=20;
{
var a=20;//syntaxerror:a is already declared
} //this cannot be doen let cannot be shadowed using var,it can only be done by let only
but we can shadow a var using let

var a=20;
{
let a=20;
}//this can be sone
