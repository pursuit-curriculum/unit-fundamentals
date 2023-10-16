# Programming Principles

Up until this point, you have been solving challenges and building functions in whatever way you can to solve the problem. As a new learner, this is absolutely the right approach. However, as your skills develop, you will want to improve the way you write code so that it follows some clear best practices.

In this chapter, we will explore some fundamental programming principles that every new coder should embrace. These principles can be applied to whenever you are coding and understanding these principles will help you write clean, maintainable, and efficient code.

## Learning Objectives

By the end of this lesson, you should be able to:

- Define the KISS and YAGNI acronyms and how they apply to programming.
- Define the principle of least astonishment.
- Describe what the happy path refers to in programming and why it is useful to focus on first.

---

## Why conventions matter

Before we delve into the programming principles, let's talk about the importance of following conventions. Conventions are like the grammar and syntax of a programming language. Just as good grammar is vital for clear communication, coding conventions are crucial for writing code that is easy to read, understand, and maintain. When you follow conventions, you make your code more predictable, which helps both you and others who might work with your code in the future.

You may have already heard of some key conventions:

- **Naming conventions**. Use meaningful and consistent names for variables, functions, and classes.

- **Formatting**. Indentation, whitespace, and code structure should be consistent throughout your code.

- **Comments**. Write clear and concise comments to explain your code's purpose and functionality.

Now, let's explore some other programming principles and tips that will guide you in writing high-quality JavaScript code.

## KISS - Keep it simple, sweetheart

The KISS principle suggests that simplicity is a virtue in programming. This principle encourages you to write code that is straightforward, without unnecessary complexity. Simple code is easier to understand and maintain even though it may not be as "clever" as a different solution. For example, take a look at the following two code blocks, both of which lead to the same output.

```javascript
// Clear example
function findById(products, id) {
  for (let product of products) {
    if (product.id === id) {
      return product;
    }
  }
  return null;
}

const products = [
  { id: 1, name: "T-Shirt" },
  { id: 2, name: "Jeans" },
  { id: 3, name: "Baseball Cap" },
];
findById(products, 2); //> { id: 2, name: "Jeans" }
```

```javascript
// Unclear example
function findById(p, id) {
  for (let i = 0; i < p.length; i++) if (p[i].id === id) return p[i];
  return null;
}

const products = [
  { id: 1, name: "T-Shirt" },
  { id: 2, name: "Jeans" },
  { id: 3, name: "Baseball Cap" },
];
findById(products, 2); //> { id: 2, name: "Jeans" }
```

Just because the second version of the function is shorter does not mean it's more readable or impressive. In fact, the first option is better because it is more likely to be understood by software developers with a varying level of expertise in JavaScript. Remember, software development is a team activity. Writing code that is simple to understand is often better than clever code.

## YAGNI - You Aren't Gonna Need It

The YAGNI principle advises against adding functionality or features to your code that you don't currently need. Avoid unnecessary complexity, as it can make your code harder to understand and maintain. Write code for what is required now, not what might be needed in the future. For example, imagine you have the following function that creates an email listing based on a user profile.

```javascript
function generateEmailListingFromProfile(profile) {
  const { firstName, lastName, email } = profile;
  return `${firstName} ${lastName} <${email}>`;
}
```

This function has a very specific purpose. It may be tempting, when writing this function, to anticipate other functions that are not needed now but may be needed in the future, such as a `generateEmailSignature()` function or `generateWelcomeMessage()` function. While it can be tempting to write dozens of functions with all kinds of uses, it is better to only write what is needed to solve a specific feature. Writing more code than you need can lead to a bloated codebase that is hard to navigate.

## Principle of least astonishment

This principle suggests that code should behave in a way that is least surprising to the programmer. Code should be intuitive, with predictable outcomes. Unexpected behavior can lead to confusion and errors. For example, take a look at the following code:

```javascript
// Surprising behavior
const result = 1 + "1"; // Result is '11' (string concatenation)

// Expected behavior
const sum = 1 + 1; // Sum is 2 (numeric addition)
```

While JavaScript allows for the concatenation of numbers and strings, it is a bit unintuitive. Write your code so that other developers you work with, or even your future self, is not surprised at how something works.

## Start with the happy path

When implementing a feature, begin by considering the scenario where everything goes as planned. This is the "happy path." Once you have a working solution, you can add error handling and edge cases. Starting with the happy path simplifies development and debugging.

For example, imagine you need to write a function that loops over an array of names and randomly chooses some of them, inputted by the user. You may wonder what you should do if the array is empty or if the number inputted by the user is larger than the array length. These are good questions that should be asked! However, once you have these answers and begin coding, focus _first_ on developing code that works for the main use case.

```javascript
function pluckNames(names, count) {
  const result = [];
  for (let i = 0; i < count; i++) {
    const randomIndex = Math.floor(Math.random() * names.length);
    const [name] = names.splice(randomIndex, 1);
    result.push(name);
  }
  return result;
}

const names = ["Isabelle", "Lorelai", "Jemma", "Zak", "Trey", "Bo", "Bradley"];
pluckNames(names, 3); //> e.g., [ "Zak", "Trey", "Isabelle" ]
```

As long as the edge cases are not met, the code above will work for most cases. After completing the happy path, _then_ go back and add code to handle edge cases.

```javascript
function pluckNames(names, count) {
  if (names.length === 0) {
    return "`names` array is empty.";
  }

  if (count > names.length) {
    return "`count` is greater than length of the `names` array.";
  }

  if (count === names.length) {
    return names;
  }

  const result = [];
  for (let i = 0; i < count; i++) {
    const randomIndex = Math.floor(Math.random() * names.length);
    const [name] = names.splice(randomIndex, 1);
    result.push(name);
  }
  return result;
}

const names = ["Isabelle", "Lorelai", "Jemma", "Zak", "Trey", "Bo", "Bradley"];
pluckNames(names, 15); //> "`count` is greater than length of the `names` array."
```

Focusing on the happy path will allow you to get the majority of the function working first, as opposed to getting bogged down in what could potentially go wrong.
