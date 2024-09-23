# JavaScript Basics

## Learning Objectives

- Connect a JavaScript file with `<script>`

## Connect a JavaScript file

```html
<head>
  ...
  <script src="./index.js" defer></script>
</head>
<body>
  ...
</body>
```
___

## Selecting HTML Elements: `.querySelector()`

- Select elements with `querySelector`

Before we can add interactivity, we need to select the necessary HTML-Elements:

```html
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```

There are multiple ways to select the above main section within our JavaScript. A good practice is
to use a
[data-\* attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*),
like the **data-js** in the following example:

```js
const mainElement = document.querySelector('[data-js="main"]');
```

Other css selectors work as well, but the data-\* attribute selectors should be preferred.

```js
// tag as identifier
const mainElement = document.querySelector("main");
// class as identifier -> .
const mainElement = document.querySelector(".main");
// id as identifier -> #
const mainElement = document.querySelector("#main");
```

> 💡 We try to separate our concerns: Classes are for CSS and data-\* attributes are for JavaScript.

---

## Add Interaction: `.addEventListener()`

- Add, remove and toggle CSS classes on `click` with `addEventListener`

We can listen to **events** like **clicks** on an Element and execute code when the event is
triggered. The method `addEventListener` is used to react to events.

```html
<button type="button" data-js="button">Log into console</button>
```

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```

First you specify the kind of event, e.g. **click**, then you define what code should be executed
when the event is triggered. You write that code between the `{}` brackets, e.g. a `console.log`.

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```

There different events you can listen to, for example:

```js
button.addEventListener("mouseover", () => {});
```

```js
button.addEventListener("keydown", () => {});
```

> 💡 Here you can find a
> [list of event types](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing).

> 💡 You don't have to understand the syntax for now, we will cover this in a later session.

---

## Add/remove & toggle classes: `.classList.`

You can add, remove and toggle classes, e.g. to change the styling of an element.

```html
<main data-js="main">
  <button type="button" data-js="button">Add a class</button>
</main>
```

Add **page--primary** class to the above main section by using the `selectedElement.classList.add`
method:

```js
const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');

button.addEventListener("click", () => {
  main.classList.add("page--primary");
});
```

A click on the button adds the class **page--primary** to the main element:

```html
<main data-js="main" class="page--primary">
  <button type="button" data-js="button">Add a class</button>
</main>
```

You can also remove or toggle a class in the same way:

```js
main.classList.remove("page--primary");
```

```js
main.classList.toggle("page--primary");
```

___

## Variable Declarations

Variablen sind eine Referenz oder ein Alias ​​für im Speicher abgelegte Daten. Mit Hilfe dieser Variablen kann auf diese Daten zugegriffen werden. 
Es gibt 3 verschiedene Schlüsselwörter verwenden, um eine Variable zu deklarieren:

const – deklariert eine Konstante, der Wert kann nicht geändert werden. Standardmethode zum Deklarieren von Variablen.

let – deklariert eine Variable, der Wert kann geändert werden. Wird nur verwendet, wenn die Neuzuweisung eines neuen Werts erforderlich ist.

var – veraltet, wird nicht mehr verwendet.

Normally the keyword `const` is used to declare a variable.

```js
const aNewVariable = 1234;
```

The keyword `let` is only used when you need to reassign a value, for example when you want to
increase a counter.

```js
let counter = 0;
counter = counter + 1; // reassigning the value of counter
```

The `=` sign in programming doesn't quite work like the mathematical equality that you (maybe)
remember from school. It means: "the value of the item on the right of the equal sign is saved in
the item on the left of it". What the item on the right actually represents is calculated first and
saved afterwards.
