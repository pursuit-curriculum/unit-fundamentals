# Problem Solving with Code Part 1

## Learning Objectives

By the end of this lesson you should be able to:

- Implement Polya's on coding challenges.

---

## Guiding Questions

Let's write a function to reverse a string.

Let's use Polya's Problem Solving Methodology

- Do you understand all the words used in stating the problem?

- What are you asked to find or show?

- Can you restate the problem in your own words (this problem may be too simple to reword. That's ok!)

- Can you think of a picture or diagram that might help you understand the problem?

- Is there enough information to enable you to find a solution?

Once you have put together your strategy, build the most basic function and test it:

```js
const testCase = "reverse this string";
const testCase2 = "Was it a car or a cat I saw?";

function reverseString(str) {
  return str;
}

console.log(reverseString(testCase));
console.log(reverseString(testCase2));
```

After coming up with your own solution with the class, compare and contrast the different versions.

What do you think of the test cases? Are they good? Would you add or replace any of them?

<details><summary>One solution</summary>

- Create a new array that will hold the letters in reverse
- Write a for loop that will take each letter and put it into the new array from the last letter to the first
- Join the array back to a string

```js
function reverseString(str) {
  const reversedArray = [];
  for (let i = str.length - 1; i >= 0; i--) {
    reversedArray.push(str[i]);
  }
  const reversedString = reversedArray.join("");
  return reversedString;
}
```

<hr>

</details>

<details><summary>Second solution</summary>

- Create a new array that will hold the letters in reverse
- Use the array method reverse
- Join the array back to a string

```js
function reverseString(str) {
  const reversedArray = str.split("");
  reversedArray.reverse();
  const reversedString = reversedArray.join("");
  return reversedString;
}
```

Can we make this solution more succinct? Let's chain two methods.

```js
function reverseString(str) {
  const reversedArray = str.split("").reverse();
  const reversedString = reversedArray.join("");
  return reversedString;
}
```

Let's chain three methods.

```js
function reverseString(str) {
  const reversedString = str.split("").reverse().join("");
  return reversedString;
}
```

Let's return the value right away instead of saving it to a variable.

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}
```

Notice that we started with a long version and made sure it worked. Then we went back and shortened the solution. This is totally ok!

<hr>

</details>

- Is one better than the others? Why or why not?

- What makes a good solution?

- What makes a bad solution?

- What makes code good or bad in terms of working on big project with a team?
