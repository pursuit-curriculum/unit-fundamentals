# Common Methods and Tools

## Introduction

Now that you've been introduced to fundamentals, you can combine what you know to solve more exciting challenges.

However, you'll also encounter some really common problems, like converting a string into a number, making all lowercase letters capital, or removing the first item from an array that would be quite tedious to create and re-create over and over again for your coding projects.

JavaScript has many built-in methods that will provide you with some handy functionality.

The best way to learn built-in methods is to learn about a small number of them: figure out how they work, how to use the documentation, and learn how to google for what you need. You don't need to memorize all the methods. You will naturally begin to memorize some of the ones you use most often. For the ones you use less frequently, it's totally ok to look them up.

> **Note**: When a function belongs to a group of functions, it is usually referred to as a `method`. You can tell it belongs to a group, because the syntax is `.someMethod()`, for example, `"hello".toUpperCase()`. This is in contrast to a function which is usually written as `someFunction()`, for example, `Math.floor()`.

## Learning Objectives

- Be able to describe why JavaScript has built-in methods and tools.
- Use resources like MDN or W3 schools to look up methods and implement them to solve coding problems.
- Understand how to copy, reference and modify a code resource.
- Be able to name a few names and functionality common built-in methods for numbers, strings, and arrays.

## Number methods

### Number()

You have a number with a type of string: "33". How can you convert it to a number?

You can use the [Number()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) function:

```js
let myNumber = "33";
myNumber = Number(myNumber);
console.log(myNumber, typeof myNumber);
Math.random();
```

If you want a random number, you can use the [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)method:

```js
console.log(Math.random());
```

`Math.random()` will give you a floating point number between 0 and 1. How could you do it if you want the range of random numbers to be between (and including) 1 and 10?

Start with the documentation for [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random).

After the introduction is some headers for different number ranges. Find [Getting a random integer between two values, inclusive](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random#getting_a_random_integer_between_two_values_inclusive).

You can copy the function provided, then add a comment of where you found this code, and then modify it to be your own:

Adding a comment about where you found helpful information will be useful when you want to find the same resource. Googling can bring up different examples after a few weeks or months, and you might be sad you can't find the great resource you once used. Additionally, adding a comment lets your instructor see how you've worked on the solution and can give you more meaningful feedback:

```js
// Original function from:
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random#getting_a_random_integer_between_two_values_inclusive

// Get a random number with a range of 1 to 10
// Add min = 1 and max = 10 to be the defaults
function getRandomInt(min = 1, max = 10) {
  return Math.floor(Math.random() * (max - min + 1) + min);
  // The maximum is inclusive, and the minimum is inclusive
}

// Run this a few times to confirm you are getting all the numbers
console.log(getRandomInt());
// Try with a different range:
// console.log(getRandomInt(0, 2));
```

### How to copy code examples and use them correctly

You might be asking - is it ok to copy code? The answer is "yes, but..."

One way developers learn is by copying and modifying code. There are a few things to keep in mind.

When you copy code:

- Provide where you got it from. If a classmate helped you, give them credit as well.
- Only copy small bits of code that fit your specific project. Don't copy someone else's whole project then change a few words and say it is yours - this is plagiarism.
- Be ready to explain every line of code you copied.
- Be sure to modify it and add comments that suit your needs to make it your own.

For this course, the code you copy must represent your current technical ability. If you are stuck or feeling behind, reach out to an instructor. Remember, the ultimate goal of this program is for you to pass a coding interview and get a job as a developer. Therefore you must be able to demonstrate the skills and abilities that you've learned. Submitting work you don't understand to "get it done" will not help you attain your goal.

It's also important to note that your early code will be messy, have issues like having too many variables, and your solutions will be inelegant. It can feel tempting to get code that looks better, but if you can't explain what the other code does, it won't help you build your skills. So it's better to write and share the code you have written and get feedback. Like someone who has begun to learn to paint, your early work will be rough. That's ok! With practice, you'll gain speed, efficiency, and elegance.

## String methods

### .toUpperCase()

You can make all your text capital letters using a string method.

Google for and then look at the documentation at MDN. First, you may notice that this method says `String.prototype.toUpperCase()`. When you see this syntax (with `prototype` in the middle), you can attach the function to your value. This is in contrast to the Math method, where you have to start with the word `Math` and then add `.something()`. You'll learn more about the keyword prototype later in the course.

As you read the documentation, there are a few sections. They generally show a pattern that shows a demo, then the syntax and some other sections that may or may not have the information you are looking for. Finding what you need in documentation is a skill you'll build over time.

Let's look at the code below, and before running it, take a moment to think about the output. What will happen to the comma and period? Will the code error be because of these characters? Then run the code and compare and contrast what you thought would happen with what did happen. This process will help you gain understanding and learn to use new methods faster and better.

```js
const pangram = "When zombies arrive, quickly fax judge Pat.";

console.log(pangram.toUpperCase());
```

### .replace() and .replaceAll()

You can replace some text using the `.replace()` method. Let's say you want to change the text `To be or not to be` to read `To code or not to code`.

Let's look at [the documentation.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#syntax)

What this method shows is that it takes two parameters `pattern` and `replacement`. What do those words mean? Please take a moment to put it in your own words.

Let's look at the code below:

```js
let myQuote = `To be or not to be`;
myQuote = myQuote.replace("be", "code");
console.log(myQuote);
// To code or not to be
```

The `.replace()` method goes after your value of `myQuote`. However, this one only changed the first `be`. Your next move would be to look and see if another method fits your needs or to google how to do what you want to do.

In this case, there is another method that will change all the instances.

```js
myCompleteQuote = myQuote.replaceAll("be", "code");
console.log(myCompleteQuote);
// To code or not to code
```

### .split()

Here is another string method where you can split the string into an array. `.split()` takes one argument, the character you want to split the words apart with. If you wish to split every letter individually, you will put an empty string. However, if you want every word as an array item, you would pass a quoted space.

Using empty string:

```js
const stringToArray = "The quick brown fox jumped over the lazy dog";
console.log(stringToArray.split(""));
// [
// 'T', 'h', 'e', ' ', 'q', 'u', 'i',
// 'c', 'k', ' ', 'b', 'r', 'o', 'w',
// 'n', ' ', 'f', 'o', 'x', ' ', 'j',
// 'u', 'm', 'p', 'e', 'd', ' ', 'o',
// 'v', 'e', 'r', ' ', 't', 'h', 'e',
// ' ', 'l', 'a', 'z', 'y', ' ', 'd',
// 'o', 'g'
// ]
```

Using a space:

```js
console.log(stringToArray.split(" "));
// [
// 'The', 'quick',
// 'brown', 'fox',
// 'jumped', 'over',
// 'the', 'lazy',
// 'dog'
// ]
```

## Array Methods

Modifying an array with methods
Let's return to our previous array example and explore some array methods;

```js
const backpack = [
  "boomerang",
  "map",
  "candle",
  "tent",
  "Tums",
  "hairclip",
  "coin pouch",
];

console.log(backpack);
```

## .pop()

You can remove the last item by using a method called `.pop()`.

```js
backpack.pop();
console.log(backpack);
```

## .push()

And add an item to the end by using a method called .push().
What is notable about the .push() method is that it can take a minimum of one argument to an unlimited number of arguments. Let's look at the syntax from the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push#syntax).

The document demonstrates adding one element, then two, and finally, the `/* ..., */ , elementN` represents that you can continue to add any number of arguments.

```js
push(element0);
push(element0, element1);
push(element0, element1, /* … ,*/ elementN);
```

For now, add just one item to the backpack:

```js
backpack.push("clowder of fierce kittens");
console.log(backpack);
```

### .shift()

You can remove the first item of the array using a method called .`shift()`.

```js
backpack.shift();
console.log(backpack);
```

### .unshift()

You can add an item to the front of the array using a method called
`.unshift()`.

```js
backpack.unshift("bedazzled boomerang");
console.log(backpack);
```

### .slice()

You can also slice your array using the `.slice()` method. In the documentation for `.slice()`, you can see that `.slice()` can take either none, one, or two arguments. It is important to note that regardless of the number of arguments, you must always put them in the same order.

Take the first two items and put them in a new array. The first parameter is the starting position, and the second parameter is the last index position (up to, but not including). Notice that the original array stays the same.

```js
const newBackpack = backpack.slice(0, 2);
console.log(newBackpack);
console.log(backpack);
```

What do you think `.slice()` with no arguments returns? How could you test it?

### .splice()

You can add elements to the middle of your array with the `.splice()` method. The first parameter is the index position where to insert (or remove), the second parameter is how many items to remove (in this case, none), and the last one is what to insert.

```js
backpack.splice(6, 0, "kitten food");
console.log(backpack);
```

Notice that unlike `.slice()`, `.splice()` does change the original array.

### .join()

Finally, you can convert an array into a string. Like the string `.split()` method, you must provide an argument that is a string to provide how the array should be joined.

Join with a space:

```js
const pangramArray = [
  "Amazingly",
  "few",
  "discotheques",
  "provide",
  "jukeboxes.",
];
const pangramString = pangramArray.join(" ");
console.log(pangramString);
// Amazingly few discotheques provide jukeboxes.
```

Join with three `*`:

```js
const starryPangramString = pangramArray.join("***");
console.log(starryPangramString);
// Amazingly***few***discotheques***provide***jukeboxes.
```
