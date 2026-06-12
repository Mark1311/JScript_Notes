# What is Higher Order function:-
JavaScript me Higher-Order Function ek aisa function hota hai jo ya toh ek ya ek se zyada functions ko as an argument (input) leta hai, ya fir ek naye function ko as a result (output) return karta hai.

### Higher-Order Functions Ke Do Main Types

> Type A: Function Jo Doosre Function Ko As an Argument Leta Hai
Jo function andar pass kiya jata hai, use hum Callback Function kehte hain, aur jo function use receive karta hai use Higher-Order Function kehte hain.
```js
// 1. Yeh ek normal function hai (Callback Function)
function greet() {
    return "Hello World!";
}

// 2. Yeh ek Higher-Order Function hai kyunki yeh argument me function le raha hai
function wrapperFunction(callback) {
    console.log("HOF Starting...");
    console.log(callback()); // Yahan callback function run ho raha hai
}

// Wrapper function ko call kiya aur greet function pass kar diya
wrapperFunction(greet);
```
> Type B: Function Jo Ek Naye Function Ko Return Karta Hai
```js
// Yeh ek Higher-Order Function hai kyunki yeh naya function return kar raha hai
function multiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = multiplier(2); // double ab ek function ban gaya hai
console.log(double(5)); // Output: 10
```
> Type C Built-in Higher-Order Functions
- map(): Array ke har element par ek function chalakar naya array banata hai.
- filter(): Ek condition ke basis par elements ko filter karke naya array deta hai.
- reduce(): Poore array ko calculate karke ek single value me badal deta hai.
- forEach(): Array ke har element par loop chalane ke liye callback function leta hai.

# JavaScript me data types ko do main categories me divide kiya gaya hai: Primitive Data Types aur Non-Primitive (ya Reference) Data Types.

### 1. Primitive Data Types
Primitive data types wo hote hain jo sabse simple aur basic hote hain. Yeh single values ko store karte hain aur immutable (jinhe badla nahi ja sakta) hote hain.

- Number: Saare numbers (integers aur decimals), jaise 10, 3.14.
- String: Text data, jaise "Hello".
- Boolean: Sirf do values, true ya false.
- Undefined: Jab ek variable declare ho jaye par use value na di jaye (jaise let x;).
- Null: Jaan-bujhkar kisi variable ko khali (empty) rakhna.
- Symbol: Unique aur private identifiers banane ke liye (ES6 me aaya).
- BigInt: Bohot bade numbers ko store karne ke liye jo normal Number range se bahar hon.

### 2. Non-Primitive Data Types (Reference Types)
Non-primitive data types wo hote hain jo complex data aur multiple values ko ek sath store karne ke kaam aate hain. Yeh mutable (jinhe badla ja sakta hai) hote hain.

- Object: Key-value pairs ka collection, jaise { name: "Rahul", age: 25 }.
- Array: Elements ki ordered list, jaise [1, 2, 3, 4].
- Function: Code ka block jise reuse kiya ja sake.(Note: JavaScript me Array aur Function bhi internally Objects hi hote hain).

| Feature | Primitive Data Types | Non-Primitive Data Types |
| :--- | :--- | :--- |
| **Values** | Single (Simple) value store karte hain. | Multiple/Complex values ka collection hote hain. |
| **Mutability** | **Immutable** (Value ko direct modify nahi kiya ja sakta, naye variable me naya space banta hai). | **Mutable** (Inki andar ki properties ya elements ko change kiya ja sakta hai). |
| **Memory** | **Stack Memory** me store hote hain. | Actual data **Heap Memory** me hota hai aur uska reference (address) **Stack** me hota hai. |
| **Copy Behavior** | **Passed by Value** (Nayi bilkul alag copy banti hai). | **Passed by Reference** (Memory address share hota hai, naya data nahi banta). |
| **Examples** | `Number`, `String`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`. | `Object`, `Array`, `Function`. |

# Template Literals / Strings:-
Template Literals JavaScript (ES6) ka ek feature hai jo string interpolation, multi-line strings, aur embedded expressions ko allow karta hai. Isme hum strings ko wrap karne ke liye Backticks (`) ka use karte hain aur variables ko embed karne ke liye ${expression} syntax ka use karte hain.
```js
let name = "Rahul";
let age = 25;

// ❌ Purana Tarika (Concatenation)
let oldWay = "Mera naam " + name + " hai aur meri age " + age + " saal hai.";

//  Naya Tarika (Template String)
let newWay = `Mera naam ${name} hai aur meri age ${age} saal hai.`;

console.log(newWay); // Output: Mera naam Rahul hai aur meri age 25 saal hai.
```

| Feature | Old Way (Single/Double Quotes) | New Way (Template Strings - Backticks) |
| :--- | :--- | :--- |
| **Syntax** | `'Hello'` ya `"Hello"` | `` `Hello` `` |
| **Variable Join** | `+` operator use hota hai (`'Hi ' + name`) | `${}` syntax use hota hai (`\`Hi ${name}\``) |
| **Multi-line** | `\n` ya `+` lagana mandatory hai | Direct Enter maar kar multi-line likh sakte hain |
| **Readability** | Complex aur ganda lagta hai jab bohot variables hon | Clean aur asani se samajh aane wala hota hai |

# Ternary Operator
Ternary operator JavaScript ka akela aisa operator hai jo teen operands leta hai: ek condition, uske baad ek question mark (?), fir ek expression jo condition ke true hone par chalta hai, aur aakhiri me ek colon (:) jo condition ke false hone par chalta hai. Yeh aksar if-else ko short-hand tarike me likhne ke liye use hota hai.
```js
condition ? expression_if_true : expression_if_false;
```
| Feature | `if-else` Statement | Ternary Operator (`? :`) |
| :--- | :--- | :--- |
| **Code Length** | Zyadatar 5-6 lines leta hai. | Sirf 1 line me kaam ho jata hai. |
| **Type** | Yeh ek **Statement** hai. | Yeh ek **Expression** hai (value return karta hai). |
| **Readability** | Complex ya lambi conditions ke liye behtar hai. | Chhoti aur simple conditions ke liye sabse best hai. |
| **Variable Assignment** | Direct variable me store nahi ho sakta (andar value assign karni padti hai). | Direct variable ke aage assign kiya ja sakta hai (`let x = cond ? a : b`). |

# Switch Case Statement:-
Switch statement ek multi-way branch statement hai jo ek expression (ya variable) ki value ko multiple execution paths (jinhe cases kehte hain) ke sath match karti hai. Jaise hi koi case match hota hai, uske andar ka code block execute ho jata hai. Yeh ek lambi if-else-if ki chain ka ek clean aur zyada readable alternative hai.
```js
let dayNumber = 3;

switch (dayNumber) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday"); // Code yahan aakar match hoga
        break; 
    default:
        console.log("Invalid Day");
}
// Output: Wednesday
```

| Feature | `if-else if` Chain | `switch-case` Statement |
| :--- | :--- | :--- |
| **Comparison Type** | Yeh logical operators (`&&`, `||`, `<`, `>`) aur loose/strict comparison dono kar sakti hai. | Yeh sirf equality (`===`) check karne ke liye design ki gayi hai. |
| **Readability** | Agar 5 se zyada conditions hon toh code bohot ganda (nested) lagne lagta hai. | Bohot saari conditions ke liye bhi code ekdam clean aur structured lagta hai. |
| **Execution Speed** | Code top to bottom ek-ek karke saari conditions check karta hai. | Kuch cases me compiler/engine compiler level par iski jump table bana deta hai, jisse yeh thodi fast ho sakti hai. |
| **Default Option** | Aakhiri me ek simple `else` block lagta hai. | Isme ek `default:` keyword use hota hai. |

## 1. break Statement (Loop ko wahin rok dena)
break keyword ka kaam hota hai loop ko turant (immediately) khatam kar dena. Jaise hi loop ke andar control ko break milta hai, loop wahin ruk jata hai aur compiler loop ke bahar aa jata hai.
```js
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break; // Jaise hi i ki value 3 hogi, loop poora khatam ho jayega
    }
    console.log(i);
}
// Output: 
// 1
// 2
```

## 2. continue Statement (Sirf ek iteration ko skip karna)
continue keyword loop ko khatam nahi karta, balki sirf current iteration (chal rahi baari) ko skip kar deta hai. Jaise hi code me continue aata hai, uske niche ka bacha hua code us baari ke liye nahi chalta, aur loop agli baari (next iteration) par jump kar jata hai.
```js 
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue; // Jaise hi i ki value 3 hogi, yeh baari skip ho jayegi aur loop seedha i=4 par chala jayega
    }
    console.log(i);
}
// Output: 
// 1
// 2
// 4
// 5
// (Notice karein: 3 print nahi hua!)
```

| Feature / Criteria | `break` Statement | `continue` Statement |
| :--- | :--- | :--- |
| **Main Purpose** | Loop ko poori tarah se **terminate (khatam)** karne ke liye. | Loop ki sirf ek **current iteration ko skip** karne ke liye. |
| **Control Flow** | Control seedha loop ke **bahar** chala jata hai. | Control loop ke **agli baari (next iteration)** par jump kar jata hai. |
| **Remaining Iterations** | Baaki bache hue saare loops cancel ho jate hain. | Baaki bache hue saare loops apne normal schedule par chalte hain. |
| **Switch Case Use** | Iska use `switch` statements me bhi hota hai (fall-through rokne ke liye). | Iska use sirf aur sirf **loops** ke andar hi kiya ja sakta hai. |

# What is Set{}??
JavaScript me Set ek built-in collection object hai jo har tarah ki unique values ko store karta hai, chahe wo primitive data types hon ya object references. Yeh duplicates allow nahi karta aur values ko unke insertion order me maintain rakhta hai.

### Set vs Array
- Array: Isme duplicate values ho sakti hain (jaise [1, 2, 2, 3]).
- Set: Isme sirf unique values hoti hain (agar aap [1, 2, 2, 3] ko Set me dalenge toh wo use [1, 2, 3] bana dega).
- Performance: Set me kisi element ko dhoodna (has() method ke zariye) Array ke mukable bohot fast hota hai, kyunki yeh internally hash table ya optimized mechanism use karta hai.

### Set Kaise Banate Hain?
```js
// Ek khali (empty) Set banana
const mySet = new Set();

// Kisi Array se Set banana (Duplicates apne aap hat jayenge)
const numbersSet = new Set([1, 2, 2, 3, 4, 4]); 
console.log(numbersSet); // Output: Set(4) { 1, 2, 3, 4 }
```

### Set Ke Important Methods aur Examples
```js
// 1. Set Create Kiya
const fruits = new Set();

// 2. add(value) - Set me naya element jodna
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Orange");
fruits.add("Apple"); // Dobara Apple add kiya, par yeh ignore ho jayega

console.log(fruits); // Output: Set(3) { 'Apple', 'Banana', 'Orange' }

// 3. has(value) - Check karna ki element Set me hai ya nahi (Returns true/false)
console.log(fruits.has("Banana")); // Output: true
console.log(fruits.has("Mango"));  // Output: false

// 4. size (Property) - Set me kitne elements hain unki ginti batata hai
console.log(fruits.size); // Output: 3

// 5. delete(value) - Kisi specific element ko remove karna
fruits.delete("Banana"); 
console.log(fruits); // Output: Set(2) { 'Apple', 'Orange' }

// 6. Loop chalana (Set par hum forEach ya for...of loop chala sakte hain)
fruits.forEach(fruit => {
    console.log("Fruit Name:", fruit);
});

// 7. clear() - Set ke saare elements ko ek sath delete karna
fruits.clear();
console.log(fruits.size); // Output: 0 (Set poora khali ho gaya)
```

| Method / Property | Kaam Kya Karta Hai? | Example |
| :--- | :--- | :--- |
| `new Set()` | Naya Set object create karta hai. | `const s = new Set();` |
| `add(value)` | Set me nayi value joddta hai (agar wo pehle se na ho). | `s.add(10);` |
| `delete(value)` | Kisi value ko Set se remove karta hai. | `s.delete(10);` |
| `has(value)` | Check karta hai ki value exist karti hai ya nahi. | `s.has(10); // true` |
| `clear()` | Set ke saare elements ko delete kar deta hai. | `s.clear();` |
| `size` | Set ke andar total elements ki count batata hai. | `s.size;` |

# Strings Functions:-
JavaScript me String ek primitive data type hai jo characters ke sequence ko represent karta hai. Strings immutable hoti hain, yani ek baar string banne ke baad uske andar ke kisi character ko direct badla nahi ja sakta; jab bhi hum koi change karte hain, toh ek nayi string banti hai.
```js
let single = 'Hello'; // Single quotes
let double = "World"; // Double quotes
let template = `Hello ${double}`; // Backticks (Template String)
```

| Method | Kaam Kya Karta Hai? | Example | Output |
| :--- | :--- | :--- | :--- |
| `length` (Property) | Total characters ginta hai. | `"Hi".length` | `2` |
| `indexOf()` | Position dhoodta hai. | `"abc".indexOf("b")` | `1` |
| `includes()` | Check karta hai ki word hai ya nahi. | `"hello".includes("e")` | `true` |
| `slice(s, e)` | String ka tukda nikalta hai. | `"Frontend".slice(0, 4)` | `"Fron"` |
| `trim()` | Fuzool ke spaces hatata hai. | `"  hi  ".trim()` | `"hi"` |
| `split()` | String ko Array bana deta hai. | `"a-b-c".split("-")` | `["a", "b", "c"]` |

### String Methods

```js
// ==========================================
// JAVASCRIPT STRING METHODS COMPLETE GUIDE
// ==========================================

// 1. String Creation & Property
let str = "JavaScript is Awesome";
console.log("--- 1. Length Property ---");
console.log("Original String:", str);
console.log("Total Length:", str.length); // Output: 21
console.log("-------------------------\n");


// 2. Searching Methods
console.log("--- 2. Searching Methods ---");
// indexOf(): Pata karta hai ki word kis index se shuru ho raha hai
console.log("Index of 'is':", str.indexOf("is")); // Output: 11
console.log("Index of 'Python':", str.indexOf("Python")); // Output: -1 (Nahi mila)

// includes(): Check karta hai ki word string me hai ya nahi (returns true/false)
console.log("Contains 'Awesome'?:", str.includes("Awesome")); // Output: true

// startsWith() & endsWith(): Shuruat aur aakhir check karne ke liye
console.log("Starts with 'Java'?:", str.startsWith("Java")); // Output: true
console.log("Ends with 'Cool'?:", str.endsWith("Cool")); // Output: false
console.log("-------------------------\n");


// 3. Extracting Methods (Tukda nikalna)
console.log("--- 3. Extracting Methods ---");
// slice(start, end): Start index se lekar End index se pehle tak ka part nikalta hai
console.log("Sliced (0 to 10):", str.slice(0, 10)); // Output: JavaScript
console.log("Negative Slice (-7):", str.slice(-7)); // Output: Awesome (Piche se 7 characters)

// substring(start, end): Slice ki tarah hai par negative index accept nahi karta
console.log("Substring (14 to 21):", str.substring(14, 21)); // Output: Awesome
console.log("-------------------------\n");


// 4. Modifying Methods
console.log("--- 4. Modifying Methods ---");
// toUpperCase() & toLowerCase()
console.log("UPPERCASE:", str.toUpperCase()); // Output: JAVASCRIPT IS AWESOME
console.log("lowercase:", str.toLowerCase()); // Output: javascript is awesome

// trim(): Shuruat aur aakhiri ke faltu spaces hatata hai
let dirtyString = "   Hello Learner   ";
console.log("Before Trim:", `'${dirtyString}'`);
console.log("After Trim:", `'${dirtyString.trim()}'`); // Output: 'Hello Learner'

// replace(): Pehle match hone wale word ko badalta hai
let text = "Hello Amit, Hello Rahul";
console.log("Replace 'Hello':", text.replace("Hello", "Bye")); // Output: Bye Amit, Hello Rahul
console.log("Replace All 'Hello':", text.replaceAll("Hello", "Bye")); // Output: Bye Amit, Bye Rahul
console.log("-------------------------\n");


// 5. Converting Methods
console.log("--- 5. Converting Methods ---");
// split(): String ko todkar Array bana deta hai
let csvData = "Apple,Banana,Mango,Orange";
let fruitsArray = csvData.split(","); // Comma (,) ke basis par todo
console.log("String to Array:", fruitsArray); // Output: [ 'Apple', 'Banana', 'Mango', 'Orange' ]

// Pro Interview Trick: String ko reverse karna using split()
let word = "Hello";
let reversedWord = word.split("").reverse().join("");
console.log(`Reverse of '${word}':`, reversedWord); // Output: olleH
console.log("-------------------------");
```

```js
// ==========================================
// ADVANCED & ADDITIONAL STRING METHODS IN JS
// ==========================================

// 1. Padding Methods (String ki length fix karne ke liye)
// padStart() aur padEnd() string ke shuru ya aakhir me tab tak characters jodte hain jab tak di gayi length poori na ho jaye.
console.log("--- 1. Padding Methods ---");
let accountNo = "4321";
let maskedAccount = accountNo.padStart(10, "*"); 
console.log("Masked Card Number:", maskedAccount); // Output: ******4321 (Total length 10 ho gayi)

let text = "Hi";
console.log("Pad End:", text.padEnd(5, "!")); // Output: Hi!!!
console.log("-------------------------\n");


// 2. Character Access Methods (Kisi specific index ka character nikalna)
console.log("--- 2. Character Access ---");
let message = "CODING";

// charAt(index): Us index par kaun sa character hai wo batata hai
console.log("Character at index 2:", message.charAt(2)); // Output: D

// charCodeAt(index): Us character ka UTF-16 / ASCII code batata hai (Interview query)
console.log("ASCII Code of 'C':", message.charCodeAt(0)); // Output: 67
console.log("-------------------------\n");


// 3. Repeating & Joining Methods
console.log("--- 3. Repeat & Concat ---");
let emotion = "Ha ";
console.log("Laughing:", emotion.repeat(3)); // Output: Ha Ha Ha 

// concat(): Do ya do se zyada strings ko aapas me jodta hai (Alternative to + operator)
let str1 = "Hello";
let str2 = "World";
console.log("Joined String:", str1.concat(" ", str2, "!")); // Output: Hello World!
console.log("-------------------------\n");


// 4. Searching from Back (Piche se dhoodhna)
console.log("--- 4. Last Index Of ---");
let sentence = "apple banana apple mango";
// lastIndexOf(): Bataega ki 'apple' aakhiri baar kis index par aaya hai
console.log("Last Index of 'apple':", sentence.lastIndexOf("apple")); // Output: 13
console.log("-------------------------\n");


// 5. String Matching with Regex (Regular Expressions)
console.log("--- 5. Match & Search ---");
let info = "My age is 25 and my lucky number is 7";

// match(): Regex ke basis par string se data nikal kar array deta hai (Jaise saare numbers nikalna)
let numbersFound = info.match(/\d+/g); 
console.log("Numbers found in string:", numbersFound); // Output: [ '25', '7' ]

// search(): Regex ke mutabik check karta hai aur position batata hai
console.log("Position of first digit:", info.search(/\d/)); // Output: 10 (2 ki position)
console.log("-------------------------");
```

# Array
JavaScript me Array ek non-primitive (reference) data type hai jo multiple values (elements) ki ek ordered list ko store karta hai. JavaScript ke arrays dynamic hote hain (inki size fix nahi hoti) aur inme aap alag-alag data types (jaise number, string, boolean, object) ko ek sath ek hi array me rakh sakte hain.
```js
let fruits = ["Apple", "Banana", "Mango"];
// Indexing:    0          1         2

console.log(fruits[0]); // Output: Apple
console.log(fruits.length); // Output: 3 (Total elements)
```

# Array Methods:-
```js
// ==========================================
// JAVASCRIPT ARRAY METHODS COMPLETE GUIDE
// ==========================================

let numbers = [10, 20, 30, 40];
console.log("Original Array:", numbers);
console.log("-------------------------\n");

// ------------------------------------------
// A. ELEMENTS ADD / REMOVE METHODS
// ------------------------------------------
console.log("--- A. Add/Remove Methods ---");

// 1. push(): Array ke AKHIR (End) me naya element jodta hai
numbers.push(50);
console.log("After push(50):", numbers); // [10, 20, 30, 40, 50]

// 2. pop(): Array ke AKHIR se ek element hata deta hai
numbers.pop();
console.log("After pop():", numbers); // [10, 20, 30, 40]

// 3. unshift(): Array ke SHURUAT (Start) me naya element jodta hai
numbers.unshift(5);
console.log("After unshift(5):", numbers); // [5, 10, 20, 30, 40]

// 4. shift(): Array ke SHURUAT se ek element hata deta hai
numbers.shift();
console.log("After shift():", numbers); // [10, 20, 30, 40]
console.log("-------------------------\n");


// ------------------------------------------
// B. ADVANCED MANIPULATION METHODS
// ------------------------------------------
console.log("--- B. Advanced Manipulation ---");

// 5. slice(start, end): Array ka ek tukda nikalta hai (Original array change nahi hota)
let slicedPart = numbers.slice(1, 3); 
console.log("Sliced Part (Index 1 to 2):", slicedPart); // [20, 30]

// 6. splice(start, deleteCount, newElements): Array ke beech me se delete ya add karna
// (CRITICAL: Yeh original array ko change/modify kar deta hai)
let team = ["Amit", "Rahul", "Zeeshan", "Raj"];
// Index 1 par jao, 2 elements delete karo, aur 'Vikram' add karo
team.splice(1, 2, "Vikram"); 
console.log("After Splice:", team); // [ 'Amit', 'Vikram', 'Raj' ]
console.log("-------------------------\n");


// ------------------------------------------
// C. SEARCHING & UTILITY METHODS
// ------------------------------------------
console.log("--- C. Searching & Utility ---");

let items = ["Pen", "Paper", "Book", "Pen"];

// 7. indexOf(): Element ki position dhoodta hai
console.log("Index of 'Book':", items.indexOf("Book")); // Output: 2

// 8. includes(): Check karta hai ki element array me hai ya nahi (true/false)
console.log("Has 'Eraser'?:", items.includes("Eraser")); // Output: false

// 9. concat(): Do arrays ko aapas me jodna
let arr1 = [1, 2];
let arr2 = [3, 4];
console.log("Combined Array:", arr1.concat(arr2)); // [1, 2, 3, 4]

// 10. join(): Array ko jod kar string bana dena
console.log("Joined with '-':", items.join("-")); // "Pen-Paper-Book-Pen"
console.log("-------------------------\n");


// ------------------------------------------
// D. HIGH-ORDER ARRAY METHODS (Interview Favourites)
// ------------------------------------------
console.log("--- D. Higher-Order Methods ---");

let myNumbers = [1, 2, 3, 4, 5];

// 11. map(): Array ke har element par operation karke ek NAYI ARRAY banata hai
let doubled = myNumbers.map(num => num * 2);
console.log("Mapped (Doubled):", doubled); // [2, 4, 6, 8, 10]

// 12. filter(): Condition ke basis par elements ko filter karke NAYI ARRAY banata hai
let evenNumbers = myNumbers.filter(num => num % 2 === 0);
console.log("Filtered (Even):", evenNumbers); // [2, 4]

// 13. reduce(): Poore array ko calculate karke ek SINGLE VALUE me badal deta hai
// (acc = accumulator/total, curr = current value)
let sum = myNumbers.reduce((acc, curr) => acc + curr, 0);
console.log("Reduced (Total Sum):", sum); // Output: 15
console.log("-------------------------");
```

| Method | Kaam Kya Karta Hai? | Original Array Badalta Hai? |
| :--- | :--- | :--- |
| `push()` | Aakhir me element add karta hai. | **Yes** |
| `pop()` | Aakhir se element hatata hai. | **Yes** |
| `unshift()`| Shuruat me element add karta hai. | **Yes** |
| `shift()` | Shuruat se element hatata hai. | **Yes** |
| `slice()` | Array ka tukda nikal kar naya array deta hai. | **No** |
| `splice()`| Beech se elements delete/add karta hai. | **Yes** (Mutates) |
| `join()`  | Array ke elements ko jod kar String bana deta hai. | **No** |
| `map()`   | Har element ko modify karke naya array deta hai. | **No** |
| `filter()`| Condition match karne wale elements ka naya array deta hai. | **No** |

# Object:-
JavaScript me Object ek non-primitive (reference) data type hai jo data ko Key-Value pairs ke roop me store karta hai. Array me values index (0, 1, 2) par hoti hain, lekin Object me har value ka ek naam (Key) hota hai. Iska use real-world entities (jaise ek User, Product, ya Car) ko represent karne ke liye kiya jata hai.
```js
let user = {
    name: "Rahul",       // name hai 'Key', "Rahul" hai 'Value'
    age: 25,             // Inhe hum 'Properties' kehte hain
    isDeveloper: true
};

// Access karne ke do tarike:
console.log(user.name);    // 1. Dot Notation (Sabse zyada use hota hai) -> Rahul
console.log(user["age"]);  // 2. Bracket Notation -> 25
```

## Object Methods
```js
// ==========================================
// JAVASCRIPT OBJECT METHODS COMPLETE GUIDE
// ==========================================

// 1. Object with a Method (Object ke andar function)
let person = {
    firstName: "Amit",
    lastName: "Sharma",
    age: 30,
    // Yeh ek method hai
    fullName: function() {
        // 'this' keyword isee object (person) ko point kar raha hai
        return `${this.firstName} ${this.lastName}`;
    }
};

console.log("--- 1. Object Method ---");
console.log("Full Name Call:", person.fullName()); // Output: Amit Sharma
console.log("-------------------------\n");


// 2. Built-in Object Global Functions (CRITICAL FOR INTERVIEWS)
console.log("--- 2. Global Object Functions ---");

// A. Object.keys(): Saari 'Keys' ka ek array bana kar deta hai
let keysArray = Object.keys(person);
console.log("Keys:", keysArray); // [ 'firstName', 'lastName', 'age', 'fullName' ]

// B. Object.values(): Saari 'Values' ka ek array bana kar deta hai
let valuesArray = Object.values(person);
console.log("Values:", valuesArray); // [ 'Amit', 'Sharma', 30, [Function: fullName] ]

// C. Object.entries(): Key-Value pairs ka ek 2D array (array of arrays) deta hai
console.log("Entries:", Object.entries(person)); 
// Output: [ ['firstName', 'Amit'], ['lastName', 'Sharma'], ... ]
console.log("-------------------------\n");


// 3. Object Protection Methods (Security)
console.log("--- 3. Object Security ---");

let car = { brand: "Tata", model: "Nexon" };

// A. Object.seal(): Isse aap nayi properties ADD nahi kar sakte, par purani MODIFY kar sakte hain.
Object.seal(car);
car.model = "Harrier"; // Modify allowed hai
car.year = 2024;       // ❌ Add ignore ho jayega (Nahi chalega)
console.log("Sealed Object:", car); // { brand: 'Tata', model: 'Harrier' }

// B. Object.freeze(): Isse object bilkul LOCK ho jata hai. Na add, na delete, na modify.
Object.freeze(car);
car.model = "Safari"; // ❌ Modify bhi ignore ho jayega
console.log("Frozen Object:", car); // { brand: 'Tata', model: 'Harrier' }
console.log("-------------------------\n");


// 4. Object Cloning / Merging
console.log("--- 4. Merging Objects ---");

let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };

// Object.assign(): Do objects ko aaps me jodta hai
let mergedObj = Object.assign({}, obj1, obj2);
console.log("Merged using assign():", mergedObj); // { a: 1, b: 2, c: 3, d: 4 }

// Modern Alternative: Spread Operator (...) -> Sabse zyada use hota hai
let modernMerged = { ...obj1, ...obj2 };
console.log("Merged using Spread:", modernMerged); // { a: 1, b: 2, c: 3, d: 4 }
console.log("-------------------------");
```

| Method / Function | Kaam Kya Karta Hai? | Example |
| :--- | :--- | :--- |
| `Object.keys(obj)` | Object ki saari keys ka Array deta hai. | `Object.keys({a:1}) // ['a']` |
| `Object.values(obj)`| Object ki saari values ka Array deta hai. | `Object.values({a:1}) // [1]` |
| `Object.entries(obj)`| Keys aur Values dono ka 2D Array deta hai. | `Object.entries({a:1}) // [['a', 1]]` |
| `Object.freeze(obj)` | Object ko completely read-only bana deta hai. | `Object.freeze(obj);` |
| `Object.seal(obj)`   | Nayi property add nahi karne deta, par edit allow hai. | `Object.seal(obj);` |
| `Object.assign()`    | Do ya do se zyada objects ko merge karta hai. | `Object.assign(target, source);` |

# == (Loose Equality) aur === (Strict Equality)??

### == (Loose Equality)
Yeh operator sirf values ko compare karta hai, unke data type ko nahi. Agar dono sides ke data types alag hain, to JavaScript background me unka type automatic change kar deta hai (jise hum Type Coercion kehte hain) aur phir compare karta hai.
```js
Example: ```javascript
5 == "5"  // Output: true
```
### === (Strict Equality)
Yeh operator values aur data type dono ko check karta hai. Yeh koi shortcut nahi leta aur na hi koi background me type change karta hai. Agar type alag hai, to yeh seedha false de dega.
```js
5 === "5" // Output: false
```

# Object ke security methods Object.freeze() aur Object.seal()

### Object.freeze() (Sab kuch jam gaya)
Jaise barf (ice) me sab kuch jam jata hai aur hil nahi sakta, waise hi Object.freeze() karne ke baad object bilkul lock ho jata hai. Aap us object me kuch bhi badal nahi sakte

- Kya nahi kar sakte: * Naye properties add nahi kar sakte.
    - puraani properties delete nahi kar sakte.
    - Puraani properties ki values ko change (update) bhi nahi kar sakte.
```js
const user = { name: "Rahul", role: "Admin" };
Object.freeze(user);

user.age = 25;       // ❌ Add nahi hoga
delete user.role;    // ❌ Delete nahi hoga
user.name = "Amit";  // ❌ Change bhi nahi hoga (Rahul hi rahega)
```
### Object.seal()
Object.seal() karne ka matlab hai ki aapne object ki boundary ko seal (pack) kar diya hai. Ab na to koi naya member andar aa sakta hai aur na hi koi bahar ja sakta hai, lekin jo andar hain, unhe aap badal sakte ho.

- Kya nahi kar sakte:
    - Naye properties add nahi kar sakte.
    - Puraani properties delete nahi kar sakte.
- Kya KAR sakte hain:
    - Puraani properties ki values ko change (update) kar sakte hain.
```js
const user = { name: "Rahul", role: "Admin" };
Object.seal(user);

user.age = 25;       // ❌ Add nahi hoga
delete user.role;    // ❌ Delete nahi hoga
user.name = "Amit";  //  Change ho jayega! (Now name is "Amit")
```

# LocalStorage, SessionStorage, aur Cookies me kya differences

| Feature / Property | LocalStorage | SessionStorage | Cookies |
| :--- | :--- | :--- | :--- |
| **Storage Capacity (Limit)** | **~5MB - 10MB** (Sabse zyada space) | **~5MB** (Kafi space hota hai) | **~4KB** (Bohot hi kam space) |
| **Data Expiry (Kab tak rahega?)** | **Kabhi delete nahi hota** (Jab tak aap khud clear na karein) | **Tab band hote hi delete** ho jata hai | **Manually set karni padti hai** (Expiry date/time dena hota hai) |
| **Server Accessibility** | Server ko isse matlab nahi hota, sirf browser me rehta hai | Server ko isse matlab nahi hota, sirf browser me rehta hai | **Har HTTP request ke saath** server par automatic jata hai |
| **Window/Tab Scope** | Alag-alag tabs ya windows me bhi same data access ho jata hai | **Sirf usi specific tab tak** limited rehta hai jahan ise banaya gaya | Kisi bhi tab/window se access ho sakta hai (agar domain same ho) |
| **Kaise banaya gaya tha?** | HTML5 me naya introduce kiya gaya | HTML5 me naya introduce kiya gaya | Yeh purana tareeka hai (HTML5 se pehle ka) |

# Promise.all(), Promise.allSettled(), Promise.any(), aur Promise.race() me kya differences hain?

| Method | Kab Success (Fulfill) hota hai? | Kab Fail (Reject) hota hai? | Final Output Kya Milta Hai? |
| :--- | :--- | :--- | :--- |
| **`Promise.all()`** | Jab **saare** promises successfully complete ho jayein. | Jaise hi **koi ek bhi** promise fail ho jaye (Short-circuit). | Saare resolved values ka ek **Array**, ya fir pehle failed promise ka error. |
| **`Promise.allSettled()`** | Hamesha success hota hai! Yeh kabhi fail nahi hota. | Yeh tab tak wait karta hai jab tak saare promises khatam (settle) na ho jayein. | Ek **Array of Objects**, jisme har promise ka status (`fulfilled`/`rejected`) aur uski value hoti hai. |
| **`Promise.any()`** | Jaise hi **koi ek bhi** promise sabse pehle success ho jaye. | Jab **saare ke saare** promises fail ho jayein. | Sabse pehle kamyaab hone wale promise ki **Value**, ya fir saare errors ka ek group (`AggregateError`). |
| **`Promise.race()`** | Jo bhi promise **sabse pehle khatam (settle)** ho jaye, chahe wo success ho ya fail. | Agar sabse pehle khatam hone wala promise fail ho gaya, to yeh bhi fail ho jayega. | Sabse pehle settle hone wale promise ki **Value ya Error**. |

# Debouncing aur Throttling me kya farq hai?

### 1. Debouncing (Ek break ke baad chalna)
Debouncing ka matlab hai ki jab tak user action karna band (stop) nahi kar deta, tab tak function execute nahi hoga. Agar user baar-baar action kar raha hai, to timer baar-baar reset hota rahega. Jab user ek specific time (delay) ke liye rukega, tabhi function chalega.

- Aasan bhasha me: "Jab tum poori tarah ruk jaoge, tabhi main kaam karunga."

- Real-life Example (Lift/Elevator): Lift ka darwaza tab tak band nahi hota jab tak log uske andar aate rehte hain. Jaise hi naye logon ka aana 5 seconds ke liye band hota hai, darwaza band ho jata hai.

- Best Use Case: Search Bar (Autocomplete). Agar aap "iPhone" type kar rahe ho, to har letter (i, p, h) par API call na jaye. Jab aap typing khatam karke 300ms ke liye ruko, tabhi ek hi baar API call jaye.

### 2. Throttling (Ek fixed interval par chalna)
Throttling ka matlab hai ki chahe user jitni baar bhi baar-baar action kare, function sirf ek fixed time interval (jaise har 200ms me ek baar) par hi execute hoga. Yeh lagatar hone wale action ko ek steady pace (raftar) deta hai.

- Aasan bhasha me: "Tum chahe jitna zor lagao, main har 2 seconds me ek hi baar kaam karunga."

- Real-life Example (Game me Bullet Firing): Jab aap kisi shooting game me gun ka trigger daba kar rakhte ho, to bullets lagatar nahi nikalti, balki ek fixed gap (rate of fire) ke baad ek-ek karke nikalti hain.

- Best Use Case: Scroll Event ya Window Resize. Agar user page scroll kar raha hai aur aapko uski position check karni hai, to har millisecond me check karne ke bajaye aap throttling use karke har 200ms me ek baar check karte ho taaki browser hang na ho.