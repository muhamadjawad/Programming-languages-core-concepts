# 🚀 JavaScript Core Concepts

Welcome to the **JavaScript Core Concepts** section! This is your go-to guide for understanding key JavaScript concepts. This file is meant to grow with time, so feel free to add more concepts as you learn. 

## 📜 Topics Covered

### 1. 🌍 Scope
- **Block Scope**: `{}`  
    Variables declared with `let` and `const` are block-scoped, meaning they are only accessible within the block they are defined in.
    ```bash
    {
        let blockVariable = "I'm block scoped!";
        const anotherBlockVariable = "Me too!";
        console.log(blockVariable); // ✅ Works!
    }
    console.log(blockVariable); // ❌ ReferenceError
    ```

- **Global Scope**: `var`
    Variables declared with var have global or function scope and can lead to pollution of the global namespace.

    ```bash
    var globalVariable = "I'm globally accessible!";
    console.log(globalVariable); // ✅ Works anywhere!
    ```

### 2. ✨ IIFE (Immediately Invoked Function Expression):


IIFEs are functions that execute immediately after they are defined. They help to prevent global scope pollution by encapsulating variables.

    ```bash
    (function() {
    let privateVariable = "I live in an IIFE!";
    console.log(privateVariable); // ✅ Accessible inside
    })();
    console.log(privateVariable); // ❌ ReferenceError
    ```

### 3. ⬆️ Hoisting

- **Functions**: Can be called even before they are defined.

    ```bash
    sayHello(); // ✅ Works!
    function sayHello() {
        console.log("Hello, Hoisting!");
    }
    ```

- **Variables with var**: Declared variables are "hoisted" but not initialized.

    ```bash
    console.log(a); // undefined
    var a = 5;
    ```

- **Variables with let or const**: Will throw a ReferenceError if accessed before declaration.

    ```bash
    console.log(b); // ❌ ReferenceError
    let b = 10;
    ```

### 4. Closures

A **closure** is a function inside another function that has access to the outer function's variables. Closures have three scope chains:

- Access to their own scope (variables defined within their curly brackets).
- Access to the outer function's variables.
- Access to global variables.

    **Example:**

    ```bash
    function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log(`Outer Variable: ${outerVariable}`);
        console.log(`Inner Variable: ${innerVariable}`);
    };
    }

    const newFunction = outerFunction("Outer");
    newFunction("Inner");
    // Output:
    // Outer Variable: Outer
    // Inner Variable: Inner
    ```

### 5. Callbacks

In JavaScript, a **callback** is a function passed as a parameter to another function. It allows functions to call another function once an operation is completed.
    
  **Example:**
  ```bash
  function processData(data, callback) {
  console.log("Processing data...");
  callback(data);
  }

  function printData(data) {
  console.log(`Data: ${data}`);
  }

  processData("Hello, World!", printData);
  # Output:
  # Processing data...
  # Data: Hello, World!
  ```

  - **Callback Hell** occurs when callbacks are nested inside other callbacks multiple times, leading to code that is difficult to read and maintain. This often happens in asynchronous operations where one operation depends on the result of the previous one.

    **Example of Callback Hell:**
    ```bash
    function step1(data, callback) {
    console.log("Step 1:", data);
    callback(data + 1);
    }

    function step2(data, callback) {
    console.log("Step 2:", data);
    callback(data + 1);
    }

    function step3(data, callback) {
    console.log("Step 3:", data);
    callback(data + 1);
    }

    # Nested callbacks causing "callback hell"
    step1(1, (data) => {
    step2(data, (data) => {
        step3(data, (data) => {
        console.log("Done:", data);
        });
    });
    });

    # Output:
    # Step 1: 1
    # Step 2: 2
    # Step 3: 3
    # Done: 4
    ```


### 6. Promises, .then(), async/await

- **Promises**  
  A **Promise** is an object representing the eventual completion (or failure) of an asynchronous operation. It can be in one of three states: pending, fulfilled, or rejected.

- **.then()**  
  The `.then()` method is used to handle the fulfillment (success) or rejection (failure) of a promise. It returns a new promise, enabling chaining.

  ```bash
  promise.then(result => {
    console.log(result);  // Success
  }).catch(error => {
    console.error(error); // Error
  });
  ```

- **.async/await**  
  `async` defines a function that always returns a promise, and await pauses the execution of the function until the promise is resolved or rejected.

  ```bash
  async function fetchData() {
  const data = await someAsyncFunction();
  console.log(data);
  }
  ```
