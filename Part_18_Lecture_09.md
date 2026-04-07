# Hour 10: Asynchronous JS & Web APIs

**Talking to the Internet & The Grand Finale!**

---

### Recap & Agenda

**Where We've Been:**
*   You started with basic data and logic.
*   You learned to group logic (Functions) and data (Arrays/Objects).
*   You learned to manipulate the webpage dynamically (DOM & Events).

**Today's Agenda:**
1.  The Problem: Synchronous "Blocking" Code.
2.  The Solution: Asynchronous JavaScript.
3.  Promises & `async / await`.
4.  What is an API & JSON?
5.  Fetching data from the internet (`fetch`).
6.  Saving data to the browser (`localStorage`).
7.  **Final Project:** The Live Weather Dashboard.

---

### The Problem: Synchronous Code

By default, JavaScript is **Synchronous**. This means it executes code line by line, from top to bottom.

It must finish Line 1 before it can move to Line 2. 

Usually, this is incredibly fast. But what if Line 2 asks for data from a server in Australia, and it takes 3 seconds to arrive? 

**The whole webpage freezes for 3 seconds!** We call this "Blocking."

---

### The Restaurant Analogy

Imagine a fast-food restaurant with one cashier. 

**Synchronous (Bad):** You order a burger. The cashier goes to the kitchen, cooks the burger, waits for it to finish, hands it to you, and *then* asks the next person in line for their order. The line stops moving.

**Asynchronous (Good):** You order a burger. The cashier gives you a **receipt with an order number**, sends the ticket to the kitchen, and *immediately* takes the next person's order. When your burger is ready, they call your number.

JavaScript works exactly like the Asynchronous cashier!

---

### Asynchronous JavaScript

**Asynchronous** code allows JavaScript to start a long-running task (like downloading data), move on to other tasks, and come back to the first task when it finishes.

How does JavaScript hand you a "receipt" to say, "I'm working on it, I'll let you know when it's done"?

It uses something called a **Promise**.

---

### What is a Promise?

A **Promise** in JavaScript is exactly like a real-life promise. It is an object that represents a value that might not be available right now, but will be resolved in the future.

A Promise has three states:
1.  **Pending:** (Cooking the burger).
2.  **Fulfilled / Resolved:** (Burger is ready! Here is your data).
3.  **Rejected:** (We ran out of meat! Here is an error).

---

### Handling Promises (The `.then` way)

When a function returns a Promise, we can use the `.then()` method to tell JavaScript what to do *when* the promise is fulfilled. 

```javascript
// Imagine 'downloadData()' takes 2 seconds and returns a Promise
downloadData()
    .then( (data) => {
        // This code only runs AFTER the download is complete
        console.log("Download finished!", data);
    })
    .catch( (error) => {
        // This code runs if something goes wrong (e.g., no internet)
        console.log("Uh oh, an error:", error);
    });

console.log("This will print FIRST, before the download finishes!");
```

---

### The Modern Way: `async / await`

Using `.then()` can get messy if you have lots of nested steps. Modern JavaScript introduced a beautiful, cleaner syntax: `async` and `await`.

It makes Asynchronous code *look* and *read* like normal Synchronous code!

**The Rules:**
1. You must put the word `async` in front of your function.
2. Inside that function, you can put the word `await` in front of any Promise.
3. `await` tells JS: *"Pause this specific function right here until the Promise finishes."*

---

### `async / await` Example

```javascript
// 1. Mark the function as 'async'
async function getUserProfile() {
    
    console.log("1. Starting download...");

    // 2. 'await' pauses the function until the Promise resolves
    const data = await downloadData(); 
    
    console.log("2. Data received: ", data);
}

getUserProfile();
console.log("3. Doing other UI stuff while we wait...");

// Output Order: 1, 3, 2
```

---

### What is a Web API?

**API** stands for Application Programming Interface. 

In the context of the web, an API is a server created by another company (like Google, Twitter, or a Weather service) that allows your JavaScript to ask it for data.

*   "Hey Weather API, what is the temperature in London?"
*   "Hey Movie API, give me a list of Batman movies."

---

### How do APIs send data back? (JSON)

If we ask a server in Germany for data, what language does it use to reply? 

The universal language of web data is **JSON** (JavaScript Object Notation).

JSON is just a massive String of text that is formatted to look exactly like a JavaScript Object.

```json
{
    "city": "London",
    "temperature": 15,
    "conditions": "Rainy"
}
```

---

### The `fetch()` API

How do we actually ask an API for data? We use the built-in browser function called `fetch()`.

`fetch()` takes a URL (a web address) and returns a **Promise** containing the server's response.

Because it takes time to travel across the internet, we must use `await`!

---

### Fetching Data: Step-by-Step

Let's fetch some data using `async/await`!

```javascript
async function getDogPicture() {
    // 1. Fetch the data from the URL (takes time, use await)
    const response = await fetch("https://dog.ceo/api/breeds/image/random");

    // 2. The response is a raw network package. 
    // We must convert it to JSON! (This also takes time, use await)
    const data = await response.json();

    // 3. Now we have a usable JavaScript Object!
    console.log(data.message); // Prints a URL to a dog picture!
}
```

---

### Try It! The Random Dog Generator

Let's connect a fetch request to the DOM!

**HTML:**
```html
<button id="dogBtn">Get a Dog!</button>
<img id="dogImg" src="" width="300">
```

**JavaScript:**
```javascript
const btn = document.getElementById("dogBtn");
const img = document.getElementById("dogImg");

btn.addEventListener('click', async () => {
    // Fetch data and parse it to JSON
    let response = await fetch("https://dog.ceo/api/breeds/image/random");
    let data = await response.json();
    
    // Change the image source to the URL from the API!
    img.src = data.message;
});
```

---

### The Persistence Problem

You now know how to get live data and display it! But there is one problem left.

If a user configures their settings on your webpage (like choosing a "Dark Theme" or typing a "To-Do List"), what happens when they hit the **Refresh** button?

**It all gets erased.** JavaScript variables die when the page reloads.

---

### The Solution: Web Storage API

Browsers give us a tiny database called `localStorage`. 

Data saved in `localStorage` stays in the user's browser forever, even if they close the tab, close the browser, or restart their computer!

It is perfect for saving user preferences, high scores, or recent searches.

---

### Saving Data to `localStorage`

Data is saved in `localStorage` using Key-Value pairs (just like Objects!).

**Rule:** `localStorage` can ONLY store Strings.

We use the method: `localStorage.setItem('keyName', 'ValueToSave');`

```javascript
let username = "AlexCoder";

// Save it to the browser's hard drive!
localStorage.setItem('savedUser', username);
```

---

### Reading Data from `localStorage`

To get the data back when the user returns to the page, we use `getItem()`.

We use the method: `localStorage.getItem('keyName');`

```javascript
// Retrieve the data
let returningUser = localStorage.getItem('savedUser');

if (returningUser) {
    console.log("Welcome back, " + returningUser + "!");
} else {
    console.log("Welcome, new guest!");
}
```

---

### Final Project: The Weather Dashboard

It is time to put all 10 hours of learning into one final, impressive project.

**The Goal:**
Build an app where a user can type a city name, fetch live real-time weather data for that city, display it, and save the last searched city so it automatically loads next time they visit.

---

### Project Architecture: What You Need

1.  **Variables & Data:** To hold the city names and API URL.
2.  **DOM Selection:** Input box, Search Button, Display areas.
3.  **Events:** A click listener on the search button.
4.  **Async/Fetch:** To call the Weather API.
5.  **DOM Manipulation:** To update the HTML with the live temperature.
6.  **localStorage:** To save the most recently searched city.

---

### Step 1: The OpenWeather API

To get weather data, we need to ask a weather company. We will use **OpenWeatherMap**.

1.  Go to `openweathermap.org`.
2.  Create a free account.
3.  Go to your profile and find your **API Key** (a long string of random letters/numbers). This acts as your password to access their data.

*The URL will look like this:*
`https://api.openweathermap.org/data/2.5/weather?q={CITY_NAME}&appid={YOUR_API_KEY}&units=metric`

---

### Step 2: The HTML Shell

Create your interface:

```html
<div id="weather-app">
    <h1>Weather Dashboard</h1>
    
    <input type="text" id="cityInput" placeholder="Enter city name">
    <button id="searchBtn">Search</button>

    <div id="weatherDisplay">
        <h2 id="cityName">--</h2>
        <h3 id="temperature">-- °C</h3>
        <p id="description">--</p>
    </div>
</div>
```

---

### Step 3: The Async Fetch Function

```javascript
const apiKey = "YOUR_KEY_HERE";

async function getWeather(city) {
    // 1. Construct the URL
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

    // 2. Fetch the data
    const response = await fetch(url);
    const data = await response.json();

    // 3. Update the DOM
    document.getElementById('cityName').textContent = data.name;
    document.getElementById('temperature').textContent = data.main.temp + " °C";
    document.getElementById('description').textContent = data.weather[0].description;
}
```

---

### Step 4: Events and LocalStorage

```javascript
const searchBtn = document.getElementById('searchBtn');
const cityInput = document.getElementById('cityInput');

// 1. Check for saved city on page load
const savedCity = localStorage.getItem('lastCity');
if (savedCity) {
    getWeather(savedCity); // Load it automatically!
}

// 2. Listen for clicks
searchBtn.addEventListener('click', () => {
    const targetCity = cityInput.value;
    
    getWeather(targetCity); // Fetch new data
    
    // Save to localStorage for next time!
    localStorage.setItem('lastCity', targetCity); 
});
```

---

### Congratulations!

You have completed the 10-Hour JavaScript Bootcamp!

**Look at what you've accomplished:**
*   You understand data types, variables, and logic.
*   You can automate tasks with loops and functions.
*   You can manage complex data structures (Arrays/Objects).
*   You can manipulate the DOM and react to user events.
*   You can write Asynchronous code and communicate with the internet.

---

### Next Steps in Your Journey

Where do you go from here?

1.  **Practice:** Build small projects (Calculators, Quizzes, Clocks).
2.  **Master Advanced JS:** Learn Array methods (`map`, `filter`, `reduce`) deeply.
3.  **Learn a Framework:** Look into **React**, **Vue**, or **Angular** for the frontend.
4.  **Explore the Backend:** Use your Node.js knowledge to learn **Express.js** and build your own APIs and databases!
