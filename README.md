# Interview Questions

<br/>

## Table of Contents

* [Basics](#basics)
* [HTML Questions](#html-questions)
* [ASYMPOTIC Notations](#asympotic-notations)
* [CODING Questions](#coding-questions)
* [RXJS](#rxjs)
* [HR](#hr)

<br/>

## Basics

***One line/One Command/One Instruction/One Statement***: A Statement is one complete instruction that program can execute
<br>
***Synchronous***:  Code is executed line by line, next statement runs only after the current one has finished
<br>
***Asynchronous***: Code can start the task, but instead of waiting for it to finish, it moves to the next statement. the task completes later, and the program handles the result when its ready.

## HTML Questions

### Question 1: Sample Queston.
Sample **Answer**.

```html
<!-- Block-level element example -->
<div>
  This is a block-level element.
</div>

<!-- Inline element example -->
<span>This is an inline element.</span>
```

<br>

## ASYMPOTIC Notations

### Question 1: what are asympotic notations
***Answer:*** Asympotic notations are mathematcial way to describe efficiency of algorithms in terms of time and space complexity.

**Common Types:**
1. **Big O (O)** – Worst Case  
2. **Big Omega (Ω)** – Best Case  
3. **Theta (Θ)** – Average Case

## CODING Questions

<br>

## RXJS

### Question 1: What is difference between imperative vs declarative code [Explanation](https://www.youtube.com/watch?v=E7Fbf7R3x6I)
***Answer:***   

**Imperative** - How (Tell the machine how to do it)  
**Declarative** - What (Tell the machine what to do), example - sql query, html, css

### Question 2: What is Reactive Programming
***Answer:*** Reactive Programming(part of declartive programming) is programming with asynchronous data streams. A stream is sequence of events ordered in time, stream can emit 3 different things. some value, error or completed signal, to listen to stream is called subscribing, and to capture emitted things(events) we define functoins such as next, error or completed. these functions are called observers and stream is called observable(being observerd). in common reactive libraries, each stream has many functions attached, such as map, filter etc.

### Question 3: Why should i consider adopting/Benifits of Reactive programming
***Answer***: Reactive programming raises the abstraction of code, so we can focus on data flow and events rather than implementation details. this improves readability and makes the code concise. it's especially powerful for handling asynchronous data (such as network requests) and event-driven scenarios (such as UI interactions or real-time updates).

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

## HR
### Question 1: What is expected Salary
***Answer***: 
  I am much more interested in the opportunity to contribute to team (here at org name) than I am in the size of initial offer. we can discuss the offer details at later stage.

  I will consider any reasanable offer

  You are in much better position to know how much i am worth to (organization name) than i am. i would be happy to consider any offer you feel is fair for the role.

  Tell expected amount
