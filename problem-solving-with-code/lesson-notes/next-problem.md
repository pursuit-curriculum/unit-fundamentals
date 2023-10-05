# Problem Solving with Code Part 2

## Learning Objectives

By the end of this lesson you should be able to:

- Implement Polya's on coding challenges.

---

## Guiding Questions

Let's write a function to check if two words are palindromes.

Let's use Polya's Problem Solving Methodology

- Do you understand all the words used in stating the problem?

- What are you asked to find or show?

- Can you restate the problem in your own words?

- Can you think of a picture or diagram that might help you understand the problem?

- Is there enough information to enable you to find a solution?

Once you have put together your strategy, determine some test cases. Then
build the most basic function and test it:

```js
const testCase1 = "racecar";
const testCase2 = "palindrome";
const testCase3 = "Kayak";
const testCase4 = "Mr. Owl ate my metal worm";

function isPalindrome(str) {
  return str;
}

console.log(isPalindrome(testCase1));
console.log(isPalindrome(testCase2));
console.log(isPalindrome(testCase3));
console.log(isPalindrome(testCase4));
```

- Evaluate the given test-cases:

  - `testCase4` is a sentence, not a word. It also has punctuation. This case should be removed as it definitely does not match what the question is asking.
  - Is `palindrome` a good test case? Why or why not?
  - Is `Kayak` with a capital letter a good test-case? Why or why not? How could you get clarification if you were asked this question on a coding interview?

- What value are you returning?

<details><summary>One solution</summary>

- The name of the function `isPalindrome` is like a question and it would make sense that it would return either the value `true` or `false`.
- We need to compare the original string to the reversed string.
- We can use our solution from yesterday for string reverse here.

```js
function isPalindrome(str) {
  const reversedWord = str.split("").reverse().join("");
  const trueOrFalse = reversedWord === str;
  return trueOrFalse;
}
```

How could we get this to work with `Kayak`?

```js
function isPalindrome(str) {
  const reversedWord = str.split("").reverse().join("");
  return reversedWord.toLowerCase() === str.toLowerCase();
}
```

What if we did this?

```js
function isPalindrome(str) {
  return str.toLowerCase().split("").reverse().join("") === str.toLowerCase();
}
```

- It is all one line! Is this good or bad?

<hr>
</details>

<details><summary>Another solution</summary>

- Since we already wrote a string reversing function. Can we use it instead of re-writing the functionality?

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}

function isPalindrome(str) {
  return reverseString(str).toLowerCase() === str.toLowerCase();
}
```

<hr>
</details>

After coming up with your own solution with the class, compare and contrast the different versions. Is one better than the others?

- Why or why not?

- What makes a good solution?

- What makes a bad solution?

- What makes code good or bad in terms of working on big project with a team?
