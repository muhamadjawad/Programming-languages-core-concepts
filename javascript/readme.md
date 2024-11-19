# 🚀 JavaScript Core Concepts

Welcome to the **JavaScript Core Concepts** section! This is your go-to guide for understanding key JavaScript concepts. This file is meant to grow with time, so feel free to add more concepts as you learn. 

## 📜 Topics Covered

### 🌍 Scope
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

### ✨ IIFE (Immediately Invoked Function Expression):


IIFEs are functions that execute immediately after they are defined. They help to prevent global scope pollution by encapsulating variables.

    ```bash
    (function() {
    let privateVariable = "I live in an IIFE!";
    console.log(privateVariable); // ✅ Accessible inside
    })();
    console.log(privateVariable); // ❌ ReferenceError
    ```

### ⬆️ Hoisting

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
