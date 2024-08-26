sql comparisons with null always end up in null
custom JS events

rafael gratta

Dribbble
Behance
Awwwards
CSS Design Awards
Pinterest
Reddit

A List Apart
Smashing Magazine
UX Magazine
Web Design Weekly

"Designing with Web Standards" by Jeffrey Zeldman
"The Non-Designer's Design Book" by Robin Williams
"Designing Interfaces" by Jenifer Tidwell
Online courses and tutorials on platforms like Udemy

# Amanhã

promises
continue writing all the array methods
give examples on javascript this file
event bubbling
promiseall and promiseallsettled
map and weakmap
garbage collector
object freeze
explicit binding through call, apply or bind methods
setInterval and setTimeout
labeled statements
defer and async
json.parse in json obsidian file (json is a string so once you use JSON.parse(jsonString) you get the JS equivalent of an object)
debugger statement and console log for debugging
event loop js

The Event loop has two main components: the Call stack and the Callback queue.
Call Stack

The Call stack is a data structure that stores the tasks that need to be executed. It is a LIFO (Last In, First Out) data structure, which means that the last task that was added to the Call stack will be the first one to be executed.
Callback Queue

The Callback queue is a data structure that stores the tasks that have been completed and are ready to be executed. It is a FIFO (First In, First Out) data structure, which means that the first task that was added to the Callback queue will be the first one to be executed.
Event Loop's Workflow:

    Executes tasks from the Call Stack.
    For an asynchronous task, such as a timer, it runs in the background. JavaScript proceeds to the next task without waiting.
    When the asynchronous task concludes, its callback function is added to the Callback Queue.
    If the Call Stack is empty and there are tasks in the Callback Queue, the Event Loop transfers the first task from the Queue to the Call Stack for execution.

setTimeout(() => console.log('Hello from the timer'), 0);
console.log('Hello from the main code');

    setTimeout is processed, and because it's asynchronous, its callback is placed in the Callback Queue.
    The next line, console.log("Hello from the main code"), is logged immediately.
    Although the timer duration is 0 milliseconds, its callback has to wait until the Call Stack is empty. After the main code logs, the callback is moved from the Callback Queue to the Call Stack and executed.
    The result is "Hello from the main code" being logged before "Hello from the timer".

---

comma operator
nullish coalescing operator
appendChild and insertBefore
remove and removeChild
window api e windowscrollto
getBoundingClientRect
