# Control Flow

## Introduction

If it's raining outside, do you change what you wear? What about if it's sweltering outside?

We all make decisions based on data. For example, if you're feeling exhausted, you might not exercise in the morning. But if you haven't exercised in a while, you may decide that you'll have to push through! These decisions can be mirrored with code. This makes code powerful because it can mimic and solve real-world problems without human intervention.

The challenges of learning to code involve learning to:

- Problem solve in small, well-defined steps.
- Learning to solve problems the way computers solve problems.
- Learning to combine all the concepts to build elegant solutions.
- Learning to cope with the feelings that come with slowly building these skills.

It takes time to build all these skills, but with consistent practice, you'll build these skills. Don't worry if things don't click right away. It is normal for everything to come together over days, weeks or even months and sometimes years.

## Learning Objectives

- Learn how to use and evaluate boolean expressions
- Understand how truthy and falsy values are used with if/else statements
- Understand how truthy and falsy values are used with `if` statements.
- Describe how curly braces often signify a code block in JavaScript and why it is important.
- Control the flow of programs to solve real-world problems.

<hr>

## Boolean operators and expressions

Booleans can only have two values: `true` or `false`

You can combine boolean values to create expressions.

For example, when deciding to wear a coat outside, you likely want to determine whether the weather is below a specific temperature or it is raining. The same kinds of more complicated logic need to be created with code.

#### And `&&`

For an expression to be true with the `and` operator, both sides must be true:

```js
> true && true
true
```

```js
> true && false
false
```

```js
> false && false
false
```

#### Or `||`

For an expression to be true with the `or` operator, one side must be true:

```js
> true || true
true
```

```js
> true || false
true
```

```js
> false || false
false
```

## Truthy and falsy values

While there are only two boolean values, other values (strings, numbers) can have a truthy or falsy value associated with them.

For example, the number 0 is falsy:

```js
// You should NOT see this console.log
if (0) {
  console.log("This value is not truthy");
}
```

You can also use the not operator to get the opposite value evaluated:

```js
// You should see this console.log
if (!0) {
  console.log("This value is truthy");
}
```

Most values in JavaScript are truthy. Here is are some common ones that are falsy:

- `0`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

If you are not sure if a value is truthy or falsy you have two options.

You can test it by using two `!!`

```js
console.log(!!0);
// false
console.log(!!1);
// true
```

Or you can look at a truth table. The following [table](https://dorey.github.io/JavaScript-Equality-Table/) has three tabs:

- Loose equality (does not check whether the type of data is the same, in this case `"3" == 3` is true).
- Strict equality(checks whether the type of data is the same, in this case `"3" == 3` is false).
- if statement evaluations (determines if the code in the block should run or not).

## Conditional code

Look at the following pseudocode, which describes what you might do when you feel hungry.

```
If there is food
 And I'm very hungry
 Eat a meal.
 If I'm just a little hungry
 Eat a snack.
 If I'm not hungry at all.
 Do not eat anything.
Otherwise,
 Do not eat anything.
```

There are a few potential outcomes for this algorithm:

1. You eat a meal.
1. You eat a snack.
1. You eat nothing at all.

Each of the above outcomes is dependent on two different conditions:

1. Whether or not there is food.
1. How hungry you are.

The first case is described as either being true or false. Either there is food, or there is not. The second case is defined as more of a range. There are three possible conditions: very hungry, a little hungry, or not hungry.

It's possible to mirror this kind of algorithm in code through special syntax that will control program flow and, thereby, the output.

## If and else

The most common syntax to use in JavaScript to manage the flow of this kind of algorithm is the `if/else` statement. In general, these statements are structured like the code below.

```js
if (/* An expression that is evaluated as true or false. */) {
 // Do something.
} else if (/* Another expression that is evaluated to true or false. */) {
 // Do something different.
} else {
 // Do something else.
}
```

The code above has three conditions:

1. The `if` keyword is followed by parenthesis, where an expression will be. If that expression is truthy, the code inside the curly braces (i.e. `{}`) will be executed.
1. _If and only if_ the previous expression is falsy, the second expression after the `else if` keywords will be run. If that expression is true, the code inside the curly braces will be executed.
1. _If and only if both of the previous expressions are falsy,_ will the code after `else` be run.

The example below includes the code that will run.

```js
const temperatureInFahrenheit = 70;

if (temperatureInFahrenheit <= 32) {
  console.log("It's freezing cold!");
} else if (temperatureInFahrenheit <= 50) {
  console.log("It's pretty cold outside!");
} else if (temperatureInFahrenheit <= 65) {
  console.log("It might be a bit chilly out today.");
} else if (temperatureInFahrenheit <= 80) {
  console.log("Wow, it is really warm today!");
} else {
  console.log("It's so hot!");
}
```

Different statements will be logged in the code above depending on the temperature. When `temperatureInFahrenheit` is `70`, the statement `"Wow, it is hot today!"` will be printed. As the `temperatureInFahrenheit` changes, so too will the output.

| Input | Output Statement                    |
| ----- | ----------------------------------- |
| 70    | Wow, it is hot today!               |
| 55    | It might be a bit chilly out today. |
| 33    | It's pretty cold outside!           |
| -4    | It's freezing cold!                 |
| 86    | It's so hot!                        |

### Optional parts

The `if/else if/else` syntax is very flexible. While the `if` keyword is required, the other keywords are optional. For example, all of the code below is valid.

```js
const temperatureInFahrenheit = 70;

if (temperatureInFahrenheit > 68) {
  console.log("It's warm out today.");
} else {
  console.log("It's cold out today.");
}

if (temperatureInFahrenheit > 90) {
  console.log("Actually, it's really hot!");
}
```

The above code also allows for multiple conditions to be met. For example, in the case above, if `temperatureInFahrenheit` had a value of `91`, two messages would be logged out.

## Code blocks

The `if/else` keywords should be followed by curly braces. Inside these curly braces is where you can write the code you want to run _if and only if_ the condition inside the parenthesis is met.

```js
const temperatureInFahrenheit = 29;
if (temperatureInFahrenheit < 32) {
  console.log("It's so cold out!");
}
```

The content inside of the curly braces is often referred to as a code block. When you come across syntax that provides a code block, you can always write more code inside of it. This means you're not just limited to one line of code.

```js
const temperatureInFahrenheit = 29;
if (temperatureInFahrenheit < 32) {
  console.log("It is currently " + temperatureInFahrenheit + "°F outside.");
  console.log("It's so cold out!");
}
```

### Nested cases

It is also possible to place an `if/else` inside another `if/else` statement by placing the code inside the code block.

```js
const temperatureInFahrenheit = 29;
if (temperatureInFahrenheit < 68) {
  console.log("It's so cold out!");
  if (temperatureInFahrenheit < 32) {
    console.log("I mean, REALLY cold out!");
  }
} else {
  console.log("It's nice and warm out!");
  if (temperatureInFahrenheit > 78) {
    console.log("Well, maybe a bit too warm!");
  }
}
```

The code above will print one or two statements, depending on the temperature value.

## Solving real problems

Think back to the problem presented at the beginning of this lesson, copied once again below.

```
If there is food
 And I'm very hungry
 Eat a meal.
 If I'm just a little hungry
 Eat a snack.
 If I'm not hungry at all.
 Do not eat anything.
Otherwise,
 Do not eat anything.
```

How can this pseudocode be translated into code?

While there are many ways to approach this problem, the following is a good series of questions to ask:

1. What are the potential inputs?
1. What are the potential outputs?
1. How, if at all, are the inputs related to the outputs?

Keeping the above in mind, each question has been answered below.

### What are the potential inputs?

In the pseudocode, the only inputs are whether or not there is food and whether or not the person is hungry. Therefore, you might consider creating two variables that capture this information.

```js
const hasFood = true; // Could also be `false`.
const isHungry = "very"; // Could also be `"a little"` or `"not at all"`.
```

Determining the inputs _and their possible values_ will help with the next step.

### What are the potential outputs?

There are only three potential outputs, as described previously.

1. You eat a meal.
1. You eat a snack.
1. You eat nothing at all.

The pseudocode above does not describe what, programmatically, "eating a snack" looks like. For this example, the correct statement could just be logged.

### How, if at all, are the inputs related to the outputs?

This means following along with the logic of the pseudocode. Depending on the values of `hasFood` and `isHungry`, something different will be printed on the console. The table below shows the potential input and output combinations.

| `hasFood` | `isHungry`     | Output       |
| --------- | -------------- | ------------ |
| `false`   | `"not at all"` | Eat nothing. |
| `false`   | `"a little"`   | Eat nothing. |
| `false`   | `"very"`       | Eat nothing. |
| `true`    | `"not at all"` | Eat nothing. |
| `true`    | `"a little"`   | Eat a snack. |
| `true`    | `"very"`       | Eat a meal.  |

Looking at the table above, it's possible to deduce the following:

- If there is no food (i.e., `hasFood` is `false`), the value of `isHungry` does not matter. The result will always be to eat nothing.
- If there is food, what happens is wholly dependent on the value of `isHungry`.

### Solution

You can craft a coding solution for this challenge with the information above. Since the `hasFood` variable determines a lot of what can happen, it might make sense to start with that.

```js
if (hasFood) {
} else {
}
```

If `hasFood` is `false`, no food will be eaten.

```js
if (hasFood) {
} else {
  console.log("Eat nothing.");
}
```

Next, another `if/else` statement can be added within the first code block. This will be dependent on `isHungry`.

```js
if (hasFood) {
  if (isHungry === "very") {
    console.log("Eat a meal.");
  } else if (isHungry === "a little") {
    console.log("Eat a snack.");
  } else if (isHungry === "not at all") {
    console.log("Eat nothing.");
  }
} else {
  console.log("Eat nothing.");
}
```

At this point, upon running the code, you can see that the variables will now control the flow of the program.

> **Note:** The code above doesn't account for every case! For example, if `isHungry` were set to a value that is not accounted for, like `"somewhat"`, nothing would be logged out. Do you think this means the algorithm is working or not?

## Comparing strings

Let's look at a simple example. First predict what the answer would be. Will it be a syntax error or something else? Try to think of a reason why you think one answer is more likely. Thinking things through before you code and determining what you expect to happen will help you become better at writing and debugging code.

```js
if ("McDonald's" > "Burger King") {
  console.log("McDonald's is better");
} else {
  console.log("Burger King is the best");
}
```

Experimentation with code is encouraged. If you have a question about how the code works, first test it on your own. Make up your own examples and play around. Then look up an answer. When you know what the behavior of the code will be, you will be more likely to understand why the code does what it does. A lot of education experiences encourage you to "learn everything first" and then apply it. But with coding, you'll go back and forth between learning something and working with it to increase your skills and knowledge.
