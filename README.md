# Interview Questions

<br/>

## Table of Contents

* [Basics](#basics)
* [HTML Questions](#html-questions)
* [ASYMPOTIC Notations](#asympotic-notations)
* [CODING Questions](#coding-questions)
* [RXJS](#rxjs)

<br/>

## Basics

***One line/One Command/One Instruction/One Statement***: A Statement is one complete instruction the program can execute 

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
***Answer:*** Reactive Programming is programming with asynchronous data streams. A stream is sequence of events ordered in time, stream can emit 3 different things. some value, error or completed signal, to listen to stream is called subscribing, and to capture emitted things(events) we define functoins such as next, error or completed. these functions are called observers and stream is called observable(being observerd). in common reactive libraries, each stream has many functions attached, such as map, filter etc.
