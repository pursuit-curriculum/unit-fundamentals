# Technical Communication

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe existing code at both a conceptual and technical level, depending on the audience.
- Walk through existing code at a deep technical level, to both demonstrate and gain understanding.
- Use a scope diagram to walk through a function, to both demonstrate and gain understanding.

---

## Guiding Questions

- Why is the ability to communicate code effectively important for software developers?

- In what scenarios might you need to describe your code to different audiences, and why?

- What factors should you consider when determining the level of technical detail to include when describing code to an audience?

- What are the key differences between a technical and non-technical description of code?

- Take a look at the following code. How would you explain this code to a non-technical audience? What about to a technical audience?

  ```javascript
  function printUntil(n) {
    for (let i = 1; i <= n; i++) {
      console.log(i);
    }
  }

  printUntil(10);
  ```

- Take a look at the following code. How would you explain this code to a non-technical audience? What about to a technical audience?

  ```javascript
  function addSeatNumber(attendees) {
    const rows = "ABCDEFGH";
    const seatsPerRow = 6;

    let currentRowIndex = 0;
    let currentSeat = 1;
    for (let attendee of attendees) {
      let row = rows[currentRowIndex];
      attendee.seat = row + currentSeat;

      currentSeat++;
      if (currentSeat > seatsPerRow) {
        currentRowIndex++;
        currentSeat = 1;
      }
    }

    return attendees;
  }

  const attendees = [
    { name: "Rudy Baker" },
    { name: "Gabe Read" },
    { name: "Casey Day" },
    { name: "Brynn Scott" },
    { name: "Blake Cole" },
    { name: "Angel Hale" },
    { name: "Emerson Mullins" },
    { name: "Ray Gardner" },
    { name: "Aaren Copeland" },
    { name: "Gale Munoz" },
  ];
  addSeatNumber(attendees);
  ```

- Develop a scope diagram for the code above. What variables must you keep track of as part of the global scope? What about the function scope?

- Take a look at the code below and then answer each question underneath it. Keep in mind a tinkerer's mindset as you work through this challenge.

  ```javascript
  // Function that applies a callback function to each element in an array
  function applyCallback(array, callback) {
    const result = [];
    for (let i = 0; i < array.length; i++) {
      result.push(callback(array[i]));
    }
    return result;
  }

  // Test the function with a callback function
  const numbers = [1, 2, 3, 4, 5];
  const squaredNumbers = applyCallback(numbers, (num) => num * num);
  console.log(`Original numbers: ${numbers}`);
  console.log(`Squared numbers: ${squaredNumbers}`);
  ```

  - What is the purpose of the `applyCallback()` function?

  - What do you understand about the code or the function's purpose? What do you not understand about the code or the function's purpose?

  - What are the data types of the two arguments does `applyCallback()` accept?

  - How would you explain this code to a non-technical audience? What about to a technical audience?

  - Develop a scope diagram for the code above. What variables must you keep track of as part of the global scope? What about the function scope?

  - Reflect on the process of learning about this code and then describing it. What was challenging about it? What questions do you still have?

- How can you improve your code communication skills as a developer?
