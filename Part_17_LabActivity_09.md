### **Lab Session 8: The Web Architect (DOM & Events)**

**Total Estimated Time:** 4 - 5 hours
**Objective:** Master interacting with the Document Object Model (DOM). Learn to select elements, modify styles and text, listen for user events, and dynamically create or remove HTML elements on the fly.

---

### **Part 1: Selection & Modification (Estimated Time: 1 hour)**

Let's start by grabbing things on the screen and changing how they look and read.

#### **Activity 1: The Light Switch (Dark Mode Toggle)**
1. Create `theme.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body { transition: 0.3s; padding: 50px; font-family: sans-serif; }
        /* We will apply these classes using JavaScript! */
        .light-theme { background-color: white; color: black; }
        .dark-theme { background-color: #333; color: white; }
    </style>
</head>
<body class="light-theme" id="pageBody">
    <h1 id="statusText">It is currently DAY</h1>
    <button id="toggleBtn">Turn off the lights</button>

    <script>
        const bodyElement = document.getElementById('pageBody');
        const btnElement = document.getElementById('toggleBtn');
        const statusElement = document.getElementById('statusText');

        let isDaytime = true;

        btnElement.addEventListener('click', () => {
            // --- YOUR LOGIC HERE ---
            // 1. Check if 'isDaytime' is true.
            // 2. If true: 
            //    - Change bodyElement.className to "dark-theme"
            //    - Change statusElement.textContent to "It is currently NIGHT"
            //    - Change btnElement.textContent to "Turn on the lights"
            //    - Set isDaytime to false.
            // 3. Else (if it's night):
            //    - Change everything back to the light-theme and DAY text.
            //    - Set isDaytime to true.
        });
    </script>
</body>
</html>
```

#### **Activity 2: The Live Character Counter**
Events aren't just for clicks! Let's listen to the user typing.
1. Create `counter.html`.
2. Write an `<input type="text" id="msgInput">` and a `<p id="charCount">0/50 characters</p>`.
3. Select both elements in your JavaScript.
4. Add an event listener to the input element, but instead of `"click"`, listen for `"input"`.
   * `inputElement.addEventListener('input', () => { ... })`
5. Inside the listener, get the length of the string: `let length = inputElement.value.length;`.
6. Update the `<p>` tag's `textContent` to show the current length (e.g., `length + "/50 characters"`).
7. *Challenge:* If the length goes over 50, change the text color to red!

---

### **Part 2: Advanced Form Inputs (Estimated Time: 1.5 hours)**

#### **Activity 3: The Custom Greeting Generator**
1. Create `greeting.html`.
2. Create an interface with:
   * A text input for "First Name".
   * A text input for "Last Name".
   * A select dropdown for "Greeting Type" (Options: "Formal", "Casual", "Shouting").
   * A "Generate" button.
   * An empty `<h2>` with an ID of `output`.
3. **Your Task:**
   * Listen for the button click.
   * Grab the `.value` from all three inputs.
   * Write an `if/else` or `switch` statement based on the "Greeting Type".
   * *Formal:* Output "Good day to you, [First] [Last]."
   * *Casual:* Output "Hey [First], what's up?"
   * *Shouting:* Output "HELLO [FIRST] [LAST]!!!" (Use `.toUpperCase()`).

---

### **Part 3: Creating and Destroying Elements (Estimated Time: 1.5 hours)**

Let's build interfaces completely from scratch using arrays and DOM creation methods.

#### **Activity 4: The Dynamic Comment Section**
1. Create `comments.html`.
2. Paste this starter code:
```html
<!DOCTYPE html>
<html>
<style>
    .comment-box { border: 1px solid #ccc; padding: 10px; margin-top: 10px; background: #f9f9f9;}
    .author { font-weight: bold; color: blue; }
    .delete-btn { color: red; cursor: pointer; font-size: 12px; margin-left: 10px;}
</style>
<body>
    <h2>Leave a Comment</h2>
    <input type="text" id="authorInput" placeholder="Your Name"><br><br>
    <textarea id="commentInput" placeholder="Your comment..."></textarea><br><br>
    <button id="postBtn">Post Comment</button>

    <div id="commentSection"></div>

    <script>
        const authorIn = document.getElementById('authorInput');
        const commentIn = document.getElementById('commentInput');
        const postBtn = document.getElementById('postBtn');
        const section = document.getElementById('commentSection');

        postBtn.addEventListener('click', () => {
            const authorText = authorIn.value;
            const commentText = commentIn.value;

            if(authorText === "" || commentText === "") {
                alert("Please fill out both fields!");
                return;
            }

            // --- YOUR LOGIC HERE ---
            // 1. Create a <div> element (call it 'newComment').
            // 2. Add the class "comment-box" to it: newComment.className = "comment-box";
            // 3. Set the innerHTML of newComment to include the authorText and commentText.
            //    Example: `<p class="author">${authorText}</p><p>${commentText}</p>`
            // 4. Append 'newComment' to the 'section'.
            // 5. Clear both input boxes.
        });
    </script>
</body>
</html>
```

#### **Activity 5: Generating a UI from an Array of Objects**
This is a core skill for React/Modern JS developers.
1. Create `gallery.html`.
2. Provide an empty `<div id="gallery"></div>`.
3. In your script, create this array:
```javascript
const animals = [
    { name: "Lion", emoji: "🦁", desc: "King of the jungle" },
    { name: "Penguin", emoji: "🐧", desc: "Loves the cold" },
    { name: "Monkey", emoji: "🐒", desc: "Eats bananas" }
];
```
4. **Task:** Use `animals.forEach()` to loop through the array. For *each* animal:
   * Create a `div`.
   * Set its `innerHTML` to display the emoji, an `h3` of the name, and a `p` of the desc.
   * Append it to the `gallery` div on the screen.

---

### **Part 4: The 20-Question DOM Master Quiz (Estimated Time: 1 hour)**

**Section A: The DOM & Selection**
1. What does DOM stand for?
2. Which global JavaScript object represents the entire HTML page?
3. Which method is best for selecting an element that has `id="main-title"`?
4. How would you select an element with `class="card"` using `querySelector`?
5. True or False: `querySelector('p')` selects *all* paragraph tags on the page.

**Section B: Modifying Elements**
6. Which property changes the text inside an element *without* rendering HTML tags?
7. Which property changes the text inside an element *and* renders any HTML tags included in the string?
8. If I have `const box = document.getElementById('box')`, how do I change its background color to blue using JS?
9. How do you get the text that a user has typed into an `<input>` element?
10. True or False: `document.write()` is the best way to update a small part of a modern webpage.

**Section C: Events**
11. What method is used to make JavaScript "listen" for user actions on an element?
12. List three common types of events (e.g., `"click"`).
13. In `btn.addEventListener("click", myFunction)`, what is `myFunction` acting as? (Hint: It's passed as an argument).
14. If you want to run code every time a user presses a key inside a text box, which event should you listen for: `"click"`, `"input"`, or `"submit"`?
15. Look at this code: `button.addEventListener("click", console.log("Hi"))`. Why will this print "Hi" immediately when the page loads, instead of waiting for a click? *(Hint: Look at the parentheses).*

**Section D: Element Creation & Destruction**
16. What method is used to conjure a brand new HTML element in JavaScript's memory?
17. Once a new element is created, what method must you call on a parent element to actually put the new element onto the screen?
18. How do you delete an element from the screen using JavaScript?
19. Order these steps for creating dynamic content: 
    a) Append it.
    b) Customize it (add text/classes).
    c) Create it.
20. True or False: You can add an Event Listener to an element that you just created using `document.createElement()`, even before it is appended to the screen.

---

### **Instructor Answer Key for Quiz**
1. Document Object Model
2. `document`
3. `document.getElementById('main-title')`
4. `document.querySelector('.card')`
5. False. It only selects the *first* matching paragraph. (To get all, you'd use `querySelectorAll`).
6. `.textContent`
7. `.innerHTML`
8. `box.style.backgroundColor = "blue";`
9. By accessing its `.value` property.
10. False. It overwrites the whole page.
11. `.addEventListener()`
12. `"click"`, `"input"`, `"submit"`, `"mouseenter"`, `"keydown"`, etc.
13. A callback function.
14. `"input"` (or `"keydown"`/`"keyup"`).
15. Because the parentheses `()` execute the function immediately. You should pass an arrow function: `() => console.log("Hi")` or just the function name without parentheses.
16. `document.createElement('tagName')`
17. `parentElement.appendChild(newElement)`
18. `element.remove()`
19. C, B, A
20. True. It exists in memory, so you can fully configure it (listeners included) before showing it to the user.
