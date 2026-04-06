### **Hour 1: Introduction and Environment Setup**

### Your First Lines of JavaScript

**From Static Pages to Dynamic Magic**

---

### What We'll Cover Today

**Agenda for Hour 1:**

*   **What is JavaScript?** The language that brings websites to life.
*   **Two Worlds of JS:** Browser (Client-side) vs. Node.js (Server-side).
*   **Setting Up Our Tools:** Installing VS Code and Node.js.
*   **Our First Lines of Code:**
    *   Using `console.log()` for developer messages.
    *   Using `document.write()` to write on a webpage.
*   **Activity:** Write "Hello, World!" in both the browser and Node.js.

---

### What is JavaScript?

Think of a website like a house:
*   **HTML** is the **structure** (the walls, the floors, the roof).
*   **CSS** is the **decoration** (the paint color, the furniture, the style).
*   **JavaScript** is the **electricity & plumbing** (the lights turn on, the doorbell rings, the water runs).

It's the language that adds **interactivity** and **behavior** to your web pages.

---

### The Two Worlds of JavaScript

Where does JavaScript run?

**1. Client-Side (The Browser)**
*   Runs on the user's computer.
*   Interacts with the webpage (HTML & CSS).
*   **Tool:** Web Browser (Chrome, Firefox, Safari).

**2. Server-Side (Node.js)**
*   Runs on a remote computer (server) or your local terminal.
*   Interacts with databases, files, and other servers.
*   **Tool:** Node.js Runtime.

---

### Setting Up Our Tools

We only need two things to start our journey:

**1. VS Code (Visual Studio Code)**
*   A modern, free code editor.
*   It's where we will write all our code.

**2. Node.js**
*   A JavaScript "runtime."
*   It allows us to run JavaScript code *outside* of a web browser on our own computers.

---

### Output Method #1: `console.log()`

`console.log()` is used to print messages to the developer console. It's invisible to regular users but essential for developers.

*   Think of it as looking "under the hood" of your program.
*   It's our primary tool for **debugging** and checking data.

```javascript
console.log("Hello from the console!");
console.log("The current number is:", 42);
```

---

### Output Method #2: `document.write()`

`document.write()` writes content directly into the HTML document. It's a very simple way to see an immediate result on the webpage.

```javascript
document.write("<h1>Hello from the Webpage!</h1>");
```

**⚠️ Important Beginner's Note:**
`document.write()` is great for our first few lessons, but it has a major drawback: if used *after* the page has loaded, it will erase everything on the page! We will learn better methods later.

---

### Activity (Part 1): "Hello World" in the Browser

**Let's Code: Your First Web Script**

1.  Open VS Code.
2.  Create a new file named `index.html`.
3.  Add the following code:

```html
<!DOCTYPE html>
<html>
<body>
    <h1>Welcome to my Page!</h1>

    <!-- This is where our JavaScript lives -->
    <script>
        // This will write directly onto the page
        document.write('<h2>Hello, World! I am on the page.</h2>');

        // This will only be visible in the developer console
        console.log('Hello, Console! I am a secret message.');
    </script>
</body>
</html>
```

---

### Viewing Your Web Script

1. Save the `index.html` file.
2. Open that file in your web browser (Chrome/Edge/Firefox).
3. You should see the `h1` and `h2` text on the screen.
4. **The Secret Message:** Right-click the page -> Click "Inspect" -> Click the "Console" tab. You will see your `console.log()` message there!

---

### Activity (Part 2): "Hello World" with Node.js

**Let's Code: Your First Server Script**

1.  In VS Code, create a new file named `app.js`.
2.  Add this single line of code:

```javascript
// In Node.js, we don't have a document, so we only use the console.
console.log('Hello, Node.js World!');
```
3.  Save the file.
4.  Open the terminal in VS Code (`Ctrl + `` ` or `View -> Terminal`).
5.  Type: `node app.js` and press Enter.

---

### What Just Happened?

We wrote the **exact same language** (JavaScript) but ran it in two different environments.

*   **In `index.html`:** The browser read our HTML and then executed the JavaScript. It had access to a "document" (the webpage).
*   **In `app.js`:** Node.js directly executed our file. It had no "document" to interact with, only a "console" (the terminal).

---

### Key Takeaways for Hour 1

*   JavaScript adds interactivity to websites.
*   It can run in the **browser** (client) or on a **server/terminal** (with Node.js).
*   `console.log()` is our primary tool for seeing values and debugging.
*   `document.write()` is a simple first step for adding content to a webpage.

---

### Next Time...

**Coming Up in Hour 2: Variables & Data**

Now that we can write messages, our next step is to learn how to store, manage, and work with information.

We will cover:
*   **Variables:** `let` and `const`.
*   **Data Types:** Storing text (Strings), numbers, and more.
*   Building our first "User Profile" dynamically.





