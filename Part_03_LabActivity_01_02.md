### **Lab Session 1: JavaScript Foundations - Scripts, Variables & Data**

**Objective:** By the end of this lab, you will have hands-on experience with:
*   Creating and running JavaScript code in both a browser and a Node.js environment.
*   Declaring variables using `let` and `const`.
*   Working with `String`, `Number`, and `Boolean` data types.
*   Using `console.log()` to debug and check your work.
*   Using `document.write()` to dynamically create a formatted HTML page.

**Setup:**
1.  Create a new folder on your computer named `js_lab_1`.
2.  Open this entire folder in Visual Studio Code. All the files you create for this lab will be saved inside this folder.

---

### **Part 1: Environment and Output Practice (30-45 minutes)**

This part reinforces the concepts from Hour 1.

#### **Activity 1: My First Browser Script**

1.  Inside your `js_lab_1` folder, create a new file named `introduction.html`.
2.  Write the basic HTML structure.
3.  Inside the `<body>`, add an `<h1>` that says "About Me".
4.  Below the `<h1>`, add a `<script>` tag.
5.  Inside the script, do the following:
    *   Use `document.write()` to add a `<p>` tag that contains your name.
    *   Use `document.write()` again to add another `<p>` tag with your city and country.
    *   Use `console.log()` to write a "secret" message that will only appear in the browser's developer console. For example: `console.log('Page loaded successfully!');`.
6.  Save the file and open `introduction.html` in your browser.
7.  Verify that your name and city appear on the page.
8.  Open the developer console (F12 or Right-click -> Inspect -> Console) to see your secret message.

#### **Activity 2: My First Node.js Script**

1.  Back in VS Code, create a new file named `server_message.js`.
2.  In this file, you will only write JavaScript (no HTML).
3.  Do the following:
    *   Use `console.log()` to print the message: "Loading application..."
    *   Use `console.log()` to print your favorite quote.
    *   Use `console.log()` to print the message: "Application finished."
4.  Save the file.
5.  Open the VS Code terminal (`Ctrl + `` ` or `View -> Terminal`).
6.  Run your script using the command: `node server_message.js`
7.  You should see your three messages printed in order in the terminal.

---

### **Part 2: Variables and Dynamic Content (45-60 minutes)**

This part reinforces the concepts from Hour 2 and combines them with Part 1.

#### **Activity 3: The "Product Details" Page**

This is the main activity. You will create a dynamic product page using variables.

1.  Create a new file named `product.html`.
2.  Add the basic HTML structure and a `<title>` of "Product Details".
3.  Inside the `<body>`, add a `<script>` tag.
4.  **Inside the script, declare the following variables:**
    *   A `const` named `productName` and assign it a string value like `'Eco-Friendly Water Bottle'`.
    *   A `const` named `category` and assign it a string value like `'Drinkware'`.
    *   A `let` named `price` and assign it a number value like `15.99`.
    *   A `const` named `currency` and assign it a string value like `'USD'`.
    *   A `let` named `isAvailable` and assign it a boolean value: `true`.

5.  **Use `document.write()` to display the product information.** Combine HTML tags, text, and your variables to create a structured page. The output on the webpage should look something like this (your values may differ):

    # Eco-Friendly Water Bottle
    ## Drinkware
    **Price:** 15.99 USD
    **Available:** true

    *   **Hint:** You will need to use string concatenation (`+`) to join your text with your variables. For example: `document.write('<h2>' + category + '</h2>');`

6.  **Log variable types to the console.** After all your `document.write()` lines, use `console.log()` and the `typeof` operator to print the data type of each variable you created. The console output should look like this:

    ```
    Type of productName is: string
    Type of price is: number
    Type of isAvailable is: boolean
    ```

7.  Save and open `product.html` in your browser to see your work!

---

### **Part 3: Challenges (For Early Finishers)**

#### **Challenge 1: Add a Sale Price**
*   In `product.html`, declare a new `const` variable called `salePercentage` and give it a numeric value (e.g., `0.20` for 20% off).
*   Calculate the sale price: `let salePrice = price - (price * salePercentage);`
*   Add a new line to your page using `document.write()` that says "Sale Price: [your calculated price] USD".

#### **Challenge 2: Use Template Literals**
*   Refactor one of your `document.write()` lines from Activity 3 to use template literals (backticks `` ` ``) instead of the `+` sign.
*   Example: `document.write(`<p><strong>Available:</strong> ${isAvailable}</p>`);`

---

### **Quiz: Check Your Understanding (15-20 minutes)**

This quiz tests your conceptual knowledge from the first two hours.

#### **Section A: Multiple Choice Questions**

1.  **Which keyword should you use by default to declare a variable in modern JavaScript?**
    a) `var`
    b) `let`
    c) `const`
    d) `variable`

2.  **What will `typeof 42` return?**
    a) `"number"`
    b) `"integer"`
    c) `"string"`
    d) `Number`

3.  **Which command do you use in the terminal to run a JavaScript file named `app.js` with Node.js?**
    a) `run app.js`
    b) `javascript app.js`
    c) `node app.js`
    d) `execute app.js`

4.  **A variable that can only be `true` or `false` is called a:**
    a) String
    b) Number
    c) Condition
    d) Boolean

5.  **Which of these will cause an error?**
    a) `let score = 10; score = 20;`
    b) `const name = 'Tim';`
    c) `let message = "Hello";`
    d) `const year = 2023; year = 2024;`

---

#### **Section B: What's the Output?**

What will be printed to the console for each of these snippets?

**Snippet 1:**
```javascript
let city = 'Paris';
city = 'London';
console.log(city);
```
**Output:** ____________

**Snippet 2:**
```javascript
const quantity = 5;
const item = 'Apples';
console.log('You bought ' + quantity + ' ' + item);
```
**Output:** ____________

**Snippet 3:**
```javascript
let user = null;
let score;
console.log(typeof user);   // Hint: This is a tricky one!
console.log(typeof score);
```
**Output 1:** ____________
**Output 2:** ____________

---

#### **Section C: Find the Bug**

Find and correct the single error in each code snippet.

**Bug 1:**
```javascript
// The goal is to declare a user's name
let user name = 'Jessica';
```
**Correction:** ______________________________

**Bug 2:**
```javascript
// The goal is to print a message
const message = 'Hello World;
console.log(message);
```
**Correction:** ______________________________

---
### **Answer Key (For the Instructor)**

*   **Quiz A:** 1-c, 2-a, 3-c, 4-d, 5-d
*   **Quiz B:**
    *   Snippet 1: `London`
    *   Snippet 2: `You bought 5 Apples`
    *   Snippet 3: `object` (this is a known quirk of JS), `undefined`
*   **Quiz C:**
    *   Bug 1: Variable names cannot have spaces. Correction: `let userName = 'Jessica';`
    *   Bug 2: The string is missing a closing quote. Correction: `const message = 'Hello World';`
