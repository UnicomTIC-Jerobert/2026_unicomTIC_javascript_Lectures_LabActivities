# Hour 6: Functions & Scope

**Building Your Own Reusable Mini-Programs**

---

### Recap & Agenda

**Where We've Been:**
*   We know how to store data (Variables).
*   We know how to make decisions (`if/else`).
*   We know how to repeat actions (Loops).

**Today's Agenda:**
1.  Why do we need Functions? (The DRY Principle continues).
2.  Declaring vs. Calling a Function.
3.  Inputs: Parameters and Arguments.
4.  Outputs: The magical `return` keyword.
5.  Default Parameters.
6.  Modern syntax: Arrow Functions.
7.  Scope: Where do my variables live?
8.  **Activity:** Building an Age Calculator.

---

### The Problem: Repeating Logic

Loops are great for doing the *exact same thing* right now, 10 times in a row.

But what if you need to do something, then do a bunch of other stuff, and then do that first thing again later?

If you copy and paste your code, you violate the **DRY (Don't Repeat Yourself)** principle. If you find a bug, you have to fix it in 50 different places!

---

### What is a Function?

A **Function** is a reusable block of code designed to perform a single, specific task.

**The Machine Analogy:**
Think of a function like a coffee machine. 
1. It sits there doing nothing until you turn it on (**Call**).
2. You put water and beans into it (**Inputs**).
3. It does some work inside (**Execution**).
4. It gives you a cup of coffee (**Output**).

---

### Two Phases of a Function

Working with functions always involves two distinct steps:

**Phase 1: Defining (Declaring) the function.**
*   This is building the machine. You write the instructions, but the code *does not run yet*.

**Phase 2: Calling (Executing) the function.**
*   This is pressing the "Start" button on the machine. You tell JavaScript, "Go find those instructions and run them right now."

---

### Phase 1: Declaring a Function

We use the `function` keyword, give it a name, add parentheses `()`, and open curly braces `{}`.

**Syntax:**
```javascript
function sayHello() {
  // The code to run goes here
  console.log("Hello, World!");
}
```
*Note: If you run this file, absolutely nothing happens. We just built the machine; we haven't turned it on.*

---

### Phase 2: Calling a Function

To make the function run, we write its name followed by parentheses `()`.

```javascript
// 1. Declare it
function sayHello() {
  console.log("Hello, World!");
}

// 2. Call it
sayHello(); // Output: Hello, World!
sayHello(); // Output: Hello, World!
sayHello(); // Output: Hello, World!
```
*We just reused that code three times with only three short lines!*

---

### Making Functions Smart: Parameters

A function that does the *exact* same thing every time is boring. We want our coffee machine to make *different kinds* of coffee.

We use **Parameters**. A parameter is a temporary variable that acts as an "input slot" for our function.

```javascript
// 'name' is the parameter
function greetUser(name) {
  console.log("Welcome back, " + name + "!");
}
```

---

### Giving Data to Functions: Arguments

When we *call* the function, we provide the actual data to fill those input slots. These are called **Arguments**.

```javascript
function greetUser(name) { // 'name' is the parameter
  console.log("Welcome back, " + name + "!");
}

// "Alice" and "Bob" are the arguments
greetUser("Alice"); // Output: Welcome back, Alice!
greetUser("Bob");   // Output: Welcome back, Bob!
```

---

### Multiple Parameters

Functions can take as many inputs as you want. Just separate them with commas.

```javascript
function calculateArea(width, height) {
  let area = width * height;
  console.log("The area is " + area);
}

calculateArea(10, 5); // Output: The area is 50
calculateArea(3, 3);  // Output: The area is 9
```
*Order matters! `10` goes into `width`, and `5` goes into `height`.*

---

### The Most Common Beginner Mistake

Look at this code:

```javascript
function addNumbers(a, b) {
  let sum = a + b;
  console.log(sum);
}

let myTotal = addNumbers(5, 5);
console.log("My total is: " + myTotal);
```
**Expected Output:** My total is: 10
**Actual Output:** My total is: undefined

*Why? Because `console.log` only prints to the screen. It DOES NOT give data back to the program.*

---

### Getting Data Back: The `return` Keyword

To actually get a usable answer back from our machine, we must use the `return` keyword.

`return` is the function's way of handing data back to the person who called it.

```javascript
function addNumbers(a, b) {
  let sum = a + b;
  return sum; // Hand the answer back!
}

// Now we can capture the answer in a variable
let myTotal = addNumbers(5, 5); 

console.log("My total is: " + myTotal); // Output: My total is: 10
```

---

### The Golden Rule of `return`

**`return` instantly stops the function.**

Any code written *after* a `return` statement inside a function will never be executed. It's the exit door.

```javascript
function testReturn() {
  return "I am done!";
  console.log("This will never print."); // JavaScript ignores this line
}
```

---

### Default Parameters

What happens if a user forgets to provide an argument? The parameter becomes `undefined`.

We can prevent errors by providing **Default Parameters**.

```javascript
// If no name is provided, use "Guest"
function greet(name = "Guest") {
  return "Hello, " + name;
}

console.log( greet("Sarah") ); // Output: Hello, Sarah
console.log( greet() );        // Output: Hello, Guest
```

---

### Different Ways to Write Functions

JavaScript has evolved over the years, and there are now a few ways to write functions. You will see all of them in the real world.

1.  **Function Declaration** (What we've been doing).
2.  **Function Expression**.
3.  **Arrow Function** (Modern JS).

Let's look at the other two.

---

### Function Expressions

Instead of giving the function a name directly, we can create an *anonymous* (nameless) function and store it inside a variable.

```javascript
// Function Expression
const multiply = function(a, b) {
  return a * b;
};

console.log( multiply(4, 5) ); // Output: 20
```
*This does the exact same thing, but it proves that functions in JavaScript are just values, like numbers or strings, that can be stored in variables!*

---

### Modern JS: The Arrow Function

Introduced in ES6 (2015), **Arrow Functions** provide a shorter, cleaner syntax. They are incredibly popular in modern development (like React or Node.js).

Instead of the `function` keyword, we use an arrow `=>`.

**Old Way:**
```javascript
const add = function(a, b) {
  return a + b;
};
```

**New Arrow Way:**
```javascript
const add = (a, b) => {
  return a + b;
};
```

---

### Arrow Function Superpowers

If your arrow function is only one line long and just returns a value, you can remove the curly braces `{}` and the `return` keyword entirely!

**The one-liner:**
```javascript
const add = (a, b) => a + b;

console.log( add(10, 5) ); // Output: 15
```
*Clean, concise, and beautiful.*

---

### Introduction to Scope

**Scope** is the set of rules that determines where your variables "live" and who is allowed to see them.

Imagine a house with a yard.
*   **Global Scope:** The yard. Everyone walking by can see what's in the yard.
*   **Local (Block/Function) Scope:** A locked bedroom. Only people inside the bedroom can see what's in there.

---

### Global Scope

Variables declared *outside* of any function or block have Global Scope. They can be accessed and modified from *anywhere* in your file.

```javascript
let playerName = "Mario"; // Global Scope

function printName() {
  // The function can see the global variable
  console.log("The player is " + playerName); 
}

printName(); // Output: The player is Mario
```

---

### Local (Function) Scope: The Vegas Rule

Variables declared *inside* a function are Local to that function. 

> **The Vegas Rule:** What happens in the function, stays in the function.

```javascript
function secretMission() {
  let secretCode = 12345; // Local variable
  console.log("Inside: " + secretCode); // Works fine
}

secretMission();

// Trying to access it from the outside will cause a FATAL ERROR!
console.log("Outside: " + secretCode); // ERROR: secretCode is not defined
```

---

### Why is Local Scope Good?

It prevents variables from colliding! You can have multiple functions using the same variable names (like `i`, `total`, or `result`) without them messing each other up.

```javascript
function mathOne() {
  let total = 50;
  return total;
}

function mathTwo() {
  let total = 100; // This 'total' is completely separate from the one above!
  return total;
}
```

---

### Activity Prep: The Age Calculator

We are going to build a function that takes a person's birth year, calculates their age, and returns the result.

**The Goal:**
1. Create a function using an Arrow Function.
2. Give it parameters.
3. Make it `return` the age.
4. Output the result using `console.log()` first, and then attach it to an HTML page using `document.write()`.

---

### Activity: Code Along (The Logic)

1. Create a file named `calculator.html`.
2. Add the basic HTML structure and a `<script>` tag.
3. Write this inside the script:

```javascript
// 1. Declare the Arrow Function
const calculateAge = (birthYear) => {
    const currentYear = 2024; // You can hardcode this for now
    const age = currentYear - birthYear;
    return age; // Send the data back!
};

// 2. Call the function and store the returned data
const myAge = calculateAge(1995);

// 3. Test it in the console
console.log("Calculated Age:", myAge);
```

---

### Activity: Code Along (The DOM)

Now let's display it on the screen dynamically.

```javascript
// ... (previous code) ...

// Let's ask the user for their birth year!
// prompt() is a built-in browser function that asks for input
let userYearString = prompt("What year were you born?");

// Convert the string to a number
let userYear = Number(userYearString);

// Call our custom function with the user's input
let userAge = calculateAge(userYear);

// Write to the page
document.write("<h1>Age Calculator Results</h1>");
document.write("<p>If you were born in " + userYear + ", you are " + userAge + " years old.</p>");
```

---

### Key Takeaways for Hour 6

*   **Functions** allow us to write reusable blocks of code.
*   **Parameters** are the input slots (variables in the definition).
*   **Arguments** are the actual data passed in when calling.
*   **`return`** is how a function hands a value back to the program (it is NOT the same as `console.log`).
*   **Arrow functions** `() => {}` are a modern, shorter way to write functions.
*   **Local Scope** ensures variables created inside a function cannot be accessed from the outside.

---

### Next Time...

**Coming Up in Hour 7: Arrays & Array Methods**

Right now, our variables can only hold one thing at a time. What if we want to store a whole list of things, like a shopping list or 100 user scores?

We will learn about:
*   Creating Arrays.
*   Accessing data using Indexes.
*   Methods to add, remove, and modify lists (`push`, `pop`, etc.).
*   Iterating over arrays with loops.
```
