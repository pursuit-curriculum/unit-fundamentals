# Measuring Complexity

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe how efficiency is measured in programming.
- Define time and space complexity and how it relates to programming.
- Evaluate and measure the time complexity of a program.

---

## Guiding questions

- What are the three main ways to measure the quality of code mentioned in the reading, and why are they important?

- What is the significance of efficiency in software development, and how is it typically measured?

- What is time complexity, and how does it relate to algorithm efficiency?

- Explain Big O notation and its role in expressing algorithm efficiency.

- Why do software developers focus on the worst-case scenario when assessing time complexity?

- What does it mean for an algorithm to have constant time complexity O(1)? Can you provide an example?

- How does linear time complexity O(n) differ from constant time complexity, and can you provide an example of a linear time complexity algorithm?

- What is quadratic time complexity O(n²), and why is it considered less performant? Provide an example.

- How can complexities with constant factors be simplified when measuring Big O notation, and why is it done?

- What are logarithmic time complexity O(log(n)) and factorial time complexity O(n!)? How do they compare to other complexities in terms of efficiency?

- The following measurements of Big O can all be simplified to smaller measurements. Reduce each to highlight it's more important measurement.

  - O(50)

  - O(2n)

  - O(n² + 10)

  - O(n² + log n)

- Take a look at the following function. What is its time complexity, represented using Big O?

  ```javascript
  function multiplyByThree(n) {
    return n * 3;
  }

  multiplyByThree(10); //> 30
  ```

- Take a look at the following function. What is its time complexity, represented using Big O?

  ```javascript
  function multiplyAll(arr1, arr2) {
    if (arr1.length !== arr2.length) {
      return null;
    }

    let total = 0;
    for (let i = 0; i < arr1.length; i++) {
      for (let j = 0; j < arr2.length; j++) {
        total += i * j;
      }
    }

    return total;
  }

  multiplyAll([1, 2], [5, 6]); //> 33
  ```

- Take a look at the following function. What is its time complexity, represented using Big O?

  ```javascript
  function searchPhrase(phrase, keyword) {
    const words = phrase.split(" ");
    for (let word of words) {
      if (word.toLowerCase() === keyword.toLowerCase()) {
        return true;
      }
    }

    return false;
  }

  searchPhrase("Welcome to our Classroom", "class"); //> false
  searchPhrase("Welcome to our Classroom", "our"); //> true
  ```

- In what scenarios might you prioritize time complexity over space complexity, and vice versa, when developing software?
