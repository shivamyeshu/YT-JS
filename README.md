# YT-JS
TOPICS TO COVER : 

### 1 JS BASICS 
 html + css + js = web an all 

### 2 PROPERTIES OF JS : 
i) Interpreted
JavaScript is an interpreted language, meaning it's executed line-by-line at runtime by the JavaScript engine in the browser or server environment, 
rather than being compiled into machine code beforehand


BENIFITS : THERE WILL BE LESS ONE STEP 

DEMERITS : 
a) Performance Overhead
b) More prone to runtime errors

ii) Dynamically Typed
 Variables in JavaScript are not bound to a specific data type. Types are determined at runtime and can change as the program executes


 iii) Single threaded thread sinle execution of a lang 
JavaScript executes code in a single-threaded environment, meaning it processes one task at a time. We will dive deeper into this next week.

iv) Garbage collected (auto memory allocation and deallocation)
JavaScript automatically manages memory allocation and deallocation through garbage collection, 
which helps prevent memory leaks by automatically reclaiming memory used by objects no longer in use.


### Syntax of Javascript
1. Variables
Variables are used to store data. In JavaScript,
you declare variables using ( var, let, or const )

ex : 
let name = "John";     // Variable that can be reassigned
const age = 30;        // Constant variable that cannot be reassigned
var isStudent = true;  // Older way to declare variables, function-scoped

2. Data types
let number = 42;             // Number
let string = "Hello World";  // String
let isActive = false;        // Boolean
let numbers = [1, 2, 3];     // Array

3. Operators
let sum = 10 + 5;          // Arithmetic operator
let isEqual = (10 === 10); // Comparison operator
let isTrue = (true && false); // Logical operator

4. Functions
   
// Function declaration
function greet(name) {
    return "Hello, " + name;
}

// Function call
let message = greet("John"); // "Hello, John"

5. If/Else
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}

6. Loops ( initalization condition and updation
// For loop
for (let i = 0; i < 5; i++) {
    console.log(i); // Outputs 0 to 4
}

// While loop
let j = 0;
while (j < 5) {
    console.log(j); // Outputs 0 to 4
    j++;
}

### Complex types

Objects
An object in JavaScript is a collection of key-value pairs,
where each key is a string and each value can be any valid JavaScript data type, including another object.

ex :

let user = {
	name: "Shivam",
	age: 20
}

console.log("Shivam's age is " + user.age);

2) Arrays
   
Arrays let you group data together
const users = ["shivam", "yeshu", "sachin"];
const tatalUsers = users.length;
const firstUser = users[0];

3) Arrays of Object
 We can have more complex objects, for example an array of objects

const users = [{
		name: "shivam",
		age: 20
	}, {
		name: "yeshu",
		age: 21
	}
}

const user1 = users[0] 
const user1Age = users[0].age


## deep dive into functions part 2
### function 

Find sum of two numbers

function sum(a, b) {
	return a + b;
}

let ans = sum(2, 3)
console.log(sum);

|| 

Find sum from 1 to a number
function sum(n) {
	let ans = 0;
	for (let i = 1; i <= n; i++) {
		ans = ans + i
	}
	return ans;
}

const ans = sum(100);
console.log(ans);

before this lets under stand 
### Synchronous code
Synchronous code is executed line by line, in the order it's written. 
Each operation waits for the previous one to complete before moving on to the next one.

For example

function sum(n) {
	let ans = 0;
	for (let i = 1; i <= n; i++) {
		ans = ans + i
	}
	return ans;
}

const ans1 = sum(100);
console.log(ans1);
const ans2 = sum(1000);
console.log(ans2);
const ans3 = sum(10000);
console.log(ans3);

### I/O heavy operations

I/O (Input/Output) heavy operations refer to tasks in a computer program that involve a lot of data transfer between the program and external systems or devices. 
These operations usually require waiting for data to be read from or written to sources like disks, networks, databases, or other external devices, 
which can be time-consuming compared to in-memory computations.

for example read the content from the file 

var a = readFile(a.txt)

Examples of I/O Heavy Operations:
Reading a file
Starting a clock
HTTP Requests

Let’s try to write code to do an I/O heavy operation - 

A)

Create a file in there (a.txt) with some text inside
Write the code to read a file synchronously

soln: 
const fs = require("fs");

const contents = fs.readFileSync("a.txt", "utf-8"); // readFileSync
console.log(contents);

B)

Create another file (b.txt)
Write the code to read the other file synchronously
const fs = require("fs");

const contents = fs.readFileSync("a.txt", "utf-8");
console.log(contents);

const contents2 = fs.readFileSync("b.txt", "utf-8");
console.log(contents2);

 ### I/O bound tasks vs CPU bound tasks
A} CPU bound tasks
CPU-bound tasks are operations that are limited by the speed and power of the CPU. 
These tasks require significant computation and processing power, meaning that the performance bottleneck is the CPU itself.

example. 

let ans = 0;
for (let i = 1; i <= 1000000; i++) {
	ans = ans + i
}
console.log(ans);	

💡
A real world example of a CPU intensive task is running for 3 miles. Your legs/brain have to constantly be engaged for 3 miles while you run.

B} I/O bound tasks
I/O-bound tasks are operations that are limited by the system’s input/output capabilities, such as disk I/O, 
network I/O, or any other form of data transfer. These tasks spend most of their time waiting for I/O operations to complete.
const fs = require("fs");

const contents = fs.readFileSync("a.txt", "utf-8");
console.log(contents);

💡
A real world example of an I/O bound task would be Boiling water. I don’t have to do much,
I just have to put the water on the kettle, and my brain can be occupied elsewhere.

#### IO bound task  in real life 

![image](https://github.com/user-attachments/assets/061a29e2-7b3b-4782-825a-55eda69b98be)

What if you were tasked with doing 3 things
Boil some water.
Do some laundry
Send a package via mail

Would you do these 
One by one (synchronously) ??
Context switch between them (Concurrently) ??
Start all 3 tasks together, and wait for them to finish. The first one that finishes gets catered to first. ?

------------------------------------

### Synchronously (One by one)
![image](https://github.com/user-attachments/assets/760852a9-3c01-46ae-8214-1c8129731ed5)

const fs = require("fs");

const contents = fs.readFileSync("a.txt", "utf-8");
console.log(contents);

const contents2 = fs.readFileSync("b.txt", "utf-8");
console.log(contents2);

const contents3 = fs.readFileSync("b.txt", "utf-8");
console.log(contents3);


------------------------------------

Start all 3 tasks together, and wait for them to finish. 
![image](https://github.com/user-attachments/assets/f29821d2-deee-47a2-8d2c-88df8baa629a)

const fs = require("fs");

fs.readFile("a.txt", "utf-8", function (err, contents) {
  console.log(contents);
});

fs.readFile("b.txt", "utf-8", function (err, contents) {
  console.log(contents);
});

fs.readFile("a.txt", "utf-8", function (err, contents) {
  console.log(contents);
});

before this lets understand functional argunment 
### functional argument 

A) Write a calculator program that adds, subtracts, multiplies, divides two arguments.
Approach #1

Calling the respective function
function sum(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

function subtract(a, b) {
  return a - b;
}

function divide(a, b) {
  return a / b;
}

console.log(sum(1, 2))

B) 
Approach #2
Passing in what needs to be done as an argument.
function sum(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

function subtract(a, b) {
  return a - b;
}

function divide(a, b) {
  return a / b;
}

function doOperation(a, b, op) {
  return op(a, b)
}

console.log(doOperation(1, 2, sum))

here op is working as a functional argument 

## Asynchronous code, callbacks
Let’s look at the code to read from a file asynchronously. Here, we pass in a function as an argument. 
This function is called a callback since the function gets called back when the file is read 

![image](https://github.com/user-attachments/assets/1f6be0a9-9c3b-404f-9860-99abe434cd45)

const fs = require("fs");

fs.readFile("a.txt", "utf-8", function (err, contents) {
  console.log(contents);
});

setTimeout
setTimeout is another asynchronous function that executes a certain code after some time
function run() {
	console.log("I will run after 1s");
}

setTimeout(run, 1000);
console.log("I will run immedietely");

------------------------------------------------------------------------------------
JS Architecture for async code
How JS executes asynchronous code - http://latentflip.com/loupe/ 

1. Call Stack
 The call stack is a data structure that keeps track of the function calls in your program. It operates in a "Last In, First Out" (LIFO) manner, meaning the last function that was called is the first one to be executed and removed from the stack.
When a function is called, it gets pushed onto the call stack. When the function completes, it's popped off the stack.
Code
function first() {
  console.log("First");
}
function second() {
  first();
  console.log("Second");
}
second();

2. Web APIs
Web APIs are provided by the browser (or the Node.js runtime) and allow you to perform tasks that are outside the scope of the JavaScript language itself, such as making network requests, setting timers, or handling DOM events.
3. Callback Queue 
The callback queue is a list of tasks (callbacks) that are waiting to be executed once the call stack is empty. These tasks are added to the queue by Web APIs after they have completed their operation.
4. Event loop
The event loop constantly checks if the call stack is empty. If it is, and there are callbacks in the callback queue, it will push the first callback from the queue onto the call stack for execution.
