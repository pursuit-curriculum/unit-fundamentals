# Arrays

## Introduction

Imagine you have a grocery list and want to write a program so you can see your grocery list on your phone instead of on paper, and then you want to be able to add, delete, and modify items on the list. How could you do it with code? Would you use a string? A number? A boolean? None of these data types make sense for a grocery list. We need new datatype called an array that will allow us to store many items in one place.

## Learning Objectives

- Define what an array is and describe its properties.
- Create arrays with the array literal syntax.
- Access elements in an array through bracket notation.
- Add elements to an array with the bracket notation.
- Update values in an array with the bracket notation.
- Use methods to add and remove elements to the back and front of an array.
- Iterate over an array
- Combine functions, conditionals, loops and arrays.

<hr>

## Introduction to Arrays

An array is a data structure, and you can assign it to a variable like a number or string. Let's begin by creating an empty array:

```js
const myArray = [];

console.log(myArray);
```

Arrays have a property called `length`. You can access this property at any time by adding `.length` to the end of the array.

```js
console.log(myArray.length);
```

Arrays contain elements that are separated by commas `,`. The elements can be any datatype: strings, numbers, booleans, or even another array! Though typically, elements in an array are all the same datatype.

```js
const squares = [1, 4, 9, 16, 25];
```

Let's imagine an adventurer named Rynn. Rynn has a magic backpack that can hold everything they need for their adventures.

```js
const backpack = [
  "boomerang",
  "map",
  "candle",
  "tent",
  "Tums",
  "hair clip",
  "coin pouch",
];

console.log(backpack);
```

## Accessing elements in an array

Above, we created an array and could console log the whole thing. How can we access one item? Each item in the array has a numbered `index` position. The first element in an array has an index of `0`.

To access an element in an array, you put the index position inside square brackets `[]`.

```js
console.log(backpack[0]);
// "boomerang"
console.log(backpack[2]);
// "candle"
```

What happens if you try to access something in an index position that doesn't exist?

```js
console.log(backpack[333]);
```

You can use expressions between the square brackets to access array elements:

```js
console.log(backpack[3 * 1 - 2]);
// "map"
```

And you can use variables:

```js
const index = 4;

console.log(backpack[index]);
// "Tums"
```

How can you always get the last item in an array? Arrays can be any length, and the length can change over the duration of your program.

Setting up a value that can change based on data is referred to as `dynamic`. A value that never changes is usually referred to as `static`. When you write code that does not change with the data it can also be referred to as `hard-coded`.

```js
const lastItem = backpack.length - 1;

console.log(backpack[lastItem]);
```

Why is the last value at `.length - 1` and not just `.length`?

## Changing elements

You can change an element in the array by accessing the index position and reassigning it:

```js
backpack[2] = "solar powered super lantern";

console.log(backpack);
```

You can also add an element to the end of an array.

```js
backpack[backpack.length] = "fierce kitten";

console.log(backpack);
```

## Iterating over an array

Use a `for` loop to iterate over all the items in an array.

```js
for (let i = 0; i < backpack.length; i++) {
  console.log(
    `I take out my ${backpack[i]}. I clean it and carefully put it back.`
  );
}

// I take out my boomerang. I clean it and carefully put it back.
// I take out my map. I clean it and carefully put it back.
// I take out my solar-powered super lantern. I clean it and carefully put it back.
// I take out my tent. I clean it and carefully put it back.
// I take out my Tums. I clean it and carefully put it back.
// I take out my hair clip. I clean it and carefully put it back.
// I take out my kitten food. I clean it and carefully put it back.
// I take out my coin pouch. I clean it and carefully put it back.
// I take out my fierce kitten. I clean it and carefully put it back.
```

You can also iterate with a different number of steps:

```js
for (let i = 1; i < backpack.length; i += 2) {
  console.log(`A rouge is trying to steal my ${backpack[i]}!!!`);
}
// A rogue is trying to steal my map!!!
// A rogue is trying to steal my tent!!!
// A rogue is trying to steal my hair clip!!!
// A rogue is trying to steal my coin pouch!!!
```

You can combine loops, arrays, and conditionals.

```js
for (let i = 0; i < backpack.length; i++) {
  if (i % 3 === 0) {
    console.log("A lovely sprite has enchanted my " + backpack[i] + ".");
  }
}

// A lovely sprite has enchanted my boomerang.
// A lovely sprite has enchanted my tent.
// A lovely sprite has enchanted my kitten food.
```

You can include more complex conditionals.

```js
for (let i = 0; i < backpack.length; i++) {
  if (i === 5 || (i % 2 === 0 && i !== 8)) {
    console.log("A sneaky elf has set fire to my " + backpack[i] + "!");
  }
}

// A sneaky elf has set fire to my Tums!
// A sneaky elf has set fire to my hair clip!
// A sneaky elf has set fire to my kitten food!
```

## Putting it all together

Finally, you can combine everything with a function.

```js
function checkContents(array, favNumber = 0) {
  console.log(`I have ${array.length} items in my backpack`);
  for (let i = 0; i < array.length; i++) {
    if (array[i] === "map") {
      console.log("I love my map");
    } else if (array[i] === "tent") {
      console.log("I love sleeping in my tent");
    } else {
      console.log(`I have accounted for my ${array[i]}`);
    }

    if (i == favNumber) {
      console.log(`${array[i]} is my favorite item.`);
    }
  }
}

checkContents(backpack);
checkContents(backpack, 8);
```

Before running the above code, write out what you think the output will be. Taking the time to make a hypothesis about the outcome and then comparing and contrasting your expectations and results will help you understand the code better and how to fix any unexpected results.

## Accessing a value when an array is inside another array

```js
const orders = [
  ["fish", "chips"],
  ["pancakes", "coffee"],
];
```

Access the first array
```js
console.log(orders[0]);
```

Access the second item in the first array

```js
console.log(orders[0][1]);
```

## An array's type

If you use `typeof` on an array you will get...

```js
const shortNumberArray = [1, 2, 3];
console.log(typeof shortNumberArray);
// object
```

An object! We will cover objects in a later lesson and explore why an array has a type of object.

In the meantime, if you want to check if something is an array, there is a method:

```js
const shortNumberArray = [1, 2, 3];
console.log(typeof shortNumberArray);
// object
console.log(Array.isArray(shortNumberArray));
// true
```

## JSDoc array notation

An array can be made up of numbers, strings, booleans and more. When commenting with JS Docs, you would write the type of element in the array and then follow it with square brackets.

```js
/**
 * Examples of how to note arrays with different data types
 * @param {string[]} employees - The employee's names, which are strings
 * @param {number[]} employeesAges - The employee's ages, which are numbers
 * @param {boolean[]} employeesCurrentlyOnVacation - The employee's status (boolean), whether they are currently on vacation
 * @param {(string|string[])} loanedEquipment - this value could either be a string or an array of strings.
 * @param {(string[])} [otherNames = "none" ]- this value has a default value of none.
 */
```

[JS Doc params examples](https://jsdoc.app/tags-param.html)
