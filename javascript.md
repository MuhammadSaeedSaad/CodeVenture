# Javascript

## General
1. weakely typed language.
2. Object-oriented language.
   1. has primitive and reference types.
3. Versatile language (can be ran on many platforms i.e. Browsers, PC, servers, ...).

## Object-Oriented
1. In a Key-value pair key can also be called property or field.

## Leetcode quizs

1. [Create Hello World Function](https://leetcode.com/problems/create-hello-world-function/description/).

---

## Functions

### General
1. pure functions.

### 1. normal

```javascript
function f(a, b) {
  const sum = a + b;
  return sum;
}
console.log(f(3, 4)); // 7
```

### 2. Anonymous

```javascript
var f = function (a, b) {
  const sum = a + b;
  return sum;
};
console.log(f(3, 4)); // 7
```

### 3. Immediately Invoked Function Expression (IIFE)

```js
const result = (function (a, b) {
  const sum = a + b;
  return sum;
})(3, 4);
console.log(result); // 7
```

### 4. Functions within functions

```js
function createFunction() {
  function f(a, b) {
    const sum = a + b;
    return sum;
  }
  return f;
}
const f = createFunction();
console.log(f(3, 4)); // 7
```

### 5. Function Hoisting

```js
function createFunction() {
  return f;
  function f(a, b) {
    const sum = a + b;
    return sum;
  }
}
const f = createFunction();
console.log(f(3, 4)); // 7
```

### 6. Closures

```js
function createAdder(a) {
  function f(b) {
    const sum = a + b;
    return sum;
  }
  return f;
}
const f = createAdder(3);
console.log(f(4)); // 7
```

### 7. Arror Syntax

1. basic

```js
const f = (a, b) => {
  const sum = a + b;
  return sum;
};
console.log(f(3, 4)); // 7
```

2. Shorthand

```js
const f = (a, b) => a + b;
console.log(f(3, 4)); // 7
```

#### differences between arrow syntax and function syntax

1. More minimalistic syntax. This is especially true for anonymous functions and single-line functions. For this reason, this way is generally preferred when passing short anonymous functions to other functions.
2. No automatic hoisting. You are only allowed to use the function after it was declared. This is generally considered a good thing for readability.

```js
// won't work
// will generate the Error: Cannot access 'f' before initialization
function createFunction() {
  return f;
  const f = (a, b) => a + b;
}

const f1 = createFunction();
console.log(f1(3, 4));
```

3. Can't be bound to this, super, and arguments or be used as a constructor. These are all complex topics in themselves but the basic takeaway should be that arrow functions are simpler in their feature set.

## Research
1. IIFE and its benefits
2. Factory functions.
