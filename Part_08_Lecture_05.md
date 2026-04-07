# Hour 5: Loops & Repetition

**Doing Things Over and Over (Without Losing Your Mind)**

---

### Recap & Agenda

**Where We've Been:**
*   **Hour 2:** Storing data (Variables).
*   **Hour 3:** Calculating & comparing data (Operators).
*   **Hour 4:** Making decisions (Control Flow with `if/else`).

**Today's Agenda:**
1.  The DRY Principle & Why we need loops.
2.  The `for` loop (The workhorse).
3.  The `while` loop (The condition-checker).
4.  The `do-while` loop (The action-first loop).
5.  Infinite Loops (How to crash your browser!).
6.  Loop Control: `break` and `continue`.
7.  **Nested Loops** (Loops inside loops).
8.  **Activity:** Multiplication Table in Node.js and the Browser.

---

### The Problem: Repetitive Tasks

Imagine I ask you to print the numbers 1 to 5 to the console. 
You would probably write:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

That's easy enough. But what if I asked you to print the numbers 1 to **10,000**? 

---

### The DRY Principle

In programming, we have a golden rule: 

> **DRY: Don't Repeat Yourself.**

If you find yourself copying and pasting the exact same lines of code over and over, you are doing something wrong. 

Computers are incredibly fast at doing repetitive tasks. We just need to know how to give them the right instructions.

---

### The Solution: Loops

A **Loop** is a programming structure that repeats a block of code a specific number of times, or until a specific condition is met.

**Real-world analogies:**
*   A race track (Go around 10 times).
*   Eating a bowl of cereal (Keep taking bites *while* the bowl is not empty).
*   Searching a keychain (Check each key *until* you find the right one).

---

### Three Main Types of Loops in JS

JavaScript gives us a few different tools for looping. We will cover the big three:

1.  **`for` loop:** Best when you know *exactly how many times* you want to repeat.
2.  **`while` loop:** Best when you want to repeat *until a condition changes*.
3.  **`do-while` loop:** Best when you want to run the code *at least once*, and then check the condition.

---

### 1. The `for` Loop

The `for` loop is the most common loop in JavaScript. It packs everything needed to control the loop into one single line.

**Syntax:**
```javascript
for (initialization; condition; increment) {
  // Code to be repeated goes here
}
```

Let's break down those three strange words in the parentheses...

---

### `for` Loop Breakdown: Part 1

**1. Initialization: `let i = 0;`**
*   This is the starting line. 
*   We create a temporary variable (usually named `i` for "index" or "iteration") to act as our counter.
*   *This only happens ONCE, right at the beginning.*

---

### `for` Loop Breakdown: Part 2

**2. Condition: `i < 5;`**
*   This is the "keep going" rule. 
*   Before every single lap, the loop asks: "Is this condition still true?"
*   If `true`, run the code inside the loop. If `false`, stop the loop entirely.

---

### `for` Loop Breakdown: Part 3

**3. Increment: `i++` (or `i = i + 1`)**
*   This is the step taken at the *end* of every lap.
*   It updates our counter variable so we don't get stuck in the loop forever.

---

### The `for` Loop: In Action

Let's put it all together to count from 1 to 5.

```javascript
for (let i = 1; i <= 5; i++) {
  console.log("Count: " + i);
}
```

**What the computer does:**
*   Start: `i = 1`. Is `1 <= 5`? Yes. Print "Count: 1". Increase `i` to 2.
*   Lap 2: `i = 2`. Is `2 <= 5`? Yes. Print "Count: 2". Increase `i` to 3.
*   ...
*   Lap 5: `i = 5`. Is `5 <= 5`? Yes. Print "Count: 5". Increase `i` to 6.
*   Lap 6: `i = 6`. Is `6 <= 5`? **No. Stop the loop.**

---

### 2. The `while` Loop

The `while` loop separates the initialization, condition, and increment into different lines. It's much simpler to look at.

**Syntax:**
```javascript
let i = 1;         // Initialization (Outside the loop)

while (i <= 5) {   // Condition (The gatekeeper)
  console.log(i);  // The repeated code
  i++;             // Increment (Inside the loop)
}
```

---

### `for` vs. `while`: Which to choose?

They can often achieve the exact same result! But here is a general rule of thumb:

*   **Use `for`** when you are counting or doing math (e.g., "Run this exactly 10 times").
*   **Use `while`** when you don't know how many times it will run, but you are waiting for a state to change (e.g., "Keep asking the user for a password until they get it right").

---

### 3. The `do-while` Loop

This loop is the rebellious cousin of the `while` loop. 

A normal `while` loop checks the condition *before* letting you inside. 
A `do-while` loop runs the code first, and checks the condition *after*.

**Syntax:**
```javascript
let count = 10;

do {
  console.log("This will print at least once!");
  count++;
} while (count < 5); // Condition is checked at the end
```
*(Notice that 10 is NOT less than 5, but the code still ran once!)*

---

### Beware the Infinite Loop! ☠️

What happens if your condition *never* becomes false?

```javascript
let x = 1;

while (x < 10) {
  console.log("Hello!");
  // Oops, I forgot to write x++!
}
```
If you run this, your program will print "Hello!" millions of times a second until your Node.js terminal crashes or your web browser freezes. 

**Always double-check your increment!**

---

### Loop Control: `break`

Sometimes you want to pull the emergency brake and stop a loop early, even if the condition is still true. We use the `break` keyword.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    console.log("I found 5! Stopping the loop.");
    break; // Exits the loop completely
  }
  console.log(i);
}
// Output: 1, 2, 3, 4, I found 5! Stopping the loop.
```

---

### Loop Control: `continue`

Sometimes you want to skip the *current* lap and jump straight to the next one. We use the `continue` keyword.

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue; // Skip the rest of this lap and go to i=4
  }
  console.log(i);
}
// Output: 1, 2, 4, 5 (Notice 3 is missing!)
```

---

### Advanced Level: Nested Loops

What happens if you put a loop *inside* another loop? This is called a **Nested Loop**.

```javascript
for (let outer = 1; outer <= 3; outer++) {
    for (let inner = 1; inner <= 3; inner++) {
        // Code here
    }
}
```
This looks scary, but it follows a strict rule: **The inner loop must finish ALL its laps before the outer loop can take its next lap.**

---

### Nested Loops: The Clock Analogy

Think of a digital clock.

*   The **Minute** is the inner loop (0 to 59).
*   The **Hour** is the outer loop (1 to 12).

For every **1 hour** that passes (outer loop laps once), the **minutes** must go through all **60 laps** (inner loop completes entirely).

---

### Nested Loops: Code Example

Let's see the clock logic in code (simplified):

```javascript
for (let hour = 1; hour <= 3; hour++) {
    console.log("--- HOUR: " + hour + " ---");
    
    // For every hour, print 2 minutes
    for (let minute = 1; minute <= 2; minute++) {
        console.log("Minute: " + minute);
    }
}
```
**Output:**
--- HOUR: 1 ---
Minute: 1
Minute: 2
--- HOUR: 2 ---
Minute: 1
...

---

### Activity Prep: The Multiplication Table

We are going to generate a Multiplication Table (e.g., 5 x 1 = 5, 5 x 2 = 10, etc.).

We will do this twice to see the power of loops:
1.  In Node.js (Terminal Output).
2.  In the Browser (Dynamically creating HTML elements).

---

### Activity 1: Node.js Multiplier

1. Create a file named `multiplier.js`.
2. Pick a number you want to multiply (e.g., `let number = 7;`).
3. Write a `for` loop that runs from 1 to 10.
4. Inside the loop, calculate the result (`number * i`).
5. Print it beautifully using template literals!

```javascript
let num = 7;

for (let i = 1; i <= 10; i++) {
  let result = num * i;
  console.log(`${num} x ${i} = ${result}`);
}
```
Run it in your terminal: `node multiplier.js`

---

### Activity 2: Browser Multiplier (HTML Magic!)

Loops are how we generate lists and tables on websites!

1. Create `table.html`. Add standard HTML tags.
2. Inside a `<script>` tag, write this:

```html
<script>
    let baseNumber = 5;
    
    document.write('<h2>Multiplication Table for ' + baseNumber + '</h2>');
    document.write('<ul>'); // Start an HTML list

    for(let i = 1; i <= 10; i++) {
        let answer = baseNumber * i;
        // We are generating HTML <li> tags over and over!
        document.write('<li>' + baseNumber + ' x ' + i + ' = ' + answer + '</li>');
    }

    document.write('</ul>'); // End the HTML list
</script>
```

---

### What Did We Just Do in the Browser?

By using a loop and `document.write()`, we generated 10 lines of HTML code using only 4 lines of JavaScript.

Imagine if you were pulling 1,000 products from a database for an online store. You wouldn't write 1,000 HTML `<div>` tags. You would write **one** loop that runs 1,000 times!

---

### Key Takeaways for Hour 5

*   **Loops** prevent us from writing repetitive code (DRY Principle).
*   **`for` loops** are best for a known number of repetitions (initialization; condition; increment).
*   **`while` loops** are best when waiting for a condition to change.
*   **`break`** stops a loop completely; **`continue`** skips the current lap.
*   **Nested loops** place one loop inside another (outer loop waits for the inner loop to finish).

---

### Next Time...

**Coming Up in Hour 6: Functions & Scope**

We know how to repeat code sequentially with loops. Next, we will learn how to package code into reusable blocks that we can call upon *whenever and wherever* we want!

*   Declaring functions.
*   Passing data into functions (Arguments).
*   Getting data back (Return).
*   Global vs. Local Scope.

```
