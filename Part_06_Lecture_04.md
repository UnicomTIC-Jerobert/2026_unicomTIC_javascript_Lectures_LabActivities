# Hour 4: Control Flow & Decision Making

**Making Your Code Smart**

---

### Recap & Agenda

**Where We've Been:**
*   We learned how to **store data** (`let`, `const`).
*   We learned how to **perform calculations and comparisons** with operators (`+`, `-`, `===`, `>`). Our code runs top-to-bottom, one line after another.

**Today's Agenda:**
1.  **What is Control Flow?** - The "fork in the road" for your code.
2.  The fundamental `if` / `else if` / `else` statements.
3.  A critical concept: **Truthy and Falsy** values.
4.  Using **Logical Operators** (`&&`, `||`) to create complex conditions.
5.  An alternative: The `switch` statement.
6.  A shortcut: The **Ternary Operator**.
7.  **Activity:** Build a "Traffic Signal" script in the browser.

---

### What is Control Flow?

So far, our code is like a straight road. It starts at the top and executes every single line until it reaches the end.

But what if we want our program to **make decisions**?

> Control Flow allows us to choose which lines of code get executed based on certain conditions. It gives our program a "brain."



---

### The `if` Statement

The `if` statement is the most basic decision-making tool. It runs a block of code **only if** a condition is `true`.

**Syntax:**
```javascript
if (condition) {
  // This code runs ONLY if the condition is true
}
```

**Example:**
```javascript
const userAge = 20;

if (userAge >= 18) {
  console.log("You are eligible to vote.");
}
```
*Because `20 >= 18` is `true`, the message is printed.*

---

### The `else` Statement

What happens if the `if` condition is `false`? The `else` statement provides an alternative block of code to run.

**Syntax:**
```javascript
if (condition) {
  // Runs if condition is true
} else {
  // Runs if condition is false
}
```
**Example:**
```javascript
const score = 70;

if (score >= 50) {
  console.log("Congratulations, you passed!");
} else {
  console.log("Sorry, you need to retake the test.");
}
```

---

### The `else if` Statement

What if you have more than two possibilities? You can chain multiple conditions together with `else if`.

**Syntax:**
```javascript
if (condition1) {
  // Runs if condition1 is true
} else if (condition2) {
  // Runs if condition1 is false AND condition2 is true
} else {
  // Runs if all previous conditions are false
}
```

---

### `else if` Example: Grading System

```javascript
const grade = 85;

if (grade >= 90) {
  console.log("You got an A!");
} else if (grade >= 80) {
  console.log("You got a B!");
} else if (grade >= 70) {
  console.log("You got a C!");
} else {
  console.log("You need to improve.");
}

// Output: You got a B!
```
*JavaScript checks the conditions from top to bottom and stops at the first one that is `true`.*

---

### A Critical Concept: Truthy & Falsy

In JavaScript, a condition doesn't have to be strictly `true` or `false`. Every value has an inherent "truthiness".

**The 6 Falsy Values:**
Anything not on this list is **Truthy**.
1.  `false`
2.  `0`
3.  `""` (an empty string)
4.  `null`
5.  `undefined`
6.  `NaN` (Not a Number)

---

### Truthy & Falsy in Action

This is extremely powerful for checking if a variable has a "real" value.

**The Long Way:**
```javascript
let userName = ""; // User hasn't entered their name

if (userName !== "") {
  console.log("Welcome, " + userName);
} else {
  console.log("Please enter your name.");
}
```
**The "Truthy" Way (Better!):**
```javascript
let userName = ""; // This is a falsy value

if (userName) { // This condition becomes false
  console.log("Welcome, " + userName);
} else {
  console.log("Please enter your name.");
}
```
*This is cleaner and more common in professional JavaScript code.*

---

### Combining Conditions: Logical Operators

We can check multiple conditions in a single `if` statement using logical operators.

*   `&&` (**AND**): Both conditions must be `true`.
*   `||` (**OR**): At least one condition must be `true`.
*   `!` (**NOT**): Inverts a boolean (`true` becomes `false`, `false` becomes `true`).

---

### Logical Operators Example: Login System

```javascript
const user = 'admin';
const password = 'password123';
const isLoggedIn = false;

// Using AND (&&)
if (user === 'admin' && password === 'password123') {
  console.log('Admin access granted.');
}

// Using OR (||)
if (user === 'admin' || user === 'manager') {
  console.log('You have staff privileges.');
}

// Using NOT (!)
if (!isLoggedIn) {
  console.log('Access denied. Please log in.');
}
```

---

### The `switch` Statement

A `switch` statement is a good alternative to a long `if / else if / else` chain when you are checking the **same variable** against a list of **specific values**.

**Syntax:**
```javascript
switch (expression) {
  case value1:
    // Code to run if expression === value1
    break; // IMPORTANT: break stops the execution
  case value2:
    // Code to run if expression === value2
    break;
  default:
    // Code to run if no other case matches
}
```

---

### `switch` Example: Days of the Week

```javascript
const day = 'Wednesday';

switch (day) {
  case 'Monday':
    console.log('Time to start the week!');
    break;
  case 'Friday':
    console.log('Weekend is almost here!');
    break;
  default:
    console.log('Just another day.');
}
```
*This is often cleaner and easier to read than multiple `else if` statements for the same variable.*

---

### Shorthand: The Ternary Operator

The Ternary Operator is a compact, one-line shortcut for a simple `if / else` statement.

**Syntax:**
```javascript
condition ? expressionIfTrue : expressionIfFalse;
```

**Regular `if/else`:**
```javascript
let message;
const age = 20;

if (age >= 18) {
  message = "You can vote.";
} else {
  message = "You cannot vote yet.";
}
```

**Ternary Equivalent:**
```javascript
const age = 20;
const message = age >= 18 ? "You can vote." : "You cannot vote yet.";
```

---

### Activity Prep: Traffic Signal Logic

Let's use our new decision-making skills to build a simple "Traffic Signal" program.

**Our Goal:**
1.  Create a variable to store the current color of the traffic light.
2.  Use an `if / else if / else` statement to check the color.
3.  Based on the color, use `document.write()` to display a specific instruction on a webpage (e.g., "Go!", "Slow Down", "Stop!").

---

### Activity: Code Along

1.  Create a new file named `traffic.html`.
2.  Add the following code.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Traffic Signal Logic</title>
</head>
<body>
    <script>
        const signalColor = 'yellow'; // Try changing this to 'red' or 'green'

        document.write('<h1>Traffic Signal Instructions</h1>');

        if (signalColor === 'green') {
            document.write('<p style="color: green;">Action: Go!</p>');
        } else if (signalColor === 'yellow') {
            document.write('<p style="color: orange;">Action: Slow Down!</p>');
        } else if (signalColor === 'red') {
            document.write('<p style="color: red;">Action: Stop!</p>');
        } else {
            document.write('<p>Error: Invalid signal color.</p>');
        }

    </script>
</body>
</html>
```
3.  Save the file and open it in your browser. Change the `signalColor` variable and refresh the page to see the logic work!

---

### Challenge For You: ATM Withdrawal

Write a script that simulates a simple ATM withdrawal.

1.  Create a file named `atm.html`.
2.  Inside a `<script>` tag, create two variables:
    *   `let accountBalance = 500;`
    *   `let withdrawalAmount = 100;`
3.  **Write the logic:**
    *   Use an `if` statement to check if the `withdrawalAmount` is **greater than** the `accountBalance`. If it is, `document.write("Insufficient funds.")`.
    *   Use an `else if` statement to check if the `withdrawalAmount` is **less than or equal to 0**. If it is, `document.write("Invalid withdrawal amount.")`.
    *   Use an `else` block for a successful transaction. It should:
        1.  Subtract the withdrawal amount from the balance.
        2.  `document.write()` a success message, including the `new balance`.

---

### Key Takeaways for Hour 4

*   **Control Flow** lets our programs make decisions.
*   `if / else if / else` is the primary tool for executing code based on conditions.
*   Understanding **Truthy/Falsy** values makes your `if` statements cleaner and more powerful.
*   The `switch` statement is a good alternative for checking a single variable against multiple specific values.
*   The **Ternary Operator** is a concise shortcut for simple `if/else` logic.

---

### Next Time...

**Coming Up in Hour 5: Loops & Repetition**

We've learned how to make our code make decisions. Next, we'll learn how to make it perform tasks over and over again without re-writing the same code.

*   `for` loops
*   `while` loops
*   Automating repetitive tasks.
