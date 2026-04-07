### **Lab Session 5: The Function Forge**

**Total Estimated Time:** 4 - 5 hours
**Objective:** Master the creation of reusable logic blocks (functions), pass data in (arguments), extract data out (`return`), and grasp the critical concept of variable scope.

---

### **Part 1: The `return` Keyword & Pure Functions (Estimated Time: 1.5 hours)**

In this section, we focus strictly on Node.js to understand data flow without UI distractions.

#### **Activity 1: The Basic Math Library**
1. Create `math_lib.js`.
2. Write four separate **Arrow Functions**: `add`, `subtract`, `multiply`, and `divide`.
3. Each function should take two parameters (`a`, `b`) and `return` the mathematical result.
4. Call each function, store the result in a variable, and `console.log` the variable.
   *Example:*
   ```javascript
   const add = (a, b) => { return a + b; };
   let sumResult = add(10, 5);
   console.log("Sum:", sumResult);
   ```

#### **Activity 2: The Text Formatter**
Let's work with strings.
1. Create `formatter.js`.
2. Write a function declaration (the `function` keyword) called `createGreeting`.
3. It takes two parameters: `firstName` and `lastName`.
4. It must `return` a string in this format: `"Hello, [firstName] [lastName]! Welcome back."`
5. Write a second function called `shout`. It takes one parameter: `message`.
6. It must `return` the message in all capital letters. *(Hint: use the built-in string method `message.toUpperCase()`)*.
7. **The Combo Challenge:** Call `createGreeting`, pass the result *into* `shout`, and print the final loud greeting.
   *Example structure:* `let loudGreeting = shout( createGreeting("John", "Doe") );`

#### **Activity 3: The Temperature Converter (Refactored)**
Remember the temperature converter from Lab 2? Let's make it reusable.
1. Create `converter.js`.
2. Write a function `celsiusToFahrenheit(celsius)`. It `return`s the Fahrenheit value.
3. Write a function `fahrenheitToCelsius(fahrenheit)`. It `return`s the Celsius value. *(Formula: C = (F - 32) * 5/9)*
4. Call both functions with different values and print the results clearly.

---

### **Part 2: Default Parameters and Scope (Estimated Time: 1.5 hours)**

#### **Activity 4: The Order Generator (Default Parameters)**
1. Create `orders.js`.
2. Write an arrow function `createOrder(item, quantity = 1, status = "Pending")`.
3. The function should return a string like: `"Order: 2x Laptop - Status: Pending"`.
4. Test it by calling it three ways:
   * `console.log(createOrder("Book", 3, "Shipped"));` (Provides all 3 arguments)
   * `console.log(createOrder("Mouse", 5));` (Relies on default status)
   * `console.log(createOrder("Monitor"));` (Relies on default quantity and status)

#### **Activity 5: The Scope Investigation**
This is a debugging exercise. Read the code, predict what will happen, run it, and then fix the errors.
1. Create `scope_test.js`.
2. Paste this code:
```javascript
let globalScore = 100;

function playGame() {
    let level = 1;
    let globalScore = 50; // Shadowing the global variable
    console.log("Inside Game - Level:", level);
    console.log("Inside Game - Score:", globalScore);
}

playGame();

console.log("Outside Game - Score:", globalScore);
// console.log("Outside Game - Level:", level); // UNCOMMENT THIS LINE TO SEE THE ERROR
```
3. **Your Task:**
   * Run the code. Notice that `globalScore` inside the function didn't change the `globalScore` outside.
   * Uncomment the last line. You will get a `ReferenceError: level is not defined`.
   * **Fix it:** Write a comment explaining *why* that error happened (Vegas rule!). Then, fix the code so the `playGame` function *actually updates* the `globalScore` defined at the very top, instead of creating a new local one.

---

### **Part 3: Interactive Web Functions (Estimated Time: 1 hour)**

Let's connect our functions to HTML buttons.

#### **Activity 6: The Interactive Calculator**
1. Create `web_calc.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>Simple Calculator</h2>
    <input type="number" id="num1" placeholder="First number">
    <input type="number" id="num2" placeholder="Second number">
    <br><br>
    <!-- Notice we are calling different functions on click! -->
    <button onclick="handleAddition()">Add (+)</button>
    <button onclick="handleSubtraction()">Subtract (-)</button>
    <h3 id="resultDisplay">Result: --</h3>

    <script>
        // --- 1. YOUR PURE FUNCTIONS ---
        // Write two arrow functions here: 'add(a, b)' and 'subtract(a, b)'
        // They should ONLY do the math and return the result. No DOM stuff here.
        

        // --- 2. THE DOM HANDLER FUNCTIONS ---
        // These are provided. They get data from the screen, call YOUR pure functions, and update the screen.
        function handleAddition() {
            let n1 = Number(document.getElementById('num1').value);
            let n2 = Number(document.getElementById('num2').value);
            let total = add(n1, n2); // Calls your pure function!
            document.getElementById('resultDisplay').textContent = "Result: " + total;
        }

        function handleSubtraction() {
            let n1 = Number(document.getElementById('num1').value);
            let n2 = Number(document.getElementById('num2').value);
            let total = subtract(n1, n2); // Calls your pure function!
            document.getElementById('resultDisplay').textContent = "Result: " + total;
        }
    </script>
</body>
</html>
```
3. **Your Task:** Fill in the pure functions (`add` and `subtract`) at the top of the `<script>`. Test it in the browser! Note how we separate pure logic from DOM manipulation.

---

### **Part 4: The 20-Question Function Master Quiz (Estimated Time: 1 hour)**

**Section A: Terminology**
1. What is the keyword used to create a traditional function?
2. The variables listed in the function definition (the "input slots") are called _________.
3. The actual data passed into a function when it is called are called _________.
4. What keyword is required to get a usable value out of a function?
5. What happens to any code written *after* the `return` statement inside a function?

**Section B: Syntax and Arrow Functions**
6. Convert this to an arrow function: 
   `function sayHi() { return "Hi"; }`
7. Convert this to a one-line arrow function (implicit return):
   `const double = function(x) { return x * 2; }`
8. In a function defined as `function greet(name = "User")`, what is "User" called?

**Section C: What's the Output?**

9.
```javascript
function add(a, b) {
    console.log(a + b);
}
let result = add(3, 4);
console.log(result);
```
Output 1 (from inside function): \_\_\_\_\_\_\_\_
Output 2 (value of result): \_\_\_\_\_\_\_\_

10.
```javascript
function checkAge(age) {
    if (age >= 18) {
        return "Adult";
    }
    return "Minor";
}
console.log(checkAge(20));
```
Output: \_\_\_\_\_\_\_\_

11.
```javascript
function doMath(x) {
    return x + 5;
    return x * 10;
}
console.log(doMath(5));
```
Output: \_\_\_\_\_\_\_\_

12.
```javascript
let animal = "Cat"; // Global
function changeAnimal() {
    let animal = "Dog"; // Local
    return animal;
}
changeAnimal();
console.log(animal);
```
Output: \_\_\_\_\_\_\_\_ *(Careful! Think about scope).*

13.
```javascript
let score = 10;
function increaseScore() {
    score = score + 5; 
}
increaseScore();
increaseScore();
console.log(score);
```
Output: \_\_\_\_\_\_\_\_

**Section D: Find the Bug**

14. 
```javascript
function multiply(x, y) {
    let answer = x * y;
}
let total = multiply(5, 5);
console.log("Total is: " + total); // Prints: Total is undefined
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

15. 
```javascript
// Trying to call the function
calcArea[10, 5];

function calcArea(w, h) {
    return w * h;
}
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

16. 
```javascript
const greet = (name) => {
    "Hello " + name;
}
console.log(greet("Sam")); // Prints undefined
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ *(Hint: Curly braces require something specific).*

17. 
```javascript
function getSecret() {
    let pinCode = 9999;
}
console.log(pinCode);
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

18. 
```javascript
function makeMessage(msg = "Welcome") {
    return msg;
}
console.log(makeMessage("Hello"));
```
Question: Does this print "Welcome" or "Hello"?

19. True or False: An arrow function is just a different syntax for writing a function expression.
20. True or False: Variables declared with `let` outside of any block or function are globally scoped.

---

### **Instructor Answer Key for Quiz**
1. `function`
2. Parameters
3. Arguments
4. `return`
5. It is completely ignored (never executed).
6. `const sayHi = () => { return "Hi"; }` (or `() => "Hi"`)
7. `const double = (x) => x * 2;`
8. A default parameter.
9. Output 1: `7`, Output 2: `undefined` (because there is no `return` statement).
10. `"Adult"`
11. `10` (The function stops at the first return).
12. `"Cat"` (The local variable "Dog" was returned but not saved anywhere, and `console.log` is asking for the global variable).
13. `20`
14. Missing the `return answer;` statement.
15. Function calls require parentheses `()`, not square brackets `[]`. Should be `calcArea(10, 5)`.
16. If you use curly braces `{}` in an arrow function, you *must* use the `return` keyword. Either `return "Hello " + name;` or remove the braces entirely for an implicit return.
17. Scope Error. Trying to log a local variable (`pinCode`) from the global scope.
18. "Hello" (Arguments override default parameters).
19. True.
20. True.
