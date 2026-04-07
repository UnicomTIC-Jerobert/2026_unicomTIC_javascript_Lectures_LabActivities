### **Lab Session 4: The Loop Factory**

**Total Estimated Time:** 4 - 5 hours
**Objective:** Master `for`, `while`, and nested loops to automate repetitive tasks, generate patterns, and dynamically build HTML structures.

---

### **Part 1: Basic Repetition in Node.js (Estimated Time: 1 hour)**

Let's warm up with pure logic in the terminal.

#### **Activity 1: The Rocket Countdown (`for` loop)**
1. Create a file named `countdown.js`.
2. Write a `for` loop that starts at 10 and counts down to 1. 
   *(Hint: Your increment will actually be a decrement: `i--`)*
3. Inside the loop, `console.log` the current number.
4. After the loop finishes (outside the loop), `console.log("Blastoff! 🚀")`.
5. Run it with `node countdown.js`.

#### **Activity 2: The Investment Simulator (`while` loop)**
A `while` loop is perfect when we don't know *how many* times to loop, but we know *when* we want to stop.
1. Create `investment.js`.
2. Create `let bankBalance = 1000;` and `let years = 0;`.
3. The interest rate is 5% (`0.05`) per year.
4. Write a `while` loop that continues running **as long as the `bankBalance` is less than 2000**.
5. Inside the loop:
   * Add 5% interest to the balance: `bankBalance = bankBalance + (bankBalance * 0.05);`
   * Add 1 to the `years` variable: `years++;`
6. Outside the loop, print: `console.log("It took " + years + " years to double the money.");`

#### **Activity 3: Skipping Evens (`continue`)**
1. Create `odds_only.js`.
2. Write a `for` loop that counts from 1 to 20.
3. Inside the loop, write an `if` statement to check if the number is even (`i % 2 === 0`).
4. If it is even, use the `continue` keyword to skip printing it.
5. If it is odd, `console.log(i)`.

---

### **Part 2: Visualizing Nested Loops (Estimated Time: 1.5 hours)**

Nested loops are best understood by drawing shapes in the terminal.

#### **Activity 4: The Number Grid**
1. Create `grid.js`.
2. We want to print a 3x3 grid of coordinates like this:
   `(1,1) (1,2) (1,3)`
   `(2,1) (2,2) (2,3)`
   `(3,1) (3,2) (3,3)`
3. **Your Task:**
   * Write an outer `for` loop (let `row = 1`; `row <= 3`).
   * Inside it, create a variable `let rowString = "";` (to hold the text for that row).
   * Inside the outer loop, write an inner `for` loop (let `col = 1`; `col <= 3`).
   * Inside the inner loop, add the coordinate to `rowString`: `rowString += "(" + row + "," + col + ") ";`
   * After the inner loop finishes, `console.log(rowString);`.

#### **Activity 5: ASCII Art Triangle (Challenge)**
1. Create `triangle.js`.
2. Your goal is to draw this exact shape in the console:
   ```
   *
   **
   ***
   ****
   *****
   ```
3. **Hint:** The outer loop runs 5 times (for 5 rows). The inner loop controls how many asterisks (`*`) to print on that specific row. The condition of the inner loop will depend on the current value of the outer loop's counter!

---

### **Part 3: Generating the DOM (Estimated Time: 1.5 hours)**

Now let's see why loops are the secret weapon of Web Developers!

#### **Activity 6: The Dynamic Year Dropdown**
Imagine writing `<option>` tags for every year from 1900 to 2024 by hand. No thanks! Let's loop it.
1. Create `registration.html` and paste this code:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>Sign Up</h2>
    <label>Select Birth Year:</label>
    <!-- We will use JS to fill this empty select tag! -->
    <select id="yearDropdown"></select>

    <script>
        const dropdown = document.getElementById('yearDropdown');
        
        // --- YOUR LOGIC HERE ---
        // 1. Write a for loop that starts at 2024 and goes down to 1900.
        // 2. Inside the loop, create a string of HTML for each option.
        //    Example: let newOption = "<option>" + i + "</option>";
        // 3. Add that string to the innerHTML of the dropdown.
        //    Hint: dropdown.innerHTML += newOption;
        
    </script>
</body>
</html>
```

#### **Activity 7: The FizzBuzz Visualizer (Combining Logic & Loops)**
This is a famous interview question, but we are bringing it to the browser.
1. Create `fizzbuzz.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<style>
    .fizz { color: blue; font-weight: bold; }
    .buzz { color: green; font-weight: bold; }
    .fizzbuzz { color: red; font-size: 20px; font-weight: bold; }
</style>
<body>
    <h2>The FizzBuzz List</h2>
    <ul id="numberList"></ul>

    <script>
        const list = document.getElementById('numberList');

        // --- YOUR LOGIC HERE ---
        // 1. Write a loop from 1 to 50.
        // 2. For each number, check:
        //    - If divisible by BOTH 3 and 5 (i % 3 === 0 && i % 5 === 0): 
        //         Add <li class="fizzbuzz">FizzBuzz!</li> to the list.
        //    - Else If divisible by 3: Add <li class="fizz">Fizz</li>
        //    - Else If divisible by 5: Add <li class="buzz">Buzz</li>
        //    - Else: Add <li> [the number] </li>
        // 3. Update list.innerHTML += ...

    </script>
</body>
</html>
```

---

### **Part 4: The 20-Question Loop Master Quiz (Estimated Time: 1 hour)**

**Section A: Core Concepts**
1. What does the acronym DRY stand for in programming?
2. Which loop is best when you know *exactly* how many iterations you need?
   a) `while`   b) `for`   c) `do-while`
3. Which loop is guaranteed to run its code block at least once, even if the condition is false?
   a) `while`   b) `for`   c) `do-while`
4. What happens if a loop's condition never becomes false?
5. What does `i++` mean?

**Section B: Loop Control Keywords**
6. Which keyword stops a loop entirely and breaks out of it?
7. Which keyword skips the rest of the current iteration and jumps to the next lap?
8. True or False: You can use `break` inside a `for` loop, but not inside a `while` loop.

**Section C: What's the Output? (Trace the code carefully!)**

9.
```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);
}
```
Output: \_\_\_\_\_\_\_\_

10.
```javascript
for (let i = 5; i > 2; i--) {
    console.log(i);
}
```
Output: \_\_\_\_\_\_\_\_

11.
```javascript
let count = 0;
while (count < 3) {
    count++;
    console.log(count);
}
```
Output: \_\_\_\_\_\_\_\_ *(Hint: Note where `count++` is placed!)*

12.
```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }
    console.log(i);
}
```
Output: \_\_\_\_\_\_\_\_

13.
```javascript
for (let i = 1; i <= 3; i++) {
    if (i === 2) {
        continue;
    }
    console.log(i);
}
```
Output: \_\_\_\_\_\_\_\_

**Section D: Nested Loops**

14. In a nested loop setup, if the outer loop runs 3 times, and the inner loop runs 4 times, how many times in total does the code *inside the inner loop* execute?
   a) 3 times   b) 4 times   c) 7 times   d) 12 times
15. True or False: The inner loop must finish all its laps before the outer loop can move to its next lap.

16. 
```javascript
for (let i = 1; i <= 2; i++) {
    for (let j = 1; j <= 2; j++) {
        console.log(i + "-" + j);
    }
}
```
Output: \_\_\_\_\_\_\_\_

**Section E: Find the Bug**

17. *(Infinite Loop Warning!)*
```javascript
let x = 1;
while (x < 10) {
    console.log(x);
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

18. 
```javascript
for (let i = 1, i <= 5, i++) {
    console.log(i);
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

19. 
```javascript
do {
    console.log("Hello");
} while (false)
```
Question: Does this cause an error, print nothing, or print "Hello" once?

20. 
```javascript
let sum = 0;
for (let i = 1; i <= 3; i++) {
    let sum = sum + i; 
}
console.log(sum);
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ *(Hint: Think about variable declaration and `let` inside the loop vs outside).*

---

### **Instructor Answer Key for Quiz**
1. Don't Repeat Yourself
2. b) `for`
3. c) `do-while`
4. It creates an Infinite Loop (crashes program/browser).
5. Increment `i` by 1 (same as `i = i + 1`).
6. `break`
7. `continue`
8. False (can be used in both).
9. 0, 1, 2
10. 5, 4, 3
11. 1, 2, 3 (Because `count` increments *before* the `console.log`).
12. 1, 2
13. 1, 3
14. d) 12 times (3 * 4)
15. True
16. 1-1, 1-2, 2-1, 2-2
17. Missing `x++` inside the loop. `x` will always be 1.
18. `for` loops require semicolons `;` between conditions, not commas `,`.
19. It prints "Hello" once.
20. Re-declaring `let sum` inside the loop creates a *new*, temporary variable that gets destroyed every lap. It doesn't update the `let sum = 0;` at the top. The fix: remove `let` from the inner calculation: `sum = sum + i;`. Output as written would just be `0`.
