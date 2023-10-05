# Binary Search

## Introduction

Have you ever thought about how often you search for things online? Chances are, you do it quite frequently. Searching is a standard feature on websites and computer programs, and a wide range of algorithms are designed to optimize various types of searches.

When deciding on a search algorithm, one critical factor is the state of your data—whether it's sorted or not. Binary search, for instance, is a robust algorithm that requires the data to be sorted beforehand to work effectively. This makes it ideal for efficiently finding items in large, sorted datasets, saving time and resources.

Another popular search algorithm is linear search, where the algorithm goes through each item in the data, one by one until it finds the desired item or reaches the end of the list. This is useful when the data is not sorted or when you need to search a small dataset, as it's simple and easy to implement.

Hash-based search algorithms, like hash tables, offer a balance of speed and efficiency by associating keys with values using a hash function. This enables quick data retrieval, making them ideal for applications like databases, caches, and in-memory data stores.

Search trees, such as the B-tree, provide an efficient solution in scenarios where the data constantly changes or needs frequent updates. B-trees are balanced tree structures that enable efficient search, insertion, and deletion of data, making them suitable for file systems and databases.

Understanding these different search algorithms and their appropriate use cases can significantly enhance the efficiency and effectiveness of your searches, depending on the nature of the data and the application requirements.

Today's focus will be on binary search.

## Learning Objectives

- Build a binary search algorithm.
- Identify the Big O of binary search and describe why it is so efficient.
- Identify situations where binary search can be applied to solve a problem.

<hr>

## Searching for a number

Let's build a simple guessing game that allows the computer to choose a random one. As you guess a number, the computer will tell you whether the answer is higher or lower. In this game, the numbers are already in order, a critical feature to implement a binary search.

To code along, create an`index.html` file and open it in your browser (type `open index.html` from your terminal) or copy/paste the JavaScript code into Chrome when you are on a blank webpage, or you can also do this at www.example.com. If you need to reset, refresh the page.

> **Note**: The JavaScript code will not work in Repl.it because Repl.it blocks the prompt and alert windows.

```HTML
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Game</title>
    <script src="app.js"></script>
  </head>
  <body>
    <p>Refresh the page to play again</p>
  </body>
</html>
```

```js
// app.js
const gameVersion1 = () => {
  const limit = 128;
  let theNumber = Math.ceil(Math.random() * limit);
  let guess = prompt(`Guess a number between 1 and ${limit}`);
  let count = 0;
  guess = Number(guess);

  while (guess !== theNumber && guess !== 0) {
    console.log(guess);
    if (guess < theNumber) {
      guess = prompt(`Too low! Guess again!`);
    } else {
      guess = prompt(`Too high! Guess again!`);
    }
    guess = Number(guess);
    count++;
  }
  if (guess === 0) {
    alert(
      `You chose to quit. The number was ${theNumber}. Please play again soon!`
    );
  } else {
    alert(
      `That's right! The number was ${theNumber}. You made ${count} guesses`
    );
  }
};
```

Play this game a few times. What is your method for finding the correct number?

Try to write it down in pseudo-code.

Now, try to code an answer.

Here is a naive coding solution. But it will always be the worst-case scenario - the last guess will always be correct. That means it would take a while if this guessing game were between 1 and 100 million. What is the Big O for this algorithm?

> **Note**: Since this code guesses the solution for you, you can just run it in Node.js or open the dev console in the browser.

Now that the computer is guessing and we don't need user input, we'll use `console.log` instead.

```js
const gameVersion2 = (limit = 128) => {
  let theNumber = Math.ceil(Math.random() * limit);

  let guess = 0;

  while (guess !== theNumber) {
    if (guess < theNumber) {
      console.log(`Too low! Guess again!`);
      guess++;
    } else {
      console.log(`Too high! Guess again!`);
      guess--;
    }
  }
  console.log(
    `That's right! The number was ${theNumber}. The number of guesses was ${guess}`
  );
};
```

You will need 128 guesses always to be sure you get the correct guess.

How close is this solution to the one you used when trying it yourself? If it matched what you tried, can you think of another way?

Try to code your approach if it isn't how you approached it.

## Binary search

You likely devised an algorithm when guessing a number from 1 to 128 to start with the middle number, 64.

- When you found out the number was lower than 64, your next guess would be the middle number of that range, 32.

- When you discovered the number was lower than 32, your next guess would be the middle number of that range, 16.

- When you find out that the number was higher than 16, you are looking at a range of 17 to 31.

- Again, you would guess the middle number: 24. Let's say this was the number you were looking for.

Each iteration of the algorithm cuts down the number of possibilities by half.

So, how many guesses would it take to be enough guesses always to find the answer?

```
128/2 = 64
64/2  = 32
32/2  = 16
16/2  = 8
8/2   = 4
4/2   = 2
2/ 2  = 1

```

That's seven guesses. Seven is much better than the naive approach (which would take 128 guesses to ensure you can get the correct answer). This vast improvement is what makes the binary search so important.

## Visualizing binary search

Let's say you are looking up a word in a dictionary: `inconceivable`

First, you would go to the middle of all the words (remember, they are already alphabetized). Let's say that the middle word is `luminous`. `luminous` comes after `inconceivable`. Therefore, you no longer need to search any words that come after it. You can eliminate every word from `luminous` through words starting with `z`.

Next, you would find the middle word from the range of `a` to `l`. Let's imagine it is `formidable`. `formidable` comes before `inconceivable`, so you can remove all the words from a to `formidable`.

Next, you will be looking for all the words between `formidable` and `luminous`.

And you would continue looking through smaller and smaller sets, until you find `inconceivable`.

![binary search](./assets/binary-search.png)

## Binary search in terms of code

It will have to be set up a little differently to play the guessing game. There will be two functions.

First, set up the main game, notice the guesses are between 1 and 1000. Can you determine the maximum number of guesses required for the correct answer? The counter is set to 10. How often will the automatic guessing function 'win'?

```js
const game = () => {
  let start = 1;
  let limit = 1000;
  let midpoint = 0;
  let number = Math.ceil(Math.random() * limit);
  let values = {
    start,
    limit,
    midpoint,
  };

  let counter = 1;
  while (values.midpoint !== number && counter <= 10) {
    if (values.midpoint > number) {
      values = myAutomaticGuesser(values, true);
    } else if (values.midpoint < number) {
      values = myAutomaticGuesser(values, false);
    }
    counter++;
  }

  if (counter <= 11) {
    console.log(
      `That's right! The number was ${number} and the number of guesses was ${
        counter - 1
      }`
    );
  } else {
    console.log(`Sorry, out of guesses! The number was ${number}`);
  }
};
```

The following function is going to use the binary search algorithm:

```js
const myAutomaticGuesser = ({ start, midpoint, limit }, tooHigh) => {
  if (tooHigh) {
    if (midpoint === 2) midpoint = 1;
    limit = midpoint;
    midpoint = limit - Math.floor((limit - start) / 2);
  } else {
    start = midpoint;
    midpoint = limit - Math.floor((limit - start) / 2);
  }
  return { midpoint, start, limit };
};

game();
```

Be sure to play with the code and add console logs and comments to help familiarize yourself with how the algorithm works in terms of code.
