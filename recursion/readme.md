# Recursion

Imagine you're tasked with solving a complex puzzle, but instead of tackling it all at once, you break it down into smaller, manageable pieces. Each piece, in turn, might have its own intricate details that require further simplification. This process continues until you reach the simplest, most straightforward components, allowing you to assemble the solution piece by piece. Imagine solving a jigsaw puzzle - first you go through each of the jumbled pieces of the puzzle, until you find the corner pieces. Then you search again until you find all the edge pieces and you put them aside. Then you choose one corner piece and find the connecting edge pieces and so on - until you have solved the puzzle.

Recursion is a powerful technique used by programmers to solve complex problems by breaking them down into smaller, similar sub-problems. In this exploration, you'll learn not only the fundamentals of recursion but also gain insights into its strengths and limitations. We'll learn how recursive thinking can transform seemingly intricate challenges into manageable solutions.

## Learning Objectives

By the end of this lesson, you should be able to:

- Identify what recursion is and when it can be helpful to implement.
- Identify the critical components of a recursive function.
- Rewrite algorithms that use loops to use recursion.
- Rewrite algorithms that use recursion to use loops.

---

## What is a recursive function?

Recursion is a programming concept where a function calls itself to solve a problem. It may sound strange, but it's a powerful and elegant approach for tackling complex tasks. When should you use recursion? Here are a few scenarios:

- Tasks that can be broken down into smaller, similar subtasks: When a problem can be divided into identical, smaller sub-problems, recursion is a good choice.

- Tasks that require branching decisions: Recursion is handy when different decisions lead to different sub-problems, like exploring all possible paths in a maze.

A recursive function must have three properties:

1. **A base case or cases.** The base case or cases represents the terminating scenario or scenarios for a function. The base case should not use recursion and should allow for the function to end.

1. **The inductive step.** The remainder of the code within a recursive function is aimed at leading the code to the base case, eventually.

1. **The recursive call.** The function must call itself in order for the function to be recursive.

Without these three properties, recursive functions will run incorrectly or infinitely. Lacking a base case, in particular, is like coding a `while` loop that can never end.

### Adding numbers example

Let's think about adding the following numbers:

```
1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

Average humans do not add all the numbers at once. We add two numbers together, store that number, and then add the following number until we are left with one number. When we have one number, that is our answer.

```
1 + 2 = 3
3 + 3 = 6
6 + 4 = 10
10 + 5 = 15
15 + 6 = 21
21 + 7 = 28
28 + 8 = 36
36 + 9 = 45
45 + 10 = 55
55 + no numbers left means our answer is 55
```

We're going to follow the above problem the same way using recursion. First, since we have a list of numbers, let's express them as an array. Then, let's define our function.

```javascript
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const sumNumbers = (numbers) => {
  // Code will go here.
};

console.log(sumNumbers(array));
```

The first step of reproducing what we manually did is to add the first two numbers together. Let's see what that looks like in code.

```javascript
const sumNumbers = (numbers) => {
  const sum = numbers[0] + numbers[1];

  return sum;
};
```

Now we need to somehow continue the function _by calling the function again._ Let's see what that might look like.

```javascript
const sumNumbers = (numbers) => {
  const sum = numbers[0] + numbers[1];

  return sumNumbers(numbers, sum);
};
```

In the case above, we are now recalling the function and passing our `sum` to the next invocation of that function. However, the function above will not work as we would like. It will only add the first two numbers of the array and will never stop. Let's first address the problem of never adding any other numbers in the array.

```javascript
const sumNumbers = (numbers, sum = 0) => {
  const numberToAdd = numbers.shift();
  sum += numberToAdd;

  return sumNumbers(numbers, sum);
};
```

The function above has several interesting changes:

- A new parameter is added to the function definition, called `sum`. This value is, by default, set to 0.

- The first number of the array is removed via the `.shift()` method. This means the array length will be smaller on future runs of this function.

- The `sum` variable is increased by the previously removed number.

The `sum` variable is now "holding on" to our value as we continue to add more and more to it. However, how can we stop the function from running at the appropriate time? This is where we add our base case.

```javascript
const sumNumbers = (numbers, sum = 0) => {
  // Base case
  if (numbers.length === 0) {
    return sum;
  }

  // Inductive step
  const numberToAdd = numbers.shift();
  sum += numberToAdd;

  // Recursive call
  return sumNumbers(numbers, sum);
};
```

If the `numbers` array is empty, that means the array was either empty to begin with or we've removed every element of the array. We remove elements from the array in the part of the code below the base case. This function now adds all up numbers in an array through recursion.

## Convert between loops and recursion

If you ever are writing a loop, it's likely you can make the function recursive. The same is true when writing recursion -- it can always be a loop instead.

Take a look at the following three functions, all of which countdown from a given number.

```javascript
// for Loop version
function countdownForLoop(n) {
  for (let i = n; i >= 0; i--) {
    console.log(i);
  }
}

countdownForLoop(5);

// while Loop version
function countdownWhileLoop(n) {
  while (n >= 0) {
    console.log(n);
    n = n - 1;
  }
}

countdownWhileLoop(5);

// Recursive version
function countdownRecursive(n) {
  if (n < 0) {
    return; // Base case
  } else {
    console.log(n);
    countdownRecursive(n - 1); // Recursive call
  }
}

countdownRecursive(5);
```

While all functions retain the `console.log()` statement, each are written differently depending on the approach. Notice in particular the similarities between the `while` loop version of the code and the recursive version.

### Why use recursion?

Now that you see you can write recursive functions as loops, you may be wondering what the purpose of recursion is. It's most helpful to think of recursion as another way of expressing an idea as opposed to a tool that will provide any particular benefit. Recursion is about developing an elegant solution as opposed to adding a new feature to your code.

When writing code at a job, recursion should likely only be used if it adds clarity to the function. Many times a simple loop will do.
