### **Lab Session 6: The Data Manager (Arrays)**

**Total Estimated Time:** 4 - 5 hours
**Objective:** Master the creation, modification, and iteration of arrays. Learn to transform data using modern methods (`map`, `filter`) and dynamically generate web page content from array data.

---

### **Part 1: Basic Array Manipulation (Estimated Time: 1 hour)**

Let's practice the core methods: `push`, `pop`, `shift`, `unshift`, and `splice` using Node.js.

#### **Activity 1: The Tech Support Queue**
1. Create `queue.js`.
2. Create an array called `customers` with three names: `["Alice", "Bob", "Charlie"]`.
3. **Task:**
   * A new customer, "Diana", joins the back of the line. Add her.
   * A VIP customer, "Ethan", gets to cut to the very front of the line. Add him.
   * The tech support agent finishes helping the first person in line. Remove them from the array and store their name in a variable called `servedCustomer`.
   * Print `servedCustomer` and the updated `customers` array to the console.

#### **Activity 2: The Playlist Editor**
1. Create `playlist.js`.
2. Create an array: `let songs = ["Song 1", "Song 2", "Song 3", "Song 4", "Song 5"];`
3. **Task:**
   * You hate "Song 5". Remove it from the end of the list.
   * You want to replace "Song 3" with "New Hit Song". Use `.splice()` to do this in one line.
   * You want to add "Intro Track" right after "Song 1" (so it becomes the new index 1). Use `.splice()` to insert it without deleting anything.
   * Print the final `songs` array.

---

### **Part 2: Modern Array Iteration (Estimated Time: 1.5 hours)**

Time to use the heavy hitters: `forEach`, `map`, and `filter`.

#### **Activity 3: The Receipt Printer (`forEach`)**
1. Create `receipt.js`.
2. Create an array of prices: `let cartPrices = [12.99, 4.50, 25.00, 9.99];`
3. Create a variable `let total = 0;`.
4. **Task:**
   * Use `.forEach()` to loop through `cartPrices`.
   * Inside the loop, add each price to the `total` variable.
   * After the loop, `console.log("Your total is: $" + total);`

#### **Activity 4: The Grade Curve (`map`)**
1. Create `grades.js`.
2. Create an array of test scores: `let testScores = [72, 85, 90, 65, 88];`
3. The teacher decided the test was too hard and is adding 5 points to everyone's score.
4. **Task:**
   * Use `.map()` to create a **new** array called `curvedScores`.
   * Inside the map function, return the score + 5.
   * Print both the original `testScores` and the new `curvedScores` to prove the original wasn't changed.

#### **Activity 5: The VIP Bouncer (`filter`)**
1. Create `ages.js`.
2. Create an array of ages: `let guestAges = [16, 21, 18, 30, 15, 25];`
3. **Task:**
   * Use `.filter()` to create a new array called `adults`. It should only contain ages 18 and older.
   * Use `.filter()` again to create a new array called `minors`. It should only contain ages strictly less than 18.
   * Print both new arrays.

---

### **Part 3: Connecting Arrays to the DOM (Estimated Time: 1.5 hours)**

This is where the magic happens. We will use arrays to render HTML.

#### **Activity 6: The Dynamic Movie List**
1. Create `movies.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>My Favorite Movies</h2>
    <input type="text" id="movieInput" placeholder="Add a movie...">
    <button onclick="addMovie()">Add</button>
    
    <ul id="movieList">
        <!-- Movies will appear here -->
    </ul>

    <script>
        // 1. Create our "State" (the data)
        let movies = ["The Matrix", "Inception"];
        const listElement = document.getElementById('movieList');

        // 2. Function to render (draw) the array to the screen
        function renderMovies() {
            // Clear the current list so we don't get duplicates!
            listElement.innerHTML = ""; 

            // Loop through the array and create <li> tags
            movies.forEach((movie) => {
                listElement.innerHTML += "<li>" + movie + "</li>";
            });
        }

        // 3. Initial render when page loads
        renderMovies();

        // 4. Function to handle the button click
        function addMovie() {
            // --- YOUR LOGIC HERE ---
            // A. Get the text from the input box (document.getElementById('movieInput').value)
            // B. Push that text into the 'movies' array
            // C. Call renderMovies() to redraw the screen with the new data!
            // D. (Optional) Clear the input box so it's empty for the next movie.
        }
    </script>
</body>
</html>
```

#### **Activity 7: The E-commerce Product Filter**
1. Create `filter.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<body>
    <h2>Products</h2>
    <button onclick="showAll()">Show All</button>
    <button onclick="showCheap()">Under $50</button>
    <button onclick="showExpensive()">Over $50</button>

    <ul id="productDisplay"></ul>

    <script>
        let prices = [10, 85, 25, 120, 45, 90, 5];
        const display = document.getElementById('productDisplay');

        function renderList(arrayToRender) {
            display.innerHTML = "";
            arrayToRender.forEach((price) => {
                display.innerHTML += "<li>$" + price + "</li>";
            });
        }

        // Show all on load
        renderList(prices);

        function showAll() {
            renderList(prices);
        }

        function showCheap() {
            // --- YOUR LOGIC HERE ---
            // 1. Use .filter() on the 'prices' array to get prices < 50.
            // 2. Pass that new filtered array into the renderList() function!
        }

        function showExpensive() {
            // --- YOUR LOGIC HERE ---
            // 1. Use .filter() on the 'prices' array to get prices >= 50.
            // 2. Pass that new filtered array into the renderList() function!
        }
    </script>
</body>
</html>
```

---

### **Part 4: The 20-Question Array Master Quiz (Estimated Time: 1 hour)**

**Section A: Syntax and Indexing**
1. Which brackets are used to create an array? `{}`, `[]`, or `()`?
2. In the array `let colors = ["Red", "Blue", "Green"]`, what is the index of "Blue"?
3. How do you access the *first* item in any array?
4. What property tells you how many items are in an array?
5. If an array has 5 items, what is the index of the *last* item?

**Section B: Mutating Methods (Changing the Array)**
6. Which method adds an item to the *end* of an array?
7. Which method removes the *first* item from an array?
8. Which method would you use to remove an item from the *exact middle* of an array?
9. True or False: `.pop()` returns the item that was removed.
10. If I want to add an item to the very front of the line, I use `._________()`.

**Section C: Modern Methods (Iterating and Transforming)**
11. Which method is the modern equivalent of a `for` loop, designed specifically to execute a function once for every item in an array?
12. True or False: `.map()` changes the original array.
13. If you have an array of 10 items, and you run `.map()` on it, exactly how many items will be in the new array?
14. Which method returns a new array containing only the items that pass a specific `true/false` condition?
15. Fill in the blank: `forEach`, `map`, and `filter` all take a ___________ as their argument.

**Section D: What's the Output?**
16. 
```javascript
let animals = ["Dog", "Cat"];
animals[2] = "Bird";
console.log(animals.length);
```
Output: \_\_\_\_\_\_\_\_\_

17. 
```javascript
let nums = [1, 2, 3];
nums.push(4);
nums.shift();
console.log(nums);
```
Output: \_\_\_\_\_\_\_\_\_

18. 
```javascript
let scores = [10, 20, 30];
let newScores = scores.map(s => s + 1);
console.log(scores[0]);
```
Output: \_\_\_\_\_\_\_\_\_

19. 
```javascript
let words = ["Hi", "Hello", "Hey"];
words.splice(1, 1, "Greetings");
console.log(words);
```
Output: \_\_\_\_\_\_\_\_\_

**Section E: Find the Bug**
20. 
```javascript
let cars = ("Ford", "Chevy", "Honda");
console.log(cars[1]);
```
Bug: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

---

### **Instructor Answer Key for Quiz**
1. `[]` (Square brackets)
2. 1
3. `arrayName[0]`
4. `.length`
5. 4 (Because of zero-based indexing)
6. `.push()`
7. `.shift()`
8. `.splice()`
9. True
10. `.unshift()`
11. `.forEach()`
12. False (It creates and returns a brand new array).
13. 10 (Map always returns an array of the exact same length).
14. `.filter()`
15. Function (specifically, a callback function).
16. 3
17. `[2, 3, 4]` (1 was shifted off, 4 was pushed on).
18. `10` (Map doesn't change the original `scores` array).
19. `["Hi", "Greetings", "Hey"]` (Starts at index 1, deletes 1 item, inserts "Greetings").
20. Used parentheses `()` instead of square brackets `[]` to declare the array.
