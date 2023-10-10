# Tinkerer Mindset

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe a tinkerer mindset and how it differs from other learning mindsets.
- Given a small set of code, "tinker" with the code to better understand how it works.
- Given a small set of information, ask clarifying questions that lead to new paths of understanding.

---

## Guiding questions

- What is the tinkerer mindset, and why is it important in the learning process, particularly in technology-related fields?

- How does the tinkerer mindset differ from traditional learning approaches that rely on structured lessons and clear instructions?

- Why is the tinkerer mindset considered crucial when dealing with rapidly changing technologies and programming languages?

- How does the tinkerer mindset embrace mistakes and challenges as valuable learning opportunities?

- Why is adaptability an essential skill in today's rapidly changing world, and how does active learning better prepare learners for adaptability?

- Explain why the "What if...?" question is significant for tinkerers, especially when dealing with code or technology-related concepts.

- Take a look at the code below and then answer each question underneath it.

  ```javascript
  // Function to reverse a string
  function reverseString(str) {
    let reversed = "";
    for (let i = str.length - 1; i >= 0; i--) {
      reversed += str[i];
    }
    return reversed;
  }

  // Test the function
  const originalString = "Hello, World!";
  const reversedString = reverseString(originalString);
  console.log(`Original: ${originalString}`);
  console.log(`Reversed: ${reversedString}`);
  ```

  - What is the purpose of the `reverseString()` function?

  - How does the `for` loop work? How is it different from what you've normally seen?

  - Is there any input that would cause the function call to throw an error? If so, what is it and why does it cause an error?

- Take a look at the code below and then answer each question underneath it.

  ```javascript
  // Function to filter even numbers from an array
  function filterEvenNumbers(numbers) {
    return numbers.filter((num) => num % 2 === 0);
  }

  // Test the function
  const numbersArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const evenNumbers = filterEvenNumbers(numbersArray);
  console.log(`Original array: ${numbersArray}`);
  console.log(`Even numbers: ${evenNumbers}`);
  ```

  - What is the purpose of the `filterEvenNumbers()` function?

  - What do you understand about the code or the function's purpose? What do you not understand about the code or the function's purpose?

  - What is `.filter()` and what type of argument does it accept?

  - Is there any input that would cause the function call to throw an error? If so, what is it and why does it cause an error?
