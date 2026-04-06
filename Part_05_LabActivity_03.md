### **Lab Session 2: Working with Operators and Data**

**Objective:** By the end of this lab, you will be able to:
*   Confidently use arithmetic operators to perform calculations.
*   Understand and use assignment operators for concise code.
*   Apply manual type conversion (`Number()`) to handle string inputs.
*   Write scripts that solve simple, real-world mathematical problems.
*   See a preview of how JavaScript logic can interact with an HTML page.

**Setup:**
1.  Continue working in your `js_lab_1` folder from the previous lab.
2.  For each activity, create a new file as instructed.

---

### **Part 1: Node.js Logic Practice (Focus on pure JS)**

This part focuses on pure calculation and logic within the Node.js environment.

#### **Activity 1: Simple Age Calculator**

1.  Create a new file named `age_calculator.js`.
2.  Inside the file, create a `const` variable named `birthYear` and assign it your birth year.
3.  Create another `const` variable named `currentYear` and assign it the current year.
4.  Calculate the age by subtracting `birthYear` from `currentYear`. Store the result in a variable named `age`.
5.  Print a clear message to the console.
    *   **Example Output:** `If you were born in 1995, you are 28 years old.`

#### **Activity 2: Temperature Converter (Celsius to Fahrenheit)**

This activity introduces a slightly more complex formula.

1.  Create a new file named `temperature_converter.js`.
2.  Declare a `const` variable named `celsius` and give it a value (e.g., `25`).
3.  The formula to convert Celsius to Fahrenheit is: `F = (C * 9/5) + 32`.
4.  Use this formula to calculate the equivalent Fahrenheit temperature and store it in a variable named `fahrenheit`.
5.  Print a user-friendly message to the console.
    *   **Example Output:** `25°C is equal to 77°F.`

#### **Activity 3 (Challenge): Area of a Circle**

This activity uses a built-in JavaScript value.

1.  Create a new file named `circle_area.js`.
2.  Declare a `const` variable named `radius` and assign it a number (e.g., `10`).
3.  The formula for the area of a circle is `Area = π * r²`.
    *   In JavaScript, you can get the value of Pi with `Math.PI`.
    *   You can square the radius using the exponent operator `** 2` or by doing `radius * radius`.
4.  Calculate the area and store it in a variable.
5.  Print the result to the console.
    *   **Example Output:** `The area of a circle with a radius of 10 is 314.159...`

---

### **Part 2: Interactive Browser Applications (A Glimpse into the DOM)**

**Instructor Note:** Explain to the students: *"For these next activities, we are providing the HTML and the code to get values from the page. Your job is to focus only on the section marked 'YOUR LOGIC HERE'. We will learn exactly how this DOM interaction works in a future lesson, but for now, you can see how your JS logic can power a real webpage!"*

#### **Activity 4: Currency Converter (USD to EUR)**

1.  Create a new file named `currency_converter.html`.
2.  **Copy and paste this exact code into the file.** Do not change the HTML or the first few lines of the script.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Currency Converter</title>
    <style>body { font-family: sans-serif; padding: 20px; }</style>
</head>
<body>
    <h1>Currency Converter</h1>
    <h3>USD to EUR</h3>

    <p>Amount in USD: <strong id="usd-amount">100</strong></p>
    <p>Current Rate (1 USD to EUR): <strong id="exchange-rate">0.92</strong></p>
    <hr>
    <h2>Amount in EUR: <span id="eur-amount">--</span></h2>

    <script>
        // --- DO NOT EDIT THIS PART ---
        // This code gets the text from the HTML elements above.
        // Notice the values are STRINGS!
        const usdValueString = document.getElementById('usd-amount').textContent;
        const exchangeRateString = document.getElementById('exchange-rate').textContent;
        const eurAmountElement = document.getElementById('eur-amount');
        
        // --- YOUR LOGIC HERE ---
        
        // 1. Convert the string values to numbers.
        //    Hint: Use Number()
        const usdValue = /* Your code here */;
        const exchangeRate = /* Your code here */;
        
        // 2. Calculate the equivalent amount in EUR.
        const eurValue = /* Your code here */;
        
        // 3. Update the text on the page to show the result.
        //    (We've done this part for you!)
        eurAmountElement.textContent = eurValue.toFixed(2); // .toFixed(2) rounds to 2 decimal places

    </script>
</body>
</html>
```

3.  **Your Task:** Fill in the three lines in the `// --- YOUR LOGIC HERE ---` section.
    *   You need to convert the two string variables to numbers.
    *   You need to multiply them to get the final `eurValue`.
4.  Save the file and open it in your browser. If your logic is correct, you should see the EUR amount calculated on the page. Try changing the numbers in the HTML (`<strong id="usd-amount">150</strong>`) and refreshing the page to see your calculator work with new values!

#### **Activity 5 (Advanced Challenge): Simple Tip Calculator**

This requires a little more logic.

1.  Create a new file named `tip_calculator.html`.
2.  **Copy and paste this exact starter code:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Tip Calculator</title>
    <style>body { font-family: sans-serif; padding: 20px; }</style>
</head>
<body>
    <h1>Tip Calculator</h1>

    <p>Bill Amount: $<strong id="bill-amount">50.00</strong></p>
    <p>Tip Percentage: <strong id="tip-percentage">18</strong>%</p>
    <hr>
    <h3>Tip Amount: $<span id="tip-amount">--</span></h3>
    <h2>Total Bill: $<span id="total-bill">--</span></h2>

    <script>
        // --- DO NOT EDIT THIS PART ---
        const billString = document.getElementById('bill-amount').textContent;
        const tipPercentString = document.getElementById('tip-percentage').textContent;
        const tipAmountElement = document.getElementById('tip-amount');
        const totalBillElement = document.getElementById('total-bill');

        // --- YOUR LOGIC HERE ---

        // 1. Convert the bill and tip percentage strings to numbers.
        const bill = /* Your code here */;
        const tipPercent = /* Your code here */;

        // 2. Calculate the tip amount.
        //    Hint: A percentage is (value / 100). So, 18% is 0.18.
        const tipAmount = /* Your code here */;

        // 3. Calculate the total bill (bill + tip).
        const totalBill = /* Your code here */;

        // 4. Update the text on the page.
        tipAmountElement.textContent = tipAmount.toFixed(2);
        totalBillElement.textContent = totalBill.toFixed(2);
    </script>
</body>
</html>
```

3.  **Your Task:** Complete the logic to calculate the `tipAmount` and `totalBill`.
4.  Open the file in the browser to test your work. Experiment by changing the bill amount and tip percentage in the HTML to see your calculations update.

---
This lab structure effectively balances pure logic practice in a sterile Node.js environment with the excitement of seeing that same logic power an interactive webpage, providing a perfect bridge to the upcoming lessons on DOM manipulation.

---
You're right, expanding the console section will build a stronger foundation in pure logic before they even touch the DOM activities. A 5-hour lab is quite extensive, so the key is to provide enough content with varying difficulty levels to keep all students engaged, from the slowest to the fastest.

This revised lab structure is designed to be a comprehensive "bootcamp" of the first three hours. It can easily fill 3-5 hours depending on the students' pace and how much time is allocated to the quizzes and challenges.

---

### **Revised & Extended Lab Session: JavaScript Fundamentals Bootcamp**

**Total Estimated Time:** 3 - 5 hours
**Objective:** This comprehensive lab solidifies your understanding of JavaScript's core foundations. By the end, you will be a confident user of variables, data types, and operators, capable of solving multi-step problems in both Node.js and the browser.

---

### **Part 1: The Basics - Setup & Revision (Estimated Time: 30-45 minutes)**

This section is a warm-up and ensures everyone is on the same page.

#### **Activity 1: Environment Check**
1.  Create a new folder named `js_bootcamp_lab`. Open it in VS Code.
2.  **Browser Check:** Create `hello_browser.html`. Inside, use `document.write()` to display your name in an `<h1>` tag and `console.log()` to print your favorite food to the console. Open it in a browser and verify both outputs.
3.  **Node.js Check:** Create `hello_node.js`. Inside, use `console.log()` to print three lines: your name, your age, and the current year. Run it with `node hello_node.js` and verify the output.

---

### **Part 2: Deep Dive into Node.js Logic (Estimated Time: 1.5 - 2 hours)**

This is the core of the lab, focusing on problem-solving with operators without the distraction of a UI.

#### **Activity 2: Simple Age Calculator**
1.  Create `age_calculator.js`.
2.  Define `const birthYear` and `const currentYear`.
3.  Calculate the `age`.
4.  **Output:** `If you were born in 1995, you are 29 years old.`

#### **Activity 3: Temperature Converter (Celsius to Fahrenheit)**
1.  Create `temperature_converter.js`.
2.  Define `const celsius`.
3.  Use the formula `F = (C * 9/5) + 32` to calculate `fahrenheit`.
4.  **Output:** `25°C is equal to 77°F.`

#### **Activity 4: Property Splitter**
This activity involves multiple steps and is great for practicing variable updates.
1.  Create `property_splitter.js`.
2.  Imagine you and a partner sold a house. Define a `const totalValue` (e.g., `500000`).
3.  There's a `const realtorFeePercentage` of `0.06` (6%).
4.  First, calculate the `realtorCut` by multiplying `totalValue` by `realtorFeePercentage`.
5.  Next, calculate the `netValue` which is the `totalValue` minus the `realtorCut`.
6.  Finally, calculate the `partnerShare`, which is the `netValue` divided by 2.
7.  **Log each step clearly to the console:**
    *   **Example Output:**
        ```
        Original house value: $500000
        Realtor's cut: $30000
        Net value after fees: $470000
        Each partner's share: $235000
        ```

#### **Activity 5: The Reading Speed Estimator**
This activity requires careful unit conversion and breaking down a problem.
1.  Create `reading_estimator.js`.
2.  Define a `const wordsInBook` (e.g., `350000`).
3.  Define a `const wordsPerMinute` (the user's reading speed, e.g., `250`).
4.  **Step 1:** Calculate the total minutes required to read the book. Store this in `totalMinutes`.
5.  **Step 2:** Convert `totalMinutes` into hours. Store this in `totalHours`. (Hint: `minutes / 60`).
6.  **Step 3 (Challenge):** The `totalHours` might be a decimal (e.g., 23.33 hours). Can you split this into full hours and remaining minutes?
    *   Use `Math.floor(totalHours)` to get the `fullHours`.
    *   Use the modulo operator (`%`) or subtraction to find the remaining minutes. `remainingMinutes = totalMinutes % 60;`
7.  **Log the results:**
    *   **Example Output:**
        ```
        The book has 350000 words.
        With a reading speed of 250 WPM...
        It will take approximately 23.33 hours to read.
        More specifically: 23 full hours and 20 minutes.
        ```
    *   *(Note: The `toFixed(2)` method can be useful for rounding decimals: `totalHours.toFixed(2)`)*

---

### **Part 3: Interactive Browser Applications (Estimated Time: 1 - 1.5 hours)**

This section previews the power of connecting your JS logic to a user interface. Use the provided starter code for each.

#### **Activity 6: Currency Converter (USD to EUR)**
*   (Use the starter code provided in the previous response).
*   **Task:** Implement the logic to convert `usdValueString` and `exchangeRateString` to numbers, calculate the `eurValue`, and see it appear on the webpage.

#### **Activity 7: Tip Calculator**
*   (Use the starter code provided in the previous response).
*   **Task:** Implement the logic to calculate the `tipAmount` and `totalBill` based on the bill and tip percentage from the HTML, and display both results on the page.

---

### **Part 4: Quiz & Final Challenges (Estimated Time: 30-45 minutes)**

This section tests conceptual understanding and pushes faster students.

#### **Activity 8: Concept Quiz**
*   (Use the quiz provided in the previous response: Multiple Choice, "What's the Output?", and "Find the Bug"). This is a great way to break up the coding and reinforce the "why".

#### **Activity 9: Final Challenge (Node.js) - The BMI Calculator**
1.  Create `bmi_calculator.js`.
2.  The formula for BMI is `weight (kg) / (height (m)²)`.
3.  Define `const weightInKg` (e.g., `70`).
4.  Define `const heightInCm` (e.g., `175`).
5.  **Your Task:**
    *   You must first convert `heightInCm` to `heightInM` (Hint: `cm / 100`).
    *   Then, calculate the BMI using the formula. Remember to square the height in meters (`heightInM ** 2`).
    *   **Output:** `A person with a weight of 70kg and a height of 1.75m has a BMI of 22.86.`

---
