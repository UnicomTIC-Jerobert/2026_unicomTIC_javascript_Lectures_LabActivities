### **Hour 2: Variables, Data Types, and Comments**

# Hour 2: Variables & Data Types

**The Building Blocks of Every Program**

---

### Recap & Agenda

**Where We've Been:**
*   We learned what JavaScript is.
*   We set up our tools (VS Code & Node.js).
*   We wrote our first code using `console.log()` and `document.write()`.

**Today's Agenda:**
1.  **What is a Variable?** - Our program's memory.
2.  **Declaring Variables:** `let` and `const`.
3.  **Data Types:** The different kinds of information we can store.
4.  **Dynamic Typing:** JavaScript's special magic.
5.  **Activity:** Build a "User Profile Card" on a webpage.

---

### Why Do We Need Variables?

Imagine you want your program to remember a user's name. You can't just write "Alex" in your code everywhere and expect the program to know what it means.

We need a way to **store** and **label** pieces of information so we can use them later.

**This is where variables come in!**

---

### What is a Variable?

A variable is simply a **named container** in your program's memory where you can store a piece of data.

Think of it like a physical box with a label on it.

You can:
1.  **Declare** it (build the box and write the label).
2.  **Assign** a value to it (put something inside the box).
3.  **Access** the value later by using its label (look inside the box).

---

### How to Create Variables: `let`

We use the `let` keyword to declare a variable when we expect its value **might change** later in the program.

Think of it like a name written on a whiteboard. You can erase it and write a new one.

```javascript
let currentScore = 0;
console.log(currentScore); // Output: 0

// The score changes later in the game
currentScore = 100;
console.log(currentScore); // Output: 100
```

---

### How to Create Variables: `const`

We use the `const` keyword to declare a variable when we know its value **will never change**.

Think of it as a name carved in stone. Once set, it cannot be altered.

```javascript
const birthYear = 1995;
console.log(birthYear); // Output: 1995

// If we try to change it...
birthYear = 2000; // ❌ THIS WILL CAUSE A FATAL ERROR!
```
*(Getting an error here is actually a good thing! It protects us from accidentally deleting important data).*

---

### `let` vs. `const`: The Golden Rule

This choice seems tricky, but there's a very easy rule to follow:

**Always declare your variables with `const` first.**

If you later realize that the value of the variable needs to change, simply go back and switch it to `let`. 

This is a modern best practice that makes your code safer.

---

### A Quick Word on `var`

You will see the keyword `var` in older JavaScript tutorials.

```javascript
var oldVariable = "I am from the past";
```

For our course, we will **avoid using `var`**. It has some quirky, confusing behaviors that can cause bugs. `let` and `const` were introduced to be better, modern replacements.

---

### Introduction to Data Types

Variables can hold many different types of data. JavaScript has several basic (primitive) data types.

Let's look at the three most common ones:
1.  **String**
2.  **Number**
3.  **Boolean**

---

### Data Type 1: String

A **String** is used for any textual data (words, sentences, even a single letter). 
You create a string by wrapping text in quotes (`" "` or `' '`).

```javascript
const userName = "Alice"; // Double quotes
const city = 'New York';  // Single quotes

// We can join strings together using the + sign
const greeting = "Hello, " + userName + "!";

console.log(greeting); // Output: Hello, Alice!
```

---

### Data Type 2: Number

The **Number** type is used for all numerical data, including whole numbers (integers) and decimals.

You do **not** use quotes around numbers.

```javascript
const userAge = 28;
const price = 19.99;
const temperature = -5;

// If you put quotes around it, it's a string, not a number!
const fakeNumber = "25"; 
```

---

### Data Type 3: Boolean

A **Boolean** can only have two possible values: `true` or `false`.

Think of it as a light switch: it's either ON (`true`) or OFF (`false`). Booleans are the foundation of decision-making in code.

```javascript
const isLoggedIn = true;
const hasAdminAccess = false;
```
*(Notice there are no quotes around `true` or `false`. They are special keywords).*

---

### The "Empty" Values

There are two special values that represent "nothing":

*   **`undefined`**: A variable has been declared, but hasn't been given a value yet. (The box exists, but it's empty).
    ```javascript
    let userEmail;
    console.log(userEmail); // Output: undefined
    ```

*   **`null`**: An intentional absence of value. (We explicitly put a note in the box saying "There is nothing here").
    ```javascript
    let selectedItem = null;
    ```

---

### The Magic of Dynamic Typing

In some older programming languages, you have to explicitly tell the computer what type of data a variable will hold (e.g., `String myName = "Alex"`).

JavaScript is **dynamically typed**. The variable automatically figures out its type based on what you put inside it.

```javascript
let myData = 42; // JS knows this is a Number
console.log(typeof myData); // Output: "number"

myData = "Hello"; // JS automatically changes it to a String!
console.log(typeof myData); // Output: "string"
```
*(The `typeof` operator is great for checking what type of data you currently have).*

---

### Comments in Code

Before our activity, let's learn how to leave notes for ourselves. **Comments** are ignored by JavaScript.

```javascript
// This is a single-line comment. It's just a note for humans.
const score = 100;

/* 
  This is a multi-line comment.
  It is great for writing long explanations
  or temporarily hiding blocks of code.
*/
```

---

### Activity Prep: The User Profile Card

We are going to use everything we've learned to create a simple user profile and display it on a webpage.

**Our Goal:**
1.  Create variables for a user's name, age, and employment status.
2.  Use `document.write()` to print this information.
3.  Add HTML tags directly into our `document.write()` strings to format the output.

---

### Activity: Code Along

1.  Create a new file named `profile.html`.
2.  Add the following code:

```html
<!DOCTYPE html>
<html>
<body>
    <script>
        // 1. Declare variables
        const userName = 'Alex Smith';
        const userAge = 32;
        const isEmployed = true;
        
        // 2. Output with HTML formatting
        document.write('<h1>User Profile Card</h1>');
        document.write('<p><strong>Name:</strong> ' + userName + '</p>');
        document.write('<p><strong>Age:</strong> ' + userAge + '</p>');
        document.write('<p><strong>Employed:</strong> ' + isEmployed + '</p>');
    </script>
</body>
</html>
```

---

### Activity Breakdown

What did we just do?

*   `const userName = 'Alex Smith';`
    *   We created a **constant variable** and assigned it a **String**.
*   `document.write('<p><strong>Name:</strong> ' + userName + '</p>');`
    *   We used the `+` operator to **concatenate** (glue together) plain text, HTML tags, and the dynamic value stored in our variable.
*   Because JS is dynamically typed, it easily converted the `userAge` (Number) and `isEmployed` (Boolean) into text to display on the screen!

---

### Key Takeaways for Hour 2

*   **Variables** are named containers for storing data.
*   Use `const` by default, and switch to `let` only if the value needs to change later.
*   The most common data types are **String** (text), **Number**, and **Boolean** (`true`/`false`).
*   JavaScript is **dynamically typed**—it figures out the data type for you.
*   We use the `+` sign to concatenate strings and variables together.

---

### Next Time...

**Coming Up in Hour 3: Operators & Logic**

We've learned how to store data. Next, we'll learn how to **work with it**.

*   Performing math with **Arithmetic Operators** (`+`, `-`, `*`, `/`).
*   Comparing values with **Comparison Operators** (`>`, `<`, `===`).
*   Understanding **Type Coercion**.
*   Building our first **Node.js console application**: a simple calculator.
```
