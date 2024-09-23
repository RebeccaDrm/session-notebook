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


## Primitive Data Types

JavaScript is a dynamically typed language, which means, that you don't have to specify what kind of
value you want to store, JavaScript detects this automatically.

There are 7 primitive data types:

| type        | represents                                                                                                                  |
| ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| `string`    | a sequence of characters: "abcd"                                                                                            |
| `number`    | a number: 1234                                                                                                              |
| `boolean`   | a binary statement, can be `true` or `false`                                                                                |
| `null`      | represents "nothing", is typically set by developers                                                                        |
| `undefined` | represents the state of "not existing". Anything not specified or not found in JavaScript defaults to the value `undefined`

___

Truthy and Falsy Values
Sometimes you want to have a condition depending on another type of value. JavaScript can transform any value into a boolean with type coercion. That means that some values act as if they were true and others as if they were false: Truthy values become true, falsy values become false.

truthy values:

non zero numbers: 1, 2, -3, etc.
non empty strings: "hello"
true
falsy values:

0 / -0
null
false
undefined
empty string: ""

## Comparison Operators

Comparison operators produce boolean values by comparing two expressions:

| Operator  | Effect                                                                           |
| --------- | -------------------------------------------------------------------------------- |
| A `===` B | strict equal: is `true` if both values are equal (including their type).         |
| A `!==` B | strict not equal: is `true` if both values are not equal (including their type). |
| A `>` B   | strictly greater than: is `true` if A is greater than B.                         |
| A `<` B   | strictly less than: is `true` if A is less than B.                               |
| A `>=` B  | greater than or equal: is `true` if A is greater than or equal B.                |
| A `<=` B  | less than or equal: is `true` if A is less than or equal B.    


---

## Logical Operators

Logical operators combine up to two booleans into a new boolean.

| Operator                      | Effect                                                 |
| ----------------------------- | ------------------------------------------------------ |
| `!`A                          | `not`: flips a `true` value to `false` and vice versa. |
| A <code>&#124;&#124;</code> B | `or`: is `true` if either A `or` B is true.            |
| A `&&` B                      | `and`: is `true` if both A `and` B is true.            |


## Control Flow: `if / else`

With an if statement we can control whether a part of our code is executed or not, based on a
condition.

```js
const isSunShining = true;

if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
}
```

The else block is executed only if the condition is `false`.

```js
const isSunShining = false;

if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
} else {
  // code that is executed only if condition "isSunShining" is false
}
```

The condition expression between the `()` brackets can be composed of logical or comparison
operators as well. You can distinguish between more cases by chaining `else if` statements:

```js
if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
}
```

If the condition is not a boolean, it is converted into one by type coercion. This can be used to
check whether a value is not 0 or an empty string:

```js
const name = "Alex";
if (name) {
  console.log("Hi " + name + "!"); // only executed if name is not an empty string
}
```

---

## Ternary Operator: `? :`

With if / else statements whole blocks of code can be controlled. The ternary operator can be used
if you want to decide between two _expressions_, e.g. which value should be stored in a variable:

```js
const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
```

The ternary operator has the following structure:

```js
condition ? expressionIfTrue : expressionIfFalse;
```

If the condition is true, the first expression is evaluated, otherwise the second expression. The
ternary operator can be used to decide which function should be called:

```js
isUserLoggedIn ? logoutUser() : loginUser();
```

It can also distinguish which value should be passed as an argument to a function:

```js
moveElement(xPos > 300 ? 300 : xPos); // the element can't be moved further than 300.
```

---

## Function Declarations

You can define a function using a `function declaration`, which consists of:

- The keyword `function`, which goes first.
- A function `name`, which should describe its purpose.
- A single `parameter` or a list of `parameters` between the parentheses `()`.
- A function `body`, which contains the JavaScript code, between the curly braces `{}`.

> 💡 Defining a function doesn't execute its code; you must call the function to run the code.

```js
function functionName() {
  // Function body
}

function bakeCake() {
  console.log("Mix the ingredients.");
  console.log("Pour the batter into a pan.");
  console.log("Bake at 180°C for 30 minutes.");
}
```
____

## Function Parameters

- A function that always shows the same message isn't very useful.
- Adding parameters makes a function more flexible by allowing different inputs.
- Functions use `parameters` like predefined variables inside the function body.
- You can name parameters freely, except for [reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#reserved_words).
- When defining a function, these variables are called `parameters`
- When calling a function, the values passed are called `arguments`.
- When the function is called, the given values become `local variables` that the function uses.

To clarify these terms:

> 💡 A `parameter` is the variable listed inside the parentheses in the function declaration (declaration-time term).

> 💡 An `argument` is the value that is passed to the function when it is called (call-time term).

```js
//           parameter ↓
function printLetter(name) {
  console.log("Hi " + name + ", hope you are fine. Your Mum");
}

//    argument ↓
printLetter("Alice");

//             parameters ↓
function printSum(first, second, third) {
  const sum = first + second + third;
  console.log("The sum of your numbers is: " + sum);
}
//   arguments ↓
printSum(3, 6, 9);
```

---
