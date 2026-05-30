# What is the difference between null and undefined?

#### Null:

* Null ek intentional value hoti hai, jo dikhata hai ki kisi variable ki value khaali hai.

* Ye developer ke dwara manually assign hoti hai.

* Null ek object type hota hai.


```python
let x = null;
console.log(x); // null
```

#### Undefined:

* Undefined ka matlab hai ki variable declare toh kiya gaya hai, lekin usme koi value assign nahi hui.

* Ye JavaScript ke dwara automatically diya jata hai agar variable ki value na ho.

* Undefined ek undefined type hota hai.




```python
let y;
console.log(y); // undefined
```

#### Key Difference:
Null: "Khaali value", jo developer assign karta hai.

Undefined: "Value nahi hai", jo JavaScript assign karta hai.


```python
let a = null;       // Developer ne khaali kiya
let b;              // Value assign nahi hui
console.log(a);     // null
console.log(b);     // undefined
```

# What is the event loop in JavaScript?

JavaScript ek single-threaded language hai, iska matlab ek waqt me sirf ek hi kaam execute kar sakti hai. Event loop is cheez ko manage karta hai ki kab synchronous code run kare aur kab asynchronous code ko handle kare.



### Event Loop Kaise Kaam Karta Hai?
#### Call Stack:

Synchronous code (jaise functions) yahan execute hote hain.

Agar koi function execute hota hai, toh wo stack me push hota hai, aur jab wo complete hota hai toh stack se pop ho jata hai.

#### Web APIs:

JavaScript ke asynchronous kaam (jaise setTimeout, HTTP requests, DOM events) browser APIs ya Node.js APIs ke through handle hote hain.

Jab ye kaam complete hota hai, toh result Callback Queue me bhej diya jata hai.

#### Callback Queue:

Asynchronous tasks (jaise setTimeout ka callback) queue me wait karte hain jab tak call stack khaali nahi ho jata.

#### Event Loop:

Event loop continuously check karta hai:

Kya call stack khaali hai?

Agar haan, toh callback queue se kaam uthake call stack me execute kar deta hai.


```python
console.log("Start");

setTimeout(() => {
  console.log("Inside setTimeout");
}, 1000);

console.log("End");
```

* "Start" console pe print hoga (synchronous), kyunki ye call stack me turant execute hota hai.

* setTimeout browser API ko call karega, aur iska callback (1 second ke baad) callback queue me bheja jayega.

* "End" console pe print hoga (synchronous).

* Event loop check karega ki call stack khaali hai, tab callback queue se "Inside setTimeout" ka callback uthake execute karega.

# What are ES6 features, and how do they differ from ES5?

### ES6 Features (Naye Updates):

1. Block-Scoped Variables (let aur const)
* let aur const block-level scoping dete hain.
* let: Mutable (change ho sakta hai).
* const: Immutable (fix value, change nahi hota).
* ES5: Sirf var tha, jo function-level scoped hota hai.

2. Arrow Functions
* Ek concise aur chhoti syntax functions likhne ke liye.
* this ka context automatically bind hota hai.
* ES5: Normal function syntax use hota tha.

3. Template Literals
* Strings ke liye backticks (`) use karte hain.
* Multi-line strings aur interpolation easy ho jata hai.
* ES5: String concatenate karte the.

4. Default Parameters
* Function ke parameters ke liye default value set kar sakte hain.
* ES5: Manually default set karte the.

5. Destructuring Assignment
* Arrays aur objects ke values ko alag-alag variables me assign karte hain.
* ES5: Properties manually access karte the.

6. Spread aur Rest Operators (...)
* Spread: Array ya object expand karta hai.
* Rest: Remaining elements ko ek array me collect karta hai.

7. Modules (import aur export)
* Code ko alag-alag modules me todte hain.
* ES5: CommonJS ka require use karte the.

8. Classes
* Objects aur inheritance ke liye ek clean syntax.
* ES5: Prototype-based inheritance.



| Feature            | ES5                    | ES6                                |
| ------------------ | ---------------------- | ---------------------------------- |
| **Variables**      | `var`                  | `let` aur `const`                  |
| **Functions**      | Normal function syntax | Arrow functions aur default params |
| **Strings**        | Concatenation with `+` | Template literals                  |
| **Modules**        | CommonJS (`require`)   | Native `import/export`             |
| **Async Code**     | Callback functions     | Promises aur `async/await`         |
| **Classes**        | Prototype-based        | Class syntax                       |
| **New Structures** | Objects, Arrays        | Map, Set                           |


# What are limitations of arrow functions in javascript ?


1. Fixed this Binding:

Arrow functions ka this hamesha apne surrounding (lexical) context se bind hota hai. Iska matlab hai ki ye this dynamically bind nahi hota, jo kuch scenarios me problematic ho sakta hai, jaise objects ke methods ya event handlers me.

2. No arguments Object:

Arrow functions me arguments object nahi hota. Agar aapko dynamic arguments handle karne hain, to arrow functions use nahi kar sakte.

3. Constructor ke Liye Nahi:

Arrow functions ko constructors ke roop me use nahi kiya ja sakta, kyunki inke paas prototype nahi hota. Isliye, agar aapko object instantiate karna ho, to normal function ya ES6 class ka use zaroori hai.

4. Event Handlers me Issues:

Event handlers me this ka reference element ke bajaye parent scope ko point karta hai, jo galat behavior de sakta hai. Agar this ka reference DOM element ke liye chahiye, to arrow functions use nahi karne chahiye.

5. Complex Logic me Kam Readable:

Arrow functions concise syntax ke liye bane hain, lekin agar function ka logic complex ho, to ye readability ko reduce kar sakte hain. Aise cases me traditional function better choice hota hai.

6. Line Break Restrictions:

Arrow functions syntax me line breaks directly allowed nahi hote, jo kabhi-kabhi syntax error create kar sakte hain.

# How do Modules work in JS?


#### Named Exports and Imports


```python
// Exporting Module (math.js):

// Named exports
export const add = (a, b) => a + b;
export const multiply = (a, b) => a * b;
```


```python
// Importing Module (app.js):

// Named imports
import { add, multiply } from './math.js';

console.log(add(5, 3));       // Output: 8
console.log(multiply(5, 3));  // Output: 15
```

####  Default Export and Import


```python
// Exporting Module (greet.js):


// Default export
export default function greet(name) {
  return `Hello, ${name}!`;
}

// Importing Module (app.js):

// Default import
import greet from './greet.js';

console.log(greet('John')); // Output: Hello, John!
```

#### Combined Export and Import


```python
// Exporting Module (math.js):


// Named and default exports together
export const subtract = (a, b) => a - b;

export default function divide(a, b) {
  return a / b;
}
// Importing Module (app.js):


// Import default and named exports together
import divide, { subtract } from './math.js';

console.log(divide(10, 2));   // Output: 5
console.log(subtract(10, 2)); // Output: 8
```

####  Dynamic Imports (Lazy Loading)
Dynamic imports runtime par module ko load karte hain, jo performance ko optimize karta hai.


```python
setTimeout(async () => {
  const { add } = await import('./math.js');
  console.log(add(10, 20)); // Output: 30
}, 2000);

```

# What is call by value vs call by reference?


#### Call by Value
1. Definition:
* Jab variable ki actual value ko ek copy ke roop me function me pass kiya jata hai, to ise call by value kehte hain.
* Function ke andar ki changes original variable ko affect nahi karte.

2. Primitive Types:
* JavaScript me primitive types (e.g., number, string, boolean) call by value ke saath pass hote hain.

3. Example:
* Ek nayi copy banti hai, aur agar function ke andar changes hote hain, to wo sirf copy me hoti hai.
* Original variable ki value intact rehti hai.


```python
let x = 10;

function modifyValue(y) {
  y = 20; // Changes y (copy), not x
}

modifyValue(x);
console.log(x); // Output: 10

```

#### Call by Reference

1. Definition:
* Jab variable ka memory reference pass hota hai, to ise call by reference kehte hain.
* Function ke andar ki changes directly original variable ko affect karte hain.

2. Non-Primitive Types:
* Objects aur arrays jaise non-primitive types call by reference ke saath pass hote hain.

3. Example:
* Function me reference pass hota hai, jo original data ka location point karta hai.
* Isliye, agar function ke andar changes hote hain, to wo original variable ko impact karte hain.


```python
let obj = { name: "John" };

function modifyReference(o) {
  o.name = "Jane"; // Directly modifies the original object
}

modifyReference(obj);
console.log(obj.name); // Output: Jane

```

| Aspect                 | Call by Value                          | Call by Reference                           |
| ---------------------- | -------------------------------------- | ------------------------------------------- |
| **Definition**         | Value ki ek copy pass hoti hai.        | Memory location (reference) pass hota hai.  |
| **Data Type**          | Primitive types (number, string, etc.) | Non-primitive types (objects, arrays)       |
| **Effect on Original** | Original variable unaffected.          | Original variable directly modify hota hai. |
| **Use Case**           | Immutable data.                        | Mutable data.                               |


# How does the bind(), call(), and apply() methods work in JavaScript?

#### bind() Method
1. Definition:
* bind() ek nayi function copy return karta hai jo specific this context aur arguments ke sath bindi hoti hai.

2. Key Features:
* Function immediately execute nahi hota.
* Sirf ek nayi function instance banata hai jo later execute ki ja sakti hai.


```python
const obj = { name: "John" };
function greet(greeting) {
  return `${greeting}, ${this.name}`;
}

const boundGreet = greet.bind(obj, "Hello");
console.log(boundGreet()); // Output: Hello, John
```

#### call() Method

1. Definition:
* call() ek function ko immediately execute karta hai aur uska this context set karta hai.

2. Key Features:

* this ko specific object me set karta hai.
* Arguments ko comma-separated pass karte hain.


```python
const obj = { name: "John" };
function greet(greeting) {
  return `${greeting}, ${this.name}`;
}

console.log(greet.call(obj, "Hi")); // Output: Hi, John
```

#### apply() Method

1. Definition:
* apply() bhi call() ki tarah kaam karta hai, lekin arguments ko array ke form me pass karta hai.

2. Key Features:
* this ko specific object me set karta hai.
* Arguments ek array ya array-like object (e.g., arguments) ke roop me pass hote hain.


```python
const obj = { name: "John" };
function greet(greeting, punctuation) {
  return `${greeting}, ${this.name}${punctuation}`;
}

console.log(greet.apply(obj, ["Hey", "!"])); // Output: Hey, John!
```

| Method    | Returns          | Executes Function | Arguments Pass Format          | Use Case                                 |
| --------- | ---------------- | ----------------- | ------------------------------ | ---------------------------------------- |
| `bind()`  | New function     | No                | Individually                   | Predefine context for future execution   |
| `call()`  | Undefined/Result | Yes               | Individually (comma-separated) | Immediate execution with custom context  |
| `apply()` | Undefined/Result | Yes               | Array                          | Immediate execution with array arguments |


* bind(): Function ko later execute karne ke liye ek naya version create karta hai with predefined this.

* call(): Function ko immediately execute karta hai, arguments ko comma-separated form me accept karta hai.

* apply(): Function ko immediately execute karta hai, arguments ko array form me accept karta hai.



### Real Example of This Three Functions?

Maan lijiye humare paas ek "order management system" hai jisme customers ke orders ka record hai. Hume ek function banani hai jo customer ke naam ke sath order ki details ko display kare, aur hum iska this context dynamically change karte hain using bind(), call(), aur apply().


```python
// Ek customer ka object
const customer = {
  name: "Rahul",
};

// Order function (context ko dynamically set karenge)
function displayOrderDetails(product, price) {
  return `${this.name} ne ${product} ko ₹${price} me order kiya.`;
}
```


```python
// Using bind()

const rahulOrder = displayOrderDetails.bind(customer, "Laptop", 50000); // Bind context and arguments

console.log(rahulOrder()); // Output: Rahul ne Laptop ko ₹50000 me order kiya.
```


```python
// Using Call()

console.log(displayOrderDetails.call(customer, "Mobile", 20000)); 
// Output: Rahul ne Mobile ko ₹20000 me order kiya.
```


```python
// Using Apply()

console.log(displayOrderDetails.apply(customer, ["Tablet", 15000]));
// Output: Rahul ne Tablet ko ₹15000 me order kiya.
```

| Method    | Use Case                                        | Result                                     |
| --------- | ----------------------------------------------- | ------------------------------------------ |
| `bind()`  | Future use ke liye predefined function banaya   | `Rahul ne Laptop ko ₹50000 me order kiya.` |
| `call()`  | Turant execution aur arguments comma-separated  | `Rahul ne Mobile ko ₹20000 me order kiya.` |
| `apply()` | Turant execution aur arguments array ke roop me | `Rahul ne Tablet ko ₹15000 me order kiya.` |


# Different ways to create object in javascript ?


```python
// Object Literal

const obj = { name: "Rahul", age: 25 };

// Using new Object()

const obj = new Object();
obj.name = "Rahul";
obj.age = 25;

// Using Constructor Function

function Person(name, age) {
  this.name = name;
  this.age = age;
}
const obj = new Person("Rahul", 25);


// Using ES6 Classes

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
const obj = new Person("Rahul", 25);


// Using Object.create()

const prototypeObj = { greet: function() { return "Hello!"; } };
const obj = Object.create(prototypeObj);
obj.name = "Rahul";

// Using Factory Function

function createPerson(name, age) {
  return { name, age };
}
const obj = createPerson("Rahul", 25);


//  JSON.parse()

const obj = JSON.parse('{"name": "Rahul", "age": 25}');

// Using Object.assign()

const obj1 = { name: "Rahul" };
const obj2 = { age: 25 };
const obj = Object.assign({}, obj1, obj2);

// Singleton Pattern

const obj = new (function() {
  this.name = "Rahul";
  this.age = 25;
})();


// Using ES6 Spread Operator

const obj1 = { name: "Rahul", age: 25 };
const obj = { ...obj1, city: "Delhi" };
```

| Method                   | Description                          | Example                         |
| ------------------------ | ------------------------------------ | ------------------------------- |
| **Object Literal**       | Most common and simple               | `{ name: "Rahul" }`             |
| **`new Object()`**       | Built-in constructor                 | `new Object()`                  |
| **Constructor Function** | Custom function to create objects    | `function Person()`             |
| **ES6 Classes**          | Modern syntax for objects            | `class Person {}`               |
| **`Object.create()`**    | Prototype-based object creation      | `Object.create(prototypeObj)`   |
| **Factory Function**     | Function that returns a new object   | `createPerson(name, age)`       |
| **JSON.parse()**         | Convert JSON string to object        | `JSON.parse('{...}')`           |
| **`Object.assign()`**    | Merge or copy properties             | `Object.assign({}, obj1, obj2)` |
| **Singleton Pattern**    | Unique global object                 | `new (function(){...})`         |
| **Spread Operator**      | Copy properties into a new object    | `{ ...obj1, city: "Delhi" }`    |
| **Static Method**        | Create objects via a reusable method | `class with create()`           |
| **`Object.freeze()`**    | Immutable objects                    | `Object.freeze({...})`          |


# IIFE (Immediately Invoked Function Expression) kya hai?



IIFE ka matlab hai Immediately Invoked Function Expression. Yeh ek aisa JavaScript function hai jo declare hote hi turant execute hota hai.

IIFE ka primary purpose hai data encapsulation aur global namespace ko pollute hone se bachana.


```python
// 1st Way

(function() {
  // Code yaha likha jata hai
})();


// 2nd Way

(() => {
  // Arrow function version
})();

```


```python
(function() {
  console.log("IIFE executed!");
})();

```


```python
(function(name) {
  console.log(`Hello, ${name}!`);
})("Rahul");

```

# CORS (Cross-Origin Resource Sharing) in JavaScript

CORS ek security feature hai jo browser ko control deta hai ki ek website ke resources (data) ko doosri website ke saath share kiya ja sake ya nahi. Yeh server aur browser ke beech ek policy enforce karta hai jo unauthorized access ko rokta hai.

#### CORS Kya Hai?
* Default Behavior: Web browsers security ke liye Same-Origin Policy lagate hain. Iska matlab hai ki ek web page sirf usi origin ke resources ko access kar sakta hai jisse wo load hua hai.
* CORS Same-Origin Policy ka exception hai jo allow karta hai ek origin se doosre origin ke resources ko access karna (agar server ne permission di ho).

# What is difference between find vs findIndex ?


| Feature          | `find()`                   | `findIndex()`                   |
| ---------------- | -------------------------- | ------------------------------- |
| **Return Value** | First matching **element** | First matching **index**        |
| **No Match**     | Returns `undefined`        | Returns `-1`                    |
| **Use Case**     | Element ko fetch karna     | Element ka index fetch karna    |
| **Modification** | Sirf value fetch karta hai | Position modify karne me useful |



```python
const numbers = [10, 20, 30, 40, 50];

// Using find()
const foundValue = numbers.find(num => num > 25);
console.log(foundValue); // Output: 30

// Using findIndex()
const foundIndex = numbers.findIndex(num => num > 25);
console.log(foundIndex); // Output: 2
```

# What are cookies

Cookies ek chhoti si text file hoti hai jo browser ke through user ke device par store ki jaati hai. Iska primary purpose user ke data ko store karna aur server aur client ke beech ka communication better banana hota hai.

#### Cookies Ka Kaam
1. User Information Store Karna:

Jaise ki login credentials, preferences, aur shopping cart data.

2. Session Management:

Session-based tracking ke liye cookies ka use hota hai, jisse ek user ke multiple requests ko identify kiya ja sake.

3. Tracking and Analytics:

User ke browsing behavior ko track karne ke liye (e.g., advertisements).

4. Personalized Experience:

User preferences store karke website ko customized banane ke liye.


```python
// Set Cookie
document.cookie = "username=Rahul; expires=Fri, 31 Dec 2025 12:00:00 UTC; path=/";

// Get cookie
console.log(document.cookie); // Output: username=Rahul

// Delete cookie
document.cookie = "username=Rahul; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";
```

# What is the difference between Pure and Impure functions?

#### 1. Pure Function
Definition
* Pure function woh hota hai jo:

* Same input par hamesha same output deta hai (deterministic behavior).

* Koi side effect nahi create karta (kisi external variable ya state ko modify nahi karta).

Key Features
* Immutable data ko handle karta hai.

* Kisi external value ya state par depend nahi karta.

* Debugging aur testing ke liye reliable hota hai.


```python
function add(a, b) {
  return a + b; // Input ke basis par predictable output
}

console.log(add(2, 3)); // Output: 5
console.log(add(2, 3)); // Output: 5 (Same input, same output)
```

#### 2. Impure Function

Definition
* Impure function woh hota hai jo:
* Different output de sakta hai same input ke liye.
* Side effects create karta hai (external state ko modify karta hai ya uspar depend karta hai).

Key Features
* External variables ko modify karta hai.
* External state ke basis par output change ho sakta hai.
* Debugging aur testing mushkil hoti hai.


```python
let count = 0;

function increment() {
  count++; // External variable modify karta hai
  return count;
}

console.log(increment()); // Output: 1
console.log(increment()); // Output: 2 (Same function, different output)
```

| Aspect                | **Pure Function**                                | **Impure Function**                                  |
| --------------------- | ------------------------------------------------ | ---------------------------------------------------- |
| **Deterministic**     | Same input → Same output                         | Same input → Different output possible               |
| **Side Effects**      | No side effects                                  | External variables ko modify kar sakta hai           |
| **Dependency**        | Sirf function ke parameters par depend karta hai | External state ya variables par depend kar sakta hai |
| **Debugging/Testing** | Easy to debug aur test                           | Hard to debug aur test                               |
| **Example**           | `return a + b`                                   | Modifies external variable (`count++`)               |


# What is temporal dead zone

1. Temporal Dead Zone (TDZ) in JavaScript
Temporal Dead Zone (TDZ) ek term hai jo let, const, aur class declarations ke behavior ke sath related hai. TDZ wo time period hai jab variable declare to ho gaya hai, lekin usse use karne ki koshish karne par error aata hai kyunki wo abhi "initialized" nahi hua hota.

2 .TDZ Kab Hota Hai?
* Jab JavaScript code ko execute karta hai (hoisting ke time), tab variables aur functions memory me allocate ho jate hain.
* let aur const hoist to hote hain, lekin unhe tab tak initialize nahi kiya jata jab tak unki declaration line execute nahi hoti.
* TDZ wahi phase hai jab variable hoist ho chuka hai lekin initialize nahi hua hai.


```python
console.log(x); // ReferenceError: Cannot access 'x' before initialization
let x = 10;
```

* Yaha x ka declaration memory me ho gaya hai, lekin initialize nahi hua hai jab tak let x = 10; execute nahi hota.
* Isliye, TDZ ke dauran x ko access karne ki koshish karna error throw karega.


```python
// TDZ Behavior with let and const

{
  console.log(a); // ReferenceError
  let a = 5;
}


{
  console.log(b); // ReferenceError
  const b = 10;
}


// Difference with var
// var variables hoist hote hain aur immediately initialize ho jate hain with undefined, isliye unme TDZ nahi hota.

console.log(c); // Output: undefined
var c = 15;

```

Temporal Dead Zone (TDZ) ek JavaScript mechanism hai jo developers ko predictable aur error-free code likhne me help karta hai. TDZ ke wajah se let aur const safer aur more reliable hote hain, jo bugs ko prevent karte hain jo var ke saath ho sakti thi.

# What are DRY, KISS, YAGNI, SOLID Principles?

| **Principle** | **Full Form**                | **Purpose**                                                                                   | **Key Focus**                                          |
| ------------- | ---------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **DRY**       | Don't Repeat Yourself        | Avoid duplication in code. Centralize reusable logic in one place to enhance maintainability. | Code reusability and maintainability.                  |
| **KISS**      | Keep It Simple, Stupid       | Write simple and straightforward code, avoiding unnecessary complexity.                       | Code simplicity and clarity.                           |
| **YAGNI**     | You Aren't Gonna Need It     | Do not implement features or functionality until it’s absolutely necessary.                   | Avoid unnecessary features and premature optimization. |
| **SOLID**     | Acronym for 5 OOP principles | Improve code scalability and maintainability in object-oriented programming.                  | Follow SRP, OCP, LSP, ISP, and DIP.                    |


### Detailed Breakdown of SOLID Principles

| **Letter** | **Full Form**                         | **Explanation**                                                                                 | **Key Focus**                                        |
| ---------- | ------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **S**      | Single Responsibility Principle (SRP) | A class or function should have only one responsibility or purpose.                             | Focused design with one clear functionality.         |
| **O**      | Open/Closed Principle (OCP)           | Code should be open for extension but closed for modification.                                  | Extend functionality without altering existing code. |
| **L**      | Liskov Substitution Principle (LSP)   | Subclasses should be replaceable with their base class without altering the program's behavior. | Maintain correct inheritance and behavior.           |
| **I**      | Interface Segregation Principle (ISP) | Classes should not be forced to implement methods they do not use.                              | Design interfaces specific to client needs.          |
| **D**      | Dependency Inversion Principle (DIP)  | High-level modules should not depend on low-level modules but on abstractions.                  | Decouple high-level and low-level logic.             |


# What is event delegation in JavaScript?

Event Delegation ek technique hai jisme hum ek parent element par event listener attach karte hain, aur uske child elements par hone wale events ko handle karte hain.

Ye concept event bubbling ka use karta hai, jisme event sabse niche ke element (target element) se bubble hokar uske ancestors tak propagate hota hai.


```python
// Example With Event Delegation

document.getElementById("parent").addEventListener("click", (event) => {
  if (event.target.tagName === "BUTTON") {
    console.log(`${event.target.textContent} clicked`);
  }
});
```


```python
<div id="parent">
  <button id="button1">Button 1</button>
  <button id="button2">Button 2</button>
</div>
```

Explanation:
* Parent element (#parent) par event listener lagaya gaya hai.
* event.target ka use karke identify kiya gaya ki kaunsa button click hua.
* Agar dynamically naya button add karenge, wo bhi handle ho jayega.

# What is event bubbling

1. Event Bubbling in JavaScript
* Event Bubbling ek concept hai JavaScript me jo tab hota hai jab ek DOM element par event trigger hota hai aur wo event parent elements tak propagate karta hai.

2. Kaise Kaam Karta Hai?
* Jab ek child element par event trigger hota hai (e.g., click), to wo sabse pehle child element par handle hota hai.
* Uske baad wo parent element, phir uske ancestor elements tak propagate hota hai.
* Ye process document element tak ja sakta hai, jab tak propagation ko explicitly stop na kiya jaye.


```python
<div id="parent" style="padding: 20px; background-color: lightblue;">
  Parent
  <div id="child" style="padding: 20px; background-color: lightgreen;">
    Child
  </div>
</div>
```


```python
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Child clicked");
});


// OUTPUT
// Child clicked
// Parent clicked

```

##### Stop Event Bubbling
Agar aapko event bubbling ko rokhna hai, to aap event.stopPropagation() method ka use kar sakte ho.




```python
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", (event) => {
  event.stopPropagation(); // Stop event bubbling
  console.log("Child clicked");
});

// Output
// Child clicked
```

1. Advantages of Event Bubbling
* Single Event Listener:

Parent element par ek hi listener lagakar multiple child elements ke events handle karna.

* Better Performance:

Har child element ke liye alag listener lagane ki zarurat nahi hoti.

* Dynamic Elements:

Aise child elements ko handle karna jo runtime par DOM me add hote hain.

2. Disadvantages of Event Bubbling
* Unintended Behavior:

Agar bubbling control nahi kiya gaya, to irrelevant elements par bhi events trigger ho sakte hain.

* Stop Propagation Logic:

Har event ke liye propagation stop karne ka logic likhna padta hai.

| **Aspect**           | **Event Bubbling**                            | **Event Capturing**                                           |
| -------------------- | --------------------------------------------- | ------------------------------------------------------------- |
| **Order**            | Event child se parent tak propagate hota hai. | Event parent se child tak propagate hota hai.                 |
| **Default Behavior** | JavaScript me default behavior hai.           | Event listener explicitly capturing mode me lagana padta hai. |
| **Use Case**         | Most common scenarios me use hota hai.        | Rarely use hota hai, especially in nested elements.           |


# What is event capturing

Event Capturing (jo trickling phase ke naam se bhi jana jata hai) ek DOM event propagation mechanism hai. Isme event sabse pehle parent element se start hota hai aur step-by-step child element tak propagate karta hai.

#### Event Capturing Kaise Kaam Karta Hai?
Jab ek event trigger hota hai (e.g., click), to wo pehle outermost parent element par fire hota hai.

Uske baad wo progressively inner elements (child elements) par propagate karta hai.

Ye propagation ke process ko capturing phase kehte hain

Event Capturing Ka Syntax:-

Capturing phase ke liye, addEventListener method ka third argument true set karte hain.


```python
element.addEventListener("event", callback, true);
```


```python
<div id="parent" style="padding: 20px; background-color: lightblue;">
  Parent
  <div id="child" style="padding: 20px; background-color: lightgreen;">
    Child
  </div>
</div>
```


```python
document.getElementById("parent").addEventListener(
  "click",
  () => {
    console.log("Parent clicked");
  },
  true // Enabling capturing phase
);

document.getElementById("child").addEventListener(
  "click",
  () => {
    console.log("Child clicked");
  },
  true // Enabling capturing phase
);

// Output
// Parent clicked
// Child clicked
```

| **Aspect**        | **Event Capturing**                           | **Event Bubbling**                            |
| ----------------- | --------------------------------------------- | --------------------------------------------- |
| **Order**         | Event parent se child tak propagate hota hai. | Event child se parent tak propagate hota hai. |
| **How to Enable** | `addEventListener` me third argument `true`.  | Default behavior, third argument `false`.     |
| **Use Case**      | Rarely used, specific scenarios me.           | Commonly used in most cases.                  |


# What is the difference between async and defer attributes on <​script> tags?


1. Default Behavior (Without async or defer)

* Agar script tag me async aur defer attributes nahi diye gaye:

* Browser JavaScript ko download aur execute karta hai immediately.

* Is process ke dauraan HTML parsing temporarily block ho jata hai.

2. async Attribute
* Behavior:

JavaScript ko asynchronously download karta hai, lekin uska execution immediate hota hai (jese hi script download ho jaye).

HTML parsing ko block karta hai jab script execute hoti hai.

Execution Order:
Scripts ka execution download completion ke order par hota hai, HTML ke parsing se pehle.



3. defer Attribute
* Behavior:

JavaScript ko asynchronously download karta hai, lekin uska execution tab tak delay hota hai jab tak HTML parsing complete na ho jaye.

* Execution Order:

Scripts document me appear hone ke order me execute hote hain (irrespective of download completion time).

| **Aspect**           | **`async`**                                 | **`defer`**                                                      |
| -------------------- | ------------------------------------------- | ---------------------------------------------------------------- |
| **Download**         | Asynchronously (HTML parsing ke sath)       | Asynchronously (HTML parsing ke sath)                            |
| **Execution Timing** | Download hote hi execute hota hai.          | HTML parsing complete hone ke baad execute hota hai.             |
| **Execution Order**  | Download completion ke order me.            | Document me script ke order ke hisaab se.                        |
| **HTML Parsing**     | Block hoti hai jab script execute hota hai. | Block nahi hoti, parsing complete hone ke baad execute hota hai. |
| **Use Case**         | Independent scripts (e.g., ads, analytics). | Scripts dependent on HTML structure (e.g., DOM manipulation).    |


#### Best Practices for Using async and defer
1. Use async for Non-Critical Scripts:

* Analytics scripts, third-party widgets, or ads scripts ke liye best hai jo DOM ya doosre scripts par depend nahi karte.

2. Use defer for Critical Scripts:

* DOM manipulation ya HTML ke structure ke sath interact karne wale scripts ke liye defer use karein.

3. Avoid Blocking Scripts Without async or defer:

* By default, <script> tag HTML parsing ko block kar deta hai, jo page load performance ko slow kar sakta hai.



# What is the main difference between Local Storage and Session storage

| **Aspect**        | **Local Storage**                                                           | **Session Storage**                                                            |
| ----------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Data Lifetime** | Data **permanent** hota hai (tab tak jab tak manually delete na kiya jaye). | Data **temporary** hota hai aur browser tab close hone par delete ho jata hai. |
| **Scope**         | Across all tabs aur windows available hota hai (same origin).               | Sirf ek specific tab ke liye accessible hota hai.                              |
| **Storage Limit** | Approximately **5MB** (per origin).                                         | Approximately **5MB** (per origin).                                            |
| **Persistence**   | Data tab tak rehta hai jab tak user ya code usse remove na kare.            | Data sirf tab session ke duration tak rehta hai.                               |
| **Use Case**      | Long-term storage, e.g., user preferences, tokens.                          | Temporary data, e.g., form data during session.                                |
| **API**           | Accessible via `localStorage` object.                                       | Accessible via `sessionStorage` object.                                        |



```python
// 1. Local Storage

// Set data
localStorage.setItem("username", "John");

// Get data
console.log(localStorage.getItem("username")); // Output: "John"

// Remove data
localStorage.removeItem("username");

// Clear all data
localStorage.clear();

```


```python
// Session Storage

// Set data
localStorage.setItem("username", "John");

// Get data
console.log(localStorage.getItem("username")); // Output: "John"

// Remove data
localStorage.removeItem("username");

// Clear all data
localStorage.clear();
```

| **Property**         | **Local Storage**                                                 | **Session Storage**                                          |
| -------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------ |
| **When to Use**      | Long-term data storage needs (e.g., user settings, JWT tokens).   | Temporary data for single session (e.g., cart info for tab). |
| **Data Sharing**     | Same data can be shared between tabs.                             | Data is unique to each tab.                                  |
| **Automatic Expiry** | No (manually delete karna padta hai).                             | Yes (tab close hone par delete ho jata hai).                 |
| **Security**         | Easily accessible via JavaScript (not secure for sensitive info). | Same vulnerability but less risk due to session lifespan.    |


# Is javascript a dynamically typed language or a statically typed language 

| **Aspect**           | **Dynamically Typed (JavaScript)**                | **Statically Typed (Java, C++)**                       |
| -------------------- | ------------------------------------------------- | ------------------------------------------------------ |
| **Type Declaration** | Explicitly declare karna zaruri nahi hota.        | Types compile time pe explicitly declare karte hain.   |
| **Type Checking**    | Runtime ke dauraan hota hai.                      | Compile time pe hota hai.                              |
| **Flexibility**      | High (variables ka type change ho sakta hai).     | Low (variables ka type fix hota hai).                  |
| **Error Detection**  | Type-related errors runtime par detect hote hain. | Type-related errors compile time par detect hote hain. |


# Slice vs Splice in javascript ?

slice() Method

* slice() ek non-destructive method hai jo ek array ka shallow copy banata hai, bina original array ko modify kiye.


```python
let arr = [1, 2, 3, 4, 5];

// Extract elements from index 1 to 3 (3 is exclusive)
let sliced = arr.slice(1, 3);
console.log(sliced); // Output: [2, 3]
console.log(arr);    // Original array: [1, 2, 3, 4, 5]
```

splice() Method
* splice() ek destructive method hai jo array ko directly modify karta hai. Ye elements ko remove kar sakta hai, add kar sakta hai, ya replace kar sakta hai.


```python
// Remove

let arr = [1, 2, 3, 4, 5];

// Remove 2 elements starting from index 1
arr.splice(1, 2);
console.log(arr); // Output: [1, 4, 5]


// Adding

let arr = [1, 4, 5];

// Add elements at index 1
arr.splice(1, 0, 2, 3);
console.log(arr); // Output: [1, 2, 3, 4, 5]


// Replacing

let arr = [1, 4, 5];

// Add elements at index 1
arr.splice(1, 0, 2, 3);
console.log(arr); // Output: [1, 2, 3, 4, 5]

```

| **Aspect**         | **`slice()`**                                        | **`splice()`**                                    |
| ------------------ | ---------------------------------------------------- | ------------------------------------------------- |
| **Purpose**        | Ek array ka shallow copy banata hai.                 | Array ke elements ko modify karta hai.            |
| **Original Array** | Original array ko safe rakhta hai (non-destructive). | Original array ko modify karta hai (destructive). |
| **Return Value**   | Nayi array return karta hai.                         | Removed elements ki array return karta hai.       |
| **Operations**     | Sirf elements extract karta hai.                     | Remove, add, aur replace kar sakta hai.           |
| **Syntax**         | `array.slice(start, end)`                            | `array.splice(start, deleteCount, item1, ...)`    |


# What is meant by debouncing and throttling

Debouncing aur Throttling dono hi techniques hain jo performance optimization ke liye use hoti hain, particularly jab koi function frequent events (e.g., scroll, resize, keypress) ke response me repeatedly call hota hai.

1. Debouncing

* Debouncing ek technique hai jo ensure karti hai ki ek function tabhi execute ho, jab event ke frequent triggers ke beech ek specific time delay complete ho jaye.

Key Points:

* Function ko delay ke baad execute karta hai.

* Agar event fir se trigger hota hai, to timer reset ho jata hai.

* Useful for events jo frequent aur fast hote hain, jaise resize, keypress, ya input.

Example Use Case:

* Search Bar Suggestions: Jab user search input type karta hai, to API ko unnecessary frequent calls avoid karne ke liye debounce use hota hai.


```python
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer); // Reset the timer
    timer = setTimeout(() => {
      func.apply(this, args); // Execute the function after delay
    }, delay);
  };
}

// Usage
const searchInput = document.getElementById("search");
searchInput.addEventListener(
  "keyup",
  debounce((event) => {
    console.log("API Call for search:", event.target.value);
  }, 300)
);
```

2. Throttling

* Throttling ek technique hai jo ensure karti hai ki ek function ek fixed interval ke andar sirf ek baar execute ho, chahe event kitni baar bhi trigger ho.

Key Points:

* Function ko fixed time interval ke andar execute hone ki permission deta hai.

* Useful for events jo continuously trigger hote hain, jaise scroll, mousemove.

Example Use Case:
* Infinite Scroll: Jab user continuously scroll karta hai, to content load karne ke liye throttling use hota hai.




```python
function throttle(func, limit) {
  let lastFunc;
  let lastRan;
  return function (...args) {
    const now = Date.now();
    if (!lastRan) {
      func.apply(this, args); // Execute immediately for the first time
      lastRan = now;
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (now - lastRan >= limit) {
          func.apply(this, args); // Execute if enough time has passed
          lastRan = now;
        }
      }, limit - (now - lastRan));
    }
  };
}

// Usage
const scrollHandler = () => {
  console.log("Scroll event triggered");
};

window.addEventListener("scroll", throttle(scrollHandler, 200));
```

| **Aspect**    | **Debouncing**                                                        | **Throttling**                                             |
| ------------- | --------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Execution** | Function tabhi execute hota hai jab event triggers ke beech delay ho. | Function fixed interval ke andar ek baar execute hota hai. |
| **Purpose**   | Frequent event calls ko reduce karna.                                 | Continuous event calls ko control karna.                   |
| **Delay**     | Dynamic delay ke baad execute hota hai.                               | Fixed interval ke hisaab se execute hota hai.              |
| **Use Cases** | Search bar, form validation, window resizing.                         | Scroll events, drag-and-drop, mouse movement.              |

