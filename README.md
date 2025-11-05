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


