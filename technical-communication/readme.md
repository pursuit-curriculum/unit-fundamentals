# Technical Communication

You may not have realized it, but one of the most important jobs of a software developer is the ability to communicate code. Writing code, even if it is excellent code, is not enough as software development is always a collaborative process. In this lesson, you'll learn how to more clearly communicate existing code depending on the audience.

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe existing code at both a conceptual and technical level, depending on the audience.
- Walk through existing code at a deep technical level, to both demonstrate and gain understanding.
- Use a scope diagram to walk through a function, to both demonstrate and gain understanding.

---

## Talking about code

You'll be asked to talk about your code consistently throughout your career as a software developer. Every day at work, you may need to share out what you're working on and the specific way you've solved a problem. When speaking with your supervisor or a product manager, you may need to communicate the intention of code you've written. You may even need to communicate code on a stage, in front of other developers, when you're presenting at a conference!

| ![Karri Saarinen presenting at Nordic Design](./assets/conference.jpg)                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Photo by <a href="https://unsplash.com/@xteemu?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Teemu Paananen</a> on <a href="https://unsplash.com/photos/bzdhc5b3Bxs?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a> |

### Determining your audience

When talking about code, it's important to first identify who the audience is. In particular, you will want to determine what level of technical proficiency your audience has and what their overriding interest is in your code.

When you're working with your fellow developers on a feature, you will need to be quite technical in talking about code. It may be important to describe exactly how you've solved a problem using specific features of JavaScript. However, if you're discussing the completion of a feature with your product manager, your description may be more general and focus on the feature that was completed rather than the specific techniques that were used to solve the problem.

For example, the following two statements could both describe the same code.

- "This code I've written sorts a list of songs based on the ratings they received by the user. It then returns the top three highest rated songs for users. We'll use this function to help inform our song suggestion engine."

- "This code I've written uses the native `.sort()` JavaScript method to organize the songs array by rating in descending order. I then use destructuring to pull out the top three songs and create a new array with those top rated songs. That song array can then be passed as an argument into our suggestion engine."

Do you see the difference between the two statements above? Both describe the functionality of the code and how it will be used, but one has a higher level of detail. As a software developer, you will need to be capable of doing both and appropriately choose the audience as needed.

If you are ever unsure of how detailed you should go, you can always ask. Typically the more technical the person or the environment, the more technical of an explanation they will want. However, it can always be to your benefit to clarify what level of explanation that person is looking for in the event you are unsure.

## Describing code in depth

Take a look at the following code which contains two functions. _Don't skim the code!_ Take a few minutes to really try and understand what the two functions are doing and how they may be related to one another.

```javascript
/**
 * Returns an array of all states from each product.
 * @param {Object[]} products - An array of product objects.
 * @param {string} products[].state - A string representation of the state where the product was sold.
 * @returns {string[]} An array of state names, all lowercase.
 */
function getStatesFromProducts(products) {
  const result = [];

  for (let product of products) {
    const { state } = product;
    const lowercase = state.toLowerCase();
    result.push(lowercase);
  }

  return result;
}

/**
 * Returns an array of unique states, unordered.
 * @param {string[]} states - an array of state names, lowercase.
 * @returns {string[]} an array of states, unique but unordered
 */
function getUniqueListOfStates(states) {
  const uniqueList = {};

  for (let state of states) {
    uniqueList[state] = true;
  }

  return Object.keys(uniqueList);
}
```

Were you able to see a relationship between the two functions above? The first function, `getStatesFromProducts()`, plucks a string from the array of objects used as an argument into the function. It places all of those states into an array. The `getUniqueListOfStates()` function takes an array of states and returns a unique list of strings. The functions might be used in the following way.

```javascript
const products = [
  { name: "Fancy T-shirt", state: "Colorado" },
  { name: "Cedarwood candle", state: "IDAHO" },
  { name: "Pink Toque", state: "Colorado" },
];
const states = getStatesFromProducts(products);
//> [ "colorado", "idaho", "colorado" ]
const uniqueList = getUniqueListOfStates(states);
//> [ "colorado", "idaho" ]
```

While the above explanation is sufficient in most cases, it's important to be able to walk through the code using more technical language. For example, the `getStatesFromProduct()` function could be described as follows:

> The `getStatesFromProduct()` function takes an array of product objects as input and extracts the state where each product was sold. It returns an array containing all these states, converted to lowercase.
>
> It does this by first creating a `results` variable that contains an empty array. This will be used to collect all of the states in the products.
>
> Next, the function iterates through each `product` in the `products` array using a `for...of` loop. Inside the loop, it uses destructuring to extract the `state` property from each `product` object. The extracted `state` is converted to lowercase using the `.toLowerCase()` method, ensuring uniformity in the output. The lowercase `state` is then pushed into the `result` array.
>
> Finally, the function returns the `result` array, which contains lowercase state names for all products.

The above explanation is much more technical, in that it describes specific keys, methods, and variables. This kind of explanation would be excellent in speaking with another developer or even on a software development interview.

## Scope diagrams

One way to cleanly describe how a function works is to use a scope diagram. Scope diagrams can be useful when explaining a tricky function, when attempting to debug, or during interviews. The purpose of a scope diagram is to help demonstrate how a functions inputs led to its output. At its core, a scope diagram is simply a table that tracks what variable values are set at different points of the program execution.

For example, revisit the `getUniqueListOfStates()` function from above. Note that two lines have been added below the function definition which run the function with an input.

```javascript
/**
 * Returns an array of unique states, unordered.
 * @param {string[]} states - an array of state names, lowercase.
 * @returns {string[]} an array of states, unique but unordered
 */
function getUniqueListOfStates(states) {
  const uniqueList = {};

  for (let state of states) {
    uniqueList[state] = true;
  }

  return Object.keys(uniqueList);
}

const stateList = ["colorado", "idaho", "colorado", "new york"];
const result = getUniqueListOfStates(stateList);
```

To build a scope diagram, you'd start by creating a table of all of the variables at the _global_ level. At the very beginning, the values for each variable should be empty as you are simulating the program being run from the very beginning.

> **Global variables**
>
> | Variable                  | Value |
> | ------------------------- | ----- |
> | `getUniqueListOfStates()` |       |
> | `stateList`               |       |
> | `result`                  |       |

Were you surprised to see `getUniqueListOfStates()` as a variable? Remember that functions are assigned names as well!

When the program begins, `getUniqueListOfStates` is assigned the value of a function. To represent this, the scope diagram can be updated in the following way.

> **Global variables**
>
> | Variable                  | Value |
> | ------------------------- | ----- |
> | `getUniqueListOfStates()` | fn()  |
> | `stateList`               |       |
> | `result`                  |       |

Next, `stateList` is assigned the value of an array.

> **Global variables**
>
> | Variable                  | Value                                           |
> | ------------------------- | ----------------------------------------------- |
> | `getUniqueListOfStates()` | fn()                                            |
> | `stateList`               | `["colorado", "idaho", "colorado", "new york"]` |
> | `result`                  |                                                 |

Next, the program will execute the `getUniqueListOfStates()` function with `stateList` as the sole argument. To represent the scope contained within the function, _another_ scope diagram would be created.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` |                                                 |
> | `state`      |                                                 |

The process contains within the function scope. First, a new value is assigned to the `uniqueList` variable of an empty object.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` | `{}`                                            |
> | `state`      |                                                 |

Next, the `for...of` loop begins to run. The first state in the array is `"colorado"`, which will be assigned the `state` variable.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` | `{}`                                            |
> | `state`      | `"colorado"`                                    |

The `uniqueList` object is then updated where the key is set to the state name and the value is set to `true`.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` | `{ colorado: true }`                            |
> | `state`      | `"colorado"`                                    |

That loop continues, adding `"idaho"` to the object. In the diagram below, both `state` and `uniqueList` have been updated at the same time.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` | `{ colorado: true, idaho: true }`               |
> | `state`      | `"idaho"`                                       |

What happens when we get to the third element in the array, which is once again `"colorado"`? Objects cannot have duplicate keys with the same name, so nothing is changed in the `uniqueList` even though the `state` variable does change.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                           |
> | ------------ | ----------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]` |
> | `uniqueList` | `{ colorado: true, idaho: true }`               |
> | `state`      | `"colorado"`                                    |

Finally, `"new york"` is added to the list as the loop finishes.

> **getUniqueListOfStates() variables**
>
> | Variable     | Value                                               |
> | ------------ | --------------------------------------------------- |
> | `states`     | `["colorado", "idaho", "colorado", "new york"]`     |
> | `uniqueList` | `{ colorado: true, idaho: true, "new york": true }` |
> | `state`      | `"new york"`                                        |

The last line of the function is to return `Object.keys(uniqueList)`. However, instead of storing that value in the `getUniqueListOfStates()` scope diagram, it can be assigned back in the original global scope diagram.

> **Global variables**
>
> | Variable                  | Value                                           |
> | ------------------------- | ----------------------------------------------- |
> | `getUniqueListOfStates()` | fn()                                            |
> | `stateList`               | `["colorado", "idaho", "colorado", "new york"]` |
> | `result`                  | `["colorado", "idaho", "new york"]`             |

The code is now complete. By completing the above scope diagrams you've seen how, at every step of the process, the values have changed as the program has executed. Scope diagrams are incredibly useful in that they allow humans to gain deep insight into what exactly is happening when a program is run.
