# Hour 9: DOM Manipulation & Events

**Making Web Pages Come Alive**

---

### Recap & Agenda

**Where We've Been:**
*   We mastered JavaScript basics: Variables, Loops, Logic, Functions.
*   We learned how to structure complex data with Arrays and Objects.
*   *We are finally ready to apply all of this to the browser!*

**Today's Agenda:**
1.  Saying Goodbye to `document.write()`.
2.  What is the DOM? (The Document Object Model).
3.  Selecting Elements (`getElementById`, `querySelector`).
4.  Changing Content and Styles.
5.  What are Events? (`click`, `input`).
6.  Adding Event Listeners.
7.  Creating and Appending new elements dynamically.
8.  **Activity:** Build an Interactive To-Do List!

---

### The End of an Era

Since Hour 1, we've used `document.write()` to put text on the screen.

**Why did we use it?** 
Because it's the absolute easiest way for a beginner to see JavaScript work.

**Why must we stop using it today?**
If you use `document.write()` *after* a webpage has fully loaded, **it deletes the entire webpage** and replaces it with your text. 

Modern web apps don't erase the page; they *update* specific parts of it. 

---

### Welcome to the DOM

**DOM** stands for **Document Object Model**.

When a web browser loads an HTML document, it translates all your HTML tags (`<h1>`, `<p>`, `<div>`) into a giant JavaScript **Object**. 

This object is called `document`. 

Because it's an object, we can use **Methods** (like we learned in Hour 8) to read it, change it, and add to it!

---

### The DOM Tree

Think of the DOM like a family tree.

*   `document` is the great-grandparent.
    *   `<html>` is the grandparent.
        *   `<head>` and `<body>` are the parents.
            *   `<h1>`, `<p>`, and `<button>` are the children.

JavaScript allows us to "select" any specific branch or leaf on this tree and modify it.

---

### The 3 Steps of DOM Manipulation

To change a webpage using JavaScript, we almost always follow this 3-step process:

1.  **Select** the element you want to change.
2.  **Listen** for an action (like a button click). *(Optional but common)*
3.  **Modify** the element (change text, color, add a class, etc.).

Let's look at Step 1.

---

### Step 1: Selecting Elements by ID

The fastest way to grab an element is by its unique HTML `id` attribute.
We use the method: `document.getElementById('idName')`

**HTML:**
```html
<h1 id="title">Hello World</h1>
```

**JavaScript:**
```javascript
// We grab the h1 and store it in a variable!
const titleElement = document.getElementById("title");

console.log(titleElement); // Prints the actual HTML element
```

---

### Step 1: Selecting Elements with QuerySelector

What if an element doesn't have an ID? We use `document.querySelector()`.

This method is incredibly powerful because you select elements exactly the same way you do in **CSS**.

```javascript
// Selects by ID (use the #)
const myTitle = document.querySelector("#title");

// Selects by Class (use the .)
const myButton = document.querySelector(".btn-primary");

// Selects by Tag Name (grabs the FIRST p tag it finds)
const firstParagraph = document.querySelector("p");
```

---

### Step 2: Modifying Content 

Once we have stored an element in a variable, we can change what's inside it.

*   `.textContent`: Changes the plain text.
*   `.innerHTML`: Changes the text AND renders any HTML tags inside it.

```javascript
const box = document.getElementById("message-box");

// This just shows the literal text "<strong>Hi!</strong>"
box.textContent = "<strong>Hi!</strong>";

// This actually makes the word "Hi!" bold on the screen
box.innerHTML = "<strong>Hi!</strong>"; 
```

---

### Step 2: Modifying Styles Dynamically

You can also change CSS directly from JavaScript using the `.style` property.

*Note: CSS properties with hyphens (like `background-color`) become camelCase in JS (`backgroundColor`).*

```javascript
const alertText = document.getElementById("alert");

// Make it red
alertText.style.color = "red";

// Make the font massive
alertText.style.fontSize = "40px";

// Hide it completely!
alertText.style.display = "none";
```

---

### What are Events?

A webpage isn't a static painting; it's a living interface. 

**Events** are things that happen on the screen:
*   A user clicks a button.
*   A user types in an input field.
*   A user hovers over an image.
*   A user presses the "Enter" key.

JavaScript can "listen" for these events and run a function when they happen!

---

### Step 3: Event Listeners

To make an element interactive, we attach an **Event Listener** to it using `.addEventListener()`.

It requires two arguments:
1.  The name of the event (e.g., `"click"`).
2.  The **Function** to run when the event happens.

---

### Event Listener Syntax

```html
<button id="clickMeBtn">Click Me!</button>
<h2 id="status">Waiting...</h2>
```

```javascript
// 1. Select the elements
const btn = document.getElementById("clickMeBtn");
const statusText = document.getElementById("status");

// 2. Attach the Event Listener
btn.addEventListener("click", () => {
    // 3. What happens when clicked?
    statusText.textContent = "You clicked the button!";
    statusText.style.color = "green";
});
```

---

### Getting User Input

If you have an `<input>` box on your page, you can get whatever the user typed into it by accessing the `.value` property.

```html
<input type="text" id="userName" placeholder="Enter name">
<button id="saveBtn">Save</button>
```

```javascript
const inputField = document.getElementById("userName");
const btn = document.getElementById("saveBtn");

btn.addEventListener("click", () => {
    // Grab the text exactly when the button is clicked!
    let typedText = inputField.value; 
    console.log("The user typed: " + typedText);
    
    // Clear the input box afterwards
    inputField.value = ""; 
});
```

---

### Creating Brand New Elements

Up to now, we've only modified existing HTML. What if we want to add *new* things to the screen (like adding a new task to a list)?

We use `document.createElement("tagName")`.

```javascript
// This creates an <li> in the computer's memory, 
// BUT it is not on the screen yet!
const newListItem = document.createElement("li");

// Let's add some text to it
newListItem.textContent = "Buy groceries";
```

---

### Appending Elements to the Page

To get our newly created element onto the screen, we have to attach it to an existing element on the DOM tree.

We use `.appendChild()`.

```html
<ul id="myList">
    <!-- Our new item will go here -->
</ul>
```

```javascript
const listElement = document.getElementById("myList");
const newListItem = document.createElement("li");

newListItem.textContent = "Buy groceries";

// Finally, attach it to the screen!
listElement.appendChild(newListItem);
```

---

### The 3-Step Creation Process

Whenever you want to add new HTML via JavaScript, memorize this sequence:

1.  **Create It:** `document.createElement()`
2.  **Customize It:** `.textContent`, `.style`, `.className`
3.  **Append It:** `parent.appendChild(newElement)`

---

### Removing Elements

Just as easily as we add them, we can remove elements from the screen using the `.remove()` method.

```javascript
const adBanner = document.getElementById("annoying-ad");

// Poof! It's gone.
adBanner.remove();
```

---

### Activity Prep: The To-Do List

We are going to combine EVERYTHING we've learned today to build a working To-Do List application.

**The Requirements:**
1.  An input box to type a task.
2.  An "Add Task" button.
3.  When the button is clicked, create a new `<li>` with the text.
4.  Append it to a `<ul>` on the screen.
5.  Clear the input box for the next task.

---

### Activity: The HTML Structure

1. Create a file named `todo.html`.
2. Write the following HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My To-Do List</title>
</head>
<body>
    <h1>Task Tracker</h1>
    
    <input type="text" id="taskInput" placeholder="What needs to be done?">
    <button id="addTaskBtn">Add Task</button>

    <ul id="taskList">
        <!-- New tasks will appear here -->
    </ul>

    <script src="app.js"></script> <!-- Link to external JS -->
</body>
</html>
```

---

### Activity: The JavaScript Logic (Part 1)

1. Create a file named `app.js` in the same folder.
2. First, let's select all our DOM elements.

```javascript
// 1. Select the elements we need
const inputElement = document.getElementById('taskInput');
const addBtn = document.getElementById('addTaskBtn');
const ulElement = document.getElementById('taskList');
```

---

### Activity: The JavaScript Logic (Part 2)

3. Add the Event Listener and creation logic.

```javascript
// 2. Add a click listener to the button
addBtn.addEventListener('click', () => {
    
    // Get the text from the input
    const taskText = inputElement.value;

    // Check if the input is empty! (Don't add blank tasks)
    if (taskText === "") {
        alert("Please enter a task!");
        return; // Stop the function here
    }

    // 3. Create the new <li> element
    const newLi = document.createElement('li');
    newLi.textContent = taskText;

    // 4. Append it to the <ul> on the screen
    ulElement.appendChild(newLi);

    // 5. Clear the input box
    inputElement.value = "";
});
```

---

### Challenge: Removing Tasks

Want to take it to the next level? 
Add an event listener to the `newLi` you just created!

*(Add this code right below `newLi.textContent = taskText;`)*

```javascript
    // When the user clicks on this specific list item...
    newLi.addEventListener('click', () => {
        // ...remove it from the screen!
        newLi.remove(); 
    });
```
*Now you can click tasks to cross them off/delete them!*

---

### Key Takeaways for Hour 9

*   The **DOM** translates HTML into a JavaScript object (`document`).
*   **Select elements** using `getElementById` or `querySelector`.
*   **Change text** using `.textContent` or `.innerHTML`.
*   **Events** are user actions. We use `.addEventListener("click", ...)` to react to them.
*   Get user input from an `<input>` field using `.value`.
*   **Create elements** dynamically with `document.createElement()` and `appendChild()`.

---

### Next Time...

**Coming Up in Hour 10: Asynchronous JS & Web APIs**

You've built an amazing app, but right now, if you refresh the page, your To-Do list disappears! Furthermore, your app only knows the data you type into it.

In our final hour, we will learn:
*   **localStorage:** How to save data in the browser so it survives a page refresh.
*   **`fetch()` API:** How to connect your app to the internet to download live data (like weather or movie databases).
*   **Final Project:** The Weather Dashboard!
