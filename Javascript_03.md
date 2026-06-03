# Higher Order Function (HOF) in JavaScript

## Definition

Higher Order Function (HOF) wo function hota hai jo:

1. Ek ya ek se jyada functions ko argument ke roop me accept karta hai.
2. Ya phir ek function return karta hai.

Simple words me:

> Agar koi function kisi dusre function ke saath kaam karta hai (argument ya return value ke roop me), to use Higher Order Function kehte hain.

---

## Example 1: Function as Argument

```javascript
function greet(name) {
    return "Hello " + name;
}

function processUser(callback) {
    console.log(callback("Bittu"));
}

processUser(greet);
```

### Output

```javascript
Hello Bittu
```

Yaha `processUser()` ek Higher Order Function hai kyunki ye `greet` function ko argument ke roop me receive kar raha hai.

---

## Example 2: Function Returning Function

```javascript
function multiplyBy(num) {
    return function (value) {
        return value * num;
    };
}

const double = multiplyBy(2);

console.log(double(5));
```

### Output

```javascript
10
```

Yaha `multiplyBy()` ek Higher Order Function hai kyunki ye ek function return kar raha hai.

---

## Common Higher Order Functions in JavaScript

### map()

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(num => num * 2);

console.log(result);
```

Output:

```javascript
[2, 4, 6]
```

---

### filter()

```javascript
const numbers = [1, 2, 3, 4, 5];

const even = numbers.filter(num => num % 2 === 0);

console.log(even);
```

Output:

```javascript
[2, 4]
```

---

### reduce()

```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((acc, curr) => acc + curr, 0);

console.log(sum);
```

Output:

```javascript
10
```

---

## Why Use Higher Order Functions?

- Code ko reusable banata hai.
- Code duplication kam karta hai.
- Readability improve karta hai.
- Functional Programming ko support karta hai.
- Complex logic ko simple banata hai.

---

## Important Interview Points

- JavaScript me functions first-class citizens hote hain.
- Isliye functions ko variables me store, arguments me pass aur return kiya ja sakta hai.
- Higher Order Functions isi feature ka use karte hain.
- `map()`, `filter()`, `reduce()`, `forEach()` sab Higher Order Functions ke examples hain.

---

## Interview Answer (Short)

Higher Order Function wo function hota hai jo kisi function ko argument ke roop me accept karta hai ya ek function return karta hai. JavaScript me `map()`, `filter()`, `reduce()` aur `forEach()` common Higher Order Functions hain.

# Lexical Environment

Lexical Environment ek hidden structure hota hai jo JavaScript har function ke liye create karti hai.

Isme 2 cheeze hoti hain:

1. Function ke variables
2. Outer scope ka reference

Simple words me:

> JavaScript function ko yaad rehta hai ki wo kis scope me create hua tha.

Example:

```javascript
let a = 10;

function test() {
    console.log(a);
}

test();
```

Yaha `test()` ke andar `a` nahi hai, fir bhi access ho gaya kyuki JavaScript ko yaad hai ki function kis scope me bana tha.

---

# Closure

Closure tab banta hai jab ek function apne outer function ke variables ko access karta hai aur unhe yaad rakhta hai, even after outer function execute ho chuka ho.

Simple words me:

> Closure = Function + Uska Lexical Environment

Example:

```javascript
function outer() {
    let count = 0;

    return function () {
        count++;
        console.log(count);
    };
}

const counter = outer();

counter(); // 1
counter(); // 2
```

Yaha `outer()` execute hone ke baad bhi `count` variable memory me bana hua hai, kyuki inner function usko use kar raha hai.

Isi behavior ko Closure kehte hain.

---

# Difference

| Lexical Environment | Closure |
|----------|----------|
| Variables aur outer scope ka reference store karta hai | Function + Lexical Environment |
| Har function ke saath hota hai | Jab function outer variables ko yaad rakhe tab banta hai |
| Scope provide karta hai | Variables ko preserve rakhta hai |

---

# Interview Answer

Lexical Environment ek hidden structure hota hai jo variables aur outer scope ka reference store karta hai. Closure tab banta hai jab koi function apne outer function ke variables ko outer function ke execute hone ke baad bhi access kar sakta hai. Closure ko "Function + Lexical Environment" bhi kehte hain.

# JavaScript Browser Me Internally Kaise Kaam Karti Hai?

## Overview

Jab browser JavaScript code ko dekhta hai, to wo code ko directly execute nahi karta.

JavaScript Engine (V8, SpiderMonkey, JavaScriptCore, etc.) code ko process karke execute karti hai.

Flow:

```text
JavaScript Code
      ↓
Parser
      ↓
AST (Abstract Syntax Tree)
      ↓
Compilation
      ↓
Machine Code
      ↓
Execution
```

---

# 1. Parser

Parser code ko read karta hai aur check karta hai ki syntax sahi hai ya nahi.

Example:

```javascript
let a = 10;
```

Agar syntax galat hua:

```javascript
let a =
```

To parser error throw kar dega.

---

# 2. AST (Abstract Syntax Tree)

Parser code ko ek tree structure me convert karta hai.

Example:

```javascript
let a = 10;
```

Internally kuch aisa structure banta hai:

```text
VariableDeclaration
    |
    a = 10
```

JavaScript Engine isi structure ko samajh kar aage process karti hai.

---

# 3. Compilation

Modern JavaScript Engines (jaise V8) code ko compile karti hain.

Ye code ko machine code me convert karti hain jise CPU samajh sake.

---

# 4. Execution Context Creation

Code execute hone se pehle JavaScript Memory allocate karti hai.

Example:

```javascript
var a = 10;

function test() {
    console.log("Hello");
}
```

Memory Phase:

```javascript
a = undefined
test = function
```

Is phase ko Hoisting bhi kehte hain.

---

# 5. Code Execution Phase

Ab line by line code execute hota hai.

```javascript
var a = 10;
```

Ab:

```javascript
a = 10
```

store ho jata hai.

---

# JavaScript Engine Ke Main Components

## Memory Heap

Variables aur Objects yaha store hote hain.

```javascript
const user = {
    name: "Bittu"
};
```

Object Heap Memory me store hoga.

---

## Call Stack

Function calls ko manage karta hai.

Example:

```javascript
function one() {
    two();
}

function two() {
    console.log("Hello");
}

one();
```

Stack:

```text
Call Stack

one()
two()
console.log()
```

Execution complete hone par functions stack se remove hote jate hain.

---

# JavaScript Single Threaded Hai

JavaScript ke paas sirf ek Call Stack hoti hai.

Matlab:

```text
Ek time par ek hi kaam
```

kar sakti hai.

Example:

```javascript
console.log("A");
console.log("B");
console.log("C");
```

Output:

```javascript
A
B
C
```

Line by line execute hoga.

---

# Fir Asynchronous Kaise Kaam Karta Hai?

Browser additional features provide karta hai:

- Web APIs
- Callback Queue
- Event Loop

Example:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 2000);

console.log("End");
```

Output:

```javascript
Start
End
Timer
```

Kyuki `setTimeout()` browser ke Web API me chala jata hai.

Timer complete hone ke baad callback Queue me aata hai.

Event Loop check karta hai ki Call Stack empty hai ya nahi.

Jab Stack empty hoti hai tab callback execute hota hai.

---

# Important Components

```text
JavaScript Engine
    |
    ├── Memory Heap
    └── Call Stack

Browser
    |
    ├── Web APIs
    ├── Callback Queue
    └── Event Loop
```

---

# Interview Answer

Browser me JavaScript Engine code ko parse, compile aur execute karti hai. Execution ke dauran variables Memory Heap me aur function calls Call Stack me store hote hain. JavaScript single-threaded language hai, isliye ek time par ek hi task execute karti hai. Asynchronous operations ko handle karne ke liye browser Web APIs, Callback Queue aur Event Loop ka use karta hai.

# Difference Between Async and Defer in JavaScript

`async` aur `defer` dono `<script>` tag ke attributes hain jo browser ko batate hain ki JavaScript file ko kaise load aur execute karna hai.

---

# Problem Without Async/Defer

```html
<script src="app.js"></script>
```

Browser Flow:

```text
HTML Parsing
    ↓
Script Download
    ↓
Script Execute
    ↓
HTML Parsing Continue
```

Yaha browser HTML parsing ko rok deta hai jab tak script download aur execute na ho jaye.

Isse page slow ho sakta hai.

---

# Async

```html
<script async src="app.js"></script>
```

## Kaise Kaam Karta Hai?

```text
HTML Parsing
      ↓
Script Download (Parallel)
      ↓
Script Ready Hote Hi Execute
      ↓
HTML Parsing Continue
```

### Important Point

- HTML parsing aur script downloading saath-saath hoti hai.
- Jaise hi script download ho jati hai, browser parsing rok kar script execute kar deta hai.
- Multiple async scripts ka execution order guarantee nahi hota.

Example:

```html
<script async src="a.js"></script>
<script async src="b.js"></script>
```

Output ho sakta hai:

```text
b.js
a.js
```

ya

```text
a.js
b.js
```

Depends kiski download speed fast hai.

---

# Defer

```html
<script defer src="app.js"></script>
```

## Kaise Kaam Karta Hai?

```text
HTML Parsing
      ↓
Script Download (Parallel)
      ↓
HTML Parsing Complete
      ↓
Script Execute
```

### Important Point

- HTML parsing kabhi nahi rukti.
- Script download parallel me hoti hai.
- Script execution tab hota hai jab pura HTML parse ho jaye.
- Multiple defer scripts ka order maintain rehta hai.

Example:

```html
<script defer src="a.js"></script>
<script defer src="b.js"></script>
```

Output hamesha:

```text
a.js
b.js
```

---

# Difference Table

| Async | Defer |
|---------|---------|
| Download parallel me hota hai | Download parallel me hota hai |
| Download complete hote hi execute hota hai | HTML parsing complete hone ke baad execute hota hai |
| HTML parsing temporarily stop ho sakti hai | HTML parsing kabhi stop nahi hoti |
| Execution order guarantee nahi hota | Execution order maintain rehta hai |
| Independent scripts ke liye best | DOM dependent scripts ke liye best |

---

# Kab Use Kare?

## Async

Jab script kisi dusri script par depend na ho.

Examples:

- Analytics
- Ads
- Tracking Scripts

```html
<script async src="analytics.js"></script>
```

---

## Defer

Jab script DOM ya dusri scripts par depend karti ho.

Examples:

- Main Application JS
- DOM Manipulation

```html
<script defer src="main.js"></script>
```

---

# Interview Answer

`async` aur `defer` dono scripts ko parallel download karte hain. Difference ye hai ki `async` script download hote hi execute ho jati hai aur execution order guarantee nahi hota, jabki `defer` script HTML parsing complete hone ke baad execute hoti hai aur execution order maintain rehta hai. Isliye DOM dependent scripts ke liye `defer` preferred hota hai.

# Async / Await in JavaScript

## Introduction

`async` aur `await` JavaScript me asynchronous code ko likhne ka modern aur easy tarika hai.

Ye internally **Promises** ke upar hi kaam karte hain, lekin code ko synchronous jaisa readable bana dete hain.

---

# Async Function

Jis function ke aage `async` likha hota hai, wo hamesha ek Promise return karta hai.

Example:

```javascript
async function greet() {
    return "Hello";
}

console.log(greet());
```

Output:

```javascript
Promise { "Hello" }
```

Yaha `"Hello"` return hua, lekin JavaScript ne automatically usse Promise me wrap kar diya.

---

# Await Keyword

`await` kisi Promise ke resolve hone ka wait karta hai.

Important:

> `await` sirf `async` function ke andar hi use kiya ja sakta hai.

Example:

```javascript
async function getData() {
    let result = await Promise.resolve("Data Received");

    console.log(result);
}

getData();
```

Output:

```javascript
Data Received
```

---

# Real Example

Without Async/Await:

```javascript
fetch("/api/users")
    .then(response => response.json())
    .then(data => {
        console.log(data);
    });
```

With Async/Await:

```javascript
async function getUsers() {
    const response = await fetch("/api/users");
    const data = await response.json();

    console.log(data);
}
```

Same kaam ho raha hai, lekin code jyada clean aur readable hai.

---

# Async/Await Ka Flow

Example:

```javascript
async function demo() {
    console.log("Start");

    await new Promise(resolve =>
        setTimeout(resolve, 2000)
    );

    console.log("End");
}

demo();
```

Output:

```javascript
Start
End
```

### Kya Hua?

1. Function start hua.
2. `await` par Promise ka wait hua.
3. JavaScript ne function ko temporarily pause kar diya.
4. Baaki code/Event Loop kaam karta raha.
5. Promise resolve hone ke baad execution continue hua.

---

# Error Handling

Async/Await ke saath `try...catch` use karte hain.

```javascript
async function getData() {
    try {
        const response = await fetch("wrong-url");
        const data = await response.json();

        console.log(data);
    } catch (error) {
        console.log("Error:", error);
    }
}
```

---

# Advantages

- Code readable hota hai.
- Promise chaining kam ho jati hai.
- Error handling easy ho jati hai.
- Complex asynchronous code simple lagta hai.

---

# Difference Between Promise and Async/Await

| Promise (.then) | Async/Await |
|----------|----------|
| `.then()` use hota hai | `await` use hota hai |
| Code nesting ho sakti hai | Code clean hota hai |
| Readability kam hoti hai | Readability better hoti hai |
| Error handling `.catch()` se | `try...catch` se |

---

# Important Interview Points

- `async` function hamesha Promise return karta hai.
- `await` Promise ke resolve hone ka wait karta hai.
- `await` sirf `async` function ke andar use ho sakta hai.
- Async/Await Promise ka hi syntactic sugar hai.
- Async/Await asynchronous code ko synchronous jaisa dikhata hai.

---

# Interview Answer

`async` aur `await` JavaScript me asynchronous operations handle karne ka modern tarika hai. `async` function hamesha Promise return karta hai aur `await` Promise ke resolve hone tak execution ko pause karta hai. Ye Promise-based code ko jyada readable aur maintainable bana deta hai.