# Hour 7: Arrays & Array Methods

**Managing Collections of Data**

---

### Recap & Agenda

**Where We've Been:**
*   Variables hold single pieces of data.
*   Operators and `if/else` let us manipulate and check data.
*   Loops repeat actions.
*   Functions group actions into reusable blocks.

**Today's Agenda:**
1.  The Problem: Too Many Variables.
2.  What is an Array?
3.  Zero-Based Indexing (How computers count).
4.  Basic Array Methods: `push`, `pop`, `shift`, `unshift`.
5.  The Swiss Army Knife: `splice`.
6.  Looping over Arrays (`for` loop vs. `forEach`).
7.  Modern Array Magic: `map` and `filter`.
8.  **Activity:** Build a Node.js Shopping List manager.

---

### The Problem: Too Many Variables

Imagine you are building a website for a school and need to store the names of 5 students. 

With what we know so far, we'd have to do this:

```javascript
let student1 = "Alice";
let student2 = "Bob";
let student3 = "Charlie";
let student4 = "Diana";
let student5 = "Ethan";
```

What if there are 1,000 students? This approach is impossible to manage, impossible to loop through, and violates the DRY principle.

---

### The Solution: Arrays

An **Array** is a special type of variable that can hold **more than one value at a time**. 

Think of a standard variable as a small box that holds a single item. 
Think of an Array as a **filing cabinet with multiple numbered drawers**.

We group related items together into a single list.

---

### Creating an Array

To create an array, we use **square brackets `[]`**. 
Inside, we separate our individual items (called "elements") with commas.

```javascript
// An array of Strings
let students = ["Alice", "Bob", "Charlie", "Diana", "Ethan"];

// An array of Numbers
let testScores = [85, 92, 78, 100, 88];

// An empty array (ready to be filled later!)
let shoppingList = [];
```

---

### A Crucial Concept: Zero-Based Indexing

How do we access a specific item inside that list? We use its position number, called an **Index**.

But there is a catch: **Computers start counting at ZERO.**

| Index | 0 | 1 | 2 | 3 | 4 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Value** | "Alice" | "Bob" | "Charlie" | "Diana" | "Ethan" |

*   "Alice" is the **1st** item, but she is at **Index 0**.
*   "Ethan" is the **5th** item, but he is at **Index 4**.

---

### Accessing Data in an Array

To look inside a specific "drawer" of our array, we write the variable name followed by square brackets and the index number.

```javascript
let students = ["Alice", "Bob", "Charlie", "Diana", "Ethan"];

console.log( students[0] ); // Output: Alice
console.log( students[2] ); // Output: Charlie

// What if we ask for an index that doesn't exist?
console.log( students[10] ); // Output: undefined
```

---

### Modifying Data in an Array

We can use the exact same bracket syntax to change an existing value.

```javascript
let colors = ["Red", "Green", "Blue"];

// Let's change "Green" to "Yellow"
colors[1] = "Yellow";

console.log(colors); // Output: ["Red", "Yellow", "Blue"]
```

---

### The `.length` Property

How do we know how many items are in our array? JavaScript tracks this automatically using the `.length` property.

```javascript
let movies = ["Matrix", "Inception", "Interstellar"];

console.log(movies.length); // Output: 3
```

> **Pro-Tip:** The length is always **one number higher** than the last index! (Because the index starts at 0, but counting length starts at 1).

---

### Introduction to Array Methods

Arrays are incredibly powerful because JavaScript provides built-in tools called **Methods** to manipulate them. 

Think of methods as built-in functions that belong specifically to arrays. You access them using a "dot" `.` after the array's name.

Let's look at how to add and remove elements.

---

### Adding/Removing from the END

The most common way to add or remove data is at the very end of the list.

*   **`.push(item)`**: Adds one or more items to the **end** of the array.
*   **`.pop()`**: Removes the **last** item from the array (and hands it back to you).

```javascript
let fruits = ["Apple", "Banana"];

fruits.push("Orange"); 
console.log(fruits); // Output: ["Apple", "Banana", "Orange"]

let removedFruit = fruits.pop();
console.log(fruits);       // Output: ["Apple", "Banana"]
console.log(removedFruit); // Output: "Orange"
```

---

### Adding/Removing from the BEGINNING

Sometimes you need to modify the front of the list.

*   **`.unshift(item)`**: Adds items to the **beginning** of the array.
*   **`.shift()`**: Removes the **first** item from the array.

```javascript
let line = ["Bob", "Charlie"];

line.unshift("Alice"); // Alice cuts to the front!
console.log(line); // Output: ["Alice", "Bob", "Charlie"]

line.shift(); // The person at the front is served and leaves
console.log(line); // Output: ["Bob", "Charlie"]
```

---

### The Swiss Army Knife: `.splice()`

What if you want to add or remove items from the *middle* of an array? We use `.splice()`.

**Syntax:** `array.splice(startIndex, deleteCount, itemsToAdd...)`

```javascript
let months = ["Jan", "March", "April", "June"];

// 1. Insert "Feb" at index 1, delete 0 items
months.splice(1, 0, "Feb");
console.log(months); // ["Jan", "Feb", "March", "April", "June"]

// 2. Replace "June" (at index 4) with "May"
months.splice(4, 1, "May");
console.log(months); // ["Jan", "Feb", "March", "April", "May"]
```

---

### Iterating: Arrays + Loops = Magic

The true power of arrays is unlocked when we combine them with loops to process large amounts of data automatically.

**The "Old" Way (Classic `for` loop):**

```javascript
let scores = [10, 20, 30];

// We use i as our index! It goes from 0, to 1, to 2.
for (let i = 0; i < scores.length; i++) {
    console.log("Score " + (i + 1) + ": " + scores[i]);
}
```

---

### Modern Iteration: `.forEach()`

Modern JavaScript gives us specialized array methods that do the looping for us. They are cleaner and easier to read.

`.forEach()` takes a **function** as an argument and runs that function *for every single item* in the array.

```javascript
let scores = [10, 20, 30];

// Using an Arrow Function inside forEach
scores.forEach( (score) => {
    console.log("The score is: " + score);
});
```
*Notice we don't have to worry about `[i]` or `.length` anymore!*

---

### Data Transformation: `.map()`

What if you want to change every item in a list and create a brand **new array**? You use `.map()`.

`.map()` creates a new array populated with the results of calling a provided function on every element.

```javascript
let prices = [10, 20, 30];

// Let's double all the prices
let doubledPrices = prices.map( (price) => {
    return price * 2;
});

console.log(prices);        // [10, 20, 30] (Original is safe!)
console.log(doubledPrices); // [20, 40, 60] (New array!)
```

---

### Filtering Data: `.filter()`

What if you have a list of 1,000 users and only want the ones over 18? You use `.filter()`.

`.filter()` creates a **new array** with all elements that pass the test implemented by the provided function.

```javascript
let ages = [15, 22, 16, 40, 12, 35];

let adultsOnly = ages.filter( (age) => {
    return age >= 18; // Must return a boolean!
});

console.log(adultsOnly); // Output: [22, 40, 35]
```

---

### Arrays Can Hold Anything

Arrays are not restricted to just numbers or just strings. They can hold mixed data types, including variables and even other arrays!

```javascript
let active = true;
let score = 99;

let mixedBag = [
    "Hello", 
    42, 
    active, 
    score, 
    ["Another", "Array"] // Yes, an array inside an array!
];

console.log(mixedBag[4][0]); // Output: "Another"
```

---

### Activity Prep: Node.js Shopping List

We are going to build a console application that manages a shopping list.

**The Goal:**
1. Create an array of groceries.
2. Use `.push()` to add items.
3. Use `.pop()` or `.splice()` to remove items.
4. Use `.forEach()` to neatly print the final list to the console.

---

### Activity: Code Along

1. Create a file named `shopping.js`.
2. Write the following logic:

```javascript
console.log("--- Shopping List Manager ---");

// 1. Create the array
let cart = ["Milk", "Bread", "Eggs"];
console.log("Initial Cart:", cart);

// 2. User forgot apples! Let's add them to the end.
cart.push("Apples");

// 3. User realizes they are lactose intolerant. Remove "Milk" (Index 0).
// Let's use shift() since it's at the beginning!
let removedItem = cart.shift(); 
console.log("Removed:", removedItem);

// 4. Print the final receipt
console.log("\n--- Final Receipt ---");
cart.forEach( (item, index) => {
    // We can add a second parameter to get the current index!
    console.log(`${index + 1}. ${item}`);
});
```

---

### Key Takeaways for Hour 7

*   **Arrays `[]`** store multiple values in a single, ordered list.
*   **Zero-Based Indexing:** The first item is at index `0`.
*   `.push()` and `.pop()` modify the **end** of the array.
*   `.unshift()` and `.shift()` modify the **beginning**.
*   `.splice()` modifies the **middle**.
*   **`.forEach()`** runs a function for every item.
*   **`.map()`** and **`.filter()`** return brand **new** arrays based on your rules, without altering the original array.

---

### Next Time...

**Coming Up in Hour 8: Objects & Advanced Logic**

Arrays are great for simple lists, but what if an item needs multiple properties? 
(e.g., A user doesn't just have a name; they have an email, age, and password).

We will learn about:
*   Objects `{}` and Key-Value pairs.
*   Properties and Methods inside Objects.
*   Combining Arrays and Objects (The standard format for data on the web!).
