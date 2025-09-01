Q.What is JavaScript?
JavaScript is a lightweight, interpreted, prototype-based, single-threaded, and event-driven programming language that enables dynamic behavior and interactivity in web applications, making it the core of modern front-end development.

Q.What is Interpreted?
The code is executed line by line at runtime by an interpreter (like the browser’s JavaScript engine), instead of being fully translated into machine code beforehand (like compiled languages such as C++ or Java)

Q.What is prototye-based?
It means that objects in JavaScript can inherit properties and methods directly from other objects through a prototype chain, instead of using classes like in classical OOP.


example:
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function () {
  console.log(`Hello, I am ${this.name}`);
};

const hemant = new Person("Hemant");

hemant.sayHello(); // "Hello, I am Hemant"

🔎 What’s happening:

Person is a constructor function.

We add sayHello to its prototype.
Any object created with new Person() doesn’t store sayHello itself — instead, it inherits it from Person.prototype.

Q.What are the different data types in JavaScript?

JavaScript has **8 data types** divided into two categories:

## 📍 Primitive Data Types (7 types)
These are immutable and stored by value:

### 1. **Number** 
- Represents both integers and floating-point numbers
- Range: -(2^53 - 1) to 2^53 - 1
```javascript
let age = 25;
let price = 99.99;
let infinity = Infinity;
let notANumber = NaN;
```

### 2. **String**
- Text data enclosed in quotes (single, double, or backticks)
```javascript
let name = "John";
let message = 'Hello World';
let template = `Hi ${name}`;
```

### 3. **Boolean**
- Logical values: `true` or `false`
```javascript
let isActive = true;
let isComplete = false;
```

### 4. **Undefined**
- Variable declared but not assigned a value
```javascript
let x;
console.log(x); // undefined
```

### 5. **Null**
- Intentional absence of value
```javascript
let data = null; // explicitly set to "nothing"
```

### 6. **Symbol** (ES6)
- Unique identifier, mainly used for object properties
```javascript
let sym = Symbol('id');
let sym2 = Symbol('id');
console.log(sym === sym2); // false (always unique)
```

### 7. **BigInt** (ES2020)
- For integers larger than Number.MAX_SAFE_INTEGER
```javascript
let bigNumber = 123456789012345678901234567890n;
let anotherBig = BigInt("123456789012345678901234567890");
```

## 📍 Non-Primitive Data Type (1 type)

### 8. **Object**
- Complex data type that can store multiple values
- Includes: Objects, Arrays, Functions, Dates, etc.
```javascript
// Object
let person = { name: "Alice", age: 30 };

// Array
let colors = ["red", "green", "blue"];

// Function
let greet = function() { return "Hello"; };

// Date
let today = new Date();
```

## 🔍 Key Differences:

| **Primitive Types** | **Non-Primitive Types** |
|-------------------|------------------------|
| Stored by value | Stored by reference |
| Immutable | Mutable |
| Compared by value | Compared by reference |

```javascript
// Primitive - stored by value
let a = 5;
let b = a;
a = 10;
console.log(b); // Still 5

// Non-primitive - stored by reference
let obj1 = { name: "John" };
let obj2 = obj1;
obj1.name = "Jane";
console.log(obj2.name); // "Jane" (both point to same object)
```

## 🧪 Type Checking:
```javascript
console.log(typeof 42);          // "number"
console.log(typeof "hello");     // "string"
console.log(typeof true);        // "boolean"
console.log(typeof undefined);   // "undefined"
console.log(typeof null);        // "object" (this is a known quirk!)
console.log(typeof Symbol());    // "symbol"
console.log(typeof 123n);        // "bigint"
console.log(typeof {});          // "object"
console.log(typeof []);          // "object"
console.log(typeof function(){}); // "function"
```

Q.What is the mean of mutable and immutable?

## 🔄 Mutability in JavaScript

**Mutable** and **Immutable** refer to whether an object's state can be changed after creation.

### 📍 **Immutable (Cannot be changed)**
- Once created, the value cannot be modified
- **All primitive types** are immutable
- When you "change" a primitive, you're actually creating a new value

```javascript
// Strings are immutable
let str = "Hello";
str[0] = "h"; // This doesn't work
console.log(str); // Still "Hello"

// When we "modify" a string, we create a new one
str = str.toLowerCase(); // Creates new string "hello"

// Numbers are immutable
let num = 5;
num++; // Creates new value 6, doesn't modify the original 5
```

### 📍 **Mutable (Can be changed)**
- The object's contents can be modified after creation
- **All non-primitive types** (objects) are mutable
- Changes affect the original object

```javascript
// Objects are mutable
let person = { name: "John", age: 25 };
person.name = "Jane"; // Modifies the original object
person.city = "NYC";  // Adds new property
console.log(person); // { name: "Jane", age: 25, city: "NYC" }

// Arrays are mutable
let fruits = ["apple", "banana"];
fruits.push("orange"); // Modifies original array
fruits[0] = "mango";   // Changes existing element
console.log(fruits); // ["mango", "banana", "orange"]
```

## 🔍 **Key Differences with Examples:**

### **Primitive Types (Immutable):**
```javascript
let a = "Hello";
let b = a;           // b gets a copy of the value
a = a + " World";    // Creates new string, doesn't modify original
console.log(a);      // "Hello World"
console.log(b);      // "Hello" (unchanged)
```

### **Object Types (Mutable):**
```javascript
let obj1 = { name: "Alice" };
let obj2 = obj1;              // obj2 points to same object
obj1.name = "Bob";            // Modifies the shared object
console.log(obj1.name);       // "Bob"
console.log(obj2.name);       // "Bob" (both changed!)
```

## 📝 **Practical Implications:**

### **1. Assignment Behavior:**
```javascript
// Primitive assignment creates copies
let x = 10;
let y = x;
x = 20;
console.log(y); // 10 (independent copy)

// Object assignment creates references
let arr1 = [1, 2, 3];
let arr2 = arr1;
arr1.push(4);
console.log(arr2); // [1, 2, 3, 4] (shared reference)
```

### **2. Function Parameters:**
```javascript
// Primitives: pass by value
function changePrimitive(val) {
    val = 100;
}
let num = 5;
changePrimitive(num);
console.log(num); // 5 (unchanged)

// Objects: pass by reference
function changeObject(obj) {
    obj.name = "Modified";
}
let person = { name: "Original" };
changeObject(person);
console.log(person.name); // "Modified" (changed!)
```

## 🛠️ **Creating Immutable Copies:**

### **Shallow Copy:**
```javascript
// Object.assign()
let original = { a: 1, b: 2 };
let copy = Object.assign({}, original);

// Spread operator
let copy2 = { ...original };

// Array spread
let arr = [1, 2, 3];
let arrCopy = [...arr];
```

### **Deep Copy:**
```javascript
// JSON method (limited - no functions, dates, etc.)
let deepCopy = JSON.parse(JSON.stringify(original));

// Using structuredClone() (modern browsers)
let deepCopy2 = structuredClone(original);
```

## 🔒 **Making Objects Immutable:**

```javascript
let obj = { name: "John", age: 25 };

// Object.freeze() - shallow immutability
Object.freeze(obj);
obj.name = "Jane";     // Ignored in strict mode, throws error
obj.city = "NYC";      // Ignored in strict mode, throws error
console.log(obj);      // { name: "John", age: 25 }

// Object.seal() - prevents adding/removing properties
Object.seal(obj);      // Can still modify existing properties

// Object.preventExtensions() - prevents adding new properties
Object.preventExtensions(obj);
```

## 💡 **Memory Impact:**

```javascript
// Immutable: Each operation creates new value
let str = "Hello";
str = str + " World";  // Old "Hello" becomes garbage, new "Hello World" created
str = str + "!";       // Old "Hello World" becomes garbage

// Mutable: Same object modified in place
let arr = [1, 2, 3];
arr.push(4);          // Same array object, just modified
arr.push(5);          // Same array object, just modified
```

**🎯 Remember:**
- **Primitives**: Always immutable (new values created)
- **Objects**: Always mutable (can be modified in place)
- Understanding this is crucial for avoiding bugs with object references!

Q.What is the let var and const in JavaScript?

## 🔤 Variable Declarations in JavaScript

JavaScript has **three ways** to declare variables: `var`, `let`, and `const`. Each has different behavior regarding scope, hoisting, and reassignment.

## 📊 **Quick Comparison Table:**

| Feature | `var` | `let` | `const` |
|---------|-------|-------|---------|
| **Scope** | Function/Global | Block | Block |
| **Hoisting** | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |
| **Redeclaration** | Allowed | Not Allowed | Not Allowed |
| **Reassignment** | Allowed | Allowed | Not Allowed |
| **Introduced** | ES1 (1997) | ES6 (2015) | ES6 (2015) |

---

## 🔍 **Detailed Breakdown:**

### **1. var (Function Scoped)**
```javascript
// Function scoped
function example() {
    if (true) {
        var x = 1;
    }
    console.log(x); // 1 (accessible outside if block)
}

// Global scoped when declared outside function
var globalVar = "I'm global";

// Hoisting behavior
console.log(hoistedVar); // undefined (not error!)
var hoistedVar = "Hello";

// Redeclaration allowed
var name = "John";
var name = "Jane"; // No error
console.log(name); // "Jane"
```

### **2. let (Block Scoped)**
```javascript
// Block scoped
function example() {
    if (true) {
        let y = 1;
    }
    console.log(y); // ReferenceError: y is not defined
}

// Temporal Dead Zone (TDZ)
console.log(letVar); // ReferenceError (not undefined!)
let letVar = "Hello";

// Redeclaration not allowed
let age = 25;
let age = 30; // SyntaxError: Identifier 'age' has already been declared

// But reassignment is allowed
let count = 1;
count = 2; // ✅ This works
console.log(count); // 2
```

### **3. const (Block Scoped + Immutable Binding)**
```javascript
// Must be initialized at declaration
const pi = 3.14159;
const name; // SyntaxError: Missing initializer

// Cannot be reassigned
const score = 100;
score = 200; // TypeError: Assignment to constant variable

// Block scoped like let
if (true) {
    const temp = "temporary";
}
console.log(temp); // ReferenceError: temp is not defined

// Objects/Arrays: binding is constant, content is mutable
const person = { name: "Alice", age: 25 };
person.age = 26; // ✅ This works (modifying content)
person.city = "NYC"; // ✅ This works

const colors = ["red", "blue"];
colors.push("green"); // ✅ This works
console.log(colors); // ["red", "blue", "green"]

// But reassigning the entire object/array fails
// person = { name: "Bob" }; // ❌ TypeError
// colors = ["yellow"]; // ❌ TypeError
```

---

## 🎯 **Key Concepts Explained:**

### **📍 Scope Differences:**
```javascript
function scopeDemo() {
    // var: function scoped
    if (true) {
        var funcScoped = "I'm function scoped";
    }
    console.log(funcScoped); // ✅ Works

    // let/const: block scoped  
    if (true) {
        let blockScoped = "I'm block scoped";
        const alsoBlockScoped = "Me too";
    }
    // console.log(blockScoped); // ❌ ReferenceError
    // console.log(alsoBlockScoped); // ❌ ReferenceError
}
```

### **📍 Hoisting Behavior:**
```javascript
// var hoisting
console.log(varExample); // undefined
var varExample = "Hello";

// let/const hoisting (Temporal Dead Zone)
console.log(letExample); // ReferenceError
console.log(constExample); // ReferenceError
let letExample = "World";
const constExample = "!";
```

### **📍 Loop Behavior (Classic Example):**
```javascript
// var in loops (common mistake)
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // Prints: 3, 3, 3
}

// let in loops (correct behavior)
for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // Prints: 0, 1, 2
}
```

---

## 🚫 **Common Mistakes & Gotchas:**

### **1. var Hoisting Confusion:**
```javascript
function confusing() {
    console.log(x); // undefined (not error!)
    if (false) {
        var x = 1; // This declaration is hoisted
    }
    console.log(x); // undefined
}
```

### **2. const with Objects:**
```javascript
const config = { debug: true };
config.debug = false; // ✅ Allowed (modifying property)
config = {}; // ❌ TypeError (reassigning variable)
```

### **3. let/const in Temporal Dead Zone:**
```javascript
function tdz() {
    console.log(typeof x); // ReferenceError (not "undefined"!)
    let x = 1;
}
```

---

## 💡 **Best Practices:**

### **🎯 Modern JavaScript Guidelines:**

1. **Default to `const`** - Use when value won't be reassigned
2. **Use `let`** - When you need to reassign the variable
3. **Avoid `var`** - Unless working with legacy code

```javascript
// ✅ Good practices
const name = "Alice"; // Won't change
const users = []; // Array content may change, but not the binding
let counter = 0; // Will be reassigned
let currentUser; // May be assigned later

// ❌ Avoid
var oldStyle = "Please don't use me";
```

### **🔒 Immutability with const:**
```javascript
// For true immutability, use Object.freeze()
const config = Object.freeze({
    apiUrl: "https://api.example.com",
    timeout: 5000
});

config.apiUrl = "hacker-site"; // Silently ignored (strict mode: TypeError)
console.log(config.apiUrl); // Still "https://api.example.com"
```

---

## 🏃‍♂️ **Real-world Example:**
```javascript
function processUsers() {
    const API_URL = "https://api.example.com/users"; // Never changes
    let isLoading = true; // Will be toggled
    let users = []; // Will be populated
    
    // Block scope in action
    if (localStorage.getItem('cache')) {
        let cachedData = JSON.parse(localStorage.getItem('cache'));
        users = cachedData; // cachedData only exists in this block
        isLoading = false;
    }
    
    // cachedData is not accessible here
    return { users, isLoading };
}
```

**🎯 Remember:**
- **const**: Can't reassign, block scoped, must initialize
- **let**: Can reassign, block scoped, hoisted with TDZ  
- **var**: Can reassign, function scoped, hoisted as undefined
- **Modern preference**: `const` > `let` > avoid `var`

Q.What is the difference between declaration and initialization in term of variable?

## 🏗️ Variable Declaration vs Initialization

**Declaration** and **Initialization** are two distinct phases in a variable's lifecycle in JavaScript.

### 📍 **Declaration**
- **What it is**: Telling JavaScript that a variable exists
- **What happens**: Variable name is registered in memory
- **Memory allocation**: Space is reserved but no value is assigned

### 📍 **Initialization**  
- **What it is**: Assigning a value to the declared variable
- **What happens**: Actual value is stored in the reserved memory space
- **Can happen**: At declaration time or later

---

## 🔍 **Detailed Breakdown:**

### **📝 Declaration Only:**
```javascript
// Declaration without initialization
let name;           // Declared but not initialized
var age;            // Declared but not initialized  
// const city;      // ❌ SyntaxError: const must be initialized

console.log(name);  // undefined
console.log(age);   // undefined
console.log(typeof name); // "undefined"
```

### **📝 Declaration + Initialization:**
```javascript
// Declaration with immediate initialization
let name = "Alice";        // Declared AND initialized
var age = 25;             // Declared AND initialized
const city = "New York";  // Declared AND initialized (required for const)

console.log(name); // "Alice"
console.log(age);  // 25
console.log(city); // "New York"
```

### **📝 Separate Declaration and Initialization:**
```javascript
// Declaration first, initialization later
let score;              // Declaration
console.log(score);     // undefined

score = 100;            // Initialization (assignment)
console.log(score);     // 100

// Multiple assignments (re-initialization)
score = 200;            // Re-initialization
console.log(score);     // 200
```

---

## 🔄 **How Each Variable Type Behaves:**

### **1. var - Declaration & Initialization:**
```javascript
console.log(varExample); // undefined (declared but not initialized)
var varExample = "Hello";

// What actually happens due to hoisting:
// var varExample;        // Declaration is hoisted
// console.log(varExample); // undefined
// varExample = "Hello";    // Initialization stays in place
```

### **2. let - Declaration vs Initialization:**
```javascript
console.log(letExample); // ReferenceError: Cannot access before initialization
let letExample = "World";

// What happens:
// let letExample;        // Declaration is hoisted (but in TDZ)
// console.log(letExample); // ReferenceError (TDZ)
// letExample = "World";    // Initialization removes from TDZ
```

### **3. const - Declaration + Initialization (Mandatory):**
```javascript
// const MUST be initialized at declaration
const PI = 3.14159;     // Declaration + Initialization together

// This fails:
// const radius;        // SyntaxError: Missing initializer
// radius = 10;
```

---

## 🚀 **Advanced Examples:**

### **📍 Function Parameters:**
```javascript
function greet(name) {    // 'name' is declared as parameter
    // If no argument passed, name is declared but undefined
    console.log(name);    // Could be undefined
}

greet();               // name is declared but not initialized: undefined
greet("Alice");        // name is declared and initialized: "Alice"
```

### **📍 Object Property Declaration vs Initialization:**
```javascript
const person = {};     // Object declared and initialized

// Property declaration and initialization can be separate
person.name;           // Property declared (returns undefined)
person.name = "John";  // Property initialized
person.age = 25;       // Property declared and initialized together

console.log(person);   // { name: "John", age: 25 }
```

### **📍 Array Elements:**
```javascript
const numbers = [];         // Array declared and initialized (empty)
numbers[0];                // Index declared (returns undefined)
numbers[0] = 10;           // Index initialized
numbers[2] = 30;           // Index 2 initialized (index 1 remains undefined)

console.log(numbers);      // [10, undefined, 30]
console.log(numbers.length); // 3
```

---

## 🔍 **Hoisting Impact on Declaration vs Initialization:**

### **Example 1: var**
```javascript
console.log(x); // undefined (declared but not initialized)
var x = 5;

// Equivalent to:
var x;          // Declaration hoisted
console.log(x); // undefined
x = 5;          // Initialization stays in place
```

### **Example 2: Function Declaration vs Expression**
```javascript
// Function Declaration - both declaration and initialization hoisted
sayHello(); // ✅ Works - "Hello!"

function sayHello() {
    console.log("Hello!");
}

// Function Expression - only var declaration hoisted
sayGoodbye(); // ❌ TypeError: sayGoodbye is not a function

var sayGoodbye = function() {
    console.log("Goodbye!");
};

// Equivalent to:
var sayGoodbye;        // Declaration hoisted
sayGoodbye();          // TypeError (undefined is not a function)
sayGoodbye = function() { /* ... */ }; // Initialization stays in place
```

---

## 🎯 **Practical Implications:**

### **📍 Default Values:**
```javascript
// Using default values to handle uninitialized variables
function calculateArea(length = 0, width = 0) {
    // Parameters declared, with default initialization if not provided
    return length * width;
}

console.log(calculateArea());      // 0 (defaults used)
console.log(calculateArea(5, 3));  // 15 (values provided)
```

Q.What is hoisting in JavaScript?

## 🚀 Hoisting in JavaScript

**Hoisting** is JavaScript's behavior of moving declarations to the top of their containing scope during the compilation phase, before code execution.

### 📍 **What Actually Happens:**
- **Declarations** are processed before any code is executed
- **Variables and functions** are "lifted" to the top of their scope
- **Only declarations are hoisted, NOT initializations**

---

## 🔍 **Types of Hoisting:**

### **1. Variable Hoisting**

#### **`var` Hoisting:**
```javascript
// What you write:
console.log(x); // undefined (not ReferenceError!)
var x = 5;
console.log(x); // 5

// How JavaScript interprets it:
var x;          // Declaration hoisted to top
console.log(x); // undefined
x = 5;          // Initialization stays in place
console.log(x); // 5
```

#### **`let` and `const` Hoisting (Temporal Dead Zone):**
```javascript
// What you write:
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;

console.log(z); // ReferenceError: Cannot access 'z' before initialization
const z = 20;

// How JavaScript interprets it:
let y;          // Declaration hoisted but in "Temporal Dead Zone"
const z;        // Declaration hoisted but in "Temporal Dead Zone"
console.log(y); // ReferenceError (TDZ)
console.log(z); // ReferenceError (TDZ)
y = 10;         // Initialization removes from TDZ
z = 20;         // Initialization removes from TDZ
```

---

### **2. Function Hoisting**

#### **Function Declarations (Fully Hoisted):**
```javascript
// What you write:
sayHello(); // "Hello World!" - Works perfectly!

function sayHello() {
    console.log("Hello World!");
}

// How JavaScript interprets it:
function sayHello() {    // Entire function hoisted
    console.log("Hello World!");
}
sayHello(); // "Hello World!"
```

#### **Function Expressions (Only Variable Declaration Hoisted):**
```javascript
// What you write:
sayBye(); // TypeError: sayBye is not a function

var sayBye = function() {
    console.log("Goodbye!");
};

// How JavaScript interprets it:
var sayBye;             // Only declaration hoisted
sayBye();               // TypeError: undefined is not a function
sayBye = function() {   // Assignment stays in place
    console.log("Goodbye!");
};
```

#### **Arrow Functions (Same as Function Expressions):**
```javascript
// What you write:
greet(); // TypeError: greet is not a function

var greet = () => {
    console.log("Hi there!");
};

// How JavaScript interprets it:
var greet;              // Only declaration hoisted
greet();                // TypeError: undefined is not a function
greet = () => {         // Assignment stays in place
    console.log("Hi there!");
};
```

---

## 🎯 **Scope-wise Hoisting:**

### **Function Scope:**
```javascript
function example() {
    console.log(a); // undefined (not ReferenceError)
    console.log(b); // ReferenceError: Cannot access 'b' before initialization
    
    var a = 1;
    let b = 2;
    
    console.log(a); // 1
    console.log(b); // 2
}

// Equivalent to:
function example() {
    var a;              // var hoisted to function top
    let b;              // let hoisted but in TDZ
    
    console.log(a);     // undefined
    console.log(b);     // ReferenceError (TDZ)
    
    a = 1;              // Initialization
    b = 2;              // Initialization
    
    console.log(a);     // 1
    console.log(b);     // 2
}
```

### **Block Scope:**
```javascript
function blockExample() {
    console.log(x); // undefined (function scoped)
    // console.log(y); // ReferenceError: Cannot access before initialization
    
    if (true) {
        var x = "function scoped";
        let y = "block scoped";
        console.log(x); // "function scoped"
        console.log(y); // "block scoped"
    }
    
    console.log(x); // "function scoped"
    // console.log(y); // ReferenceError: y is not defined
}
```

---

## 🚫 **Common Hoisting Gotchas:**

### **1. Loop Variables:**
```javascript
// Confusing behavior with var
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // Prints: 3, 3, 3
}

// Due to hoisting, equivalent to:
var i;
for (i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // All closures reference same 'i'
}

// Fixed with let (block scoped):
for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // Prints: 0, 1, 2
}
```

### **2. Function Name Conflicts:**
```javascript
// What you write:
console.log(foo); // function foo() {...}

var foo = "I'm a variable";

function foo() {
    return "I'm a function";
}

console.log(foo); // "I'm a variable"

// How JavaScript interprets it:
function foo() {        // Function declaration hoisted first
    return "I'm a function";
}
var foo;                // var declaration hoisted (but ignored, name exists)
console.log(foo);       // function foo() {...}
foo = "I'm a variable"; // Assignment happens
console.log(foo);       // "I'm a variable"
```

### **3. Conditional Function Declarations:**
```javascript
if (true) {
    function conditionalFunc() {
        return "I exist";
    }
}

// In some environments this works, in others it doesn't
// Better approach:
let conditionalFunc;
if (true) {
    conditionalFunc = function() {
        return "I exist";
    };
}
```

---

## 🔄 **Temporal Dead Zone (TDZ) Explained:**

```javascript
function temporalDeadZoneExample() {
    // TDZ starts here for 'x' and 'y'
    
    console.log(typeof x); // ReferenceError (not "undefined"!)
    console.log(typeof y); // ReferenceError (not "undefined"!)
    
    let x = 1;  // TDZ ends for 'x'
    const y = 2; // TDZ ends for 'y'
    
    console.log(x); // 1
    console.log(y); // 2
}
```

---

## 📝 **Best Practices:**

### **✅ Good Practices:**
```javascript
// Always declare variables at the top of their scope
function goodExample() {
    const API_URL = "https://api.example.com";
    let data;
    let isLoading = false;
    
    // Use the variables...
    data = fetchData(API_URL);
}

// Use function expressions for conditional functions
let myFunction;
if (condition) {
    myFunction = function() {
        return "Conditional function";
    };
}

// Prefer let/const over var
const name = "Alice";
let age = 25;
```

### **❌ Avoid:**
```javascript
// Don't rely on hoisting
console.log(confusing); // undefined - but confusing!
var confusing = "Why does this work?";

// Avoid function declarations inside blocks
if (condition) {
    function badPractice() { // Avoid this pattern
        return "Unpredictable behavior";
    }
}

// Don't mix declarations and usage randomly
function messy() {
    doSomething(x); // Hard to understand
    var x = 5;
    doSomethingElse(y);
    let y = 10;
}
```

---

## 🔍 **Class Hoisting:**

```javascript
// Classes are hoisted but in TDZ (like let/const)
console.log(MyClass); // ReferenceError: Cannot access before initialization

class MyClass {
    constructor(name) {
        this.name = name;
    }
}

// Function declarations vs Class declarations
sayHello(); // Works - function declaration
// new MyClass(); // ReferenceError - class in TDZ

function sayHello() {
    console.log("Hello!");
}

class MyClass {
    constructor() {}
}
```

---

## 💡 **Real-world Example:**

```javascript
// Problematic code due to hoisting:
function processUser(user) {
    if (user.isActive) {
        var message = "User is active";
        var status = "online";
    } else {
        var message = "User is inactive";
        var status = "offline";
    }
    
    console.log(message); // undefined if user.isActive is false
    console.log(status);  // undefined if user.isActive is false
    
    // Both variables are hoisted to function top
}

// Better approach:
function processUser(user) {
    let message, status;
    
    if (user.isActive) {
        message = "User is active";
        status = "online";
    } else {
        message = "User is inactive";
        status = "offline";
    }
    
    console.log(message); // Always defined
    console.log(status);  // Always defined
}
```

**🎯 Key Takeaways:**
- **Hoisting moves declarations (not initializations) to the top**
- **`var`**: Hoisted as `undefined`
- **`let`/`const`**: Hoisted but in Temporal Dead Zone
- **Function declarations**: Fully hoisted (both declaration and definition)
- **Function expressions**: Only variable declaration hoisted
- **Understanding hoisting prevents common JavaScript bugs**


Q.Explain the concept of scope in JavaScript (global, function, block).

## 🎯 Scope in JavaScript

**Scope** determines where variables can be accessed in your code. It defines the **visibility** and **lifetime** of variables and functions.

### 📍 **What is Scope?**
- **Accessibility**: Which parts of code can access a variable
- **Lifetime**: How long a variable exists in memory
- **Name Resolution**: How JavaScript finds variables when referenced

---

## 🌍 **Types of Scope:**

### **1. Global Scope**
Variables declared outside any function or block have **global scope**.

```javascript
// Global scope
var globalVar = "I'm global with var";
let globalLet = "I'm global with let";  
const globalConst = "I'm global with const";

function testGlobal() {
    console.log(globalVar);   // ✅ Accessible
    console.log(globalLet);   // ✅ Accessible
    console.log(globalConst); // ✅ Accessible
}

if (true) {
    console.log(globalVar);   // ✅ Accessible
    console.log(globalLet);   // ✅ Accessible
    console.log(globalConst); // ✅ Accessible
}

// Accessible everywhere
console.log(globalVar);   // ✅ "I'm global with var"
console.log(globalLet);   // ✅ "I'm global with let"
console.log(globalConst); // ✅ "I'm global with const"
```

#### **Global Object Attachment:**
```javascript
var globalVar = "I'm attached to window";
let globalLet = "I'm not attached to window";
const globalConst = "I'm not attached to window";

console.log(window.globalVar);   // "I'm attached to window"
console.log(window.globalLet);   // undefined
console.log(window.globalConst); // undefined
```

---

### **2. Function Scope**
Variables declared inside a function are only accessible within that function.

```javascript
function functionScopeExample() {
    var functionVar = "I'm function scoped";
    let functionLet = "I'm also function scoped";
    const functionConst = "Me too!";
    
    console.log(functionVar);   // ✅ Accessible
    console.log(functionLet);   // ✅ Accessible
    console.log(functionConst); // ✅ Accessible
    
    // Nested function
    function innerFunction() {
        console.log(functionVar);   // ✅ Accessible (parent scope)
        console.log(functionLet);   // ✅ Accessible (parent scope)
        console.log(functionConst); // ✅ Accessible (parent scope)
    }
    
    innerFunction();
}

functionScopeExample();

// Outside the function
// console.log(functionVar);   // ❌ ReferenceError
// console.log(functionLet);   // ❌ ReferenceError
// console.log(functionConst); // ❌ ReferenceError
```

#### **Function Parameters:**
```javascript
function greet(name) {  // 'name' has function scope
    var greeting = "Hello";  // function scoped
    
    console.log(name);     // ✅ Accessible
    console.log(greeting); // ✅ Accessible
}

greet("Alice");
// console.log(name);     // ❌ ReferenceError
// console.log(greeting); // ❌ ReferenceError
```

---

### **3. Block Scope**
Variables declared inside `{}` blocks are only accessible within that block (**let** and **const** only).

```javascript
function blockScopeExample() {
    if (true) {
        var blockVar = "I'm NOT block scoped (function scoped)";
        let blockLet = "I'm block scoped";
        const blockConst = "I'm also block scoped";
        
        console.log(blockVar);   // ✅ Accessible
        console.log(blockLet);   // ✅ Accessible
        console.log(blockConst); // ✅ Accessible
    }
    
    console.log(blockVar);   // ✅ Accessible (var is function scoped)
    // console.log(blockLet);   // ❌ ReferenceError
    // console.log(blockConst); // ❌ ReferenceError
}

blockScopeExample();
```

#### **Different Block Types:**
```javascript
// if blocks
if (true) {
    let ifScoped = "Only in if block";
}

// for loops
for (let i = 0; i < 3; i++) {
    let loopScoped = "Only in loop";
    console.log(loopScoped); // ✅ Works
}
// console.log(i);          // ❌ ReferenceError
// console.log(loopScoped); // ❌ ReferenceError

// while loops
while (false) {
    let whileScoped = "Only in while";
}

// switch statements
switch (true) {
    case true:
        let switchScoped = "Only in switch";
        break;
}

// try-catch blocks
try {
    let tryScoped = "Only in try";
} catch (error) {
    let catchScoped = "Only in catch";
}

// Just curly braces
{
    let blockScoped = "Just a block";
    console.log(blockScoped); // ✅ Works
}
// console.log(blockScoped); // ❌ ReferenceError
```

---

## 🔗 **Scope Chain & Lexical Scoping:**

JavaScript uses **lexical scoping** - scope is determined by where variables are declared in the code.

```javascript
const global = "I'm global";

function outer() {
    const outerVar = "I'm in outer";
    
    function middle() {
        const middleVar = "I'm in middle";
        
        function inner() {
            const innerVar = "I'm in inner";
            
            // Inner can access all outer scopes
            console.log(innerVar);  // ✅ "I'm in inner"
            console.log(middleVar); // ✅ "I'm in middle" 
            console.log(outerVar);  // ✅ "I'm in outer"
            console.log(global);    // ✅ "I'm global"
        }
        
        inner();
        // console.log(innerVar); // ❌ ReferenceError
    }
    
    middle();
    // console.log(middleVar); // ❌ ReferenceError
    // console.log(innerVar);  // ❌ ReferenceError
}

outer();
```

### **Scope Chain Lookup:**
```javascript
let x = "global x";

function demo() {
    let x = "function x";
    
    if (true) {
        let x = "block x";
        console.log(x); // "block x" (nearest scope wins)
    }
    
    console.log(x); // "function x"
}

demo();
console.log(x); // "global x"
```

---

## ⚡ **var vs let/const Scoping Differences:**

### **Function vs Block Scope:**
```javascript
function scopeComparison() {
    if (true) {
        var varVariable = "Function scoped";
        let letVariable = "Block scoped";
        const constVariable = "Block scoped";
    }
    
    console.log(varVariable);   // ✅ "Function scoped"
    // console.log(letVariable);   // ❌ ReferenceError
    // console.log(constVariable); // ❌ ReferenceError
}
```

### **Loop Scope (Classic Example):**
```javascript
// var in loops - function scoped
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(`var: ${i}`), 100); // var: 3, 3, 3
}

// let in loops - block scoped
for (let j = 0; j < 3; j++) {
    setTimeout(() => console.log(`let: ${j}`), 100); // let: 0, 1, 2
}

console.log(i); // 3 (accessible outside loop)
// console.log(j); // ReferenceError (not accessible)
```

Q.What is the difference between == and ===?

== checks only value (with type conversion), while === checks both value and data type


Q.What are truthy and falsy values in JavaScript?
In JavaScript, every value is either truthy (treated as true) or falsy (treated as false) when evaluated in a Boolean context (like inside if conditions).

These are always considered false:

1.false
2.0
3.-0
4.0n (BigInt zero)
5."" (empty string)
6.null
7.undefined
8.NaN

Q.What is a closure and why is it used?
A **closure** is a feature where an **inner function has access to variables from its outer (enclosing) function's scope** even after the outer function has finished executing.

### 📍 **What is a Closure?**
- **Definition**: A function bundled together with references to its surrounding state (lexical environment)
- **Key Point**: Inner function "remembers" the environment in which it was created
- **Lifetime**: Variables in the closure persist even after outer function returns

---

## 🔍 **How Closures Work:**

### **Basic Example:**
```javascript
function outerFunction(x) {
    // Outer function's variable
    let outerVariable = x;
    
    // Inner function (this creates a closure)
    function innerFunction(y) {
        // Inner function can access outerVariable
        return outerVariable + y;
    }
    
    return innerFunction; // Return the inner function
}

// Usage
const addFive = outerFunction(5); // outerFunction executes and returns innerFunction
console.log(addFive(3)); // 8 (5 + 3)

// Even though outerFunction finished executing,
// innerFunction still remembers outerVariable (5)
```

### **Step-by-step Breakdown:**
1. `outerFunction(5)` is called
2. `outerVariable` is set to `5`
3. `innerFunction` is created (forming a closure over `outerVariable`)
4. `outerFunction` returns `innerFunction` and finishes execution
5. `addFive` now holds reference to `innerFunction`
6. When `addFive(3)` is called, it still has access to `outerVariable` (5)

---

## 🎯 **Classic Closure Example - Counter:**

```javascript
function createCounter() {
    let count = 0; // Private variable
    
    return function() {
        count++; // Increment the private variable
        return count;
    };
}

// Create counters
const counter1 = createCounter();
const counter2 = createCounter();

// Each counter maintains its own count
console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter1()); // 3

console.log(counter2()); // 1 (separate counter)
console.log(counter2()); // 2

// count variable is private - cannot access directly
// console.log(count); // ReferenceError: count is not defined
```
---
Q.What is the difference between function declaration and function expression?
Function Declaration

1.A function defined with the function keyword and a name.
2.Hoisted → can be called before it is defined

console.log(greet()); // ✅ works

function greet() {
  return "Hello!";
}

Function Expression

1.A function assigned to a variable (can be anonymous or named).
2.Not hoisted → can only be called after definition.
// console.log(greet()); // ❌ ReferenceError

const greet = function () {
  return "Hello!";
};
console.log(greet()); // ✅ works


Q.What is the difference between synchronous and asynchronous JavaScript?
Synchronous JavaScript executes code line by line and blocks further execution until a task finishes, while asynchronous JavaScript allows non-blocking execution where tasks like API calls or timers run in the background and complete later via callbacks, promises, or async/await.

Q. What is the difference between map() and forEach()?
map() creates a new array with transformed values, while forEach() just executes a function on each element and returns undefined. Use map() when you need a result, forEach() for side-effects.

Q.2. What is the difference between null and undefined?

1.null is an intentional empty value assigned by the developer.
2.undefined means a variable has been declared but not assigned.

Q.What is the difference between a function declaration, a function expression, and an arrow function?

1.Declarations are hoisted and can be called before definition.
2.Expressions are not hoisted.
3.Arrow functions don’t have their own this and are shorter syntax.

Q.What is the difference between for...in and for...of loops?

1.for...in iterates over object keys.
2.for...of iterates over iterable values like arrays and strings.

Q. What is the difference between call(), apply(), and bind()?

1.call() calls a function with arguments one by one.
2.apply() calls with arguments as an array.
3.bind() returns a new function with this fixed, without calling immediately.


Q. What is the difference between setTimeout() and setInterval()?

1.setTimeout() runs code once after a delay.
2.setInterval() runs repeatedly at fixed intervals.

Q.What is the difference between localStorage, sessionStorage, and cookies?

1.localStorage: data persists until cleared manually.
2.sessionStorage: clears when the tab is closed.
3.cookies: small data with expiry, sent with every HTTP request.

Q.What is the difference between a shallow copy and a deep copy?
A shallow copy only copies the first level of an object, so nested objects or arrays still share references with the original, whereas a deep copy creates a fully independent clone where even nested objects are duplicated and do not affect the original.

Q. What is the difference between event bubbling and event capturing?
In Event Bubbling, the event starts from the target element and bubbles up to the root, while in Event Capturing, the event starts from the root and travels down to the target element.

Q.What is the difference between slice() and splice() in arrays?
slice() returns a shallow copy of a portion of the array without modifying the original, while splice() actually changes the original array by adding, removing, or replacing elements

Q.What is the difference between Object.freeze() and Object.seal()?
Object.freeze() makes an object fully immutable — you can’t add, remove, or modify its properties.
On the other hand, Object.seal() prevents adding or removing properties, but you can still update the existing property values.

Q.What is the difference between Promise.all(), Promise.race(), and Promise.allSettled()?

1.Promise.all(): waits for all to resolve (fails if one rejects).
2.Promise.race(): resolves/rejects with the first settled promise.
3.Promise.allSettled(): waits for all and returns results (success or failure).

Q.What is the difference between find and filter?
Definition:

find() → Returns the first element that matches the condition.
filter() → Returns all elements that match the condition as a new array.

Q.