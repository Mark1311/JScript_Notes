# What is JavaScript?
JavaScript ek high-level, interpreted (ya JIT-compiled), aur single-threaded programming language hai, jise main web pages ko dynamic aur interactive banane ke liye use kiya jata hai. Yeh Client-side aur Server-side (Node.js ke zariye) dono jagah kaam karti hai.

### Key Technical Terms

- Single-threaded & Synchronous: JavaScript ek waqt me sirf ek hi kaam kar sakti hai (line by line chalti hai).
- Asynchronous Capabilities: Single-threaded hone ke bawajood, JS Callbacks, Promises, aur Async/Await ki madad se heavy tasks (jaise API se data lana) ko background me chala sakti hai bina browser ko freeze kiye.
- Dynamically Typed: Isme aapko variable ka data type (int, string, etc.) pehle se declare nahi karna padta. let x = 10; likha, toh yeh khud samajh jayegi ki yeh number hai.
- Multi-paradigm: Yeh Object-Oriented (OOPs) aur Functional programming dono ko support karti hai.

### How JavaScript Works?

- JS Engine: Har browser ke paas ek engine hota hai jo JS code ko machine code me badalta hai. Chrome ke paas V8 Engine hai (jo Node.js me bhi use hota hai) aur Firefox ke paas SpiderMonkey hai.

- Execution Context: Jab bhi JS ka code chalta hai, wo ek "Execution Context" ke andar chalta hai. Iske do phase hote hain:

  1. Memory Creation Phase: Saare variables aur functions ko memory allocate hoti hai (Isi waqt Hoisting hoti hai).
  2. Code Execution Phase: Code line-by-line execute hota hai.

# How JS Work?

### 1. JavaScript Engine (The Core)
Har browser ke paas ek JS Engine hota hai (jaise Chrome ka V8, Firefox ka SpiderMonkey). Engine ka kaam aapke code ko machine code (0s aur 1s) me badalna hai.

- Parsing: Aapka code line-by-line padha jata hai aur use Abstract Syntax Tree (AST) me convert kiya jata hai (jo ki ek tree-like structure hota hai).

- Compilation (JIT - Just In Time): JavaScript pehle sirf interpreted (line-by-line chalne wali) language thi, lekin ab yeh JIT Compilation use karti hai. Isme code ko pehle jaldi se machine code me convert (compile) kiya jata hai aur saath hi saath run (execute) kiya jata hai taaki speed behtareen ho.

- Execution: Code ko execute karne ke liye engine ke paas do main components hote hain:

  - Memory Heap: Jahan saare variables, objects, aur functions ko memory milti hai (raw space).

  - Call Stack: Jahan aapka code actually execute hota hai. Yeh LIFO (Last In, First Out) principle par kaam karta hai. Jo function call hoga, wo stack ke upar aayega, aur khatam hote hi bahar nikal jayega.

### 2. Execution Context (Code Kaise Chalta Hai)
Jab bhi JS code run hota hai, toh ek Global Execution Context (GEC) banta hai. Yeh do phases me kaam karta hai:

#### Phase 1: Memory Creation Phase (Creation Phase)
Code chalne se pehle, JS Engine saare variables aur functions ko scan karta hai aur unhe memory allocate karta hai.
  - Variables (var) ko shuruat me undefined value milti hai.
  - Functions ka poora ka poora code memory me copy ho jata hai. (Isi phase ko hum Hoisting kehte hain).

#### Phase 2: Code Execution Phase
Ab code line-by-line chalna shuru hota hai. Variables ko unki actual value milti hai. Agar koi function call (()) aata hai, toh us function ke liye ek naya Functional Execution Context banta hai aur wo Call Stack me chala jata hai. Function khatam hote hi wo stack se delete ho jata hai.

### 3. Asynchronous JS aur JavaScript Runtime
Aapko pata hai ki JS Single-threaded hai (ek waqt me ek hi line chalayegi). Toh fir setTimeout ya API calls jaise asynchronous kaam bina browser ko block kiye kaise hote hain?

- Call Stack: Yeh toh engine ka hissa hai jo aapka normal code chala raha hai.

- Web APIs (Browser ka hissa): Jab aap setTimeout, fetch() (API call), ya DOM click events use karte hain, toh JS Engine unhe khud handle nahi karta. Wo unhe Browser ki Web APIs ko सौंप (handover) deta hai.

- Callback Queue (ya Task Queue): Jab Web API apna kaam poora kar leti hai (jaise 3 seconds poore ho gaye ya API se data aa gaya), toh wo uske callback function ko Callback Queue me bhej deti hai.

- Event Loop (The Supervisor): Event Loop ka sirf ek hi kaam hai—wo lagatar Call Stack aur Callback Queue ko dekhta rehta hai.

  - Agar Call Stack khali (empty) hai, aur Callback Queue me koi kaam bacha hai...
  - Toh Event Loop Queue se function ko uthakar Call Stack me daal deta hai, aur wo execute ho jata hai.

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

### Summery:-
JS internally V8 Engine aur Browser Runtime ke combination se chalti hai. Engine ke andar ek Call Stack hota hai jahan execution context ke zariye code line-by-line chalta hai. Kyunki JS single-threaded hai, asynchronous tasks ko handle karne ke liye Web APIs ka use hota hai. Jab asynchronous task poora hota hai, toh wo Callback Queue me jata hai, aur Event Loop stack khali hote hi us task ko execute karne ke liye Call Stack me bhej deta hai

# strict mode

Strict mode ek tarah ka coding mode hota hai jo JavaScript me kuch errors ko zyada strict bana deta hai, jisse code safe aur predictable ban jata hai. Agar aap "strict mode" use karte hain, to kuch cheezein jo pehle JavaScript me allowed thi, unhe ab error dikha kar rok diya jata hai.
Ye ek tarah se code ko secure aur error-free banane me madad karta hai.

# declarations 

JavaScript mein declarations ka matlab hai kisi variable, function, ya class ko declare karna, yani usko define karna taake aap usko baad mein use kar sakein.

In short, declaration ka matlab hai kisi cheez ko define karna, taake aap usko baad mein use kar sakein.


```python
let name = "Bittu"
const Lname = "Kumar"

// #Another Type:-

let age;
const Name;
```

# Initialization 

JavaScript me initialization ka matlab hota hai kisi variable ko value assign karna. Jab aap ek variable declare karte hain, usse initial value dena "initialization" kehlata hai.

Direct initialization: Jaise upar wale example me kiya gaya.
Later initialization: Jab aap variable ko declare karte hain, par usse baad me value assign karte hain.


```python
let y;   // Variable declare kiya
y = 5;   // Variable 'y' ko value assign ki
```

# Re-declarations

JavaScript mein re-declaration ka matlab hota hai kisi variable ko phir se declare karna ussi scope ke andar. JavaScript mein variables ko var, let, ya const se declare kiya jata hai. Har ek ka apna behavior re-declaration ke case mein hota hai.

### var ke saath re-declaration:
var se declare kiye gaye variables ko ek hi scope mein multiple baar declare kiya ja sakta hai. Matlab, agar aap same variable ko dobara declare karte hain, to koi error nahi aayega.


```python
var x = 10;
var x = 20;  // No error
console.log(x);  // Output: 20
```

### let ke saath re-declaration:
let se declare kiye gaye variables ko same scope mein dobara declare nahi kiya ja sakta. Agar aap aise try karenge, to JavaScript error dega.


```python
let y = 30;
let y = 40;  // Error: Identifier 'y' has already been declared
```

### const ke saath re-declaration:
const se declare kiye gaye variables ko bhi same scope mein dobara declare nahi kiya ja sakta. Agar aap aise try karenge, to bhi error milega.


```python
const z = 50;
const z = 60;  // Error: Identifier 'z' has already been declared
```

var: Same scope mein dobara declare kiya ja sakta hai.
let aur const: Same scope mein dobara declare nahi kiya ja sakta, aur error dega.

# Re-assignment

JavaScript me "re-assignment" ka matlab hota hai kisi variable ko dubara se naye value se assign karna. Matlab, agar aapne pehle ek value kisi variable ko di thi, to aap usi variable ko phir se kisi naye value se assign kar sakte ho.


```python
let x = 5;    // pehle x ki value 5 hai
x = 10;        // ab x ki value ko 10 se re-assign kiya gaya hai
console.log(x); // Output: 10
```


```python
const y = 20;
y = 30;   // Error: Assignment to constant variable.
```
Let = Re-Assing Allow
var = Re-Assing Allow
const = Re-Assing Not Allow
# Hosting

JavaScript mein hosting ek mechanism hai jisme JavaScript ke variables aur functions ko unke code execution se pehle memory mein allocate kiya jata hai. Matlab, JavaScript ka engine code ko execute karne se pehle variables aur functions ko "hoist" (upar le jaata) kar leta hai.

JavaScript mein variable hoisting ek concept hai jisme variables aur functions ko unke actual position ke upar, code ke starting mein move kar diya jata hai, jab JavaScript engine code ko execute karta hai.

Hoisting kaise kaam karta hai:
Jab JavaScript ka code execute hota hai, toh engine pehle variable declarations aur function declarations ko top pe le jaata hai, lekin unki values ko as it is rakhta hai.

Hoisting mein var aur function declarations hoisted hote hain, lekin let, const aur class declarations hoist nahi hote (ya phir unka behavior alag hota hai).


```python
//   Var ke sath Hoisting
console.log(a); // undefined
var a = 5;
console.log(a); // 5
```

Pehle line mein, a ko reference kiya gaya, lekin uske baad hi value assign ki gayi thi.
    
Hoisting ke time pe JavaScript engine var a ko top pe le jata hai, lekin value assign nahi hoti, isliye pehli baar a ki value undefined hoti hai.


```python
//  Let and Const ke sath HOisting

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 10;
```

### Variables: 
Jab aap ek variable declare karte hain var, let, ya const se, to JavaScript us variable ko memory mein top pe declare kar leta hai. Lekin, agar aap us variable ko initialize karte hain, to uska value allocation uske declaration ke baad hota hai.
Undefinde is take the memory but not define is not take memory.
# Functional Hosting

Agar aap function ko declare karte hain, toh poora function body hosting ke dauran upar move kar jata hai, isliye aap function ko declare hone se pehle bhi call kar sakte hain.


```python
//  Function Declaration:

myFunction();  // "Hello"

function myFunction() {
  console.log("Hello");
}
```


```python
//  Function Expression:

myFunc();  // TypeError: myFunc is not a function

var myFunc = function() {
  console.log("Hello!");
};
```

Yahan myFunc() ko call karte waqt error aayegi, kyunki function expression ka myFunc variable undefined hoga jab tak uski initialization line tak code nahi pahunchega. Yani function expression mein hosting sirf variable declaration ka hota hai, function definition ka nahi.

Summery:---> Functional hosting ka matlab hai function declarations ka apne scope mein top par move ho jana, jisse aap function ko usse  pehle call kar sakte hain. Lekin function expressions mein yeh behavior nahi hota, aur unhein call karne ke liye unki definition tak code ko pahuncha zaroori hota hai.

#### Functional Hosting Ka Kaise Kaam Karta Hai?
Jab aap function declaration likhte hain, JavaScript engine us function ke definition ko hosting karta hai. Iska matlab hai ki aap function ko declare hone se pehle bhi call kar sakte hain

# Diff b/w Let, Var and Const???

| Feature / Criteria | `var` | `let` | `const` |
| :--- | :--- | :--- | :--- |
| **Scope** | **Function Scoped** (Agar function ke bahar hai toh Global Scoped hota hai). | **Block Scoped** (Sirf `{}` curly braces ke andar hi access ho sakta hai). | **Block Scoped** (Sirf `{}` curly braces ke andar hi access ho sakta hai). |
| **Re-declaration** | **Allowed** (Aap ek hi naam ka variable dobara declare kar sakte hain). | **Not Allowed** (Ek hi scope me same naam ka variable dobara declare nahi ho sakta). | **Not Allowed** (Ek hi scope me same naam ka variable dobara declare nahi ho sakta). |
| **Re-assignment** | **Allowed** (Aap variable ki value baad me badal sakte hain). | **Allowed** (Aap variable ki value baad me badal sakte hain). | **Not Allowed** (Iske sath mili value fix hoti hai, badli nahi ja sakti). |
| **Hoisting** | **Hoisted with `undefined`** (Execution se pehle memory me `undefined` set ho jata hai). | **Hoisted in TDZ** (Hoist hota hai, lekin "Temporal Dead Zone" me rehta hai, access karne par error aayega). | **Hoisted in TDZ** (Hoist hota hai, lekin "Temporal Dead Zone" me rehta hai, access karne par error aayega). |
| **Global Object Binding** | **Yes** (Browser me yeh `window` object ka hissa ban jata hai). | **No** (Yeh global object ya `window` me attach nahi hota). | **No** (Yeh global object ya `window` me attach nahi hota). |
| **Initialization** | Optional (Aap sirf `var a;` likh kar chhor sakte hain). | Optional (Aap sirf `let b;` likh kar chhor sakte hain). | **Mandatory** (Declare karte waqt hi value dena zaroori hai, jaise `const c = 10;`). |

# Nested Terrnery Operaters/Functions


```python
let marks = 60;
let result = (marks > 80) ? (marks > 90 ? "excell" : "Good") : "Avg";
console.log(result)
```

# Pre/Post Increment/Decrement


```python
let a = 2
b = a++
console.log(a) => 3
console.log(b) => 2
```


```python
let a = 5
b = ++a
console.log(a) => 6
console.log(b) => 6
```


```python
let a = 2
b = --a
console.log(a) => 1
console.log(b) => 1
```


```python
let a = 5
b = a--
console.log(a) => 4
console.log(b) => 5
```

# what is Closure ?

Closure tab hota hai jab ek function apne outer function ki variables ko access karta hai, even jab outer function execute ho chuka hota hai.

Closure ka matlab hai jab ek function ke andar dusra function banta hai, toh andar wala function apne bahar wale function ke variables ko yaad rakhta hai. Jab bahar wala function execute hokar khatam bhi ho jata hai aur call stack se hat jata hai, tab bhi andar wala function un variables ko bhoolta nahi hai kyunki wo ek lexical environment (scope chain) ko hold karke rakhta hai.

#### Closure ka basic structure:- 

Jab ek function doosre function ke andar defined hota hai aur us inner function ko outer function ki variables access karne ka access milta hai, to wo closure kehlaata hai.


```python
function outerFunction() {
  let outerVar = "I am from outer function";

  // Inner function
  function innerFunction() {
    console.log(outerVar);  // Inner function can access outer function's variable
  }

  return innerFunction;  // Returning the inner function
}

const closureExample = outerFunction();  // outerFunction() is executed and returns innerFunction
closureExample();  // Now, when we call closureExample(), it still remembers 'outerVar'


// #Output:- I am from outer function
```

outerFunction me ek variable outerVar hai.
innerFunction ko outerFunction ke andar define kiya gaya hai, aur ye inner function outerVar ko access kar sakta hai.
Jab outerFunction call hota hai, wo innerFunction ko return karta hai.
closureExample() ko call karne par, inner function apni outer function (outerFunction) ki variable ko yaad rakhta hai, aur outerVar ko access kar leta hai, even though outer function already execute ho chuka hota hai.

#### Closure ki Deep Explanation:

##### Function Scope:
Jab bhi aap ek function banate hain, us function ka apna ek local scope hota hai, jo uske andar ke variables ko define karta hai. Yeh variables function ke execution ke dauran available hote hain, lekin jab function execute ho jata hai toh yeh variables wapis accessible nahi hote.

##### Lexical Scoping:
JavaScript me lexical scoping ka concept hota hai, jiska matlab hai ki jab hum kisi function ko define karte hain, us function ka access un variables tak hota hai jo uske outer function ke scope me exist karte hain. Yeh concept closure me kaafi important hota hai.

##### Closure: 
Jab ek inner function apne outer function ke variables ko access karta hai (even after the outer function has finished executing), to wo closure create hota hai. Inner function apne lexical scope ko "remember" karta hai, isliye usse outer function ke variables tak access milta hai, chahe outer function ka execution end ho chuka ho.


```python
function outerFunction(outerVariable) {
  // Outer function ka variable
  let outerVar = outerVariable;

  return function innerFunction(innerVar) {
    // Inner function ko outer function ka variable accessible hai
    console.log("Outer Variable: " + outerVar); // Access to outer function's variable
    console.log("Inner Variable: " + innerVar); // Inner function ka apna variable
  };
}

const closureExample = outerFunction("Outer Function's Value");
closureExample("Inner Function's Value");


// # Outer Variable: Outer Function's Value
// # Inner Variable: Inner Function's Value
```

#### Explanation:
Jab outerFunction ko call kiya jata hai, toh uska ek outerVar ban jata hai jo uske local scope mein hota hai.

Phir outerFunction return karta hai ek innerFunction ko. Yeh inner function apne lexical scope ke through outerVar ko access kar sakta hai, chahe outerFunction ka execution complete ho gaya ho.

Jab closureExample() ko call kiya jata hai, yeh innerFunction ko call karta hai, jo outerVar ko access karta hai.

# Array.from()

JavaScript mein ek built-in method hai jo ek array-like object (jaise ek iterable object ya ek array) ko actual array mein convert karta hai.

Array.from() ka use zyada tar tab kiya jata hai jab aapko kisi aise object ko array mein convert karna ho, jo array jaisa ho ya iterable ho, lekin uska actual array ka type na ho. Is method ki madad se, aap us object ke saare elements ko ek naya array bana sakte hain.


```python
// Syntax:-

Array.from(arrayLike, mapFunction, thisArg);
```

arrayLike: Ye wo object hota hai jo ek array jaisa hota hai (jaise arguments, NodeList, string, etc.).

mapFunction (optional): Ye ek function hai jo har element ko transform karta hai jab array ban raha hota hai.

thisArg (optional): Agar mapFunction diya gaya ho, toh ye value har call ke liye this context ke roop mein use hota hai.

##### Array-Like Object to Array:

function myFunction() {
  console.log(arguments); // Arguments is array-like, not an actual array
  let argsArray = Array.from(arguments);
  console.log(argsArray); // Now it's an actual array!
}

myFunction(1, 2, 3, 4); 
// Output: [1, 2, 3, 4]

Aapka arguments object ek array-like object hota hai, par uske paas array ke methods jaise push(), map(), etc. nahi hote. Is case mein Array.from() ka use kar ke hum arguments ko array mein convert kar sakte hain.

#### Converting Strings to Arrays:-

let str = "hello";

let strArray = Array.from(str);

console.log(strArray); // ["h", "e", "l", "l", "o"]


JavaScript mein strings ko array-like objects ke roop mein treat kiya jata hai, jisme har character ko ek index diya jata hai. Array.from() se hum easily string ko array mein convert kar sakte hain.

#### Using Map Function with Array.from():-

let numbers = [1, 2, 3, 4];

let doubled = Array.from(numbers, x => x * 2);

console.log(doubled); // [2, 4, 6, 8]


Agar aapko kisi array ke elements ko convert ya modify karna hai, toh Array.from() ke second argument mein ek map function bhi de sakte hain, jo har element ko transform karega.

#### Converting Sets to Arrays:-

let mySet = new Set([10, 20, 30]);
let arrFromSet = Array.from(mySet);
console.log(arrFromSet); // [10, 20, 30]


Sets me duplicate values nahi hote, aur wo bhi iterable object hote hain. Agar aapko set ko array mein convert karna ho, toh Array.from() ka use kar sakte hain.


```python
#### Array from Map:

let myMap = new Map([[1, 'one'], [2, 'two'], [3, 'three']]);
let arrFromMap = Array.from(myMap);
console.log(arrFromMap); // [[1, 'one'], [2, 'two'], [3, 'three']]

Agar aapke paas Map object hai aur aap usse array mein convert karna chahte hain, toh bhi Array.from() use kiya ja sakta hai.
```

Summary:-

Array.from() ko use karke aap array-like aur iterable objects ko real arrays mein convert kar sakte hain.
    
Aap array elements ko map function ke zariye transform bhi kar sakte hain.

Ye method kaafi flexible hai aur aapke code ko zyada readable aur efficient bana sakta hai jab aapko array-like objects ke saath kaam karna ho.

# ForEach Loop Function:- 

forEach loop JavaScript mein ek array ke har element par function ko apply karne ka tareeqa hai. Ye ek method hai jo array objects par kaam karta hai aur array ke har item ke liye ek callback function execute karta hai.


```python
#Stynax:-

array.forEach(function(element, index, array) {
  // yahan pe aap har element ke liye kuch code likhte hain
});

```

element: Har ek element jo array mein hai.
index: Har element ka index (position) array mein.
array: Original array jo forEach method par apply ho raha hai.


```python
let fruits = ["Apple", "Banana", "Orange"];

fruits.forEach(function(fruit, index) {
  console.log(index + 1 + ". " + fruit);
});

#Output:- 
1. Apple
2. Banana
3. Orange
```

forEach loop break ya continue statements ko support nahi karta, yani agar aap loop ko rokna chahte hain ya skip karna chahte hain, to aapko for loop ya kisi aur method ka use karna padega.

Ye method ek callback function ko accept karta hai, jisme aap apna logic define karte hain.

# For Of Loop :-

JavaScript mein for...of loop ek tarika hai array ya kisi iterable object (jaise string, map, set) ke elements ko iterate karne ka. Iska use hum directly collection ke elements ko access karne ke liye karte hain bina index ka use kiye.


```python
const fruits = ["apple", "banana", "cherry"];

for (const fruit of fruits) {
    console.log(fruit);
}

#Output:-
apple
banana
cherry
```

for...of loop iterable objects (arrays, strings, sets, etc.) ke upar kaam karta hai.
    
Isme index ki zarurat nahi hoti, bas element hi directly milta hai.

# Difference between For in loop and for...in Loop:

for...in loop ko arrays ya objects mein indexes ya keys ko iterate karne ke liye use kiya jata hai, jabki for...of loop elements ko iterate karta hai.

for...of loop mein aap break, continue, ya return ka bhi use kar sakte hain:

for...of loop generally arrays ke liye efficient hota hai. Lekin, agar aapko index ke saath kaam karna ho ya performance critical code likhna ho, toh for loop ka use behtar ho sakta hai.

# For in Loop:-

JavaScript me for...in loop ek special loop hai jo objects ke properties ya array ke indices par iterate karne ke liye use hota hai. Yeh loop kisi bhi object ya array ke through iterate karta hai.

##### Object ke properties par iterate karna:


```python
const person = {
  name: 'Ali',
  age: 25,
  city: 'Karachi'
};

for (let key in person) {
  console.log(key + ': ' + person[key]); // Prints property name and value
}


#Output:-

name: Ali
age: 25
city: Karachi
```

#### Array ke indices par iterate karna:


```python
const numbers = [10, 20, 30, 40];

for (let index in numbers) {
  console.log(index + ': ' + numbers[index]); // Prints index and value
}

#Output:-
0: 10
1: 20
2: 30
3: 40
```

for...in loop objects ke enumerable properties ko iterate karta hai.
    
Agar aapko array ke elements par iterate karna ho toh for...in se bachna chahiye, kyunki yeh indices ko iterate karta hai, aur array ki length ke liye for loop ya forEach zyada suitable hai.

# Array Clone/Copy:-

#### Spread Operator (...)


```python
const originalArray = [1, 2, 3];
const clonedArray = [...originalArray];

console.log(clonedArray); // [1, 2, 3]

```

#### Array.slice()


```python
const originalArray = [1, 2, 3];
const clonedArray = originalArray.slice();

console.log(clonedArray); // [1, 2, 3]
```

#### Array.from()


```python
const originalArray = [1, 2, 3];
const clonedArray = Array.from(originalArray);

console.log(clonedArray); // [1, 2, 3]
```

# Spread Operaters:-

Spread operator ka use arrays, objects ya functions me elements ko expand karne, copy karne, ya merge karne ke liye kiya jata hai.

#### Arrays me Spread Operator:-

Agar aapko ek array ke elements ko dusre array me copy karna ho ya unko expand karna ho to aap spread operator ka use karte hain.

const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

console.log(arr2);  // Output: [1, 2, 3, 4, 5]

#### Objects me Spread Operator


```python
Objects me bhi spread operator ka use properties ko copy karne ya merge karne ke liye kiya jata hai.

const obj1 = { name: "Ali", age: 25 };
const obj2 = { ...obj1, city: "Karachi" };

console.log(obj2);  
// Output: { name: "Ali", age: 25, city: "Karachi" }

```

#### Function Arguments me Spread Operator

Spread operator ko aap function calls me bhi use kar sakte hain jab aapko kisi array ya iterable ke elements ko individual arguments me convert karna ho.

function sum(a, b, c) {
  return a + b + c;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers));  // Output: 6


# Destructuring of Array:-

Array destructuring ek feature hai jo JavaScript mein use hota hai, jisme aap ek array ke elements ko directly variable mein assign kar sakte hain, bina index ka use kiye. Yeh aapko code ko short aur clean banane mein madad karta hai.



```python
const arr = [1, 2, 3];

// Destructuring
const [a, b, c] = arr;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3

```

# Skipping Elements (Kuch elements ko skip karna)

Agar aap kisi array ke kuch elements ko skip karna chahte ho, to aap bas un elements ke liye blank space chhod sakte ho. Isse aap sirf wahi values pick kar sakte ho jo aapko chahiye.


```python
const arr = [10, 20, 30, 40, 50];

// Skipping elements
const [, , third, , fifth] = arr;

console.log(third); // 30
console.log(fifth); // 50
```

# Rest Operator with Destructuring

Agar aapko kisi array ka kuch part destructure karna ho aur baaki elements ko ek array ke roop mein lena ho, to aap rest operator (...) ka use kar sakte ho. Yeh baaki ke elements ko ek naye array mein collect kar leta hai.


```python
const arr = [1, 2, 3, 4, 5];

// Rest operator se baaki elements lena
const [first, second, ...rest] = arr;

console.log(first); // 1
console.log(second); // 2
console.log(rest); // [3, 4, 5]
```

# Nested Destructuring

Agar aapke paas nested arrays hain (array ke andar array), to aap unhe bhi destructure kar sakte ho.


```python
const arr = [1, [2, 3], 4];

// Nested destructuring
const [a, [b, c], d] = arr;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
console.log(d); // 4
```

# Object's

### Object.entries()


```python
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

for (const [key, value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}
```


```python
name: John
age: 30
city: New York
```

### Object.keys()


```python
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

for (const key of Object.keys(person)) {
  console.log(`${key}: ${person[key]}`);
}

```


```python
name: John
age: 30
city: New York
```

### Object.values()


```python
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

for (const value of Object.values(person)) {
  console.log(value);
}

```


```python
John
30
New York
```

# Fat Arrow Fun and Simple Function Difference:-

1. Syntax (Writing Style)

2. this Keyword
Arrow functions ka sabse bada difference unka this behavior hai. Arrow functions mein this ka value lexical hota hai, matlab yeh function ke surrounding context (scope) ke hisaab se decide hota hai.

Arrow Function mein this parent context ka reference hota hai, jo function ke call hone ke waqt determine hota hai.
Traditional Function mein this dynamic hota hai, jo function ko call karte waqt decide hota hai.


```python
const obj = {
  value: 10,
  arrowFunc: () => {
    console.log(this.value); // Undefined, because 'this' points to the global object
  },
  traditionalFunc: function() {
    console.log(this.value); // 10, because 'this' refers to the obj
  }
};

obj.arrowFunc();
obj.traditionalFunc();
```

arrowFunc mein this.value undefined hoga, kyunki this parent context (global object) ki taraf point kar raha hai.

traditionalFunc mein this.value 10 hoga, kyunki this obj ke andar point kar raha hai.

3. Constructor Function

Arrow Function ko constructor function ki tarah use nahi kar sakte. Arrow function new keyword ke sath nahi chal sakte.

Traditional Function ko aap constructor function ki tarah use kar sakte hain.


```python
const Person = (name) => {
  this.name = name;
};

const person1 = new Person('Ali'); // Error: Person is not a constructor
=========================================================
function Person(name) {
  this.name = name;
}

const person1 = new Person('Ali'); // Works fine

```

4. Arguments Object
Arrow Function mein arguments object available nahi hota. Agar aapko variable number of arguments ki zarurat hai toh traditional function mein arguments object ka use kiya ja sakta hai.


```python
const arrowFunc = () => {
  console.log(arguments); // Error: arguments is not defined
};

function traditionalFunc() {
  console.log(arguments); // Works fine, shows passed arguments
}

arrowFunc(1, 2, 3);
traditionalFunc(1, 2, 3);

```

4. Implicit Return

Arrow Function ka ek aur benefit yeh hai ke agar function sirf ek expression return karta ho, toh return likhne ki zarurat nahi hoti.

const multiply = (a, b) => a * b; // Implicit return



```python
Traditional Function mein hamesha return statement likhna padta hai agar koi value return karni ho.

function multiply(a, b) {
  return a * b;
}

```

# Rest Parameter:-

Rest parameter JavaScript mein ek feature hai jo function ke argument ko ek array ke form mein collect karta hai, jisse hum kisi bhi number of arguments ko handle kar sakte hain.

Jab hum kisi function ko define karte hain aur humein multiple arguments pass karne ka option dena hota hai, toh hum ... (three dots) ka use karte hain rest parameter ko define karte waqt. Isse function ke andar ek array create ho jaata hai jo sabhi extra arguments ko store karta hai jo function ko call karte waqt diye jaate hain.


```python
function addNumbers(...numbers) {
  return numbers.reduce((sum, num) => sum + num, 0);
}

console.log(addNumbers(1, 2, 3, 4)); // Output: 10
console.log(addNumbers(5, 10)); // Output: 15
```


```python
Rest parameter ko hamesha function ke last argument ke roop mein hona chahiye.
Rest parameter ek array banata hai, jismein function ke baaki arguments store hote hain.
```

# Map() Function:-

JavaScript mein map() function ek array method hota hai jo kisi array ke har element par ek function apply karta hai aur ek naya array return karta hai. Ye function original array ko modify nahi karta.


```python
let newArray = array.map(function(currentValue, index, array) {
  // Code to execute on each element
  return newValue; // New value that will be in the new array
});

```


```python
currentValue current element hota hai jo array ka part hota hai.

index element ka index hota hai (optional).

array poora array hota hai (optional).
```


```python
let numbers = [1, 2, 3, 4, 5];

let doubled = numbers.map(function(num) {
  return num * 2;
});

console.log(doubled); // Output: [2, 4, 6, 8, 10]

```

Haan, map() method JavaScript mein ek new array return karta hai. Ye original array ko modify nahi karta, balki usse ek naya array create karta hai jisme updated values hoti hain jo function ke through generate hoti hain.


```python
let numbers = [1, 2, 3, 4, 5];

let doubled = numbers.map(function(num) {
  return num * 2;
});

console.log(numbers);  // Output: [1, 2, 3, 4, 5] (original array unchanged)
console.log(doubled);  // Output: [2, 4, 6, 8, 10] (new array)
```

# Filter Function:-

JavaScript mein filter() ek array method hai jo ek new array return karta hai jo un elements ko contain karta hai jo given condition ya callback function se pass hote hain.


```python
array.filter(function(element, index, array) {
  // return condition for each element
});
```


```python
element: Array ka current element jo function ko pass hota hai.

index: Current element ka index.

array: Poora array.
```


```python
//Example--01

const numbers = [1, 2, 3, 4, 5];

// Sabhi even numbers ko filter karna
const evenNumbers = numbers.filter(function(num) {
  return num % 2 === 0;  // Sirf even numbers ko return karo
});

console.log(evenNumbers);  // Output: [2, 4]

```


```python
//Example--02

const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);  // Output: [2, 4]
```

# Reduse Function:-

JavaScript mein reduce() ek array method hota hai jo array ke elements ko ek single value mein reduce (combine) karta hai. Ye method array ke har element par ek callback function apply karta hai, jo accumulate karte hue result return karta hai.


```python
array.reduce(callback(accumulator, currentValue, currentIndex, array), initialValue);
```

callback: Ye function jo har element ke liye call hota hai. Iske 4 parameters hote hain:

accumulator: Ye wo value hoti hai jo har iteration ke baad update hoti hai.

currentValue: Ye array ka current element hota hai.

currentIndex (optional): Ye current element ka index hota hai.

array (optional): Ye poora array hota hai jisme reduce method apply ho raha hai.

initialValue (optional): Ye wo value hoti hai jo accumulator ko initial value ke taur par assign hoti hai. Agar ye provide nahi kiya jata, toh array ka pehla element initial value ke roop mein use hota hai.


```python
let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 0); // 0 is the initial value

console.log(sum);  // Output: 15

```

# Find Function:-

In JavaScript, the find() function is an array method that allows you to search for an element in an array that satisfies a given condition (i.e., a predicate function). It returns the first element that meets the condition, or undefined if no element satisfies the condition.


```python
array.find(callback(element[, index[, array]])[, thisArg])
```
callback: A function that is called for every element in the array. It accepts three arguments:
element: The current element being processed.
index: The index of the current element (optional).
array: The array that find() was called on (optional).
thisArg: (Optional) A value to use as this when executing the callback.

```python
//Example-01

const people = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 35 }
];

const person = people.find(person => person.name === "Bob");

console.log(person); // { name: "Bob", age: 30 }

```


```python
//Example --> 02

const numbers = [1, 2, 3, 4];

const result = numbers.find(num => num > 5);

console.log(result); // undefined (since no number is greater than 5)

```
find() only returns the first element that matches the condition.
If no match is found, it returns undefined.
The method does not modify the original array.
# Every() Method

JavaScript mein every() method ek array method hai jo array ke har element ko ek specified test function ke saath check karta hai. Agar array ka har element us test ko pass kar leta hai, toh every() method true return karta hai. Agar koi bhi element test ko pass nahi karta hai, toh yeh false return karta hai.


```python
array.every(function(currentValue, index, array) {
  // return true or false
}, thisArg);
```

function(currentValue, index, array): Ye ek callback function hai jo har element ke liye execute hota hai.

currentValue: Array ka current element jo function ke saath pass kiya gaya hota hai.

index (optional): Current element ka index.

array (optional): Original array jo every() method par call kiya gaya tha.

thisArg (optional): Agar aapko this ka specific value pass karni ho toh, isko use kar sakte ho.


```python
let numbers = [2, 4, 6, 8];

let result = numbers.every(function(num) {
  return num % 2 === 0; // Check if the number is even
});

console.log(result);  // Output: true

```


```python
let numbers = [2, 4, 6, 7];

let result = numbers.every(function(num) {
  return num % 2 === 0; // Check if the number is even
});

console.log(result);  // Output: false

```

every() method agar array ka har element condition ko satisfy karta hai toh true return karta hai, agar ek bhi element condition ko satisfy nahi karta, toh false return hota hai.

Agar array empty hai, toh every() method automatically true return karega, kyunki condition ko kisi bhi element ko check nahi karna padta.

# Some() Method:-

JavaScript mein some() method ek array method hai jo check karta hai ki array ke kisi bhi element ne condition ko satisfy kiya hai ya nahi. Agar array ka koi element specified condition ko meet karta hai, to yeh method true return karta hai, aur agar koi element match nahi karta to false return karta hai.


```python
array.some(callback(currentValue, index, array), thisArg);
```

callback: Ek function jo har array element ke liye call hota hai. Is function ko 3 arguments milte hain:

currentValue: Array ka current element.

index: Current element ka index (optional).

array: Pura array (optional).

thisArg: Optional. Agar provided kiya jaye, to callback function ke liye this value ko set karta hai.


```python
let numbers = [1, 2, 3, 4, 5];

let hasEven = numbers.some(function(num) {
  return num % 2 === 0;  // Checking if any number is even
});

console.log(hasEven);  // Output: true, because 2 and 4 are even
```

Is example mein, some() method check karta hai ki kya array ke kisi bhi element mein even number hai. Agar hai, to result true hoga.

Agar array mein koi bhi element condition ko match nahi karta, to result false hoga.


```python
let numbers = [1, 3, 5, 7];

let hasEven = numbers.some(function(num) {
  return num % 2 === 0;  // Checking if any number is even
});

console.log(hasEven);  // Output: false, because no even numbers

```

# Fill Method :-

JavaScript mein fill() ek array method hai jo ek array ko ek specific value se fill karta hai. Ye method ek array ko modify karta hai aur uske specified elements ko replace kar deta hai.


```python
array.fill(value, start, end)
```

value: Ye wo value hai jo aap array ke specified elements mein fill karna chahte hain.

start (optional): Ye wo index hai jahan se fill karna start hoga. Agar specify na kiya gaya ho, to default value 0 hoti hai.

end (optional): Ye wo index hai jahan tak fill karna hoga (excluding the end index). Agar specify na kiya gaya ho, to default value array ki length hoti hai.


```python
let arr = [1, 2, 3, 4, 5];

// Fill the array with 0 from index 2 to 4 (excluding 4)
arr.fill(0, 2, 4);

console.log(arr); // Output: [1, 2, 0, 0, 5]

```


```python
let arr = [1, 2, 3, 4, 5];

// Fill the array with 10
arr.fill(10);

console.log(arr); // Output: [10, 10, 10, 10, 10]

```

# Insert A Element in Array:-

#### Insert an element at the end of the array:


```python
let arr = [1, 2, 3];
arr.push(4);  // Insert 4 at the end
console.log(arr);  // Output: [1, 2, 3, 4]

```

#### Insert an element at the beginning of the array:


```python
let arr = [1, 2, 3];
arr.unshift(0);  // Insert 0 at the beginning
console.log(arr);  // Output: [0, 1, 2, 3]

```

#### Insert an element at a specific index in the array:


```python
let arr = [1, 2, 4, 5];
arr.splice(2, 0, 3);  // Insert 3 at index 2 (before the element 4)
console.log(arr);  // Output: [1, 2, 3, 4, 5]

```

The first argument (2) is the index at which to start.
The second argument (0) is the number of elements to remove (since we are just inserting, we remove 0 elements).
The third argument (3) is the element to insert.

# This Keyword:-

JavaScript mein this ek special keyword hota hai jo current execution context ya object ko refer karta hai. Yeh apne execution ke context ke hisaab se alag-alag behave karta hai.

#### this ka behavior kis context mein hota hai:

Global context (outside any function): Agar aap this ko directly global scope mein use karte hain (jaise browser mein, jab koi function nahi chal raha hota), toh this window object ko refer karega.


```python
console.log(this);  // In browser, this will refer to the window object
```

Function context: Agar aap function ke andar this use karte hain, toh this uss function ke call karne wale context ko refer karega.


```python
function example() {
    console.log(this);  // In non-strict mode, this refers to the global object (window in browsers)
}
example();

```

Method context: Jab this ko object ke method ke andar use kiya jata hai, toh this uss object ko refer karta hai.


```python
const obj = {
    name: "JavaScript",
    greet: function() {
        console.log(this.name);  // 'this' refers to the obj object
    }
};
obj.greet();  // Output: JavaScript

```

Arrow functions: Arrow functions mein this ka behavior normal functions se thoda alag hota hai. Arrow function apna this inherit karta hai jo usse baahar ke context mein hota hai, iska apna this nahi hota.


```python
const obj = {
    name: "JavaScript",
    greet: () => {
        console.log(this.name);  // 'this' refers to the global context, not the obj object
    }
};
obj.greet();  // Output will be undefined or error depending on context

```

Constructor functions: Agar aap this ko constructor function mein use karte hain, toh this newly created object ko refer karta hai.


```python
function Person(name) {
    this.name = name;
}
const person1 = new Person("John");
console.log(person1.name);  // Output: John

```

#### Conclusion:

this JavaScript mein ek dynamic keyword hai aur iske behavior ko samajhna zaroori hai, kyunki wo different contexts mein alag tareeke se behave karta hai. Yeh bahut powerful tool hai jab aap object-oriented programming ya functions ke saath kaam karte hain.

# New KeyWord

JavaScript mein new keyword ka use ek object ko create karne ke liye kiya jata hai, jab hum kisi class ya constructor function ka instance banana chahte hain.

Jab aap new keyword ka use karte hain, to yeh kuch steps perform karta hai:

1.Ek naya object banata hai.

2.Us object ko constructor function ke context mein set karta hai.

3.Agar constructor function mein return statement na ho, to by default this ko return karta hai jo object hai.

4.Agar constructor function ke andar return value ho (for example, ek object), to wahi object return hota hai.


```python
//Example---01


function Person(name, age) {
    this.name = name;
    this.age = age;
}

let person1 = new Person('John', 30);
console.log(person1.name); // Output: John
console.log(person1.age);  // Output: 30


//Example --02

class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}

let person1 = new Person('John', 30);
console.log(person1.name); // Output: John

```

## new Keyword ka Working:

Jab aap new keyword ka use karte hain, to JavaScript kuch internal steps follow karta hai:

#### Ek Naya Object Create Hota Hai:
Jab aap new ke saath kisi constructor ko call karte hain, to JavaScript internally ek naya empty object banata hai.

#### Constructor Function Ko Call Kiya Jata Hai:
Us object ko this context ke saath constructor function mein pass kiya jata hai, jisse ki aap this ke through us object ke properties set kar sakein.

#### Prototype Chain Setup Hoti Hai:
JavaScript mein har object ka ek prototype hota hai, aur jab new keyword se object create hota hai, to us object ka prototype us constructor function ke prototype object se set hota hai. Iska matlab yeh hai ki us object ko constructor function ke prototype methods aur properties bhi milte hain.

#### Return Statement:
Agar aap constructor function mein explicitly koi value return nahi karte, to new keyword this ko return karta hai, jo ki created object hota hai. Agar constructor mein koi non-object return hota hai (for example, primitive types like string ya number), to woh ignore ho jata hai aur this object hi return hota hai.

##Summary:

new ek object create karta hai, usme constructor function ko run karta hai, aur object ko return karta hai.

new keyword se object ko this context milta hai, jisse us object ki properties set hoti hain.

new se ek class ya constructor function ka instance banaya jata hai, jo methods aur properties ko inherit karne mein madad karta hai.

# DOM (Document Object Model)

DOM ka matlab hai Document Object Model. Ye ek programming interface hota hai jo web pages ko manipulate karne ke liye use hota hai. Jab aap ek webpage ko browser mein dekhte hain, to us page ka HTML code ek structure ke roop mein DOM ke through browser mein load hota hai.

DOM ek tree structure mein hota hai, jisme har element (jaise paragraphs, images, links, etc.) ek node hota hai. Aap JavaScript ya kisi aur programming language ka istemal karke DOM ko modify kar sakte hain, jaise content ko change karna, elements ko add ya remove karna, ya kisi element ko style dena.

Example: Jab aap JavaScript se kisi button ko click karne par kisi text ko change karte hain, to aap actually DOM ko modify kar rahe hote hain.

DOM ka main kaam: DOM ek tree-like structure mein hota hai, jisme har element (jaise paragraphs, headings, images, links, etc.) ek node ke roop mein represent hota hai. Is model ki madad se developers web page ke content aur structure ko dynamically manipulate kar sakte hain.

#### DOM ko use karne ki zarurat kyu hoti hai?

1. Dynamic Content Changes: DOM ka use isliye hota hai taaki aap dynamically webpage ka content change kar sakein bina page ko dobara se reload kiye. Jaise, kisi button ko click karne par content change karna, ya kisi input field mein entered value ko instantly process karna.

2. Event Handling: DOM events ko handle karne ke liye use kiya jata hai, jaise button click, mouse hover, form submission, etc. JavaScript ka use karke hum in events ko handle karte hain aur uske response mein page ka content update karte hain.

3. Interactive Features: Agar aapko webpage mein interactive elements add karne hain, jaise sliders, pop-ups, or animations, to DOM ke zariye aap easily in elements ko manipulate kar sakte hain.

4. CSS Styling: DOM ka use CSS ke saath combine karke elements ki style ko change karne ke liye bhi hota hai. Aap JavaScript se DOM ko modify karke kisi element ki styling (color, size, position, etc.) ko dynamically update kar sakte hain.

# innerHTML and innerText me kya diff ha?


### innerHTML:-

Purpose: Yeh property element ke andar ka HTML content ko access ya modify karne ke liye use hoti hai.

Kaise kaam karti hai: Agar aap innerHTML ko read karte hain, toh yeh element ke andar ka saara HTML content (tags ke sath) return karta hai. Agar aap innerHTML ko set karte hain, toh aap us element ke content ko HTML format me update karte hain.


```python
<div id="example"><p>Hello <b>World</b></p></div>
<script>
  let divContent = document.getElementById("example").innerHTML;
  console.log(divContent); // Outputs: <p>Hello <b>World</b></p>
</script>

```

#### innerText:-

Purpose: Yeh property element ke visible text content ko access ya modify karne ke liye use hoti hai. Yeh text ko sirf plain text ke roop me return karta hai, aur kisi bhi HTML tags ko ignore karta hai.

Kaise kaam karti hai: Agar aap innerText ko read karte hain, toh yeh sirf visible text ko return karega, bina HTML tags ke. Agar aap innerText ko set karte hain, toh aap plain text update kar rahe hote hain, aur existing HTML tags ko remove kar dete hain.


```python
<div id="example"><p>Hello <b>World</b></p></div>
<script>
  let divText = document.getElementById("example").innerText;
  console.log(divText); // Outputs: Hello World
</script>
```

# getAtteribute and getAtteributeNode me kya dif ha?

## getAttribute():
Ye method kisi element ka attribute value return karta hai.

Jab aap getAttribute() ka use karte hain, toh ye sirf attribute ki value ko return karta hai (agar attribute exist karta hai).

Agar attribute exist nahi karta, toh ye null return karta hai.


```python
const element = document.getElementById('myElement');
let value = element.getAttribute('class'); // "myClass"
```

## getAttributeNode():

Ye method attribute ka node return karta hai, na ke uski sirf value.
    
Iska return value ek Attr object hota hai, jisme name (attribute ka naam) aur value (attribute ki value) dono properties hoti hain.

Agar attribute exist nahi karta, toh null return hota hai.


```python
const element = document.getElementById('myElement');
let attributeNode = element.getAttributeNode('class'); 
console.log(attributeNode.name);  // "class"
console.log(attributeNode.value); // "myClass"
```

### Key Difference:

getAttribute() sirf attribute ki value ko return karta hai, jabki getAttributeNode() ek node return karta hai, jisme attribute ka naam aur value dono hote hain.

### When to use which?

1. Agar aapko sirf attribute ki value chahiye, toh getAttribute() use karein.

2. Agar aapko attribute ka name ya kisi aur specific property ki zaroorat ho, toh getAttributeNode() use karein.

# SetAtteributes 

DOM (Document Object Model) mein, setAttribute ek method hota hai jo kisi element ki attribute ko set (ya update) karne ke liye use kiya jata hai. Iska use hum tab karte hain jab humein kisi HTML element (jaise <div>, <img>, <input>, etc.) ka attribute change karna ho.


```python
#Syntax:-
element.setAttribute(attributeName, value);
```

attributeName: Ye wo attribute ka naam hota hai jo aap set karna chahte hain, jaise "src", "href", "class", etc.

value: Ye wo value hoti hai jo aap attribute ko dena chahte hain.

# Remove attribute

Remove attribute" ka matlab hota hai kisi object ya element ka koi specific attribute ya property hata dena. Ye term zyada tar programming, web development, ya data manipulation mein use hoti hai.

For example, agar aap HTML mein kisi element (jaise <div> ya <img>) se koi attribute (jaise class, src, id, etc.) remove karna chahte hain, to aap JavaScript mein removeAttribute() method ka use karte hain.


```python
#Syntax
document.getElementById("myImage").removeAttribute("src");
```

Is code mein, "src" attribute ko myImage id wale image element se remove kiya gaya hai.

Is tarah se, aap kisi bhi element se unwanted attributes ko hata sakte hain.

removeAttribute() method koi value return nahi karta. Ye method sirf attribute ko remove karne ka kaam karta hai aur uska koi return value nahi hota.

Matlab agar aap removeAttribute() ko call karte hain, to wo attribute ko element se hata deta hai, lekin aapko koi value (jaise true ya false) return nahi hoti.


```python
let element = document.getElementById("myImage");
let result = element.removeAttribute("src");

console.log(result); // undefined (kuch return nahi hota)
```

Is example mein, result ki value undefined hogi kyunki removeAttribute() method koi value return nahi karta. Wo sirf element se attribute ko hata deta hai

# QuerySelecter and QuerySelecterAll

querySelector aur querySelectorAll dono methods hain jo JavaScript mein use hoti hain, lekin in dono mein ek important difference hota hai:

## querySelector:

Ye method pehli matching element ko select karta hai jo given CSS selector se match karta hai.
    
Agar multiple elements match karte hain, to querySelector sirf pehla element return karega.


```python
const element = document.querySelector('.my-class');
```

### querySelectorAll:

Ye method sabhi elements ko return karta hai jo given CSS selector se match karte hain.

Ye ek NodeList return karta hai jo selected elements ka collection hota hai.


```python
const elements = document.querySelectorAll('.my-class');
```

Ye code sabhi elements ko select karega jinka class my-class ho, aur wo elements ek NodeList mein honge.

### Summary:

querySelector: Pehla matching element return karta hai.

querySelectorAll: Sabhi matching elements ko return karta hai (NodeList mein).

# eventListener 

JavaScript mein, eventListener ek method hota hai jo kisi bhi DOM element ko kisi specific event (jaise ki click, hover, key press, etc.) ke liye listen karne ka tareeqa deta hai. Matlab, jab bhi wo event us element par hota hai, tab ek specified function ya action execute hota hai.

eventListener ko use karte waqt, hum ek event type specify karte hain (jaise "click", "keypress", "load", etc.) aur ek callback function jo tab execute hoga jab wo event trigger ho.


```python
element.addEventListener('event_type', function() {
    // Callback function code
});
```

Agar aap chahte hain ke jab user kisi button ko click kare to ek message show ho, to aap kuch is tarah se eventListener use karenge:


```python
// HTML element
<button id="myButton">Click Me</button>

// JavaScript code
let button = document.getElementById('myButton');

button.addEventListener('click', function() {
    alert('Button clicked!');
});

```

addEventListener event ko handle karta hai.

event_type wo event hota hai jo trigger hoga (jaise "click", "mouseover", etc.).

callback function wo function hai jo execute hoga jab event occur kare.

# addeventlistener and removeeventlistener diff?


### addEventListener:

Iska use kisi element par event listener ko add karne ke liye kiya jata hai.

Jaise agar aap chahte hain ke jab user kisi button ko click kare, to ek function call ho, to aap addEventListener ka use karenge.


```python
const button = document.querySelector('button');
button.addEventListener('click', function() {
  alert('Button clicked!');
});

```

### removeEventListener:

Iska use kisi pehle se added event listener ko remove karne ke liye kiya jata hai.

Ye method tab use hota hai jab aap kisi event listener ko hataana chahte hain, taake wo future me trigger na ho.

Isme ek zaroori baat hai: jab aap removeEventListener use karte hain, to aapko wahi function reference dena padta hai jo addEventListener me use kiya gaya ho. Agar aap anonymous function (jo directly likha ho) use kar rahe hain, to wo remove nahi hoga.


```python
const button = document.querySelector('button');
function handleClick() {
  alert('Button clicked!');
}
button.addEventListener('click', handleClick);

// Later in the code
button.removeEventListener('click', handleClick);

```

# setTimeOut and ClearTimeOut me kya Diff ha?


### setTimeout:

Is function ka use ek specific time ke baad koi code execute karne ke liye kiya jata hai.

Ye function ek "timeout" set karta hai, jo ek time interval ke baad execute hota hai.


```python
setTimeout(function() {
  console.log("This will run after 3 seconds");
}, 3000);

```

### clearTimeout:

Jab aapko setTimeout ko cancel karna ho, tab clearTimeout ka use kiya jata hai.

Ye function ek timeout ko cancel karta hai, agar wo timeout ab tak execute nahi hua ho.

Aapko setTimeout ke return value ko clearTimeout mein pass karna padta hai, jo timeout ko cancel karne ka kaam karta hai.


```python
var timeoutId = setTimeout(function() {
  console.log("This won't run if cleared");
}, 3000);

// Ab timeout ko cancel karte hain
clearTimeout(timeoutId);

```

setTimeout: Kisi code ko specific time ke baad execute karne ke liye use hota hai.

clearTimeout: Ek already set ki gayi timeout ko cancel karne ke liye use hota hai.

# SetInterval and ClearInterval

### setInterval():

Ye function ek specific task ko regular interval par execute karta hai.

Iska syntax kuch is tarah hota hai:


```python
setInterval(function, interval);
```

function: Ye wo function hai jo aap ko execute karna hai.

interval: Ye wo time (in milliseconds) hai jo aap chahte hain ki function execute hone se pehle gap ho.


```python
setInterval(() => {
    console.log("This will print every 2 seconds");
}, 2000); // 2000 milliseconds = 2 seconds

```

### clearInterval():
Ye function ek active setInterval ko stop karta hai.

Jab aapko interval ko rokna ho, to aap clearInterval() ka use karte hain.

setInterval jab call hota hai, to wo ek ID return karta hai, jisse aap interval ko clear kar sakte hain.

Iska syntax kuch is tarah hota hai:


```python
clearInterval(intervalID);
```


```python
const intervalID = setInterval(() => {
    console.log("This will print every 2 seconds");
}, 2000);

// Stop the interval after 5 seconds
setTimeout(() => {
    clearInterval(intervalID);
    console.log("Interval has been cleared");
}, 5000);

```

Is example mein, setInterval() har 2 second baad console.log() print karega, lekin 5 second ke baad clearInterval() use karke interval ko stop kar diya jayega.

setInterval(): Task ko regular interval pe repeat karta hai.
    
clearInterval(): Interval ko stop karta hai jo setInterval() ke through start kiya gaya tha.

## Key Points:

#### Return Value of setInterval():

Jab aap setInterval() function call karte hain, to wo ek unique interval ID return karta hai. Is ID ko aapko use karna hota hai jab aap interval ko clearInterval() ke zariye stop karte hain.

Ye interval ID har ek interval call ke liye alag hota hai.

#### clearInterval() ko Galat Use Karna:

Agar aap galat ID use karte hain clearInterval() mein, to wo koi effect nahi karega. Isliye ensure karein ki aap correct interval ID pass kar rahe hain.

Agar interval ki zaroorat nahi hai ya jab aap usse stop karna chahte hain, to hamesha clearInterval() ka use karein.

# CallBack Function:-

JavaScript mein callback function ek aisa function hota hai jo kisi doosre function ke argument ke roop mein pass kiya jata hai, aur doosra function jab apna kaam complete karta hai, tab wo callback function ko call karta hai.

Simple shabdon mein, jab ek function kisi dusre function ko as an argument deta hai, to usse hum callback function kehte hain. Callback function ka use hum usually asynchronous operations jaise ki data fetch karne ya event handling mein karte hain.

Callback functions ka use hum asynchronous code ko handle karne ke liye karte hain, taaki ek kaam complete hone par doosra kaam execute ho sake.


```python
function greet(name) {
    console.log("Hello " + name);
}

function processUserInput(callback) {
    var name = "Alice";
    callback(name);  // Callback function ko call kiya
}

processUserInput(greet);  // greet function ko callback ke roop mein pass kiya

```

Is example mein, processUserInput function ko greet function ko callback ke roop mein pass kiya gaya hai. Jab processUserInput apna kaam complete karta hai (yaha pe name set karne ka), tab wo greet function ko call karta hai.


```python
function fetchData(callback) {
    setTimeout(() => {
        let data = "Data fetched";
        callback(data);  // Asynchronous kaam complete hone par callback function ko call kiya
    }, 2000);
}

fetchData(function(result) {
    console.log(result);  // "Data fetched" output hoga
});

```

# Callback Hell

Callback Hell (or Pyramid of Doom) ek term hai jo JavaScript me tab use hoti hai jab aap bohot zyada nested callbacks use karte hain, jiski wajah se code ka structure complex aur difficult to maintain ho jata hai.

JavaScript me asynchronous programming kaafi common hai, aur callback functions ka use uss waqt hota hai jab aapko kisi task ke complete hone ke baad next task perform karna ho. Jab aap multiple asynchronous tasks ko ek ke baad ek execute karte hain aur har ek task ke liye callback function ka use karte hain, toh code ka structure itna nested ho jata hai ki wo samajhna mushkil ho jata hai.


```python
doSomething(function(result1) {
    doSomethingElse(result1, function(result2) {
        doThirdThing(result2, function(result3) {
            doFourthThing(result3, function(result4) {
                // And so on...
                console.log(result4);
            });
        });
    });
});

```

## Callback Hell ke issues:

### Readability: 
Code samajhna mushkil hota hai jab callbacks deeply nested ho.

### Maintainability: 
Agar code me koi bug ho ya aapko kuch modify karna ho, toh changes karna bohot tough hota hai.

### Error Handling: 
Error handling bhi complex ho jati hai jab har nested callback ke andar alag error handling ki zaroorat padti hai.

### Callback Hell ka solution

### Promises:
Promises ka use karke aap callback hell ko avoid kar sakte hain. Promises ko then() aur catch() ke saath use karke, aap asynchronous code ko chain kar sakte hain.


```python
doSomething()
    .then(result1 => doSomethingElse(result1))
    .then(result2 => doThirdThing(result2))
    .then(result3 => doFourthThing(result3))
    .then(result4 => console.log(result4))
    .catch(error => console.error(error));

```

### Async/Await: 
Async/await syntax ka use karke asynchronous code ko synchronous jaisa likha ja sakta hai, jisse code zyada readable aur maintainable ho jata hai.


```python
async function executeTasks() {
    try {
        const result1 = await doSomething();
        const result2 = await doSomethingElse(result1);
        const result3 = await doThirdThing(result2);
        const result4 = await doFourthThing(result3);
        console.log(result4);
    } catch (error) {
        console.error(error);
    }
}

```

# Promise

JavaScript mein Promise ek object hota hai jo asynchronously kaam karta hai, yani ki ek future value ko represent karta hai jo abhi available nahi hai lekin future mein milne wali hai.

JavaScript me Promise ek object hai jo kisi Asynchronous operation ke eventual completion (safalta) ya failure (asafalta) aur uski resulting value ko represent karta hai


Promise ka basic concept yeh hai:-

- Pending: Jab promise abhi resolve ya reject nahi hota, tab wo pending state mein hota hai.
- Resolved (Fulfilled): Jab promise successfully complete ho jata hai, to wo resolved state mein chala jata hai.
- Rejected: Agar promise kisi error ya failure ki wajah se fail ho jata hai, to wo rejected state mein chala jata hai.


```python
let myPromise = new Promise((resolve, reject) => {
    let success = true;  // yeh condition change ho sakti hai

    if(success) {
        resolve("Operation was successful!");
    } else {
        reject("Operation failed!");
    }
});

myPromise
    .then((result) => {
        console.log(result);  // Agar promise resolve ho gaya
    })
    .catch((error) => {
        console.log(error);  // Agar promise reject ho gaya
    });

```

new Promise() constructor ke andar ek function hota hai jo resolve ya reject ko call karta hai.

.then() method ko use karke hum result ko handle karte hain jab promise resolve hota hai.

.catch() method ko use karke hum errors ko handle karte hain jab promise reject hota hai.

# Promise Chaining 

Promise Chaining ka matlab hota hai ek promise ke result ko use karte hue doosre promise ko sequentially execute karna. Isme ek promise ka result, dusre promise ko handle karne mein use hota hai, aur is tarah se promises ko chain kiya jaata hai.

Jab aap .then() method ko call karte ho, to wo ek naya promise return karta hai, jo aap chain kar sakte ho. Isse aap ek promise ke result ke basis par agle steps ko execute kar sakte ho.


```python
let myPromise = new Promise((resolve, reject) => {
    let success = true;

    if(success) {
        resolve("First operation was successful!");
    } else {
        reject("First operation failed!");
    }
});

myPromise
    .then((result) => {
        console.log(result);  // "First operation was successful!"
        return "Second operation is starting";  // Yeh return hoga aur next .then() mein pass hoga
    })
    .then((message) => {
        console.log(message);  // "Second operation is starting"
        return "Third operation is starting";  // Yeh bhi return hoga
    })
    .then((finalMessage) => {
        console.log(finalMessage);  // "Third operation is starting"
    })
    .catch((error) => {
        console.log(error);  // Agar koi error aata hai toh catch block handle karega
    });

```

First then(): Agar first promise resolve ho jata hai, to first then() ka callback execute hota hai. Isme hum ek message return karte hain.
    
Second then(): Jo message first then() se return hota hai, wo second then() ko milta hai aur next operation handle hota hai.

Third then(): Ye sequence continue hota hai, aur last then() ka result show hota hai.

Sequential Execution: Aap asynchronous operations ko ek sequence mein execute kar sakte hain.

Error Handling: Agar kisi bhi promise mein error aata hai, to wo .catch() ke through handle kiya jaata hai.

# Async and Await 

JavaScript me async aur await asynchronous programming ko handle karne ke liye use hote hain. Inka use aise cases me hota hai jahan hume code ko ek time par chalana hota hai, lekin kisi task ko complete hone me thoda waqt lagta hai, jaise kisi API se data fetch karna ya kisi file ko read karna.

#### async:
async ek keyword hai jo function ke aage lagaya jata hai, isse function ko asynchronous bana diya jata hai. Jab aap kisi function ko async banate hain, to us function ke andar aap await ka use kar sakte hain, aur wo promise ko handle kar sakega.


```python
async function myFunction() {
  // Code here runs asynchronously
}
```

### await:
await ko aap sirf async function ke andar hi use kar sakte hain. Iska kaam hota hai kisi asynchronous operation ko wait karna jab tak wo complete na ho jaye, aur uske baad aage ka code execute hota hai.


```python
async function getData() {
  let response = await fetch('https://api.example.com/data');
  let data = await response.json();
  console.log(data);
}

```

### async aur await ka fayda:

Code ko clean aur readable banaata hai: Traditional promise chaining ke comparison me, async/await ka use karna zyada readable aur samajhne me asaan hota hai.

Error handling: try/catch blocks ka use karke errors ko easily handle kiya ja sakta hai.


```python
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com/data');
    if (!response.ok) throw new Error('Network response was not ok');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.log('Error:', error);
  }
}

```

async function ko asynchronous banaata hai.

await kisi promise ka result lene ke liye wait karta hai, lekin code execution ko block nahi karta (event loop ko free rakhta hai).

# self-invoked function

A self-invoked function in JavaScript, also known as an Immediately Invoked Function Expression (IIFE), is a function that is defined and executed immediately after its creation.


```python
(function() {
  console.log("This is a self-invoked function!");
})();
```

# Event bubbling

JavaScript me event bubbling ek event propagation mechanism hai jisme event sabse pehle child element pe trigger hota hai aur phir parent elements ki taraf propagate (bubble) karta hai. Iska matlab hai ki jab koi event (jaise click, mouseover, etc.) kisi element par hota hai, to wo pehle us element ko handle karega, phir us element ke parent ko, phir uske parent ko, aur aise hi ye parent elements ki chain me upar ki taraf jaata hai, jab tak ki DOM tree ke root element tak nahi pahuch jata.

### Event Bubbling ka Example

Maan lijiye, ek {button} element hai jo ek {div} element ke andar hai. Agar dono par click event listeners hain, to jab aap {button} ko click karenge, pehle wo button ka click event trigger hoga, phir wo event {div} ke click listener ko bhi trigger karega (agar uspar bhi event listener set ho).


```python
<div id="parent">
  <button id="child">Click Me!</button>
</div>

<script>
  // Parent div pe event listener
  document.getElementById("parent").addEventListener("click", function() {
    alert("Parent clicked!");
  });

  // Child button pe event listener
  document.getElementById("child").addEventListener("click", function(event) {
    alert("Button clicked!");
    // event.stopPropagation(); // Isse event bubbling stop ho jayegi
  });
</script>

```

Pehle "Button clicked!" alert show hoga.

Phir "Parent clicked!" alert bhi show hoga, kyunki event bubbling ke through parent element ko bhi trigger kiya jaata hai.

Agar aap chahte hain ke event bubbling na ho, to aap event.stopPropagation() ka use kar sakte hain, jo event ko propagate hone se rok dega.

##### Summary:

Event bubbling ek default behavior hai jisme event child se parent element tak propagate hota hai.

Aap is behavior ko stopPropagation() se rok sakte hain.

# Event Delegation

JavaScript mein event delegation ek technique hai jisme hum ek parent element pe event listener lagate hain, aur uske child elements pe hone wale events ko handle karte hain. Isse hum directly child elements pe event listener apply karne ki bajaye, parent element pe event listener laga kar code ko zyada efficient aur maintainable bana sakte hain.

### Event Delegation ka kaam kaise karta hai?
Jab hum kisi event ko handle karte hain, jaise click ya hover, toh normally hum har ek child element par event listener laga dete hain. Lekin jab humare paas bohot saare child elements hoon, toh yeh approach inefficient ho sakti hai.

Event delegation mein, hum parent element par ek event listener lagate hain, aur jab koi child element trigger hota hai, toh event parent element tak bubble hota hai. Iske baad, hum event target ko check karte hain aur appropriate action perform karte hain.


```python
document.querySelector('.list').addEventListener('click', function(event) {
  if (event.target && event.target.matches('li.list-item')) {
    console.log('Item clicked: ', event.target.textContent);
  }
});

```

Is case mein, humne .list (parent element) pe ek event listener laga diya hai. Jab bhi koi click event kisi child .list-item par hoga, toh wo event .list par bubble ho kar aayega aur hum event target ko check kar ke uss item ka action perform karenge.

### Benefits of Event Delegation:

Performance Improve hoti hai: Agar bohot saare child elements hain, toh parent element pe ek hi listener hona chahiye, jisse memory usage aur processing time kam hota hai.

Dynamic content handle kar sakte hain: Agar list mein elements dynamically add ya remove ho rahe hain, toh aapko har time individual event listener add/remove nahi karni padti.

Code cleaner aur maintainable hota hai: Aapko bar-bar child elements pe event listener nahi lagana padta, bas parent pe ek listener laga kar kaam ho jata hai.

Memory Efficiency: Aapko har child element par alag se event listener lagane ki zarurat nahi hai. Sirf ek parent element pe listener laga ke saare child elements handle kiye jaa sakte hain.

Dynamic Content Support: Agar dynamically koi new li item add hota hai, toh aapko uss pe event listener manually add karne ki zarurat nahi hoti. Parent listener automatically new item ko handle karega.

Code Simplification: Code zyada clean aur maintainable ho jata hai, especially jab large DOM structures ho.

### Jab Kabhi Event Delegation Use Karna:

Multiple child elements hain jin par aapko ek hi type ka event handle karna ho.

Agar aapke elements dynamically create hote hain ya remove hote hain.

Performance ko improve karna ho, especially jab large DOM tree ho.


```python
document.getElementById('item-list').addEventListener('click', function(event) {
  // Check if the clicked element is a list item
  if (event.target && event.target.matches('li.list-item')) {
    alert(event.target.textContent); // Show the clicked item
  }
});

```

Event Trigger: Jab bhi li element pe click hota hai, toh click event us li element pe trigger hota hai.

Event Bubbling: Click event li element se parent element ul tak bubble karta hai. Agar ul element pe event listener laga ho, toh wo parent listener handle karega.

Event Target Matching: Hum event.target ka use karte hain, jo bataata hai ki event kis specific element pe hua. Hum event.target.matches('li.list-item') se ensure karte hain ki event sirf li element pe trigger ho raha ho.



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
