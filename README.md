# Interview Questions

<br/>

## Table of Contents

* [Basics](#basics)
* [HTML Questions](#html-questions)
* [CSS Questions](#css-questions)
* [SCSS Questions](#scss-questions)
* [Angular Material](#angular-material)
* [ASYMPOTIC Notations](#asympotic-notations)
* [Javascript](#javascript)
* [RXJS](#rxjs)
* [Angular](#Angular)
* [HR](#hr)
* [Coding Notes](#coding-notes)

<br/>

## Basics
1. ### One line/One Command/One Instruction/One Statement
   A Statement is one complete instruction that program can execute
   
2. ### Synchronous
   Code is executed line by line, next statement runs only after the current one has finished
   
3. ### Asynchronous
   Code can start the task, but instead of waiting for it to finish, it moves to the next statement. the task completes later, and the program handles the result when its ready.

4. ### Static typing
Types checked at compile time, can not change during execution
 
7. ### Dynamic typing
Types checked at runtime , can change during execution

<br>

## HTML Questions

1. ### What do H, T, M and L stand for in HTML?. Explain each term in detail.
**HTML** stands for **HyperText Markup Language**.
- **HyperText**: Ability to create Links that connect web pages.  
- **Markup**: Tags(Markup) that describe what content is (text, image, paragraph)  
- **Language**: Language (standard way to create web pages).

2. ### What is the purpose of the `<!DOCTYPE html>` declaration? What happens if you don’t include it?

`<!DOCTYPE html>` tells the browser to render the web page in **standard mode**.

- **Standard mode** follows modern rendering rules based on **W3C web standards**

If it is not included:
- The browser may enter **quirks mode** (if older browser version)
- Quirks mode rendering rules are defined by **browser vendors**
- The page may not look correct or consistent across browsers

3. ### Is HTML case-sensitive?

HTML is **case-insensitive**.

- Uppercase and lowercase are treated same  
- In practice, lowercase is preferred

4. ### Explain the `<head>` tag

`<head>` tag contains **metadata about the web page**.

It includes:
- Title
- CSS links
- JavaScript files
- Meta information (charset, viewport)

5. ### How can you refresh a page every 60 seconds using HTML?

Using the **meta refresh tag** inside the `<head>`.

```html
<!-- This refreshes page every 60 seconds -->
<meta http-equiv="refresh" content="60">
```

6. ### What are block-level and inline elements?

- **Block-level elements** take full available width and start on a new line  
  Example: `div`, `p`

- **Inline elements** take only required width and stay in same line  
  Example: `span`, `a`

7. ### What is the `<table>` tag? Why is it important?

`<table>` tag defines an HTML table.

important because:
- It organizes data in tabular form

8. ### What do `rowspan` and `colspan` do?

- **`rowspan`** span a table cell across multiple rows.  
  Example: `rowspan="2"` spans the cell across 2 rows

- **`colspan`** span a table cell across multiple columns.  
  Example: `colspan="2"` spans the cell across 2 columns

9. ### What are different ways to take input from users in HTML?

- Input box
- Radio button
- Checkbox
- Textarea
- Select (dropdown)
- Button

10. ### How do you create a file upload button?
using an input element with `type="file"`.

`<input type="file">`

11. ### How can you restrict users to select only `.jpg` files?

using the **`accept` attribute**.

```html
<!-- Only .jpg files will be selected -->
<input type="file" accept=".jpg">
```

12. ### Explain the `<marquee>` tag and its usage
was used to create moving text (simple animation) on a web page.
- It is deprecated in HTML5

13. ### What are semantic and non-semantic elements?
    
- **Semantic elements** clearly describe their meaning and purpose  
  Examples: `header`, `footer`, `section`, `nav`, `aside`

- **Non-semantic elements** do not describe their meaning  
  Examples: `div`, `span`

14. ### What is the significance of the `<noscript>` tag?

used to show **fallback content** when JavaScript is disabled or not supported in the browser.

- It runs **only if JavaScript is disabled**

```html
<noscript>
  Please enable JavaScript to use this website.
</noscript>
```

15. ### What is the `<picture>` tag and what are its advantages?

used to load different images based on screen size.

#### Benefits:
- Improves performance  
- Loads the most suitable image for the device  

**Difference:** `Media queries` resize the same image  while `<picture>` loads different image based on screen size.  

#### Example:
```html
<!-- Image will be loaded based on screen size, img is the fallback -->
<picture>
  <source media="(max-width: 600px)" srcset="small.jpg">
  <source media="(min-width: 601px)" srcset="large.jpg">
  <img src="large.jpg" alt="Responsive image">
</picture>
```

16. ### What is the `srcset` attribute and why is it used?

provides **multiple image options** for browser to choose **best image based on screen size**.

#### Why it is used:
- Browser chooses the most suitable image
- Avoids downloading large images unnecessarily
- Improves performance

```html
<!-- `600w` and `1200w` are image size hints for the browser -->
<!-- Browser compares image size with screen size and selects the best image -->
<img 
  src="image-small.jpg"
  srcset="image-small.jpg 600w, image-large.jpg 1200w"
  alt="Sample image">
```
17. ### Explain `loading="lazy"` and `loading="eager"`

- **Lazy loading**: Content loads only when needed  
- **Eager loading**: Content loads immediately

In HTML, lazy and eager loading are supported only for:
- Images (`<img>`)
- Iframes (`<iframe>`)

```html
<!-- Lazy loading image -->
<img src="image.jpg" loading="lazy" alt="Lazy loaded image">

<!-- Eager loading iframe -->
<iframe src="page.html" loading="eager"></iframe>
```
18. ### How can you change image in the browser tab (favicon)?

using a **favicon image** defined inside the `<head>` tag as `<link rel="icon" href="favicon.ico">`

19. ### How do you serve a page with content in multiple languages?
- browser sends language preferences in HTTP request header **`Accept-Language`**
- server can use this header to return content in requested language.
- returned HTML document should declare its language using the **`lang` attribute**  
  Example: `<html lang="en">`
- To inform search engines about different language versions of the same content, use:
  - `<link rel="alternate" hreflang="de" href="http://de.example.com/page.html">`

20. ### What things must you be careful about when designing or developing multilingual websites?
- Content must be consistent across languages  
- The meaning should remain the same, not just word-by-word translation  
- Dates, numbers, and formats should follow local conventions  
- Language should be declared properly (for SEO and accessibility)

21. ### What are `data-*` attributes used for?
    
used to store **extra / custom data** on an HTML element.
- do not affect layout or styling
- mainly used by JavaScript

Example:
```html
<button data-user-id="123">Click</button>
```

**Follow-up: Why not use id?**
- id is used to uniquely identify an element
- not meant to store arbitrary data
  
22. ### Why place CSS in `<head>` and JavaScript before `</body>`?

- **CSS `<link>` tags** are placed inside `<head>` so styles load before the page is rendered
- **JavaScript `<script>` tags** are placed before `</body>` so HTML loads first and the page doesn’t get blocked

23. ### What are HTML elements and attributes?
    
- **HTML elements** are the building blocks of a web page  
- **Attributes** provide additional information about an element

24. ### What is the difference between `<div>` and `<span>`?
- `<div>` is block-level element  
- `<span>` is inline element

25. ### How do you center a `<div>` ?
    
- Using flexbox
- Using grid
- Using position absolute with transform

<br>

## CSS Questions

1. ### What is CSS
- stands for **Cascading Style Sheets**.
- used to **style HTML elements**.

2. ### What is inheritance in CSS?
- child elements can inherit some styles from their parent
- only text related properties usually inherit

3. ### What is the CSS box model?
defines the **structure of an element**.
It consists of:
- Content (the actual content)
- Padding
- Border
- Margin

4. ### What is the difference between margin, padding, and border?
- **Padding** space inside the border, around the content  
- **Border** defines the boundary around the element  
- **Margin** space outside the border, separating elements

5. ### What is box-sizing in CSS?
defines how width and height of an element are calculated.
- By default, width applies only to content
- With `box-sizing: border-box`, padding and border are included in the element’s width and height

6. ### Difference between `display: none`, `visibility: hidden`, and `opacity: 0`  
- **`display: none`** → hides the element from the UI and takes no space in the UI  
- **`visibility: hidden`** → hides the element from the UI but still takes space in the UI  
- **`opacity: 0`** → makes the element transparent

7. ### What are common CSS units?
- **px** → fixed pixel unit (`1px = 1/96 inch`)
- **em** → relative to font-size of parent element
- **rem** → relative to root (`html`)
- **vh** → percentage of viewport height
- **vw** → percentage of viewport width

8. ### What are CSS selectors?
used to select HTML elements to apply styles.
- **Class selector** → can target multiple elements  
- **ID selector** → targets one unique element

9. ### What is CSS selector specificity?
Selector specificity is the priority system, to decide which style is applied.
- Inline styles (highest)
- ID selectors
- Class selectors
- Element selectors (lowest)

10. ### What is `!important` and why is it considered dangerous?
used to give a CSS property the highest priority, overriding all other styles.

why it is considered dangerous:
- it breaks the normal specificity rules
- leads to messy, unmaintainable styles

11. ### Explain CSS positioning [video explanation](https://www.youtube.com/watch?v=YEmdHbQBCSQ)

**static**
- Default value , No effect on the element 
- `top`, `left`, etc. do not work

**relative**
- Element stays in the normal flow
- Can be moved relative to its original position

**absolute**
- Element is removed from normal document flow
- Positioned relative to the nearest positioned parent element
- If none exists, positioned relative to the viewport

**fixed**
- Element is positioned relative to the viewport
- Does not move on scroll

**sticky**
- Sticks to the specified position when a scroll threshold is reached

12. ### What is `z-index` in CSS?
controls the stacking order of elements
- accepts any integer value (positive, negative, or zero)
- no defined maximum or minimum value

13. ### How does stacking context work?
stacking context is **separate stacking environment** for elements.
- `z-index` works only within the same stacking context
- Elements in different stacking contexts (parents) cannot overlap based on `z-index` alone

14. ### What is Flexbox?
CSS layout model used to arrange items in one direction (row or column).
- Enabled using `display: flex`
- Default flex direction is `row`, Can be changed to `column` using `flex-direction: column`
- used in one directional layouts ex. - nav bar, various sections

15. ### What is CSS Grid?
CSS layout model used to arrange items in two directions (rows and columns).
- Enabled using `display: grid`
- `grid-template-columns` and `grid-template-rows` define rows and columns
- Used for two-dimensional layouts like photo grids and card layouts
  

## SCSS Questions

1. ### What is Sass/Scss
Sass/Scss is css preprocessor. It extends CSS with features that CSS originally didn’t have.

Browser don't understand sass/scss. You write **Sass/Scss → compile → plain CSS → browser**.

- SASS(syntactically awesome style sheets)
   - No braces {} and semicolons ;
   - Indentation-based (like Python)

- SCSS (Sassy CSS)
   - Newer(after css3), most-used
   - Uses braces {} and semicolons ;
     
2. ### Why SCSS exists
Plain CSS becomes painful when:
- Files get large
- Styles repeat
- Components grow
  
SCSS fixes this with:
- Variables: ex- $bg-color: red;
- Operators: 5rem + 5rem
- Nesting: can write nested code
- Mixins: use @mixin for repeated code to avoid repetition
- Parameters: can use parameters
- Partials: divide code. ex. mixins code in different file and variable code in different file then we can import that code in one file using @use()

this powers SCSS to make CSS maintainable at scale.

3. ### What is preprocessor
build time tool that transform code written in extended syntax to standard syntax understood by run time.

## Angular Material

1. ### What is Angular Material?
UI component library for Angular.
- Provides ready-made, reusable components Based on Material Design

2. ### What is Material Design/MDC (Material Design Components)?
plateform agnostic, open-source design system(library), developed by Google in 2014 to create intuitive, and responsive user interfaces for mobile and web platforms.

3. ### What was Angular Material using before migrating to MDC?
Earlier, Angular Material had its own internal implementations of Material components instead of using MDC.

4. ### Why did Angular Material move to MDC-based components?
- Align with Google’s official Material Design implementation
- Reduce maintenance effort
- Improve design consistency and accessibility

## ASYMPOTIC Notations

1. ### what are asympotic notations
mathematcial way to describe efficiency of algorithms in terms of time and space complexity.
#### Common Types:
1. **Big O (O)** – Worst Case  (upper bound)
1. **Big Omega (Ω)** – Best Case  (lower bound)
1. **Theta (Θ)** – Average Case (avg bound)

**Rules To Calculate Complexity**
- Calculate worst case senario
- Avoid Constants
- Avoid Lower Values

2. ### What is time complextiy
Rate at which time taken increases with respect to input size.

**How to Calculate:**
- Write how much work happens for each outer iteration (ex: i =1 inner runs 1 time, i=2, inner runs 2 time).
- Add the work. (ex: 1 time + 2 time + 3time+ n-1 times + n times) = (1+2+3+...+(n-1)+n)
- Simplify. (1+2+3+...+n) => n(n+1)/2
- Avoid Constants (As per rule)
- Avoid Lower Values (As per rule)

**If we repeatedly halve the problem size, we remove a fraction each time so steps grow slowly. that's the logarithmic growth. O(logn)**

**Logarithmic Time Complexity (Divide by Constant Pattern)**

```js
while (n > 1) {
    n = n / c;
}
```
- After k iterations: n / c^k
- Stop when: n / c^k = 1
- Rearrange: c^k = n
- Solve for k: //k = log_c(n)
- Final Time Complexity: O(log n)


<br>

## Javascript
### 1. What is JavaScript? [How JavaScript Works?](https://youtu.be/ZvbzSrg0afE)
JavaScript is a single-threaded language, executes code synchronously by default.
When a javascript program runs a Global execution context is created, which has two parts.
- Memory Component (varialble environment): contains variables and functions as key value paris. ex. fun:{}, a:10
- Code Component (thread of execution): executes code line by line in single thread.
  
2. ### Is Javascript synchronous or asynchronous?
Synchronous by default, supports asynchronous operations using runtime environment.

3. ### Is JavaScript dynamically typed or statically typed?
- Javascript is Dynamically typed.
- Typescript is Statically typed.
  
4. ### What are different data types in javascript?
two types: **primitive** and **non-primitive**.

#### Primitive Data Types
- string
- number
- boolean
- null
- undefined
- bigint
- symbol

#### Non-Primitive Data Types
- object

> Note:
- Arrays, functions, and dates are all objects internally.
- `typeof null` returns `"object"` due to a historical bug, but `null` itself is a primitive.

4. ### Difference between null and undefined?
**null** - explicitely assigned to represent a value(null). (convey intent)
**undefined**- variable declared but not assigned a value(default state).

5. ### What are the difference between undeclared and undefined variables.
**undeclared** - variable does not exist in program at all. if we try to read value of an undeclared variable it will give error.

**undefined** - variable declared but not assigned a value(default state

6. ### What is Hoisting in javascript?
variables and functions can be used before declaring it. the javascript comiler moves all the declarations of variables and functions on top. so there will not be any error. this is called hoisting

7. ### what are varius things hoisted in javascript?
- **Function declaration**: fully hoisted
- **Arrow funcation**: not hoisted
- **Annonymous function expression**: not hoisted
- **var**: hoisted as undefined
- **let**: hoisted but in temporal dead zone
- **const**: hoisted but in  temporal dead zone
- **class declarations** - hoisted but not initialized

8. ### What is temporal dead zone?
specific time period during javascript code execution, where variables declared with let and const exist but can not be accessed until value is assigned.
Any attempt to access them result in reference errors.

9. ### What is order(priority) of hoisting?
- Function declartions
- var
- let/const/class

10. ### What are the difference between let, var and const?
**Scope**: 
   - var are function scoped, if declared outside then global scope,
   - let, const are braces scoped
**Reassignment**:
   - var, let can be reassigned
   - const can not be reassigned
**Hoisting**:
   - var hoisted with undefined
   - let and const hoisted but in temporal dead zone
     
11. ### Can we modify array declared with const?
yes, because const prevents reassignment and not immutability.

12. ### What is difference between == and === in javascript?
**===**: Compares both value and data type (without type coercion)
**==**: Compares value only (with type coercion)

13. ### What is the difference between && and ||
**&&**: returns first falsy or last truthy
**||**: returns first truthy or last

14. ### What is difference between || and ??
**||**: checks falsy values (0, "", false, null, undefined) (returns first truthy or last)
**??**: checks only null and undefined (returns first value that is not null or undefined or last)

15. ### What is the difference between 'Pass by value' and 'Pass by Reference'?
whenever a function is called, arguments can be passed in two ways, either by pass by value or pass by reference.
- Primitive data types such as string, number, boolean, null, undefined are passed by value
- In Pass by value, parameters passed as an arguments creates their own copy. so any changes made inside the function are made to the copied value. does't affect the original value.
- Non-Primitive data types such as object, arrays, are passed by reference.
- In pass by reference, parameters passed as an arguments does not create theri own copy, any change made inside the function affect original value.

16. ### What is a closure?
A closure is a function that remembers and can access variables from its outer lexical scope even after the outer function has finished execution.

used for - private variables (variables inside function), callbacks


```js
function Outer() {
    var x = 10;
    function Inner() {
        console.log(x)
    }
    return Inner
}

var close = Outer()
close(); //10
```

17. ### What is currying
Converting a function with multiple arguments into a sequence of nested functions, each taking one argument.
```js
function add(a) {
    const c = 5;
    return function add(b) {
        console.log(a+b+c)
    } 
}

add(2)(3) //10
```

18. ### What are callbacks in javascript?
Callback is a function which is passed as an argument to another function, which can be executed later in the code.

**Usage**: setTimeOut, Higher Order functions(map, filter, forEach), Handling events (click/key press events), Handling aynchronous operations (reading files, making http requests)
```js
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}

function sayBye() {
  console.log("Bye");
}

greet("Kanhaiya", sayBye);

//Hello Kanhaiya
//Bye
```

19. ### What is Callback hell?
Callback hell is a situation where multiple nested callbacks make the code hard to read and maintain. so to solve that we use promise.

20. ### What are higher order functions in javascript?
Function which takes another function as an argument or returns a function as a result.
**Example:** setTimeout, map, forEach
Adavntages- callback functions, asynchronous programming, abstraction, code reusability, concise and readable code.

21. ### What is IIFE?
Immediately invoked function expression(IIFE) is function in javascript that:
- is defined as an expression
- runs immediately after it is created
```js
(function sayHi() {
    console.log('Hi')
})()

//arrow function version
(() => {
    console.log("hello")
})()

//Wrapping in () forces javascript to treat it as expression and not declaration.
```

22. ### What is eval()?
executes string as code at runtime. string can be variable, statements, or javascript expression.
```js
eval("console.log(2 + 2)"); // 4
```

23. ### What is arrow function in javascript?
- Introduced in ES6, simple and shorter way to write function using =>
- Multiline logic needs return and {}
  
**Limitations**:
  - Can not be accessed before initialization
  - Does not have access to arguments object
  - Does not have their own this, instead inherit this from the surrounding code at the time function is defined.
  - Can not be used as constructors, Using them with the new keyword to create instances throws a typeError
  - Can not be used as generator functions
    
**How to Find this Value**
👉 Rule 1 (Arrow)
- Arrow = copy this from the first normal function above, ignores call, bind apply

👉 Rule 2 (Normal function)
- Normal = this decided by how it is called, call(x), bind(x), apply(x) set to x.

24. ###  Why arrow functions introduced/Advantages of arrow functions
shorter syntax, inreases readability, makes **this** behaviour predicatable.

25. ### What is strict mode and non strict mode in javasript?
- Non-strict: default in browser(script) -> **this** gives window
- Strict Mode: Default in module systems/Modern Framework -> **this** gives undefined

26. ### What is generator function in javascript?
- function which can be paused and resumed at any point during execution.
- defined using function, and contains one or more yield expressions
- main method is next(), when called, it runs the execution until the nearest yield.
- return an object which contains 2 properties
     - value: the yielded value
     - done: true if function code has finished, else false.
```js
function* generatorFunction() {
    yield 1;
    yield 2;
    yield 3;
    return 4
}

const generator = generatorFunction();
console.log(generator.next()) //{ value: 1, done: false }
console.log(generator.next()) //{ value: 2, done: false }
console.log(generator.next()) //{ value: 3, done: false }
console.log(generator.next()) //{ value: 4, done: true }
```

27. ### What is [object](https://www.scaler.com/topics/objects-in-javascript/) in javascript?
Collections of key-value pairs (properties), where keys are strings (or symbols), and values can be of any type, including other objects.

28. ### What are the different ways to create object in javascript?
Javascript offers multiple ways to create objects such as: 

👉 Syntax:
```js
// Object literal syntax
const obj = {
    key1: value1,
    key2: value2,
}

// new keyword syntax
function Person(name, age, city) {
    this.name = name
    this.age = age
    this.city = city
}
let person1 = new Person("Ramsey", 32, "Dreatfort")
console.log(person1.name)

class Person {
    constructor(name) {
        this.name = name;
    }
}
const p1 = new Person("Kanhaiya")
console.log(p1.name)

// Built in object constructor
const obj = new Object()
obj.name = "Kanhaiya"
console.log(obj)

// Object.create Syntax
const proto = {
  greet() {
    console.log("Hello");
  }
};

const obj = Object.create(proto);
obj.name = "Kanhaiya";
console.log(obj)
```

29. ### How to add, delete, access object properties.
```js
const obj = new Object()

//Add Properties
obj.name = "Kanhaiya"
obj.age = "28"
obj.city = "Auraiya"
obj["profession"] = "Software Engineer"

// Access Properties
console.log(Object.entries(obj)) // give properties in key value pairs
console.log(Object.keys(obj)) // give object keys
console.log(Object.values(obj)) // give ojbect values

// Delete a key
delete obj.city
delete obj["profession"]

console.log(Object.values(obj))
```
30. ### What is prototype in javascript?
An object from which other objects inherit properties and methods. when a property is not found in object, js searches it into objects prototype and continues to search until found or prototype chain ends.

```js
const animal = {
  sound: "Roar"
};
const lion = Object.create(animal); /a new lioin object is created and animal is set as prototype of lion object
console.log(lion.sound); // "Roar" -> lion.sound is not found in lion, so JavaScript searches lion's prototype (animal) and finds sound there.

const arr = [1, 2, 3];
arr.push(4);
console.log(arr); // [1, 2, 3, 4] // arr.push(4) works because push() is not stored in arr; JavaScript finds it in Array.prototype through the prototype chain.
```
31. ### What is prototype inheritance?
A mechanism in javascript, where an object can inherit properties and methods from another object through prototype chain.
```js
const person = {
  greet() {
    console.log("Hello");
  }
};

const user = {
  name: "John"
};

Object.setPrototypeOf(user, person); //here we set person object as prototype of user object

user.greet(); // Hello
```

33. ### What are Promises in JavaScript?

- Promise is an object which represents the eventual completion or failure of an asynchronous operation in javascript.

- At any point of time, promise will be in any of these below states.
  - **Fulfilled:** Action related to promise is succeded.
  - **Rejected:** Action related to the promise is failed.
  - **Pending:** Promise is neither fulfilled nor rejected.
  - **Settled:** Promise has been fulfilled or rejected.

- Promise can be consumed by registering the functions using `.then()` and `.catch()` methods.

- Promise constructor: will take one argument which is a callback function.

- This callback function takes 2 arguments:
  - `resolve`
  - `reject`

- If performed operations inside callback function wents well then we will call `resolve()` and if does not go well then we will call `reject()`.

```js
let promise = new Promise(function(resolve,reject){
const x = "Saikrishna";
const y = "Saikrishna";
if(x === y){
resolve("Valid")
} else{
let err = new Error("Invalid")
reject(err)
}
})
promise.then((response)⇒{
console.log("success",response)
}).catch((err)⇒{
console.log("failed",err)
})
```

37. ### Differences between Promise.all, allSettled, any, race ?
- Promise.all:
  - Will wait for all promises to resolve or any one promise to reject.
- Promise.allSettled:
  - Will wait for all promises to settle (either fulfilled or rejected).
- Promise.any:
  - Will return if any one promise fulfills or rejects when all the promises are rejected.
- Promise.race:
  - Will return as soon as when any one of the promise is settled.

38. ### What is the difference between async and await?
- async → marks a function as asynchronous and returns a Promise.
- await → waits for a Promise to resolve before continuing execution.

39. ### What is difference between promise and observable?
### Promise
- Has 4 states: fullfilled, rejected, pending, settled.
- Returns a single value.
- Executes immediately when created.
- Cannot be cancelled.

### Observable
- Can emit multiple values over time.
- Has 3 notifications: `next`, `error`, and `complete`.
- Executes only when subscribed.
- Can be cancelled using `unsubscribe()`.

40. ### What is [Call Stack](https://youtu.be/iLWTnMzWtj4) in JavaScript?
The **Call Stack** is a **LIFO (Last In, First Out)** data structure that manages function execution by pushing function calls onto the stack and popping them off when they complete.

### Why is it called a stack?
Because it follows the Last In, First Out (LIFO) principle, just like a stack of plates.

### What causes a Stack Overflow?
Occurs when the Call Stack exceeds its maximum size, usually due to infinite recursion or excessive nested function calls.

### Does JavaScript have multiple Call Stacks?
No. JavaScript is single-threaded and uses a single Call Stack to execute synchronous code. Asynchronous operations are handled outside the Call Stack.

41. ### What is Event Loop?
Event Loop is a mechanism that continuously monitors call stack and executes pending asynchronous callbacks when call stack becomes empty.

### Why Event Loop needed?
Since JavaScript is single-threaded, Event Loop enables asynchronous operations without blocking synchronous code execution.

### How event loop work?
   - JavaScript engine executes all synchronous code using the Call Stack.
   - Asynchronous operations are handled by the browser api or Node.js runtime.
   - Once an asynchronous operation completes, its callback is placed in a queue
   - Event Loop continuously checks whether the Call Stack is empty.
   - If the Call Stack is empty, it executes the next callback.

### Event loop has two types of task Queues.

#### 1. Microtask Queue (Higher Priority)
- Promise.then()
- queueMicrotask()
- MutationObserver()

#### 2. Callback Queue (Macrotask Queue)
- setTimeout()
- setInterval()
- setImmediate()
- DOM Events

### Execution Order
```text
1. Execute synchronous code.
2. Execute all Microtasks.
3. Execute one Macrotask.
4. Repeat.
```

42. ### What is setTimeout() in JavaScript?
`setTimeout()` allows us to execute a function once after at least the specified delay.
```js
//Syntax
setTimeout(callback, delay, arg1, arg2, ...);
```
#### Does setTimeout(fn, 1000) guarantee execution after exactly 1000 ms?
No. It guarantees that the callback will not execute before 1000 ms. The actual execution may be delayed if the Call Stack is busy.

43. ### What is `setInterval()` in JavaScript?
`setInterval()` allows repeated execution of function at a specified time interval.
```js
// Syntax
setInterval(callback, delay, arg1, arg2, ...);
```
#### How do you stop a `setInterval()`?
Use `clearInterval()` and pass the interval ID returned by `setInterval()`.
```js
const intervalId = setInterval(() => {
  console.log("Running...");
}, 1000);

clearInterval(intervalId);
```

44. ### What is `setImmediate()` in JavaScript?
`setImmediate()` schedules a function to execute immediately after the current synchronous code finishes execution.
```js
// Syntax
setImmediate(callback, arg1, arg2, ...);
```

45. ### What is difference between Local Storage and Session Storage?
Local Storage and Session Storage are browser storage features that store data as key-value pairs.

- **Local Storage** shared across all tabs of same origin, persists data until explicitly removed.
- **Session Storage** persists data only for duration of current browser tab session, cleared when the tab or window is closed. available only within the current tab.

46. ### What are Cookies?
Cookies are small pieces of data stored in browser as key-value pairs.

- Cookies can store up to **4 KB** of data.
- After a user logs in, the server uses the **`Set-Cookie`** response header to store a cookie in the browser.
- On future requests, the browser automatically sends the cookie to the server, allowing the server to identify the user.
- Mainly used to store user information such as session IDs, authentication details, and user preferences.

```js
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
```

### Common Methods

```js
localStorage.setItem(key, value);
localStorage.getItem(key);
localStorage.removeItem(key);
localStorage.clear();
localStorage.key(index);
localStorage.length;
```

47. ### What is Cache?
Cache is a temporary storage to store frequently accessed data so that it can be retrieved faster instead of fetching it again from the original source.

- The browser uses cached data if it is still valid (**cache policy sent by server: `Cache-Control: max-age=3600`**); otherwise, it fetches a new copy from the server.

48. ### What is difference between Authentication vs Authorization.

- **Authentication (Who are you?)** process of verifying the identity of user.
- **Authorization (What are you allowed to do?)** process of checking what an authenticated user is allowed to access or perform.

49. ### What is CORS?
CORS (Cross-Origin Resource Sharing) is a browser security feature that allows a web application to access resources from one origin to another.

- CORS uses HTTP headers to allow or block javascript to access the resources.
- CORS is enforced by the browser, not the server.

50. ### What is the difference between Fetch and Axios?

#### Fetch
- Built-in JavaScript API for making HTTP requests.
- Requires manual JSON parsing (`response.json()`).
- Does't support interceptors

#### Axios
- Third-party library for making HTTP requests.
- Automatically parses JSON.
- Supports interceptors.

51. ### What is the difference between IndexedDB and Session Storage?
#### IndexedDB
- Browser database for storing large amounts of structured data.
- Stores objects, files, and other complex data types.
- Data persists until it is explicitly removed.

#### Session Storage
- Browser storage for storing small amounts of data as key-value pairs.
- Stores only strings.
- Data is cleared when the browser tab or window is closed.

52. ### What are classes and what is the purpose of classes?
A class is a blueprint for creating objects. we can create multiple objects with the same properties and methods, helps avoid code repetition.

```js
// example
class Employee {
  constructor(id, name, salary) {
    this.id = id;
    this.name = name;
    this.salary = salary;
  }
}

const emp1 = new Employee(1, "John", 50000);
const emp2 = new Employee(2, "Alice", 60000);
```

> **Note:** The `new` keyword creates the object, while the class provides the blueprint for creating that object.

53. ### What is Prototype Inheritance?
Allows an object to inherit properties and methods from another object through the prototype chain.

```js
// Syntax
class Animal {
  speak() {
    console.log("Animal speaks");
  }
}

const dog = new Animal();
dog.speak();
```

> **Note:**
> - `__proto__` is a reference(link) to an object's prototype.
> - `Object.create()` creates a new object with the specified prototype. //const dog = Object.create(animal)

54. ### What are the differences between `call()`, `apply()`, and `bind()`?
All three methods are used to invoke a function with a specific `this` value.

```js
const person = {
  name: "Kanhaiya",
};

function greet(city) {
  console.log(`Hi I am ${this.name} from ${city}`);
}

greet.call(person, "Delhi");

greet.apply(person, ["Delhi"]);

const greetPerson = greet.bind(person, "Auraiya");
greetPerson();
```

> **Difference:**
> - `call()` invokes the function immediately and passes arguments individually.
> - `apply()` invokes the function immediately and passes arguments as an array.
> - `bind()` does not invoke the function immediately. It returns a new function that can be invoked later.

55. ### What are Modules in JavaScript?
Modules are used to divide code into smaller, reusable files, making it easier to maintain and avoid code duplication.

```js
// math.js
export function add(a, b) {
  return a + b;
}

// app.js
import { add } from "./math.js";

console.log(add(2, 3));
```

> **Note:** `export` is used to make variables, functions, or classes available outside a module, and `import` is used to use them in another module.

56. ### Mutability vs Immutability

### Mutable
- Original value can be modified.
- Applies to all non-primitive data types (Object, Array, Map, Set, Date).
- Stored by reference.

### Immutable
- Original value can not be modified. A new value is created instead.
- Applies to all primitive data types (String, Number, Boolean, `null`, `undefined`, Symbol, BigInt).
- Stored by value

57. ### Shallow Copy vs Deep Copy

### Shallow Copy
A shallow copy creates a new object or array but copies references of nested objects and arrays.

**Common ways to create:**
- `const copy = { ...obj }`
- `const copy = Object.assign({}, obj)`

```js
const originalArray = [1, 2, [3, 4]];

const shallowCopy = [...originalArray];

shallowCopy[2][0] = 100;

console.log(originalArray); // [1, 2, [100, 4]]
```

### Deep Copy
A deep copy creates a completely independent copy of an object or array, including all nested objects and arrays.

**Common ways:**
- `const copy = structuredClone(obj)`
- `const copy = JSON.parse(JSON.stringify(obj))`

```js
const originalArray = [1, 2, [3, 4]];

const deepCopy = JSON.parse(JSON.stringify(originalArray));

deepCopy[2][0] = 100;

console.log(originalArray); // [1, 2, [3, 4]]
```

58. ### Immutability and Side Effects

A side effect is when a function unintentionally modifies the original object or array.

```js
// Side Effect
const user = { name: "Kanhaiya" };

function updateUser(user) {
  user.name = "Rahul";
}

updateUser(user);

console.log(user.name); // Rahul
```

> **How to avoid side effects?**
> - Do not modify the original object or array.
> - Create a new object or array instead.

```js
// No Side Effect
const user = { name: "Kanhaiya" };

const updatedUser = {
  ...user,
  name: "Rahul",
};

console.log(user.name);        // Kanhaiya
console.log(updatedUser.name); // Rahul
```

59. ### Map vs Object

### Object
- Keys can only be String or Symbol.
- Size is obtained using `Object.keys(obj).length`.
- Primarily used to represent entities with properties.

### Map
- Keys can be any data type.
- Size is obtained using `map.size`.
- Primarily used to store and manage key-value pairs.

```js
// Object
const person = {
  name: "Kanhaiya",
};

// Map
const map = new Map();

map.set("name", "Kanhaiya");
map.set(1, "One");
map.set({ id: 1 }, "Employee");
```

60. ### What are the differences between Map and Set?

### Map
- Stores key-value pairs.
- Keys can be any data type.
- Uses `set(key, value)` to add entries.

### Set
- Stores only unique values.
- Does not store key-value pairs.
- Uses `add(value)` to add values.

```js
// Map
const map = new Map();

map.set("name", "Kanhaiya");
map.set(1, "One");

// Set
const set = new Set();

set.add("A");
set.add("B");
set.add("A");

console.log(set); // Set { 'A', 'B' }
```

61. ### What are the different types of errors in JavaScript?

### ReferenceError
Occurs when trying to access a variable that is not defined.

```js
console.log(a);
```

### SyntaxError
Occurs when the JavaScript code has invalid syntax.

```js
if (true {
  console.log("Hello");
}
```

### TypeError
Occurs when a value is used in an invalid way.

```js
const num = 10;

num();
```

### RangeError
Occurs when a value is outside the allowed range.

```js
const arr = new Array(-1);
```

62. ### List out some key features of ES6
    
1. Arrow Functions
2. `let` and `const` declarations
3. Destructuring
4. Default Parameters
5. Template Literals
6. Spread and Rest Operators
7. Promises
8. Classes
9. Modules (`import` / `export`)
10. Map and Set
11. Optional Chaining (`?.`)

63. ### What is the Spread Operator (`...`)?
expands(spreads) elements of an array or properties of an object into another array or object.

64. ### What is the Rest Operator (`...`)?
Collects multiple values into a single array.

65. ### What is Destructuring?
Extracts values from an array or object into separate variables.

66. ### What are the differences between `some()` and `every()`?
- `some():`Returns `true` if at least one (any) element satisfies the condition.
- `every():` Returns `true` only if all elements satisfy the condition.

67. ### What is Event Bubbling?
A process where an event starts from the target element and moves up to its parent elements (upto document if they have listeners). 

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

```javascript
parent.addEventListener("click", () => console.log("Parent"));
child.addEventListener("click", () => console.log("Child"));

// Click on button
// Output:
// Child
// Parent
```

68. ### What is Event Capturing?
A process where an event starts from the parent elements (document if they have listners) and moves down to the target element.

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

```javascript
parent.addEventListener("click", () => console.log("Parent"), true);
child.addEventListener("click", () => console.log("Child"), true);

// Click on button
// Output:
// Parent
// Child
```

69. ### What are Debounce and Throttle?

- **Debounce:** Executes a function only after user stops performing an action for a specified time.
  - Example: Search box.

- **Throttle:** Executes a function at specified time intervals even if the user keeps performing the action.
  - Example: Scroll event.
 
70. ### What are Web Workers?
Creates background threads to perform heavy tasks without blocking the main JavaScript thread.

**Can Web Workers access the DOM?**
No. Web Workers cannot directly access the DOM. They communicate with the main thread using `postMessage()`.

**Do Angular/React apps use Web Workers?**
Yes can use, but only for CPU-intensive tasks like image/video processing, complex calculations.

**Can Web Workers be used for API calls?**
No. API calls are **I/O-bound** (waiting for the network), not **CPU-bound** (heavy computation).

71. ### What is a Polyfill?
JavaScript code that **adds support for modern JavaScript features in older browsers**.

**Do we write polyfills manually in modern Angular/React applications?**
No. Modern build tools automatically add the required polyfills when needed.

72. ### What is Babel?
Babel is a JavaScript compiler that **converts modern JavaScript syntax into older JavaScript syntax** so older browsers can understand it.

73. ### What is Tree Shaking?
Process of removing unused JavaScript code during production build to reduce the bundle size and improve application performance.

**Note:** Tree Shaking works with ES Modules (`import`/`export`).

74. ### Types of Loops in JavaScript

- `for`: Used when the number of iterations is known.
- `while`: Used when the number of iterations is unknown.
- `do...while`: Executes the loop at least once before checking the condition.
- `for...of`: Iterates over the values of iterable objects (Arrays, Strings, Maps, Sets).
- `for...in`: Iterates over the keys of an object.

75. ### Arrays & Array Methods

#### What is an Array?
Array is haterogenious collection of values.

#### What is `map()`?
Creates a new array by applying a function to every element of the original array.

```js
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
console.log(doubled);
```

#### What is `filter()`?

Creates a new array containing only the elements that satisfy a given condition.

```js
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);
```

#### What is `reduce()`?
Reduces all elements of an array to a single value.
```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum);
```

#### What is `forEach()`?
Executes a function once for each element of an array. It does not modify the original array.
```js
const numbers = [1, 2, 3];

numbers.forEach(num => console.log(num));
```

#### What is `find()`?
Returns the first element that satisfies a given condition. if no match, then returns undefined.

```js
const numbers = [10, 20, 30, 40];
const result = numbers.find(num => num > 20);
console.log(result);
```

#### What is `slice()`?
creates a new array, copies elements from index start till end (end not included).

```js
//Syntax: slice(start, end)
const fruits = ["Apple", "Banana", "Mango", "Orange"];
const result = fruits.slice(1, 3);
console.log(result);
```
#### What is `splice()`?
Modifies the original array by adding, removing, or replacing elements.

```js
//Syntax- splice(pos, deleteCount, ...items) – at index pos deletes deleteCount elements and inserts items.
const fruits = ["Apple", "Banana", "Mango"];
fruits.splice(1, 1, "Orange");
console.log(fruits);
```

76. ### Difference between ^ vs ~ in package.json
`^` and `~` are version range specifiers used in `package.json`.

- `^` → Allows **minor** and **patch** updates.
- `~` → Allows **patch** updates only.

**Example**

- `^5.8.2` → `5.9.0` ✅, `6.0.0` ❌
- `~5.8.2` → `5.8.3` ✅, `5.9.0` ❌

77. ### Define DRY, KISS, YAGNI & SOLID Principles

#### DRY (Don't Repeat Yourself)
Avoid duplicate code by reusing existing logic.

#### KISS (Keep It Simple, Stupid)
Write simple and easy-to-understand code. Avoid unnecessary complexity.

#### YAGNI (You Aren't Gonna Need It)
Do not implement features until they are actually required.

#### SOLID Principles
- **S – Single Responsibility Principle (SRP):** A class should have only one responsibility (one reason to change).
- **O – Open/Closed Principle (OCP):** Software should be open for extension but closed for modification.
- **L – Liskov Substitution Principle (LSP):** A subclass should be replaceable with its parent class without changing the program's behavior.
- **I – Interface Segregation Principle (ISP):** Clients (Class) should not be forced to implement methods they do not use.
- **D – Dependency Inversion Principle (DIP):** Depend on abstractions (interfaces), not concrete implementations.


## RXJS

1. ### What is difference between imperative vs declarative code [Explanation](https://www.youtube.com/watch?v=E7Fbf7R3x6I)   
**Imperative** - How (Tell the machine how to do it)  
**Declarative** - What (Tell the machine what to do), example - sql query, html, css

2. ### What is Reactive Programming
Reactive Programming(part of declartive programming) is programming with asynchronous data streams. A stream(observable) is sequence of events ordered in time, stream can emit 3 different notifications. some value(next), error or complete signal, to listen to stream is called subscribing, and to capture emitted things(events) we define functoins such as next, error or completed. these functions are called observers and stream is called observable(being observerd). in common reactive libraries, each stream has many functions attached, such as map, filter etc. 
(Water Tap Analogy)

A Subsccription can end in three ways
1. Unsubscribe
1. Complete Signal
1. Error Signal

TearDown logic will run only after subscription ends.

Unsubcribe runs the teardown logic, if no teardown logic written in observable, then nothing will happen.

Marble Diagram - is a Visual Representation of behvaiour of an observable.

[Observable Example](https://stackblitz.com/edit/rxjs-vxjtgfs4?file=index.ts)

3. ### Why should i consider adopting/Benifits of Reactive programming
Reactive programming raises the abstraction of code, so we can focus on data flow and events rather than implementation details. this improves readability and makes the code concise. it's especially powerful for handling asynchronous data (such as network requests) and event-driven scenarios (such as UI interactions or real-time updates).

e.g. Type Ahead Search/Predictive Search

```html
<input #searchBox type="text" placeholder="Search"/>
```

```ts
export class SearchComponent implements AfterViewInit {
  @ViewChild('searchBox', { static: true }) searchBox!: ElementRef;
  items: any[] = [];

  constructor(private http: HttpClient) {}

  ngAfterViewInit() {
    fromEvent(this.searchBox.nativeElement, 'input') // creates Observable to emit each input event.
      .pipe(
        debounceTime(300), // waits 300ms of inactivity before emitting the latest value.
        switchMap((event: Event) => { // cancel previous request on new input.
          const input = (event.target as HTMLInputElement).value;
          return this.http.get<any[]>(`api/data?q=${input}`);
        })
      )
      .subscribe(results => {
        this.items = results;
      });
  }
}

//without rxjs we can do this with addEventListener + setTimeout + fetch (only answer if asked)
```

4. ### What is Rxjs
Rxjs stands for Reactive Extensions for Javascript, is a library for handling asynchonous code and event based data streams for javascript driven applications.

5. ### What is Cold Observable
Produces data on subscription, Each Subscriber gets their own independent execution. Data source is inside observalbe Logic. (On Demand) ex- http calls, of(), interval().

6. ### What is Hot Observable
Produces data whether you subscribe or not, so subscriber shares the same execution. Data source is outside the observable logic. (Already Live) ex- DOM events, Subjects

7. ### When to Unsubscribe a observable?
- **Finite data** - auto complete, no need to unsubscribe
- **Infinite data/Event Based** - need unsubscribe

8. ### What are Operators
Operators are functions.There are two kinds of operators:
- Creation Functions/Operators
- Pipeable Operators

9. ### What are Creation Functions/Operators?
Helper functions provided by rxjs to create observables.
#### Examples
  **of**: create observable from value
  ```ts
  of(1, 2, 3).subscribe(console.log);
  // output: 1, 2, 3
  ```

  **from()**: create observable from array/iterable/promise
  ```ts
  from([10, 20, 30]).subscribe(console.log);
  // output: 10, 20, 30

  // promise
  from(fetch('/api/data')).subscribe(console.log);
  ```

**fromEvent**: create observable from events
```ts
fromEvent(button, 'click').subscribe(() => {
  console.log('clicked');
});
```
**timer**: create observable and emit once or after delay
```ts
// emit once
timer(2000).subscribe(() => {
  console.log("after 2 seconds")
})

//emit after delay
const timerSubscription = timer(3000, 1000).subscribe(() => {
  console.log("first emit after 3 second, then after 1 second, until unsubscribed")
})
```
**interval**: create observable and emit continuously at defined interval (counter that starts from 0)
```ts
interval(1000).subscribe(console.log)
// output: 0,1,2,3... every second
```
**ajax**: create observable from http request
```ts
ajax('https://jsonplaceholder.typicode.com/users').subscribe(res => {
  console.log(res.response)
})
```
**forkJoin**: subscribes to **all inner observalbes at same time** and **wait for all to complete**, then **emit exaclty once** one **single value** containing **each observable's last emitted value**.
- If even one observable never completes → no emission
- If any observable errors → forkJoin errors
- When to use - If multiple things must finish first, and you need the result once (parallel api calls)
```ts
forkJoin([
  of(1, 2, 3),
  of('a', 'b'),
  of(true)
]).subscribe(res => {
  console.log(res)
})
```
**combineLatest**: subscribes to all **innner observalbes at same time** and wait for **each observable to emit atleast once**, then **emits a value** and **continues emitting whenever any observable emits**, using the **latest value from each observable**.
- emits once per emission, not once per timestamp. (if two observables emit at the same moment, it produces two emissions, not one)
- if one completes early its last value is reused
- if any observables erros - combineLatest erros
- When to use - If multiple things decide something, and any change should update it (enable a button based on multiple condition)
```
combineLatest([
  interval(1000),
  interval(2000)
]).subscribe(console.log)
```

10. ### What are pipeable operators
Functions that takes an observable as input and returns another observable. It is a pure operation, original Observable stays unmodified.
Pipeable Operators are of two types:
- Sync(Synchronous) Operators
- Flattening Operators

11. ### What are sync (synchronous) operators
Pipeable operators that process each emitted value immediately
#### Examples
**map**: transforms each emitted value into a new value.
- map should be pure — no side effects, ex-should NOT be used to update a variable or trigger a log.
```ts
interval(1000).pipe(
  map(x => x*2)
).subscribe(console.log)
```
**filter**: let value pass or block based on condition.
```ts
interval(1000).pipe(
  filter(x => x%2===0)
).subscribe(console.log)
```
**tap**: used for side effects **without changing** the value.
```ts
interval(1000).pipe(
  tap(x => console.log('Before', x)),
  map(x => x*2)
).subscribe(console.log)
```
**take**: take(n) lets only first n values pass, then completes the observable
interval(1000).pipe(
  take(3),
  map(x => x*2)
).subscribe(console.log)
// Output: 0, 2, 4

**takeUntil**: takeUntil(anotherObservable$) keeps emitting until another observable emits, then it completes.
```ts
source$.pipe(
  takeUntil(destroy$)
).subscribe();
// When destroy$ emits, subscription ends immediately.
```
**debounceTime**: debounceTime(ms) waits for silence for given time, then emits the latest value.
- Usage: Search boxes, Auto Complete
```ts
fromEvent(input, 'keyup').pipe(
  debounceTime(300)
).subscribe(console.log);
//When User stops typing for 300ms → last value emitted
```
**catchError**: catchError handles errors and **returns a new observable** so the stream doesn’t crash.
```ts
api$.pipe(
  catchError(err => of('fallback'))
).subscribe(console.log);
//If Original stream errors, catchError replaces it with another observable
```

12. ### What is higher order observable
observable that emits another observable.
```ts
const source$ = of(
  of(1, 2),
  of(3, 4)
);
// here source$ emits observables, not numbers
```

13. ### What are Flattening operators
Convert a higher-order observable into a normal observable by subscribing to the inner observables and emitting their values.
#### When a new request(observable$) comes while one is running, what should happen? (Ex- Restaurant Analogy)
- **switchMap**: cancel old, keeps latest (Maps to new observable and cancel the previous one) ex - cancel previous http request
- **mergeMap**: Run everything in parallel (Maps to new Observables and runs them all simultaneously) ex- simultanious file uploads
- **concatMap**: Run one by one, in order (Maps to new Observables but waits for each to finish before starting the next) ex - delete operation
- **exhaustMap**: Ignore new while busy (Maps to new Observable, but ignores new observables while current one is running) ex - submit button

14. ### What is a subject
Subject is both an observable and observar, and it multicasts value to multiple subscribers. (Live Microphone analogy)
- Observable → you can subscribe() to it
- Observer → you can call next() on it
- Multicast → same value goes to all subscribers
  
Use when: Events, clicks, notifications, latest(last emitted) value does't matter
```ts
const subject$ = new Subject<number>();

subject$.subscribe(v => console.log('A:', v));
subject$.subscribe(v => console.log('B:', v));

subject$.next(1)
subject$.next(2)
// output - A: 1, B: 1, A: 2, B: 2
```

15. ### What is BehaviorSubject
A BehaviorSubject is a Subject that always holds and emits the latest value to new subscribers.  (TV Analogy)
Key differences from Subject:
- Requires an initial value
- Remembers the last emitted value
- New subscribers immediately receive the latest (last emitted value) while in subject new subsribers only recieves future value.
  
Use when - user state, shared app state, last(latest) value matters
```ts
const bs$ = new BehaviorSubject<number>(0);

bs$.subscribe(res => console.log('A:', res))

bs$.next(1)

bs$.subscribe(res => console.log('B:', res))
// output - A: 0, A: 1, B: 1
```
<br>

## Angular

1. ### What is a Library?
A library is a collection of reusable code. You decide when and how to use it, and you choose other libraries for routing, state management, forms, etc.

2. ### What is a Framework?
A framework provides a complete structure for building an application. It decides how the application is organized, and you build your application by following its conventions.

3. ### What is Angular?
Angular is a TypeScript-based, open-source front-end framework maintained by Google. It is used to build modern, scalable, single-page client-side web applications.

Major features include:
- Components
- Directives
- Dependency Injection
- Routing
- Forms
- Two-way Data Binding

4. ### Angular vs AngularJS
AngularJS is the first version of Angular, released in 2010. It is based on JavaScript and follows the MVC (Model-View-Controller) architecture.
  
Angular is a complete rewrite of AngularJS and was released in 2016. It is based on TypeScript and follows a component-based architecture.

5. ### Why Angular instead of React or Vue?
Angular is preferred for large-scale enterprise applications because it provides a complete framework with built-in features like routing, dependency injection, forms, and HTTP client etc.

React and Vue are more flexible and require additional libraries for features like routing and state management (e.g., React Router, Redux. The choice depends on the project requirements.

6. ### Why Angular instead of Vanilla JavaScript?
Vanilla JavaScript is suitable for building small and simple applications. However, as an application grows, managing code becomes difficult.

Angular provides a structured way to build applications with features like components, routing, dependency injection, forms, and HTTP client, making large applications easier to develop, maintain, and scale.

7. ### Angular Latest Version
- Current latest stable Angular version is **v22**.
- Angular has shifted to a yearly major release cycle starting with Angular v22.
- New features are released through regular minor versions.

**How to check Angular version?**
```bash
ng version
```
or
```bash
ng v
```

8. ### Major Features (Angular 14 → Angular 20)

**Angular 14**
- Standalone Components

**Angular 16**
- Signals

**Angular 17**
- @if
- @for
- @switch
- @defer

**Angular 18**
- Zoneless Change Detection

**Angular 19**
- Standalone by Default

**Angular 20**
- Performance Improvements

9. ### How angular application starts?
#### Module-based
Main → Module → Metadata → Mount
- main.ts runs → platformBrowserDynamic().bootstrapModule(AppModule)
- Angular bootstraps AppModule
- Reads bootstrap: [AppComponent]
- Mounts AppComponent into <app-root>

#### Standalone-based
Main → App → Imports → Render
- main.ts runs → bootstrapApplication(AppComponent)
- AppComponent becomes root injector
- Standalone components are imported directly
- Angular renders AppComponent

**Main.ts** - first typescript file bundled by angular app.

**plateformBrowserDynamic()** - sets up angular **run time execution environment/plateform** for browser and enables JIT compilation

**Standalone apps (Angular v14+)** - plateformBrowserDynamic() is abstracted and angular handles plateform setup internally.

10. ### What is NgModule?
An **NgModule** is a class decorated with `@NgModule` that groups related Angular building blocks such as **declarations, imports, providers etc** into a single module.

**Main Properties**

- `declarations` → Components, Directives, Pipes
- `imports` → Other Modules
- `providers` → Services
- `exports` → Shares Components, Directives and Pipes with other Modules
- `bootstrap` → Root component that starts the application

#### Do we still need NgModule?
No. Since **Angular 14**, Standalone Components does not need ngModule. However, NgModules are still supported and used in existing applications.

11. ### What are Standalone Components?
Angular component that **does not require an NgModule**. It can directly import the dependencies it needs.
**Advantages**
- No need for `NgModule`
- Simpler application structure
- Easier to maintain
- Reduces boilerplate code

12. ### Can NgModules be used with Standalone Components?
Yes, Standalone Components and NgModules can be used together in same application

**Common Scenarios**
- Import Standalone Components into NgModules.
- Import NgModules into Standalone Components.
- Gradually migrate existing applications to Standalone Components.

13. ### What architectural problem did Standalone Components solve?
Standalone Components were introduced to **remove the dependency on NgModules** and simplify Angular application architecture.

**Problems with NgModules**
- Extra boilerplate code
- More files to manage
- Increased complexity

**Benefits**
- No need for NgModules
- Simpler project structure
- Better developer experience

14. ### What are Decorators?
Special function prefixed with `@` that adds metadata to a class, property, method. Angular uses decorators to define how different parts of the application should behave.

**Common Decorators**
- `@Component` → Component
- `@Directive` → Directive
- `@Pipe` → Pipe
- `@NgModule` → NgModule
- `@Injectable` → Service

15. ### Types of Decorators in Angular
Angular decorators are classified into four types:

#### Class Decorators
- `@Component`
- `@Directive`
- `@Pipe`
- `@Injectable`
- `@NgModule`

#### Property Decorators
- `@Input()`
- `@Output()`
- `@ViewChild()`
- `@ViewChildren()`
- `@ContentChild()`
- `@ContentChildren()`
- `@HostBinding()`

#### Method Decorators
- `@HostListener()`

#### Parameter Decorators
- `@Inject()`
- `@Optional()`
- `@Self()`
- `@SkipSelf()`
- `@Host()`

16. ### What is Environment Configuration?
Environment Configuration allows Angular to use different settings for different environments such as development, testing, and production.

**Examples**
- API URL
- Feature flags
- Logging settings

17. ### Environment Files
- `environment.ts` → Contains default/base configuration.
- `environment.development.ts` → Contains configuration values for development environment.
- `environment.staging.ts` → Contains configuration values for staging environment.
- `environment.production.ts` → Contains configuration values for production environment.
- 
**Example**
```ts
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000/api'
};
```

19. ### What is File Replacement?
Angular build feature to replace one environment file with another based on build configuration.

**Example**

```text
Default/Base → environment.ts
Development  → environment.development.ts
Staging      → environment.staging.ts
Production   → environment.production.ts
```

**angular.json**

```json
"configurations": {
  "development": {
    "fileReplacements": [
      {
        "replace": "src/environments/environment.ts",
        "with": "src/environments/environment.development.ts"
      }
    ]
  },
  "staging": {
    "fileReplacements": [
      {
        "replace": "src/environments/environment.ts",
        "with": "src/environments/environment.staging.ts"
      }
    ]
  },
  "production": {
    "fileReplacements": [
      {
        "replace": "src/environments/environment.ts",
        "with": "src/environments/environment.production.ts"
      }
    ]
  }
}
```

**Note**
- Angular always starts with `environment.ts`.
- Based on selected build configuration, it replaces `environment.ts` with the appropriate environment file

20. ### What is a Production Build?
Creates an optimized version of Angular application for deployment.

**Optimizations**
- AOT Compilation
- Tree Shaking
- Minification
- Dead Code Elimination

**Command**
```bash
ng build --configuration production
```

21. ### What are Components?
A **Component** is basic building block of an Angular application. Main parts are template, spec.ts, styling, and ts file.

22. ### Services vs Components
#### Component
- Controls the UI.
- Uses `@Component` decorator.
- Contains HTML, CSS, and TypeScript.
- Created for a specific view.
  
#### Service
- Contains business logic.
- Uses `@Injectable` decorator.
- Usually contains only TypeScript.
- Reusable across multiple components.

23. ### What is a Constructor?
Part of angular component, called when a new component is created. mainly used for **Dependency Injection (DI)**.

> **Note:** In newer Angular versions, `inject()` is preferred over constructor-based DI.

```ts
constructor(private userService: UserService) {}
```

23. ### What is the Component Lifecycle?
A **Component Lifecycle** is sequence of stages a component goes through from **creation to destruction**. Angular provides **Lifecycle Hooks** to perform actions at different stages.

#### Lifecycle Execution Order

1. **Constructor** – Called **once** when a new component instance is created. Used for Dependency Injection.
2. **ngOnChanges()** – Called whenever an `@Input()` property changes. Runs before `ngOnInit()`.
3. **ngOnInit()** – Called **once** after Angular initializes the component. Used for initialization.
4. **ngDoCheck()** – Called during every change detection cycle. Used for custom change detection.
5. **ngAfterContentInit()** – Called **once** after projected content (`ng-content`) is initialized.
6. **ngAfterContentChecked()** – Called after every check of projected content.
7. **ngAfterViewInit()** – Called **once** after the component's view and child views are initialized.
8. **ngAfterViewChecked()** – Called after every check of the component's view and child views.
9. **ngOnDestroy()** – Called **once** before the component is destroyed. Used for cleanup (unsubscribe, clear timers, etc.).

25. ### Normal TypeScript Class vs Angular Service

#### Normal TypeScript Class
- A regular TypeScript class.
- Not managed by Angular.

#### Angular Service
- A TypeScript class decorated with `@Injectable()`.
- Managed by Angular's Dependency Injection (DI) system.
- Used to share business logic and data across components.

26. ### What is `@ViewChild`?
`@ViewChild` is a decorator used to access a **child component, directive, or DOM element** from the parent component after the view is initialized.

**Example**

```ts
@ViewChild('input', { static: false }) input!: ElementRef;
```

#### `static: true` vs `static: false`

- **`static: true`** – The element is available in `ngOnInit()`. Use when the element always exists.
- **`static: false`** *(default)* – The element is available in `ngAfterViewInit()`. Use when the element is conditionally rendered.

27. ### What is View Encapsulation?
**View Encapsulation** controls how a component's styles are applied and whether they affect other components.

#### Types
- **Emulated (Default)** – Styles are scoped to the component.
- **Shadow DOM** – Uses the browser's native Shadow DOM to completely isolate styles.
- **None** – Styles are global and can affect other components.

28. ### What is Change Detection?
Angular process to detect changes in the application state and update the DOM automatically.

29. ### What triggers Change Detection?
- Changes to an `@Input()` property.
- DOM events (click, input, etc.).
- Async operations (HTTP calls, `setTimeout`, Promises, etc.).
- Observable/Subject/BehaviorSubject emissions.
- Manual triggering using `ChangeDetectorRef`.

30. ### Default vs OnPush
#### Default
- Checks all components during every change detection cycle.
- Simple to use.
- Can affect performance in large applications.

#### OnPush
- Checks component only when necessary.
- Improves performance.
- 
**OnPush triggers when:**
- `@Input()` reference changes.
- An event occurs inside the component.
- An Observable emits a new value (`async` pipe).
- `markForCheck()` or `detectChanges()` is called.

```ts
@Component({
  changeDetection: ChangeDetectionStrategy.OnPush
})
```

31. ### What is Manual Change Detection?
Used to manually trigger Angular's Change Detection cycle when Angular doesn't detect changes automatically.

**Note:** It is performed using `ChangeDetectorRef`.

32. ### What is `ChangeDetectorRef`?
`ChangeDetectorRef` is an Angular service used to manually control the Change Detection cycle.

**Common Methods**
- `markForCheck():` marks the component for checking in the next Change Detection cycle. It does not trigger Change Detection immediately.
- `detectChanges(): ` Immediately runs Change Detection for the component and its child components.

33. ### What is `trackBy`?
trackBy keeps track of list so Angular knows which item in list changed. and updates only that part in dom. without it angular re-renders entire list in dom, creating performance issues.

```html
<li *ngFor="let user of users; trackBy: trackById">
  {{ user.name }}
</li>
```

```ts
trackById(index: number, user: User) {
  return user.id;
}
```

34. ### What is `Zone.js`?
`Zone.js` is a library used by Angular to detect asynchronous operations and automatically trigger Change Detection.

**Examples**
- HTTP calls
- DOM events
- `setTimeout()`
- `setInterval()`
- Promises

36. ### What is Interpolation?
Used to display **typescript component data** in the **HTML template** using `{{ }}`.

37. ### What is Property Binding?
Used to bind **TypeScript property** to an **HTML element** using `[ ]`.

**Example**
```ts
isDisabled = true;
```

```html
<button [disabled]="isDisabled">Save</button>
```

38. ### What is Event Binding?
Used to bind an **HTML event** to a **TypeScript method** using `( )`.

**Example**
```html
<button (click)="save()">Save</button>
```

```ts
save() {
  console.log('Saved');
}
```

39. ### What is Two-way Data Binding?
Used to synchronize data between **TypeScript component** and the **HTML template**. It uses `[(ngModel)]`.

**Example**
```ts
name = '';
```

```html
<input [(ngModel)]="name">
<p>{{ name }}</p>
```

40. ### What are Directives?
Directives are classes that add or modify the behavior and appearance of DOM elements.

**Types**
- **Component Directive** (`@Component`) → Creates and controls a UI component.
- **Structural Directive** (`*`) → Adds or removes elements from the DOM (e.g., `*ngIf`, `*ngFor`).
- **Attribute Directive** (Attribute) → Changes the appearance or behavior of an existing element (e.g., `ngClass`, `ngStyle`).

41. ### What is `@HostBinding`?
`@HostBinding` is a decorator used to bind **property, class, style, or attribute** to the **host element** without directly manipulating the DOM.

**Example**
```ts
@HostBinding('style.color')
color = 'red';
```

42. ### What is `@HostListener`?
`@HostListener` is a decorator used to listen to **events on the host element**.

> **Note:** Commonly used in **directives** and for listening to **global events** (`window`, `document`, etc.).

**Example**
```ts
@HostListener('click')
onClick() {
  console.log('Clicked');
}
```

43. ### What are Angular Control Statements?
Angular Control Statements are used for control flow
- **`ngFor` / `@for`** → Used to iterate over a collection.
- **`ngIf` / `@if`** → Used for conditional rendering.
- **`ngSwitch` / `@switch`** → Used to render one of multiple cases.

44. ### What is `ng-template`?
Used to define template content that is not displayed by default. (e.g., rendered using *ngIf with else or ngTemplateOutlet).

**Example**
```html
<div *ngIf="isLoggedIn; else loginTemplate">
  Welcome, User!
</div>

<ng-template #loginTemplate>
  <p>Please login first.</p>
</ng-template>
```

45. ### What is `ng-container`?
`ng-container` is a logical container used to group elements **without creating an extra DOM element**.

**Example**
```html
<ng-container *ngIf="isLoggedIn">
  <h2>Welcome</h2>
  <button>Logout</button>
</ng-container>
```

46. ### What is `ng-content`?
`ng-content` is used for **Content Projection**, allowing a parent component to pass content into a child component.

**Example**

**Parent Component**

```html
<app-card>
  <h2>Welcome</h2>
</app-card>
```

**Child Component**

```html
<div class="card">
  <ng-content></ng-content>
</div>
```

47. ### What is `@defer`?
`@defer` is used to lazy load a part of the template based on a specified trigger(viewport, hover, idle, timer), improving the application's initial load performance.

**Example**
```html
@defer (on viewport) {
  <app-heavy-chart />
}
```

48. ### What are Pipes?
Pipes are used to **transform data** in the template without changing the original data.

```html
<p>{{ name | uppercase }}</p>
```

49. ### Built-in Pipes
predefined pipes provided by Angular to transform data in the template.

**Common Built-in Pipes**
- `uppercase`
- `lowercase`
- `titlecase`
- `date`
- `currency`
- `percent`
- `json`
- `slice`
- `async`

**Examples**
```ts
today = new Date();
price = 499;
percentage = 0.75;
```

```html
<p>{{ today | date }}</p>          <!-- Aug 5, 2026 -->
<p>{{ price | currency:'INR' }}</p> <!-- ₹499.00 -->
<p>{{ percentage | percent }}</p>   <!-- 75% -->
```

50. ### What are Custom Pipes?
Custom Pipes are user-defined pipes used to perform custom data transformations that are not provided by Angular's built-in pipes.

**Example**
```ts
@Pipe({
  name: 'capitalize'
})
export class CapitalizePipe implements PipeTransform {
  transform(value: string): string {
    return value.charAt(0).toUpperCase() + value.slice(1);
  }
}
```

```html
<p>{{ 'angular' | capitalize }}</p> <!-- Angular -->
```

51. ### What is a Pure Pipe?
Pure Pipe executes **only when the input value or object reference changes**, improving application performance.

**Example**
```ts
name = 'Angular';
```

```html
// this pipe will execute once, and will execute again if name value changes
<p>{{ name | uppercase }}</p>
```

52. ### What is an Impure Pipe?
An Impure Pipe executes **on every change detection cycle**, even if the input value or object reference has not changed.

> **Note:**
> - Built-in pipes are **Pure** by default (except `async`).
> - Custom pipes are also **Pure** by default.
> - Set `pure: false` to create an **Impure Pipe**.

**Example**

```ts
@Pipe({
  name: 'myImpurePipe',
  pure: false
})
export class MyImpurePipe implements PipeTransform {
  transform(value: string): string {
    return value.toUpperCase();
  }
}
```

53. ### What are Services?
Services are classes used to store **business logic, reusable functionality, and shared data** that can be used by multiple components.

**Example**

```ts
@Injectable({
  providedIn: 'root'
})
export class UserService {}
```

**Providing a Service using `providers`**
```ts
@Component({
  providers: [UserService]
})

**Injecting a Service**

**Constructor Injection**

```ts
constructor(private userService: UserService) {}
```

**Modern Angular (`inject()`)**

```ts
userService = inject(UserService);
```

> **Note:**
> - `providedIn: 'root'` creates a **singleton service** for the entire application.
> - `providers: [UserService]` creates a **new service instance** for that component and its child components.

54. ### What is the Purpose of Services?
The main purpose of Services is to:
- Store business logic.
- Share data between components.
- Reuse common functionality.
- Separate business logic from UI logic.

55. ### What is Dependency Injection (DI)?
Dependency Injection (DI) is a design pattern in which Angular automatically provides the required dependencies (services) to a component or another service instead of creating them manually.

**Example**

Instead of:

```ts
const userService = new UserService();
```

Angular injects it automatically:

**Constructor Injection**
```ts
constructor(private userService: UserService) {}
```

**Modern Angular (`inject()`)**
```ts
userService = inject(UserService);
```

56. ### What is an Injection Token?
Used to inject **values or objects that do not have a class type**, such as API URLs, configuration values, or interfaces.

**1. Create an Injection Token**
```ts
// api.config.ts
export const API_URL = new InjectionToken<string>('API_URL');
```

**2. Provide a Value**
```ts
// app.config.ts
// will be used globally
export const appConfig: ApplicationConfig = {
  providers: [
    {
      provide: API_URL,
      useValue: 'https://api.example.com'
    }
  ]
};
```

**3. Inject the Value**
```ts
// home.component.ts, only home component can use it
apiUrl = inject(API_URL);
```

57. ### What are Providers?
Providers are used to register a dependency (service or value) with Angular's Dependency Injection (DI) system so it can be injected where needed.

**Providing a Service**
```ts
@Component({
  providers: [AssetsService]
})
export class HomeComponent {}
```

**Providing a Value**
```ts
providers: [
  {
    provide: API_URL,
    useValue: 'https://api.example.com'
  }
]
```

58. ### How do you manually create a Service?
A service can be created manually using the Angular CLI.

**Command**
```bash
ng generate service services/user
```

or
```bash
ng g s services/user
```

This generates:
```text
user.service.ts
```

```ts
@Injectable({
  providedIn: 'root'
})
export class UserService {}
```

59. ### What are the different ways of Cross Component Communication in Angular?
Angular provides **4 common ways** for communication between components:

1. Parent → Child (`@Input`)
2. Child → Parent (`@Output`)
3. Sibling Components (Shared Service)
4. Unrelated Components (Shared Service / State Management - ngrx / Signals)
---

### 1. Parent → Child (`@Input`)
Used to **pass data from a parent component to a child component.**

**Parent**
```ts
name = 'Kanhaiya';
```

```html
<app-child [username]="name"></app-child>
```

**Child**

```ts
@Input() username!: string;
```

---

### 2. Child → Parent (`@Output`)

Used to **send data or events from a child component to a parent component.**

**Child**

```ts
@Output() save = new EventEmitter<void>();

this.save.emit();
```

**Parent**

```html
<app-child (save)="onSave()"></app-child>
```

---

### 3. Sibling Components
Sibling components communicate using a **shared service**.

```ts
@Injectable({
  providedIn: 'root'
})
export class DataService {}
```

---

### 4. Unrelated Components
Unrelated components communicate using a **shared service** or a **state management** such as **Signals** or **NgRx**.

60. ### What is Routing?
Routing in Angular is used to **navigate between different views/components based on the URL without reloading the entire page**.

**Example**

```ts
const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];
```

```html
<a routerLink="/about">About</a>
```

```text
/home  → HomeComponent
/about → AboutComponent
```

61. ### What is Lazy Loading?
Lazy Loading means loading a component, or route **only when the user needs it**, instead of loading it when the application starts.

It helps **reduce the initial bundle size and improve initial load performance**.

**Example**

```ts
const routes: Routes = [
  {
    path: 'admin',
    loadComponent: () =>
      import('./admin/admin.component')
        .then(m => m.AdminComponent)
  }
];
```

Here, `AdminComponent` is loaded **only when the user navigates to `/admin`**.

62. ### What is Eager Loading?
Eager Loading means loading a component or feature **when the application starts**, rather than waiting until the user navigates to it.

It can make the initial bundle larger because the required code is loaded upfront.

**Example**
```ts
const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];
```

Here, the required code is loaded as part of the application's initial loading process.

### Easy Difference

```text
Eager Loading → Load at application startup
Lazy Loading  → Load when needed
```

63. ### What is an Auth Guard?
An Auth Guard is used to **protect routes from unauthorized users**.

It checks whether the user is authenticated before allowing access to a route.

**Example**
```ts
export const authGuard: CanActivateFn = () => {
  return isLoggedIn();
};
```

```ts
const routes: Routes = [
  {
    path: 'dashboard',
    component: DashboardComponent,
    canActivate: [authGuard]
  }
];
```

If the user is not logged in, the guard can prevent access and redirect them to the login page.

64. ### What is a Role Guard?
A Role Guard is used to restrict access to a route based on the **user's role or permissions**.

For example, only an `admin` can access the admin dashboard.

**Example**
```ts
export const roleGuard: CanActivateFn = () => {
  return userRole === 'admin';
};
```

```ts
{
  path: 'admin',
  component: AdminComponent,
  canActivate: [roleGuard]
}
```

**Auth Guard** → Checks whether the user is **authenticated**.
**Role Guard** → Checks whether the user has the **required role/permission**.

65. ### What is a Route Resolver?
A Route Resolver is used to **fetch or prepare data before a route is activated**, so the component receives the required data when it loads.

**Example**

```ts
export const userResolver: ResolveFn<User> = () => {
  return inject(UserService).getUser();
};
```

```ts
{
  path: 'profile',
  component: ProfileComponent,
  resolve: {
    user: userResolver
  }
}
```

The user data is fetched **before `ProfileComponent` is loaded**.

66. ### What are Route Parameters?
Route Parameters are used to pass **dynamic values through the URL path**, such as a user ID or product ID.

**Example**
```ts
const routes: Routes = [
  {
    path: 'user/:id',
    component: UserComponent
  }
];
```

Navigate to:
```text
/user/123
```

Here, `123` is the route parameter.

**Reading the Parameter**

```ts
id = inject(ActivatedRoute).snapshot.paramMap.get('id');
```

```text
/user/123 → id = 123
/user/456 → id = 456
```

67. ### What are Query Parameters?
Query Parameters are used to pass **optional information through the URL**, commonly for filtering, searching, sorting, or pagination.

**Example**

```text
/users?page=2&role=admin
```

Here:

```text
page = 2
role = admin
```

**Reading Query Parameters**

```ts
route = inject(ActivatedRoute);

page = this.route.snapshot.queryParamMap.get('page');
role = this.route.snapshot.queryParamMap.get('role');
```

### Route Parameters vs Query Parameters

```text
Route Parameter  → /user/123
Query Parameter  → /users?page=2
```

**Route Parameters** → Generally used to identify a specific resource.

**Query Parameters** → Generally used for optional filtering, searching, sorting, pagination, etc.

68. ### What is `ActivatedRoute`?

`ActivatedRoute` is an Angular service used to **access information about the currently active route**, such as:

- Route parameters
- Query parameters
- Route data
- Resolved data

**Example**

```ts
route = inject(ActivatedRoute);

id = this.route.snapshot.paramMap.get('id');
```

For:

```text
/user/123
```

`id` will be:

```text
123
```

69. ### Router vs `ActivatedRoute`

### `Router`

Used to **navigate programmatically** between routes.

```ts
router = inject(Router);

this.router.navigate(['/dashboard']);
```

### `ActivatedRoute`

Used to **read information from the current route**.

```ts
route = inject(ActivatedRoute);

id = this.route.snapshot.paramMap.get('id');
```

### Easy Difference

```text
Router         → Navigate to a route
ActivatedRoute → Read information from the current route
```

70. ### What are Router Events?

Router Events are events emitted by Angular's Router during the **navigation lifecycle**.

They can be used to track:

- Navigation started
- Navigation completed
- Navigation cancelled
- Navigation failed

**Example**

```ts
router = inject(Router);

this.router.events.subscribe(event => {
  console.log(event);
});
```

**Common Router Events**

```text
NavigationStart   → Navigation begins
NavigationEnd     → Navigation completed
NavigationCancel  → Navigation cancelled
NavigationError   → Navigation failed
```

71. ### Multiple Modules & Routing Best Practices

In a larger Angular application, routing can be organized into **separate route files based on features** instead of keeping all routes in one place.

**Best Practices**

- Keep routes organized by feature.
- Use **lazy loading** for large or less frequently used features.
- Keep authentication/authorization guards close to protected routes.
- Use route parameters for resource IDs and query parameters for optional filters.
- Avoid unnecessarily duplicating routes.
- Keep routing configuration simple and maintainable.

**Example**

```ts
const routes: Routes = [
  {
    path: 'admin',
    loadChildren: () =>
      import('./admin/admin.routes').then(m => m.ADMIN_ROUTES)
  }
];
```

Here, the admin routes are kept separately and loaded only when `/admin` is accessed.

72. ### What is `HttpClient`?

`HttpClient` is Angular's service used to **send HTTP requests to a backend API** and receive responses.

**Common HTTP Methods**

- `GET` → Fetch data
- `POST` → Create/send data
- `PUT` → Update data
- `PATCH` → Partially update data
- `DELETE` → Delete data

**GET Example**

```ts
http = inject(HttpClient);

users$ = this.http.get<User[]>('/api/users');
```

**POST Example**

```ts
this.http.post('/api/users', { name: 'John' });
```

73. ### What is `HttpHeaders`?
`HttpHeaders` is used to **set or modify HTTP headers** when sending an HTTP request.

Common headers include:

- `Authorization`
- `Content-Type`
- `Accept`

**Example**

```ts
headers = new HttpHeaders({
  Authorization: 'Bearer token'
});

this.http.get('/api/users', { headers });
```

Here, the `Authorization` header is sent with the request.

74. ### What is `observe: 'response'`?

`observe: 'response'` is used when you want to receive the **complete HTTP response**, including:

- Response body
- HTTP status code
- Response headers

**Example**

```ts
this.http.get('/api/users', {
  observe: 'response'
}).subscribe(response => {
  console.log(response.status);
  console.log(response.headers);
  console.log(response.body);
});
```

By default, `HttpClient` returns only the **response body**.

With `observe: 'response'`, you get the **full `HttpResponse`**.

75. ### What is an HTTP Interceptor?

An HTTP Interceptor is used to **intercept HTTP requests and responses globally** before they are sent or returned.

**Common Uses**

- Add authentication tokens.
- Add common headers.
- Log requests/responses.
- Handle common errors.
- Modify requests or responses.

**Example**

```ts
export const authInterceptor: HttpInterceptorFn = (req, next) => {
  const clonedReq = req.clone({
    setHeaders: {
      Authorization: 'Bearer token'
    }
  });

  return next(clonedReq);
};
```

Here, the interceptor automatically adds the `Authorization` header to outgoing requests.

76. ### Why Modify HTTP Requests & Responses?
HTTP requests and responses are modified when we need to apply **common logic globally** instead of repeating it in every API call.

**Common Reasons**
- Add authentication tokens to requests.
- Add common headers.
- Modify request data.
- Handle common errors.
- Log requests or responses.
- Transform response data.

**Example**

Instead of adding the token to every request:

```ts
this.http.get('/api/users', {
  headers: { Authorization: 'Bearer token' }
});
```

An interceptor can add it automatically to **all outgoing requests**.

77. ### What is `HttpErrorResponse`?

`HttpErrorResponse` is an Angular class that represents an **HTTP request that failed**.

It provides information about the error, such as:

- HTTP status code
- Error message
- Error body
- Request URL

**Example**

```ts
this.http.get('/api/users').subscribe({
  next: data => console.log(data),
  error: (error: HttpErrorResponse) => {
    console.log(error.status);
    console.log(error.message);
  }
});
```

For example:

```text
error.status → 404
```

78. ### HTTP Error Handling

HTTP Error Handling is the process of handling failed API requests and providing an appropriate response to the user.

**Common Approaches**

- Handle errors using `subscribe({ error })`.
- Check the HTTP status code.
- Show an appropriate error message.
- Handle specific errors such as `401`, `403`, `404`, and `500`.
- Use an **HTTP Interceptor** for common/global error handling.

**Example**

```ts
this.http.get('/api/users').subscribe({
  next: data => console.log(data),
  error: (error: HttpErrorResponse) => {
    if (error.status === 404) {
      console.log('Users not found');
    }
  }
});
```

79. ### What is Global Error Handling?

Global Error Handling is used to handle errors **centrally across the Angular application**, instead of handling the same type of error separately in every component.

For HTTP errors, an **HTTP Interceptor** is commonly used.

**Example**

```ts
export const errorInterceptor: HttpInterceptorFn = (req, next) => {
  return next(req).pipe(
    catchError(error => {
      console.error('API Error:', error);
      return throwError(() => error);
    })
  );
};
```

This allows common API error handling to be managed in **one place**.

80. ### What is Retry?

Retry is used to automatically **attempt a failed HTTP request again**.

Angular uses RxJS operators like `retry()` for this.

**Example**

```ts
this.http.get('/api/users').pipe(
  retry(2)
);
```

Here, the request is retried **up to 2 times** if it fails before the error is passed to the error handler.

81. ### What is Fallback UI?

Fallback UI is a user-friendly UI shown when the expected data or operation **fails or is temporarily unavailable**.

For example, if an API request fails:

```html
<p *ngIf="error">
  Unable to load users. Please try again.
</p>
```

**Common Fallback UI**

- Error message
- Retry button
- Empty state
- Loading state
- Default/fallback content

82. ### Authentication vs Authorization
**Authentication** verifies **who the user is**.
**Authorization** verifies **what the authenticated user is allowed to do**.

### Easy Difference
```text
Authentication → Who are you?
Authorization  → What are you allowed to do?
```

**Example**
```text
Login → Authentication
Admin access → Authorization
```

83. ### What is the Login Flow?

The Login Flow is the process where the user provides credentials, the backend verifies them, and the application establishes an authenticated session.

**Typical Flow**

```text
User enters credentials
        ↓
Angular sends POST /login
        ↓
Backend validates credentials
        ↓
Backend creates session / returns authentication result
        ↓
Angular considers user authenticated
        ↓
User can access protected routes
```

**Example**

```ts
this.http.post('/api/login', {
  email,
  password
});
```

After successful login:

```ts
this.router.navigate(['/dashboard']);
```

84. ### What are User Roles?

User Roles define what a user is **allowed to access or do** in an application.

**Common Roles**

- `admin` → Full access
- `manager` → Management features
- `user` → Regular features

**Example**

```ts
userRole = 'admin';
```

Roles can be used with a **Role Guard** to control access to protected routes.

```text
Authentication → Who is the user?
Authorization  → What can they access?
Role           → Which permissions apply to them?
```
85. ### Cookie-based Session Persistence

Cookie-based session persistence means the backend manages the user's session using a **cookie**, allowing the user to remain logged in across requests and page refreshes.

**Typical Flow**

```text
User logs in
    ↓
Backend validates credentials
    ↓
Backend creates session
    ↓
Session information is stored in a cookie
    ↓
Browser sends the cookie with subsequent requests
    ↓
Backend identifies the logged-in user
```

**Angular Request**

```ts
this.http.get('/api/profile', {
  withCredentials: true
});
```

The browser includes the authentication cookie with the request.

86. ### What is the Logout Flow?

The Logout Flow is the process of ending the user's authenticated session and preventing further access to protected resources.

**Typical Flow**

```text
User clicks Logout
      ↓
Angular sends logout request
      ↓
Backend invalidates the session
      ↓
Authentication cookie is cleared/invalidated
      ↓
User is redirected to Login
```

**Example**

```ts
logout() {
  this.http.post('/api/logout', {}).subscribe(() => {
    this.router.navigate(['/login']);
  });
}
```

87. ### How do you Secure an Angular Application?

An Angular application can be secured by combining **frontend protections with proper backend security**.

**Key Practices**

- Use **HTTPS** for communication.
- Protect routes using **Auth Guards** and **Role Guards**.
- Use secure **cookie-based sessions** where appropriate.
- Never store sensitive data such as passwords in the frontend.
- Validate and authorize requests on the **backend**.
- Avoid trusting user-provided data.
- Protect against **XSS** by using Angular's built-in template sanitization and avoiding unsafe HTML APIs.
- Configure appropriate **CORS** policies on the backend.
- Keep Angular and dependencies updated.

> **Important:** Route guards only protect frontend navigation. **Real authorization must always be enforced by the backend.**

88. ### What is State Management?

State Management is the process of **storing, updating, and sharing application data (state) across components** in a predictable way.

**Examples of Application State**

- Logged-in user
- Shopping cart
- Selected products
- Loading/error state
- Form data
- Application settings

**Common Angular Approaches**

- **Services**
- **Signals**
- **Stores**
- **NgRx**

**Example**

```ts
user = signal<User | null>(null);

login(user: User) {
  this.user.set(user);
}
```

The shared state can then be accessed by multiple components.

89. ### State Management Using a Service

A Service can be used to **store shared application state** and provide it to multiple components.

**Example**

```ts
@Injectable({
  providedIn: 'root'
})
export class UserStateService {
  user = signal<User | null>(null);
}
```

A component can inject the service and update/read the shared state:

```ts
userState = inject(UserStateService);

this.userState.user.set(user);
```

Other components injecting the same service can access the same state.

91. ### What is a Store?

A Store is a centralized place used to **hold and manage application state** so that multiple components can access and update the same state.

A Store typically manages:

- State
- Updating state
- Reading state

**Example**

```ts
@Injectable({
  providedIn: 'root'
})
export class UserStore {
  user = signal<User | null>(null);
}
```

Components can inject the store and access the shared state:

```ts
userStore = inject(UserStore);
```

92. ### What are Signals?

A Signal is a **reactive way to store a value in Angular**. When the value changes, Angular automatically updates the parts of the UI that use it.

**Example**

```ts
count = signal(0);

this.count.set(5);
```

```html
<p>{{ count() }}</p>
```

**Easy way to remember:**

> Signal = reactive value that updates the UI when it changes.


93. ### What is NgRx?

NgRx is a state management library for Angular used to **manage complex application state in a centralized and predictable way**.

**Main Concepts**

```text
Store     → Holds application state
Actions   → Describe what happened
Reducer   → Updates the state
Selectors → Read the state
Effects   → Handle side effects such as API calls
```

**Easy way to remember:**

> **NgRx = centralized and predictable state management for Angular.**


94. ### Template-driven Forms vs Reactive Forms

**Template-driven Forms** are mainly configured in the **HTML template** using directives like `[(ngModel)]`.

**Reactive Forms** are mainly configured in **TypeScript** using `FormGroup`, `FormControl`, and related APIs.

### Simple Difference

```text
Template-driven → Form logic mainly in HTML
Reactive Forms  → Form logic mainly in TypeScript
```

**Template-driven Example**

```html
<input [(ngModel)]="name">
```

**Reactive Forms Example**

```ts
name = new FormControl('');
```

### When to Use?

- **Template-driven** → Simple forms
- **Reactive Forms** → Complex, dynamic forms and detailed validation

95. ### What is `FormGroup`?

`FormGroup` is used to **group multiple form controls together** and manage them as a single form.

**Example**

```ts
form = new FormGroup({
  name: new FormControl(''),
  email: new FormControl('')
});
```

Here, `name` and `email` are individual controls inside the `FormGroup`.

```html
<form [formGroup]="form">
  <input formControlName="name">
  <input formControlName="email">
</form>
```

> **Easy way to remember:**  
> `FormGroup` = a group/container of related `FormControl`s.


96. ### What is `FormControl`?
`FormControl` represents and manages the **value and validation state of a single form field**.

**Example**

```ts
name = new FormControl('');
```

A value can be set using:

```ts
name.setValue('Kanhaiya');
```

The value can be read using:

```ts
name.value
```

97. ### What is `FormArray`?
`FormArray` is used to manage a **dynamic list of form controls or form groups**.
It is useful when the number of fields can **change at runtime**, such as adding or removing rows.

**Example**
```ts
skills = new FormArray([
  new FormControl('Angular'),
  new FormControl('TypeScript')
]);
```

**Add a control**
```ts
skills.push(new FormControl('Node.js'));
```

**Remove a control**

```ts
skills.removeAt(0);
```

> **Easy way to remember:**
> `FormControl` → One field  
> `FormGroup` → Group of fields  
> `FormArray` → Dynamic list of fields/groups

> **Easy way to remember:**
> `FormControl` = one form field  
> `FormGroup` = group of form fields


98. ### What are Validators?
Validators are used to **check whether form values meet specific rules**.

**Common Validators**

- `required`
- `minLength`
- `maxLength`
- `email`
- `min`
- `max`

**Example**

```ts
name = new FormControl('', Validators.required);
```
If the field is empty, the control becomes **invalid**.

99. ### What are Built-in Validators?

Built-in Validators are predefined validators provided by Angular for common form validation rules.

**Common Built-in Validators**

- `Validators.required`
- `Validators.minLength()`
- `Validators.maxLength()`
- `Validators.email`
- `Validators.min()`
- `Validators.max()`

**Example**

```ts
email = new FormControl('', Validators.email);
```

Angular automatically checks whether the entered value is a valid email.

100. ### What are Custom Validators?

Custom Validators are **user-defined validators** used when Angular's built-in validators are not enough for a specific validation rule.

**Example**

```ts
function noSpaces(control: AbstractControl) {
  return control.value.includes(' ')
    ? { noSpaces: true }
    : null;
}
```

Use it with a form control:

```ts
username = new FormControl('', noSpaces);
```

- Returns an **error object** → Invalid
- Returns `null` → Valid

101. ### What are Async Validators?

Async Validators are validators that perform **asynchronous validation**, usually by calling a backend/API to check whether a value is valid.

For example, checking whether a username or email already exists.

**Example**

```ts
username = new FormControl('', {
  asyncValidators: checkUsername
});
```

The validator returns a `Promise` or `Observable`.

```text
Value entered
     ↓
API call
     ↓
Valid → null
Invalid → error object
```

102. ### Angular Performance Optimization Techniques

Angular performance can be improved by **reducing unnecessary work, loading less code initially, and optimizing rendering**.

**Common Techniques**

- Use `OnPush` change detection where appropriate.
- Use `@for` with a proper `track` expression.
- Use `@defer` for deferred loading.
- Lazy-load routes/features.
- Avoid unnecessary function calls in templates.
- Use Signals for efficient reactive updates.
- Use in-memory caching for frequently requested data.
- Optimize images.
- Reduce bundle size.
- Prevent memory leaks by cleaning up subscriptions/resources.

**Easy way to remember:**

> **Render less → Load less → Calculate less → Clean up resources**


103. ### AOT vs JIT
### AOT — Ahead-of-Time
AOT compiles Angular code **during the build process**, before the application reaches the browser.

```text
Angular Code
     ↓
Build Process
     ↓
Angular Compiler
     ↓
Compiled JavaScript
     ↓
Browser
```

**Benefits:**
- Faster startup
- Less compilation work in the browser
- Better production performance
- Errors can be detected during build

---

### JIT — Just-in-Time

JIT compiles Angular code **at runtime in the browser**.

Angular's compiler runs in the browser and compiles the Angular application before it runs.

```text
Angular Code
     ↓
Browser loads Angular + App
     ↓
Angular Compiler runs
     ↓
Application runs
```

### Easy Difference

```text
AOT → Angular compiles during build
JIT → Angular compiles at runtime in browser
```

> **AOT is preferred for production because the browser doesn't need to perform Angular compilation at runtime.**


104. ### What is In-memory Caching?

In-memory caching means storing frequently used data **temporarily in application memory** so it can be reused without making the same API request again.

**Example**

```ts
private usersCache: User[] | null = null;

getUsers() {
  if (this.usersCache) {
    return of(this.usersCache);
  }

  return this.http.get<User[]>('/api/users').pipe(
    tap(users => this.usersCache = users)
  );
}
```

**Benefits**

- Reduces unnecessary API calls.
- Improves response time.
- Reduces network/server usage.

> **Important:** In-memory cache is lost when the application/page is reloaded.


105. ### What are Memory Leaks?

A memory leak happens when an application keeps references to data or resources that are **no longer needed**, causing memory usage to grow unnecessarily.

**Common Causes in Angular**

- Unsubscribed Observables
- Event listeners that aren't removed
- Timers that aren't cleared
- Large objects unnecessarily kept in memory

**Example**

```ts
const subscription = this.service.getData().subscribe();

subscription.unsubscribe();
```

Modern Angular can also use `takeUntilDestroyed()` to automatically clean up subscriptions.

> **Easy way to remember:**  
> Memory leak = unused resources staying in memory.


106. ### What is SSR (Server-Side Rendering)?

SSR (Server-Side Rendering) means rendering Angular pages **on the server first** and sending the already-rendered HTML to the browser.

**Flow**

```text
User requests page
       ↓
Server renders Angular page
       ↓
HTML sent to browser
       ↓
Angular loads and becomes interactive
```

**Benefits**

- Faster initial page display
- Better SEO
- Useful for content-heavy/public pages

> **Easy way to remember:**  
> SSR = Render the page on the server before sending it to the browser.


107. ### SSR vs CSR

### SSR — Server-Side Rendering

The **server renders the page first** and sends HTML to the browser.

```text
Server → Renders HTML → Browser
```

### CSR — Client-Side Rendering

The **browser loads the Angular application and renders the page on the client side**.

```text
Server → Sends app files → Browser → Renders UI
```

### Easy Difference

```text
SSR → Rendering happens on the server
CSR → Rendering happens in the browser
```

**SSR** → Better initial content display and SEO.

**CSR** → Common for highly interactive web applications.

108. ### What is PWA?

PWA (Progressive Web App) is a web application that provides a **more app-like experience**, including features such as offline support, caching, and installation on a device.

In Angular, PWAs can use a **service worker** to cache application resources and support offline usage.

**Benefits**

- Offline support
- Caching
- Can be installed on a device
- Faster loading for returning users

> **Easy way to remember:**  
> PWA = Web app with app-like capabilities.

109. ### What is Deferred Loading (`@defer`)?

`@defer` is an Angular feature used to **load part of the UI only when it is needed**, instead of loading it immediately.

**Example**

```html
@defer {
  <app-heavy-component />
}
```

The deferred component is loaded **later**, which can improve the initial page load.

> **Easy way to remember:**  
> `@defer` = Load this UI later when needed.

110. ### Image Optimization

Image Optimization means reducing the cost of images so they **load faster and use less bandwidth**.

**Common Techniques**

- Use appropriate image sizes.
- Use modern formats such as **WebP/AVIF**.
- Lazy-load images that aren't immediately visible.
- Avoid serving unnecessarily large images.
- Use Angular's **`NgOptimizedImage`**.

**Example**

```html
<img
  ngSrc="/images/product.webp"
  width="400"
  height="300"
  alt="Product"
>
```

> **Easy way to remember:**  
> Image Optimization = smaller, properly sized, efficiently loaded images.


111. ### What is Bundle Optimization?

Bundle Optimization means reducing the amount of JavaScript and other resources that the browser needs to download and execute.

**Common Techniques**

- Use **lazy loading**.
- Use `@defer` for heavy components.
- Remove unused dependencies.
- Use production builds.
- Split large bundles into smaller chunks.
- Avoid importing unnecessary libraries.

> **Easy way to remember:**  
> Bundle Optimization = Reduce the amount of code the browser needs to load.


112. ### What are `import` and `export`?

**`export`** makes a class, function, variable, or component available to other files.

**`import`** allows another file to use that exported code.

**Example**

```ts
// user.service.ts
export class UserService {}
```

```ts
// home.component.ts
import { UserService } from './user.service';
```

### Easy way to remember

```text
export → Make something available
import → Use something from another file
```

113. ### What is `"type": "module"` in `package.json`?

`"type": "module"` tells **Node.js to treat `.js` files as ES Modules**, allowing `import` and `export` syntax.

**Example**

```json
{
  "type": "module"
}
```

Then JavaScript files can use:

```js
export const name = 'John';
```

```js
import { name } from './user.js';
```

> **Easy way to remember:**  
> `"type": "module"` → Enables ES Module behavior for `.js` files in Node.js.


114. ### What is `package.json`?

`package.json` contains the project's **metadata, dependencies, scripts, and configuration**.

> **Easy way to remember:**  
> `package.json` → Manages the project's packages, scripts, and metadata.

---

115. ### What is `angular.json`?

`angular.json` is the **Angular CLI configuration file**.

It contains project-level settings such as:

- Build configuration
- Serve configuration
- Assets
- Styles
- Scripts
- Output settings

> **Easy way to remember:**  
> `angular.json` → Configures how Angular CLI builds and runs the project.


116. ### What is `TestBed.configureTestingModule()`?

`TestBed.configureTestingModule()` is used to **configure the Angular testing environment** for a component, service, directive, or pipe.

You can provide:

- Components
- Services
- Imports
- Providers
- Mocks

**Example**

```ts
TestBed.configureTestingModule({
  imports: [MyComponent],
  providers: [UserService]
});
```

> **Easy way to remember:**  
> `TestBed.configureTestingModule()` → Sets up the Angular environment needed for a test.


117. ### Can `TestBed` configuration be changed after Component creation?

**No.** Once the component has been created, you cannot change the `TestBed` configuration for that test.

Configure `TestBed` **before** creating the component:

```ts
TestBed.configureTestingModule({
  imports: [MyComponent]
});

const fixture = TestBed.createComponent(MyComponent);
```

> **Easy way to remember:**  
> **Configure TestBed first → Create component after.**

117. ### What is Jasmine?

Jasmine is a JavaScript testing framework used to **write and run unit tests**.

In Angular, Jasmine is commonly used to test:

- Components
- Services
- Pipes
- Functions

**Example**

```ts
it('should add two numbers', () => {
  expect(2 + 3).toBe(5);
});
```

```text
it()     → Defines the test
expect() → Defines the expected result
toBe()   → Checks the result
```

> **Easy way to remember:**  
> Jasmine → Framework used to write unit tests.

118. ### What is Karma?

Karma is a test runner used to **execute Angular unit tests** and report the results.

### Easy Difference

```text
Jasmine → Writes the tests
Karma   → Runs the tests
```

> **Easy way to remember:**  
> Jasmine = Test framework  
> Karma = Test runner

119. ### What are Mock Services?
Mock Services are **fake services used in tests** to simulate real services without making actual API calls or using real dependencies.

**Example**

```ts
const mockUserService = {
  getUser: () => of({ name: 'John' })
};

TestBed.configureTestingModule({
  providers: [
    { provide: UserService, useValue: mockUserService }
  ]
});
```

Here, the real `UserService` is replaced with a **mock service**.

> **Easy way to remember:**  
> Mock Service = Fake service used for testing.


122. ### What is `spyOn()`?

`spyOn()` is used in Jasmine to **monitor or replace a method during a test**.

It can check whether a method was called and with what arguments.

**Example**

```ts
spyOn(service, 'getUser');

service.getUser();

expect(service.getUser).toHaveBeenCalled();
```

> **Easy way to remember:**  
> `spyOn()` → Watch a method during a test.


123. ### How do you Generate, Run, Build, and Deploy an Angular Project?

### 1. Generate a Project

```bash
ng new my-app
cd my-app
```

### 2. Run Locally

```bash
ng serve
```

Runs the Angular application locally.

### 3. Build the Project

```bash
ng build
```

Creates an optimized build, usually inside the `dist/` folder.

### 4. Deploy the Project

Deploy the generated files from the `dist/` folder to a web server or hosting platform such as:

- AWS
- Azure
- Firebase
- Netlify
- Vercel

### Easy Way to Remember

```text
ng new    → Create project
ng serve  → Run locally
ng build  → Create production build
dist/     → Deploy built files
```

## HR
1. ### What is expected Salary
  I am much more interested in the opportunity to contribute to team (here at org name) than I am in the size of initial offer. we can discuss the offer details at later stage.

  I will consider any reasanable offer

  Tell expected amount

 2. ### Tell me about yourself
  I am Kanhaiya Agnihotri. I completed my MCA from KIET Group of Institutions, Ghaziabad in 2019. I have over four years of experience in web development primarily using Angular. I started at Wikaad IT Systems, building dashboards for an oil field organization, after closure of wikaad i internally  moved to Webuters Technology to work on HireMe, a digital hiring platform. Later, at P2P Systems, I worked on Smart School, a school ERP product. Currently, I’ve built a Battery Storage Management System from scratch and i am contributing to Aeros Cloud, a saas plateform, developing various modules and implemented new theme for all authentication screens. I enjoy building user-friendly web applications, and i look forward to bring my skills and experience to contribute effectively to your team.

 3. ### What is your official Notice period?
  My Official notice period is 60 days. But my company allows buyout. So if needed i can try to join earlier. 

  How early you can join - If the role is urgent, I can try for a buyout and potentially join in 30–40 days.

  If HR pressures: “We need someone immediate” - I can request buyout and push for early release, and will join as soon as my current employer approves the release.”

  4. ### Why there is 3 years gap after MCA?
  Early in my career, I explored Python and backend fundamentals, but I realized frontend engineering suited me better. During the COVID period, I used that time to reskill and realign my career direction. I then focused on JavaScript and Angular, built hands-on projects, and once I had clarity, I entered the job market and secured my first full-time frontend role in 2022. Since then, my career has been consistent.

  ## Coding Notes
  
#### 1. Program to find the factorial of a number
Product of all positive integers from **1** to **n**.

**Logic**
- Initialize `fact = 1`.
- Iterate from `n` to `1`.
- Multiply `fact` by the current number.

**JavaScript**

```javascript
function factorial(number) {
    let fact = 1;

    for (let i = number; i>1; i--) {
        fact *= i;
    }

    return fact;
}

console.log(factorial(5)); // 120

// Time Complexity:** `O(n)`  
// Space Complexity:** `O(1)`
```





  
