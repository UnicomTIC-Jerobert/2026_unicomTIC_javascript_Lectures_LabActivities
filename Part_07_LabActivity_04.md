### **Lab Session 3: The Logic Maze (Control Flow)**

**Total Estimated Time:** 4 - 5 hours
**Objective:** Master decision-making in JavaScript by building interactive programs that respond differently based on user input and conditions.

---

### **Part 1: Node.js Interactive Console Apps (Estimated Time: 1.5 - 2 hours)**

**The Node.js Input Boilerplate:**
For the following activities, copy and paste this starting code. You will write your `if/else` logic exactly where it says `// --- YOUR LOGIC HERE ---`.

#### **Activity 1: The Club Bouncer (if / else)**
1. Create a file named `bouncer.js`.
2. Paste the following code:
```javascript
const readline = require('readline').createInterface({
  input: process.stdin,
  output: process.stdout
});

readline.question('How old are you? ', (ageInput) => {
  const age = Number(ageInput); // Convert the text input to a Number

  // --- YOUR LOGIC HERE ---
  // 1. If age is 18 or older, console.log "Welcome to the club!"
  // 2. Else, console.log "Sorry, you are too young to enter."
  

  // -----------------------
  readline.close();
});
```
3. Run `node bouncer.js` in your terminal. Type an age and press Enter to test it.

#### **Activity 2: The Grading Machine (else if)**
1. Create `grader.js` and use the same boilerplate, but change the question to `'What is your test score (0-100)? '`.
2. **Your Logic:**
   * If the score is 90 or above, print "Grade: A"
   * If the score is 80 to 89, print "Grade: B"
   * If the score is 70 to 79, print "Grade: C"
   * If the score is below 70, print "Grade: F"
   * *Challenge:* Add a check at the very top. If the score is greater than 100 or less than 0, print "Invalid score entered!"

#### **Activity 3: Coffee Shop Menu (switch statement)**
1. Create `coffee_shop.js`. Change the question to `'What size coffee do you want? (Small, Medium, Large): '`.
2. **Your Logic:** Use a `switch` statement based on `sizeInput`.
   * Case 'Small': print "That will be $2.50"
   * Case 'Medium': print "That will be $3.50"
   * Case 'Large': print "That will be $4.50"
   * Default: print "Sorry, we don't have that size."

#### **Activity 4: Even or Odd (Ternary Operator)**
1. Create `even_odd.js`. Question: `'Enter a number: '`.
2. **Your Logic:**
   * Use the modulo operator (`%`) to determine if the number is even or odd.
   * Create a variable called `result`.
   * Use the **Ternary Operator** (`condition ? true : false`) to assign either "Even" or "Odd" to the `result` variable.
   * `console.log(result);`

---

### **Part 2: Browser/DOM Interactive Apps (Estimated Time: 1.5 - 2 hours)**

Now let's connect our logic to a user interface!

#### **Activity 5: Password Strength Checker**
1. Create `password.html` and paste the following:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>Password Strength Checker</h2>
    <input type="text" id="passInput" placeholder="Enter password">
    <button onclick="checkPassword()">Check</button>
    <h3 id="feedback"></h3>

    <script>
        function checkPassword() {
            // Get the text from the input box
            const password = document.getElementById('passInput').value;
            const feedbackElement = document.getElementById('feedback');

            // --- YOUR LOGIC HERE ---
            // Hint: Use password.length to get the number of characters
            // 1. If password length is less than 5, set feedbackElement.textContent to "Weak" and change its color to red.
            // 2. If password length is between 5 and 8, set it to "Medium" (orange).
            // 3. If password length is greater than 8, set it to "Strong" (green).
            
            // Example of changing color: feedbackElement.style.color = "red";

        }
    </script>
</body>
</html>
```
2. Open in browser. Type passwords of varying lengths and click "Check".

#### **Activity 6: The E-commerce Discount System**
1. Create `discount.html` and paste the following:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>Checkout</h2>
    <p>Enter your purchase amount: $<input type="number" id="amountInput"></p>
    <p>Are you a Premium Member? <input type="checkbox" id="premiumCheck"></p>
    <button onclick="calculateTotal()">Calculate Total</button>
    
    <h3 id="finalPrice"></h3>

    <script>
        function calculateTotal() {
            const amount = Number(document.getElementById('amountInput').value);
            const isPremium = document.getElementById('premiumCheck').checked; // Returns true or false
            const display = document.getElementById('finalPrice');
            
            let discount = 0;

            // --- YOUR LOGIC HERE ---
            // 1. If amount is greater than 100 AND they are a premium member, discount = 20
            // 2. Else if amount is greater than 100 OR they are a premium member, discount = 10
            // 3. Else, discount = 0
            
            // 4. Calculate final price (amount - discount)
            // 5. Update the 'display' textContent to show the final price.

        }
    </script>
</body>
</html>
```

---

### **Part 3: The 20-Question Logic Master Quiz (Estimated Time: 1 hour)**

*Write your answers down on a piece of paper. The instructor has the answer key!*

**Section A: Truthy or Falsy? (Will the `if` block run?)**
1. `if (0) { ... }` - Runs or Doesn't Run?
2. `if ("hello") { ... }` - Runs or Doesn't Run?
3. `if ("") { ... }` - Runs or Doesn't Run?
4. `if (null) { ... }` - Runs or Doesn't Run?
5. `if (100) { ... }` - Runs or Doesn't Run?

**Section B: Logical Operators (True or False?)**
6. `true && false` evaluates to: \_\_\_\_\_
7. `true || false` evaluates to: \_\_\_\_\_
8. `!true` evaluates to: \_\_\_\_\_
9. `(5 > 3) && (10 === 10)` evaluates to: \_\_\_\_\_
10. `(10 < 5) || (5 !== 6)` evaluates to: \_\_\_\_\_

**Section C: What's the Output?**

11. 
```javascript
let score = 50;
if (score > 40) {
  console.log("You passed!");
} else if (score > 20) {
  console.log("You almost passed.");
} else {
  console.log("You failed.");
}
```
Output: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

12. 
```javascript
let isRaining = true;
let hasUmbrella = false;

if (isRaining && hasUmbrella) {
  console.log("Go outside.");
} else {
  console.log("Stay inside.");
}
```
Output: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

13. 
```javascript
let role = 'guest';
switch (role) {
  case 'admin':
    console.log('Full Access');
    break;
  case 'guest':
    console.log('Limited Access');
    break;
  default:
    console.log('No Access');
}
```
Output: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

14. *(Tricky! Note the missing break)*
```javascript
let color = 'red';
switch (color) {
  case 'red':
    console.log('Stop');
  case 'green':
    console.log('Go');
}
```
Output: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

15.
```javascript
let age = 16;
let status = age >= 18 ? "Adult" : "Minor";
console.log(status);
```
Output: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Section D: Find the Bug (Identify the syntax or logic error)**

16. 
```javascript
let x = 10;
if x > 5 {
  console.log("Big");
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

17. 
```javascript
let name = "John";
if (name = "Jane") {
  console.log("Hello Jane!");
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

18. 
```javascript
let speed = 80;
if (speed > 50) {
  console.log("Too fast");
} else if (speed > 70) {
  console.log("Way too fast"); 
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ *(Hint: Think about the order of conditions)*

19. 
```javascript
let isLogedIn = true;
if (isLoggedIn === true) {
  console.log("Welcome");
} else {
  console.log("Please log in");
}
// Assume no spelling errors in variables, what is a SHORTER way to write the if condition?
```
Answer: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

20.
```javascript
let item = 'apple';
switch(item) {
  case 'apple'
    console.log("Fruit");
    break;
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

---
### **Instructor Answer Key for Quiz**
1. Doesn't Run (0 is falsy)
2. Runs ("hello" is truthy)
3. Doesn't Run (empty string is falsy)
4. Doesn't Run (null is falsy)
5. Runs (numbers other than 0 are truthy)
6. False
7. True
8. False
9. True
10. True
11. "You passed!" (It stops at the first true condition).
12. "Stay inside."
13. "Limited Access"
14. "Stop" AND "Go" (Because there is no `break` statement, it "falls through" to the next case).
15. "Minor"
16. Missing parentheses around the condition: `if (x > 5)`
17. Single `=` is assignment, not comparison. Should be `if (name === "Jane")`. As written, it will always evaluate to true and assign "Jane" to name.
18. Logic flaw. The `speed > 50` condition catches everything over 50. The `speed > 70` block will *never* run. They need to be swapped.
19. `if (isLoggedIn)`
20. Missing colon after the case. Should be `case 'apple':`
