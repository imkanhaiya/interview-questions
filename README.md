# Interview Questions

<br/>

## Table of Contents

* [Basics](#basics)
* [HTML Questions](#html-questions)
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

1. ### Sample Queston.

```html
<!-- Block-level element example -->
<div>
  This is a block-level element.
</div>

<!-- Inline element example -->
<span>This is an inline element.</span>
```

<br>

## SCSS Questions

1. ### What is Sass/Scss
sass/scss is css preprocessor. It extends CSS with features that CSS originally didn’t have.

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
  
