# Interview Questions

<br/>

## Table of Contents

* [Basics](#basics)
* [HTML Questions](#html-questions)
* [CSS Questions](#css-questions)
* [SCSS Questions](#scss-questions)
* [ASYMPOTIC Notations](#asympotic-notations)
* [RXJS](#rxjs)
* [Angular](#Angular)
* [HR](#hr)

<br/>

## Basics
1. ### One line/One Command/One Instruction/One Statement
   A Statement is one complete instruction that program can execute
   
2. ### Synchronous
   Code is executed line by line, next statement runs only after the current one has finished
   
3. ### Asynchronous
   Code can start the task, but instead of waiting for it to finish, it moves to the next statement. the task completes later, and the program handles the result when its ready.
   

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


## ASYMPOTIC Notations

1. ### what are asympotic notations
Asympotic notations are mathematcial way to describe efficiency of algorithms in terms of time and space complexity.
#### Common Types:
1. **Big O (O)** – Worst Case  
1. **Big Omega (Ω)** – Best Case  
1. **Theta (Θ)** – Average Case

<br>

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

1. ### How angular application starts?
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
  
