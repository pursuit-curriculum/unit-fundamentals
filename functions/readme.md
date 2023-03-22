# Functions

## Introduction

Functions are another fundamental element of coding. Functions are blocks of code that can be saved and run repeatedly. When building programs, coders stick to common principles like DRY (Don't Repeat Yourself), which help coders build large and maintainable projects.

Since the first lesson, you've used a function called `console.log()`. This function prints (logs) things to your console. You didn't have to write the code to make this functionality. You just had to know how to use it. You can also use this function as often as you like, wherever you want. This utility makes functions powerful tools.

## Learning Objectives

- Define the purpose of a function.
- Create a function
- Identify the standard components of a function.
- Use (invoke) a function
- Create and use a function that accepts multiple arguments.
- Differentiate between returning within a function and logging to the console.

<hr>

## Create a function

Now, it's your turn to declare a function. First, you start with the keyword `function` and then name the function, just like you would a variable. After that, you must have a set of parentheses, then a set of curly braces. Inside the curly braces will be the code you want to run, also known as the `function body`.

```js
function helloWorld() {
  // Add whatever code you want to run here
  console.log("Hello, world!");
}
```

To call this function, also called `invoking a function`, you would write:

```js
helloWorld();
```

Including the `()` to call the function is critical. If you forget to include the parentheses, you will only reference the function but not call it to action.

```js
// Does not throw an error
// Does not console.log the message either
helloWorld;
```

## Create a function with parameters

When you create a function and put something inside the parentheses, this value is called a `parameter`.

```js
function helloPerson(name) {
  console.log(`Hello, ${name}!`);
}
```

When you invoke the function, you must pass an `argument` inside the parentheses for the function to use the value:

```js
helloPerson("Cameron");
// "Hello, Cameron!"
```

> **Note**: When you define a function the variables inside the parenthesis are called parameters. When you call a function and pass values, the values inside the parenthesis are called arguments.

You can add more parameters:

```js
function helloPersonAgain(firstName, lastName) {
  console.log(`Hello, ${firstName} ${lastName}!`);
}
```

```js
helloPersonAgain("Gordon", "Clarke");
```

And you can reuse functions over and over again:

```js
helloPersonAgain("Joe", "MacMillian");
helloPersonAgain("Donna", "Clark");
helloPersonAgain("Joe", "MacMillian");
helloPersonAgain("John", "Bosworth");
```

Parameters allow your functions to be more flexible and customizable.

## Return Values

Functions have another ability, and that is to return a value.

```js
function square(x) {
  return x * x;
}
```

That means you can assign the value that the function creates to a variable.

```js
const squareFour = square(4);
console.log(squareFour);
```

You can also put a function inside another function, and it will evaluate from the inside out:

```js
console.log(square(5));
```

> **Note**: the function `console.log` returns nothing. Therefore its return value is `undefined`. All functions that don't have a return value will have a default return value of `undefined`.

```js
// This will console log
console.log(helloPerson("Lev"));

// If you try to assign a function's result to a variable, you will get undefined
const yoYo = helloPerson("Yo-Yo");
console.log(yoYo);
// undefined because the function `helloPerson` does not return a value
```

## Default parameters

It can be helpful to have a default parameter value if no argument is supplied.

```js
function greeting(salutation = "Hello") {
  console.log(`${salutation}, world!`);
}
```

Now, you can call `greeting()`, and it will still say `Hello, world!` or you can add your own greeting as an argument.

```js
greeting();
// "Hello, world!"
greeting("Howdy");
// "Howdy, world!"
```

## Other ways to write functions

JavaScript was initially written in 10 days. It has been in use since 1999. As JavaScript grew in popularity, more and more features were added. As more and more people use it, there are also more and more opinions and styles. In this class, we will primarily use the above function definition syntax, but you may encounter two other syntaxes as you continue to research and learn.

### Function expression

A function expression uses a variable and assigns the variable a function:

```js
const myFunc = function () {
  console.log("This is my new function.");
};

myFunc();
```

### Arrow function

An arrow function skips the keyword `function` in favor of an arrow `=>`.

```js
const myArrowFunc = () => {
  console.log("This is my new arrow function.");
};

myArrowFunc();
```

## Functions can call other functions

You can build functions to call other functions.

```js
function add(num1, num2) {
  return num1 + num2;
}
function subtract(num1, num2) {
  return num1 - num2;
}
function multiply(num1, num2) {
  return num1 * num2;
}
function divide(num1, num2) {
  return num1 / num2;
}
function calculator(num1, num2, operator) {
  if (operator === "add") {
    return add(num1, num2);
  } else if (operator === "subtract") {
    return subtract(num1, num2);
  } else if (operator === "multiply") {
    return multiply(num1, num2);
  } else if (operator === "divide") {
    return divide(num1, num2);
  } else {
    return `Something went wrong`;
  }
}
console.log(calculator(1, 1, "add"));
console.log(calculator(2, 1, "subtract"));
console.log(calculator(3, 4, "multiply"));
console.log(calculator(5, 2, "divide"));
```

## Hello, world! History

If you would like, you can learn about the history of the [Hello, World! program](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program).
