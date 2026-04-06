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
