## 📘 JavaScript Notes by Ayush Prem

### 1. **Basics: Word vs Keyword**

* **Word**: Any string of characters used in the language (like `hello`, `apple`).
* **Keyword**: A reserved word in JavaScript that has special meaning and functionality (e.g., `var`, `if`, `function`).

---

### 2. **Variables: `var`, `let`, `const`**

* **`var`**: Introduced in ES5, function-scoped, allows redeclaration, and adds to the `window` object.
* **`let`**: Introduced in ES6, block-scoped, does not allow redeclaration, and does not attach to `window`.
* **`const`**: Also ES6, block-scoped, used for constants (values that don’t change).

> ❗ `const` means the *reference* cannot change, not the content (e.g., array/object content can still be modified).

---

### 3. **Hoisting**

* **Definition**: JavaScript moves declarations to the top of the scope before code execution.
* Variables declared with `var` are hoisted and initialized as `undefined`.
* Functions are hoisted with their full definitions.
* `let` and `const` are hoisted but not initialized (temporal dead zone).

---

### 4. **Data Types**

#### ✅ Primitive Types

* Examples: `String`, `Number`, `Boolean`, `null`, `undefined`, `Symbol`, `BigInt`
* Copied by value.

#### ✅ Reference Types

* Examples: `Object`, `Array`, `Function`
* Copied by reference (changes affect the original).

---

### 5. **Conditionals**

```js
if (condition) {
   // code
} else if (condition) {
   // code
} else {
   // code
}
```

---

### 6. **Loops**

#### For Loop

```js
for(let i = 0; i < 10; i++) {
    console.log(i);
}
```

#### While Loop

```js
while(condition) {
   // code
}
```

#### Do While Loop

```js
do {
   // code
} while(condition);
```

---

### 7. **Functions**

* Used for code reuse and deferred execution.

```js
function greet(name) {
    console.log("Hello, " + name);
}
greet("Ayush");
```

---

### 8. **Array Methods**

```js
let arr = [1, 2, 3, 4, 5];
arr.push(6);      // Add to end
arr.pop();        // Remove from end
arr.unshift(0);   // Add to start
arr.shift();      // Remove from start
arr.splice(2, 1); // Remove from specific index
```

---

### 9. **Objects**

```js
let person = {
    name: "Ayush Prem",
    age: 21
};
```

* Use objects to group related data (like a user's details).

---

### 10. **Window Object**

* JavaScript in the browser can access the global `window` object.
* Example: `alert()`, `console`, `setTimeout()` are part of the `window` object.

---

### 11. **Browser Context API**

* **Components**:

  * **Window**: Global environment.
  * **Call Stack**: Executes functions (LIFO).
  * **Heap**: Stores memory like variables and objects.

---

### 12. **Execution Context**

Whenever a function runs, a new execution context is created containing:

1. Variables
2. Inner Functions
3. Lexical Environment

---

### 13. **Lexical Environment**

* A scope chart that determines what a function can access.
* Every function remembers the scope in which it was created (scope chain).

---

### 14. **Copying Reference Values**

```js
let a = [1, 2, 3];
let b = [...a]; // Creates a shallow copy
b.pop(); // Does not affect `a`
```

---

### 15. **Truthy & Falsy Values**

#### Falsy:

* `0`, `false`, `""`, `null`, `undefined`, `NaN`, `document.all`

#### Truthy:

* Everything else (e.g., `[]`, `{}`, `"0"`, `true`)

---

### 16. **Switch Statement**

```js
switch(value) {
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // default code
}
```

---

### 17. **Loops on Objects**

```js
let obj = {
    name: "Ayush",
    age: 21,
    city: "Chandigarh"
};

for(let key in obj) {
    console.log(key, obj[key]);
}
```

---

### 18. **Callback Functions**

* A function passed as an argument to another function and invoked later.

```js
function greet(callback) {
    callback();
}
greet(() => console.log("Hello"));
```

---

### 19. **First-Class Functions**

* Functions in JavaScript can be:

  * Stored in variables
  * Passed as arguments
  * Returned from other functions

```js
function executor(fn) {
    fn();
}
executor(() => console.log("I’m a first-class function"));
```

---

### 20. **Higher-Order Functions**

* Functions that accept other functions or return them.

```js
function higherOrder(callback) {
    return function() {
        console.log("Inside returned function");
        callback();
    }
}
```

---

### 21. **Constructor Function**

```js
function Person(name, age) {
    this.name = name;
    this.age = age;
}
let p1 = new Person("Ayush", 21);
```

---

### 22. **The `new` Keyword**

* Creates a blank object
* Sets `this` to that object
* Returns the object implicitly

---

### 23. **IIFE (Immediately Invoked Function Expression)**

* Executes as soon as it's defined
* Used to create private variables

```js
(function() {
    console.log("IIFE ran");
})();
```

---

### 24. **Prototype**

* Every object has a hidden `[[Prototype]]` (or `__proto__`) which links to another object.

---

### 25. **Prototype Inheritance**

```js
let human = {
    canTalk: true,
    canWalk: true
};

let ayush = {
    canCode: true
};

ayush.__proto__ = human;
console.log(ayush.canTalk); // true
```

---

### **26. `this` Keyword**

**Definition**:
`this` refers to the object from which the current function is called.

#### 🧠 Behavior in Different Contexts:

* **Global Scope**:

  ```js
  console.log(this); // window (in browsers)
  ```

* **Function Scope**:

  ```js
  function abcd() {
      console.log(this); // window
  }
  abcd();
  ```

* **Method Scope**:

  ```js
  var obj = {
      name: "Ayush",
      someMethod: function () {
          console.log(this); // obj
      }
  };
  obj.someMethod();
  ```

* **Event Listener**:

  ```js
  var button = document.querySelector("button");
  button.addEventListener("click", function () {
      console.log(this); // button element
  });
  ```

> 💡 In a method, `this` refers to the parent object.
> In an event listener, it refers to the element that received the event.

---

### **27. `call`, `apply`, `bind`**

Used to manually set the value of `this` when calling a function.

#### ✅ `call()`

```js
function abcd() {
    console.log(this.age);
}
var obj = { age: 24 };
abcd.call(obj);
```

#### ✅ `apply()`

```js
function abcd(val1, val2, val3) {
    console.log(this, val1, val2, val3);
}
abcd.apply({ age: 24 }, [1, 2, 3]);
```

#### ✅ `bind()`

```js
function abcd() {
    console.log(this);
}
var obj = { age: 24 };
var bindedFunc = abcd.bind(obj);
bindedFunc();
```

---

### **28. Pure and Impure Functions**

#### ✅ Pure Functions

* Same input → same output
* No side effects (doesn't modify global state)

#### ❌ Impure Functions

* May return different results for same input
* Can alter external or global data

---

### **29. Synchronous vs Asynchronous JavaScript**

#### 🔹 Synchronous (Sync)

* One task runs at a time
* Blocking behavior

#### 🔹 Asynchronous (Async)

* Tasks start independently
* Non-blocking — responses are handled as they arrive

---

### **30. Async JS Examples**

#### **Tools to Send Requests**:

* `setTimeout`
* `setInterval`
* `fetch`
* `axios`
* `XMLHttpRequest`

#### **Tools to Handle Responses**:

* `.then()`
* `.catch()`
* `callback()`
* `async/await`

> 🔄 Use async code when results depend on external systems (like servers or APIs) and you don’t want the UI to freeze.

---

### **31. Callback Functions**

A callback is a function passed as an argument and executed after an async operation.

```js
function loadData(callback) {
    setTimeout(() => {
        callback("Data loaded");
    }, 1000);
}

loadData(function (data) {
    console.log(data); // "Data loaded"
});
```

---

### **32. Promises**

A way to handle asynchronous operations.

#### ✅ States:

* `Pending`
* `Resolved`
* `Rejected`

#### ✅ Example:

```js
var ans = new Promise(function (res, rej) {
    var n = Math.floor(Math.random() * 10);
    if (n < 5) res();
    else rej();
});

ans.then(function () {
    console.log("Number is below 5");
}).catch(function () {
    console.log("Number is 5 or above");
});
```

---

### **33. `async` / `await`**

Syntactic sugar over Promises to write async code in a cleaner way.

```js
async function fetchData() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}
```

---

### **34. Real Use Cases of Async JavaScript**

* Database operations in Node.js
* API requests with `fetch` or `axios`
* Timers (`setTimeout`, `setInterval`)
* Any third-party services

---

### **35. Concurrency vs Parallelism**

* **Concurrency**: Managing multiple async tasks at once (even if one thread).
* **Parallelism**: Executing multiple tasks literally at the same time using multiple CPU cores.

---

### **36. Throttling**

**Definition**:
A technique to control the frequency of function execution (especially in scroll, resize, or input events).

---

### **37. DOM (Document Object Model)**

DOM is the structured representation of an HTML document as a tree of objects.

#### 📍 Four Pillars of DOM:

1. **Selecting an Element**

   ```js
   var a = document.querySelector("h1");
   ```

2. **Changing HTML Content**

   ```js
   a.innerHTML = "Changed HTML";
   ```

3. **Changing CSS Styles**

   ```js
   a.style.color = "red";
   a.style.backgroundColor = "blue";
   ```

4. **Adding Event Listeners**

   ```js
   a.addEventListener("click", function () {
       console.log("Hey!");
   });
   ```

---

