# Program Design

Building a codebase is similar to building a house in that it is a complex process and requires a strong foundation. When you create a codebase that contains more than a few functions, there are some fundamental technical concepts that are essential to creating organized, maintainable, and efficient code. In this reading, you'll learn some tips on how to write code in such a way that the overall codebase you develop is better suited for the future.

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand the importance of single responsibility helper functions and how to apply this concept.
- Grasp the significance of naming conventions for variables, functions, and classes.
- Embrace the "DRY" principle and avoid code duplication.

---

## Single responsibility functions

When writing code, it's essential to ensure that each function or module has a single, well-defined responsibility. This concept is known as "single responsibility." By following this principle, you keep your code organized and easier to understand. Each function should do one thing and do it well. Not only will this make your code easier to understand, but it will also be easier to test out particular functions in the event an error occurs. For example, take a look at the following function:

```javascript
function calculateAndDisplayTotalPrice(products) {
  // Calculate the total price
  let totalPrice = 0;
  for (let product of products) {
    totalPrice += product.price;
  }

  // Display the total price
  console.log(`Total Price: $${totalPrice}`);
}
```

This function has two responsibilities: it calculates the total of all products in an array and prints out the total price of all those products. This function could be split up into two different functions, each of which have only one responsibility.

```javascript
// Calculate the total price
function calculateTotalPrice(products) {
  let totalPrice = 0;

  for (let product of products) {
    totalPrice += product.price;
  }

  return totalPrice;
}

// Display the total price
function displayTotalPrice(totalPrice) {
  console.log(`Total Price: $${totalPrice}`);
}
```

While these functions are relatively simple, you've likely already seen how some functions can balloon in size when more and more functionality is added to them. Smaller, separate functions like these are often referred to as helper functions.

### Helper functions

Helper functions are small, reusable functions that perform specific tasks within your code. They simplify complex logic by breaking it into manageable parts. Using helper functions makes your code more concise and easier to maintain. Once you have helper functions, you can then use them to compose key functions that run your program.

For example, assume your program has both the `calculateTotalPrice()` and `displayTotalPrice()` functions in it. You could then write a function that makes use of both of those functions.

```javascript
function calculateAndDisplayTotalPrice(products) {
  const totalPrice = calculateTotalPrice(products);
  displayTotalPrice(totalPrice);
}
```

The function above is very nice to read in that it almost reads like English. Even if you have no idea how the underlying functions work, you can understand what the purpose of this function is thanks to the well-named functions and the order in which those functions are called.

## Naming conventions

Choosing meaningful and consistent names for your variables, functions, and classes is essential for code readability. As you've just seen, having good names can be very beneficial to understanding code. In contrast, poorly defined names can lead to confusion and misunderstanding. For example, take a look at the following code which doesn't make use of good naming conventions.

```javascript
function calc(arr) {
  let total = 0;
  for (let el of arr) {
    total += el.price;
  }

  console.log(`Total Price: $${total}`);
}
```

You may notice this is some of the same code from above! While this code is _technically correct_, it's more difficult to follow along than the previous solution. When you're first starting out in learning to code, it can feel easier sometimes to use shorter variable names. However, in the long run, this will not benefit you or other developers you are working with.

Certain programming languages have conventions around how to name variables. In JavaScript, variable and function names are written in camel case, as seen above. While this is not required by the language, it is a good idea to follow this convention. Additionally, you may wish to follow the conventions listed below:

- Function names should begin with a verb that describes what that function is doing. For example, "display", "set", or "calculate".

- It is better for a variable name to be slightly longer and understandable than to be terse and unclear. For example, `calculateAndDisplayTotalPrice()` is better than `calculate()`.

- Single-letter variables should never make their way into your code. The one exception to this is when you create a `for` loop and need to name the index variable something like `i`. Even then, writing `index` can sometimes be preferable.

- If you do use abbreviations in your code, they should be consistent. For example, if you wish to abbreviate `element` to `el`, it should stay that way throughout the code.

Remember that the purpose of this is to make your code easier to understand and read. While following these conventions will not improve the functionality of your code, writing good code is essential to working in groups.

## DRY - Don't Repeat Yourself

The "DRY" principle encourages you to avoid code duplication. Instead of writing the same code in multiple places, encapsulate it in helper functions that can be reused throughout your program. This reduces errors, makes maintenance easier, and keeps your code concise. For example, take a look at the following code which has some duplicate code. Can you spot what code is duplicated?

```javascript
function findProductsByPrice(products, price) {
  let result = [];

  for (let product of products) {
    if (product.price === price) {
      result.push(product);
    }
  }

  return result;
}

function findProductsByName(products, name) {
  let result = [];

  for (let product of products) {
    if (product.name === name) {
      result.push(product);
    }
  }

  return result;
}
```

These two functions are essentially the same, except they aggregate products based on a different key. Realistically, a little bit of duplication is actually not the worst thing to have in a codebase, particularly when you're working on a new feature or product. However, if there were two or three more functions like this, it may be time to update our code so that the same loop is not getting repeated constantly with minimal changes.

One way to update this code to be more DRY would be to add the following helper function.

```javascript
function findProductsBy(products, key, value) {
  let result = [];

  for (let product of products) {
    if (product[key] === value) {
      result.push(product);
    }
  }

  return result;
}
```

The function above is much more generic and can then be used to rewrite the previously written functions.

```javascript
function findProductsByPrice(products, price) {
  return findProductsBy(products, "price", price);
}

function findProductsByName(products, name) {
  return findProductsBy(products, "name", name);
}
```
