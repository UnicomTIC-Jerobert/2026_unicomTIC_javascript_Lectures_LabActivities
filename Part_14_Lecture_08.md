# Hour 8: Objects & Advanced Logic

**Describing the World with Data**

---

### Recap & Agenda

**Where We've Been:**
*   Variables hold single values.
*   Arrays `[]` hold lists of values (ordered by numbers 0, 1, 2...).

**Today's Agenda:**
1.  The limits of Arrays.
2.  What is an Object? `{}`
3.  Key-Value Pairs.
4.  Dot Notation vs. Bracket Notation.
5.  Object Methods (Functions inside objects) & `this`.
6.  Arrays of Objects (The Web Data Standard).
7.  Advanced JS: Object Destructuring.
8.  Advanced JS: The Spread Operator (`...`).
9.  **Activity:** Build a Finance Tracker.

---

### The Problem: Arrays Aren't Always Enough

Let's say we want to store data about a specific user. We could use an array:

```javascript
let user = ["Alex", "Smith", 32, "asmith@email.com", true];
```

**The Issue:** 
To get the email, we have to remember it's at `user[3]`. To get the age, we need `user[2]`. 
If we add a middle name, all the numbers shift! Arrays are terrible for storing characteristics of a single entity.

---

### The Solution: Objects

If an Array is a **numbered filing cabinet**, an Object is a **dictionary** or an **ID Badge**.

Instead of using numbered indexes (`0, 1, 2`), an Object uses **Names (Keys)** to identify data.

We create objects using curly braces `{}`.

---

### Anatomy of an Object: Key-Value Pairs

Objects are collections of **Key-Value pairs** (also called Properties).
*   **Key:** The name of the property (always a string).
*   **Value:** The data stored inside (can be a string, number, boolean, array, or even another object!).

```javascript
let user = {
    firstName: "Alex",       // Key: firstName, Value: "Alex"
    lastName: "Smith",
    age: 32,
    email: "asmith@email.com",
    isActive: true
};
```
*Notice the colon `:` between key and value, and the comma `,` between pairs!*

---

### Reading Data: Dot Notation

The most common way to read data from an object is using **Dot Notation**. 
You write the object name, a dot `.`, and the exact key name.

```javascript
let user = {
    firstName: "Alex",
    age: 32
};

console.log( user.firstName ); // Output: Alex
console.log( user.age );       // Output: 32

// If a key doesn't exist:
console.log( user.address );   // Output: undefined
```

---

### Reading Data: Bracket Notation

You can also use **Bracket Notation** `[]`. You must pass the key as a **String**.

```javascript
let user = {
    firstName: "Alex"
};

console.log( user["firstName"] ); // Output: Alex
```

**Why have two ways?**
You *must* use bracket notation if your key has a space in it (e.g., `"favorite color"`) or if you are using a variable to find the key.

---

### Dot vs. Bracket: The Dynamic Key Rule

Look at this powerful use of Bracket Notation:

```javascript
let user = { name: "Alex", age: 32 };

// Imagine the user typed "age" into an input box on a website
let searchProperty = "age"; 

// Dot notation looks for a literal key named "searchProperty"
console.log( user.searchProperty ); // undefined

// Bracket notation evaluates the variable first!
console.log( user[searchProperty] ); // 32
```
*Rule of thumb: Use Dot Notation 95% of the time, unless the key is dynamic/in a variable.*

---

### Adding and Modifying Properties

Objects are flexible. You can add new properties or change existing ones at any time using either notation.

```javascript
let car = { make: "Toyota", model: "Camry" };

// Changing an existing property
car.model = "Corolla";

// Adding a brand new property
car.year = 2024;
car["color"] = "Blue";

console.log(car); 
// Output: { make: 'Toyota', model: 'Corolla', year: 2024, color: 'Blue' }
```

---

### Deleting Properties

If you need to completely remove a key-value pair from an object, use the `delete` keyword.

```javascript
let user = {
    name: "Alex",
    password: "supersecret123"
};

// We don't want to accidentally show the password!
delete user.password;

console.log(user); 
// Output: { name: 'Alex' }
```

---

### Methods: Functions inside Objects

Objects don't just hold static data; they can also hold actions! 
When a function is placed inside an object, it is called a **Method**.

```javascript
let dog = {
    name: "Buddy",
    breed: "Golden Retriever",
    // This is a method!
    bark: function() {
        console.log("Woof! Woof!");
    }
};

dog.bark(); // Output: Woof! Woof!
```
*(Does `console.log()` make sense now? `console` is a built-in object, and `log` is a method inside it!)*

---

### Introduction to `this`

What if our dog wants to say its own name? 
Inside an object's method, the keyword **`this`** refers to the object itself.

```javascript
let dog = {
    name: "Buddy",
    bark: function() {
        // "this" means "the dog object"
        console.log("Woof! My name is " + this.name);
    }
};

dog.bark(); // Output: Woof! My name is Buddy
```
*If we just wrote `name` instead of `this.name`, JavaScript would look for a global variable and crash!*

---

### Nested Objects

Remember how values can be anything? They can be other objects. This is how we organize complex data.

```javascript
let user = {
    name: "Alice",
    contact: {
        email: "alice@test.com",
        phone: "555-1234"
    }
};

// Chain the dots together!
console.log( user.contact.email ); // Output: alice@test.com
```

---

### The Ultimate Data Structure: Arrays of Objects

In the real world (APIs, Databases, Web Apps), data is almost always an **Array of Objects**. It is a list where every item has the exact same properties.

```javascript
let storeInventory = [
    { id: 1, name: "Laptop", price: 999 },
    { id: 2, name: "Mouse", price: 25 },
    { id: 3, name: "Keyboard", price: 75 }
];
```
*How do we get the name of the second item?*
`storeInventory[1].name` -> "Mouse"

---

### Looping Over Arrays of Objects

We combine Hour 7 (`.forEach`) and Hour 8 (Objects) to render lists dynamically!

```javascript
let users = [
    { name: "Alice", role: "Admin" },
    { name: "Bob", role: "Guest" }
];

users.forEach( (user) => {
    console.log(`${user.name} is a ${user.role}`);
});
// Output: 
// Alice is a Admin
// Bob is a Guest
```

---

### Advanced JS: The Extraction Problem

Often, we have a big object, but we only need to use a few pieces of it in our code.

**The Old Way:**
```javascript
let user = { name: "Sam", age: 25, city: "NY", country: "USA" };

let name = user.name;
let age = user.age;
let city = user.city;

console.log(name, age, city);
```
*This is repetitive. Let's use modern JavaScript to make it elegant.*

---

### The Solution: Object Destructuring

**Destructuring** is a special syntax that allows us to "unpack" properties from objects into distinct variables in a single line.

```javascript
let user = { name: "Sam", age: 25, city: "NY", country: "USA" };

// The Modern Way:
const { name, age, city } = user;

console.log(name, age, city); // Output: Sam 25 NY
```
*The variable names inside the `{}` MUST match the keys in the object.*

---

### Advanced JS: The Copying/Merging Problem

What if we want to copy an object and add a new property, or combine two objects together?

**The Long Way:**
```javascript
let baseUser = { name: "Sam", age: 25 };
let userWithRole = { name: baseUser.name, age: baseUser.age, role: "Admin" };
```
*Imagine doing this for an object with 50 properties!*

---

### The Solution: The Spread Operator `...`

The **Spread Operator** is written as three dots: `...`
It takes an array or an object and literally "spreads" its contents out. 
Think of it like opening a box and dumping all the items onto the floor.

---

### Spread Operator with Arrays

Let's combine two arrays.

```javascript
let fruits = ["Apple", "Banana"];
let veggies = ["Carrot", "Peas"];

// Dump the contents of both arrays into a brand new array
let groceries = [...fruits, ...veggies]; 

console.log(groceries); 
// Output: ["Apple", "Banana", "Carrot", "Peas"]
```

---

### Spread Operator with Objects

Let's copy an object and add a new property!

```javascript
let baseProfile = { name: "Sam", age: 25 };

// Open a new object {}, dump the baseProfile inside, and add a role
let completeProfile = { 
    ...baseProfile, 
    role: "Admin" 
};

console.log(completeProfile);
// Output: { name: 'Sam', age: 25, role: 'Admin' }
```
*This is used constantly in modern web frameworks like React!*

---

### Activity Prep: The Finance Tracker

We are going to build a "Finance Tracker" data object.

**The Goal:**
1. Create an object with properties for `income`, `expenses`, and `accountName`.
2. Create a method inside the object called `calculateBalance()`.
3. Use the `this` keyword to subtract expenses from income and return the result.
4. Output a summary using template literals and `document.write()`.

---

### Activity: Code Along

1. Create a file named `finance.html`.
2. Write the following inside a `<script>` tag:

```javascript
// 1. Create the Object
const account = {
    name: "Alex's Checking",
    income: 5000,
    expenses: 3200,
    
    // 2. Create the Method
    calculateBalance: function() {
        // Use 'this' to access the object's own data
        return this.income - this.expenses;
    }
};

// 3. Call the method and store the result
let currentBalance = account.calculateBalance();
```

---

### Activity: Code Along (Part 2)

Let's write it to the browser and practice Destructuring!

```javascript
// ... continued ...

// Let's destructure the object to make our HTML writing cleaner
const { name, income, expenses } = account;

document.write(`<h2>Financial Summary</h2>`);
document.write(`<p><strong>Account:</strong> ${name}</p>`);
document.write(`<p><strong>Total Income:</strong> $${income}</p>`);
document.write(`<p><strong>Total Expenses:</strong> $${expenses}</p>`);

// Using our calculated balance
document.write(`<h3>Remaining Balance: $${currentBalance}</h3>`);
```

---

### Key Takeaways for Hour 8

*   **Objects `{}`** store data in Key-Value pairs.
*   Use **Dot Notation** (`user.name`) most of the time; use **Bracket Notation** (`user["name"]`) for dynamic keys.
*   **Methods** are functions attached to objects.
*   **`this`** refers to the object itself from inside a method.
*   **Arrays of Objects** are the standard way to represent lists of complex data.
*   **Destructuring** `{ key } = object` easily unpacks variables.
*   **Spread Operator** `...` copies and merges arrays/objects effortlessly.

---

### Next Time...

**Coming Up in Hour 9: DOM Manipulation & Events**

We've been using `document.write()` as a crutch, but it's dangerous (it overwrites the whole page!). 

Now that we understand Arrays, Objects, and Methods, we are finally ready to interact with the web page the *right* way.

*   Selecting elements (`getElementById`, `querySelector`).
*   Changing styles and text dynamically.
*   Listening for user clicks and inputs (Events).
