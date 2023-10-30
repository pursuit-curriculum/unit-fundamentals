# Program Design

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand the importance of single responsibility helper functions and how to apply this concept.
- Grasp the significance of naming conventions for variables, functions, and classes.
- Embrace the "DRY" principle and avoid code duplication.

---

## Guiding questions

- Why is it important for functions to have a single, well-defined responsibility? How does this practice contribute to code organization and readability?

- Explain the concept of "helper functions" in programming. How do they simplify code and improve code maintainability?

- What is the significance of naming conventions in programming? How can well-chosen names for variables and functions improve code comprehension?

- How do you ensure that you choose meaningful and consistent names for your variables and functions? What guidelines or conventions do you follow when naming elements in your code?

- In the reading, the "DRY" principle is introduced. What does "DRY" stand for, and why is it important to avoid code duplication in software development?

- Can you identify any situations where breaking the "DRY" principle might be acceptable or even necessary in code development?

- How do these principles and concepts contribute to making codebases more maintainable and efficient, especially in larger and more complex software projects?

- If you were working in a team of developers, how would you ensure that everyone follows these coding practices and principles for a consistent and collaborative codebase?

- Discuss any challenges or potential drawbacks of adhering strictly to these programming principles. Are there situations where trade-offs may need to be considered?

- Take a look at the code below. How would you improve this code to be more readable and better organized? Consider the purpose of this function, what helper functions could exist, and what variables could be renamed.

  ```javascript
  function bestSellers(products) {
    let sold = 0;
    for (let product of products) {
      sold += product.quantitySold;
    }

    const avg = Math.ceil(sold / products.length);
    const result = [];

    for (let product of products) {
      if (product.quantitySold > avg) {
        result.push(product);
      }
    }

    const names = [];
    for (let res of result) {
      names.push(res.name);
    }

    return names;
  }

  const products = [
    { id: 1, name: "Laptop", price: 1000, quantitySold: 23 },
    { id: 2, name: "Smartphone", price: 800, quantitySold: 11 },
    { id: 3, name: "Tablet", price: 500, quantitySold: 19 },
    { id: 4, name: "Flip Phone", price: 80, quantitySold: 4 },
    { id: 5, name: "Smartphone Case", price: 25, quantitySold: 34 },
  ];
  bestSellers(products); //> [ 'Laptop', 'Smartphone Case' ]
  ```
