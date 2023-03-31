# Scope

Thus far, the amount of coding we've done in class or lab has only amounted to reasonably short amounts of code. When working as a developer, you'll work on a project for months or years, and you'll also be coding with other developers. The programs professionals work on can be thousands or even millions of lines of code.

Therefore, we must learn how to write maintainable code and follow scalable code patterns.

## Learning Objectives

- Identify and differentiate between the four scopes in JavaScript.
- Identify common problems that can arise from the misusing scope in JavaScript.
- Leverage scope to write reusable and maintainable code.

<hr>

## Introduction to scope

In coding, scope refers to a section of code. Within this section, all the functions and code blocks will be able to "look up" the other function definitions and variables.

There are four kinds of scope:

- Global
- Block
- Function
- Module

## Global scope

The highest level of scope is called `global`. Any section of code can look up and find this definition. An example is `console.log` - a global function you can call anywhere at any time.

This may seem like the best option for all of your code is to access everything you've created, and it may seem very easy to keep track of because, so far, your programs and functions have been relatively small. However, for bigger projects the amount of global functions and variables should be very limited and well thought out. This is because if a program has thousands of variables you don't want to override ones already created and you don't want to track all the variables that have been created. It makes more sense to limit where the variables can be defined and used.

## Block scope

This is any scope contained inside a set of curly braces `{}`.

```js
if (true) {
  // myVariable can be accessed anywhere inside the curly braces
  let myVariable = "yes";
  console.log(myVariable);
}
```

But outside the curly braces, it is not defined. The following will throw an error message because it is outside of the code block:

```js
if (true) {
  // myVariable can be accessed anywhere inside the curly braces
  let myVariable = "yes";
  console.log(myVariable);
}

console.log(myVariable);

// Uncaught ReferenceError: myVariable is not defined
```

Using the keyword `let` or `const` when declaring a for loop will also limit the scope to be inside the loop. 

```js
for (let i = 0; i < 3; i++) {
  console.log('The value of i inside the loop is', i)
}

// reference error
console.log('The value of i outside the loop is', i)
```

```js
for (i = 0; i < 3; i++) {
  console.log('The value of i inside the loop is', i)
}

// vaue of i is available outside of the loop
console.log('The value of i outside the loop is', i)
```

## Function scope

Parameters that are declared with a function have a scope that is limited to be inside the function. 
```js
function myFunc(myName) {
  console.log(`My name is ${myName}`);
}

myFunc("JJ");

// myName is only available inside the function

console.log(myName);

// Uncaught ReferenceError: myName is not defined
```

Each invocation of the function is separeate and does not "know" about any other invocations. 


A function can call itself. This is called recursion.

```js
function countdown(start) {
  console.log("Countdown!", start);
  if (start != 0) {
    return countdown(start - 1);
  }
}

console.log(countdown(10));
```

Try to draw out the steps and values of `start` to help you understand function scope.

## Module scope

JavaScript can be split up into modules. You can create multiple files with JavaScript and then use them together. Typically, there is one module per file. You can try this in NodeJS (if you are using an app like repl.it make sure you choose NodeJS and not html/css/JavaScript as the option).

You can create a separate file, but the code written here will not know about the code in `index.js`.

**myFile.js**

```js
const myConstant = 5;
```

**index.js**

```js
console.log(myConstant);

// Uncaught ReferenceError: myConstant is not defined
```

You can `export` variables and `import` them. Currently, NodeJS is in a transition period where you will see both the old syntax and the new syntax. As of 2023, the old syntax is still the default and to use the newer syntax, more configuration would be needed. The example given will be with the older syntax.

To export `myConstant`, you would add the following to the bottom of the **myFile.js** file:

```js
module.exports = { myConstant };
```

To import `myConstant` to the **index.js** file, you would add to the top of the file:

```js
const { myConstant } = require("./myFile.js");
```

To check that it works, run the `index.js` file.

## Looking up scope

Let's look at a bit of code:

```js
const someNumber = 10;

if (someNumber === 10) {
  console.log(`The number is equal to ten! The value is ${someNumber}`);
}
```

The definition of `someNumber` is defined outside the code block for the `if` statement.

A JavaScript file starts from the top and loads the values and executers the code in order. At the top of this file, `someNumber` was defined. JavaScript first checks for a definition inside the `if` code block when `someNumber` is referenced. JavaScript notes that it is not defined inside the block, therefore the next step is to looks up to next code block level, which is the file level in this case. Finally, it will look for the value in the global scope. If it can't find a definition, it will throw an error. In this case, it is found so it can determine the value.

If you change the order, you will get an error because `someNumber` only gets defined after the `if` code block has been executed.

```js
if (someNumber === 10) {
  console.log(`The number is equal to ten! The value is ${someNumber}`);
}

const someNumber = 10;
// ReferenceError: Cannot access 'someNumber' before initialization
```

Additionally, if you declare the same variable inside a code block, you can end up with the same variable name existing in two different places with two different values.

```js
const someNumber = 10;

if (someNumber === 10) {
  const someNumber = 555;
  console.log(
    `The outside number is equal to ten! The value of someNumber inside the code block is ${someNumber}` // 555
  );
}
console.log(`The value of someNumber outside the of block is ${someNumber}`); // 10
```

## Organizing code

Sometimes it is useful to have a value be global (within a file). For example, if you are going to be working with conversions, some constant values are useful to have in one place and not have to define them over and over again:

```js
const poundsToKg = 0.45;
const kgToPounds = 2.2;

function convertPoundsToKg(weight) {
  console.log(`Your item weighs ${poundsToKg * weight}kg`);
  if (poundsToKg * weight < 10) {
    console.log(`Your item weighs under 10kg. Congrats! We can ship it!`);
  } else {
    console.log(`Your item weighs over 10kg. Sorry! We can't ship it!`);
  }
}

convertPoundsToKg(2);
convertPoundsToKg(25);
```

There are other times when you may not want a variable to be global, but you would wish multiple code blocks to access the value.

The following code will throw an error. Can you identify what is wrong and fix it?

```js
const poundsToKg = 0.45;
const kgToPounds = 2.2;

function convertPoundsToKg(weight) {
  console.log(`Your item weighs ${poundsToKg * weight}kg`);
  if (poundsToKg * weight < 10) {
    let shipping = true;
  } else {
    let shipping = false;
  }
  if (shipping) {
    console.log(`Your item weighs under 10kg. Congrats! We can ship it!`);
  }
}

convertPoundsToKg(2);
convertPoundsToKg(25);
```

The variable `shipping` only exists inside the `if/else` blocks. If you want to reuse it, you must declare that variable in the next highest scope so that the following blocks that need access can use the value.

```js
const poundsToKg = 0.45;
const kgToPounds = 2.2;

function convertPoundsToKg(weight) {
  let shipping;
  console.log(`Your item weighs ${poundsToKg * weight}kg`);
  if (poundsToKg * weight > 10) {
    shipping = false;
  } else {
    shipping = true;
  }
  if (shipping) {
    console.log(`Your item weighs under 10kg. Congrats! We can ship it!`);
  }
}

convertPoundsToKg(2);
convertPoundsToKg(25);
```

What would happen if you had defined `shipping` outside of the function. Would this have been a better choice? Why or why not?

Scope is fairly challenging to master. It takes a lot of trial and error and practice. Over time you'll gain a better understanding.
