# Tinkerer Mindset

Learning is not a one-size-fits-all process; it is a dynamic journey that varies from person to person. Some learners excel when they follow structured lessons and clear instructions, while others thrive when they take a more hands-on, experimental approach. In this chapter, we'll explore the concept of a "tinkerer mindset" and how it differs from other learning mindsets. We'll also delve into the art of asking clarifying questions to uncover new avenues of understanding and how to tinker with code to gain a deeper comprehension of programming concepts.

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe a tinkerer mindset and how it differs from other learning mindsets.
- Given a small set of code, "tinker" with the code to better understand how it works.
- Given a small set of information, ask clarifying questions that lead to new paths of understanding.

---

## The tinkerer mindset

A tinkerer mindset is a learning approach characterized by curiosity, exploration, and a willingness to experiment. Unlike traditional learning which may rely heavily on formal instruction, tinkerers enjoy getting their hands dirty, trying things out, and learning through trial and error. They are not afraid to break things because they understand that every mistake is an opportunity to learn.

The tinkerer mindset is absolute crucial in learning to code because technology changes so quickly. There is not a manual or course for every new technology or program that is created. Even if you aren't working on the cutting edge of technology, you will need to be able to tinker with other people's code to best understand how it works.

### How does the tinkerer mindset differ?

Understanding the differences between various learning mindsets involves delving into the science of learning. Research in educational psychology has shown that not all learning approaches are created equal. Active learning, which aligns closely with the tinkerer mindset, has been found to be far more effective for knowledge retention compared to passive learning or memorization.

#### The science of learning

Studies on the science of learning have illuminated key principles that support the tinkerer mindset:

1. **Active engagement enhances retention**: Active learning, characterized by engagement, problem-solving, and experimentation, stimulates multiple areas of the brain. When you actively interact with new information or skills, your brain forms stronger neural connections. This process, known as neuroplasticity, reinforces your understanding and increases the likelihood of long-term retention.

1. **Depth of processing matters**: In active learning, learners process information deeply. They actively seek to understand, connect, and apply knowledge, resulting in a more profound understanding of the subject matter. This deep processing enhances memory recall and the ability to transfer knowledge to new contexts.

1. **Mistakes and challenges drive learning**: The tinkerer mindset embraces mistakes and challenges as opportunities for growth. Research indicates that encountering and overcoming difficulties during learning leads to more robust learning outcomes. Struggling with and solving problems activates problem-solving pathways in the brain, promoting higher-order thinking skills.

### Active learning vs. passive learning and memorization

In contrast to active learning, passive learning and memorization often involve passive consumption of information with minimal engagement. This approach relies on rote memorization, which, while useful in certain contexts, has limitations. This style of learning is what most people think of when they think of learning in a classroom. They may imagine sitting at a desk while a teacher expertly dictates their knowledge to rows of note-taking students. This style of learning can be sufficient for some types of knowledge or for more introductory courses, but it begins to fall flat when more difficult concepts are tackled.

In particular, passive learning and memorization struggle to compete with more active learning in the following ways:

1. **Limited retention**: Memorization without understanding can lead to shallow learning, making it difficult to recall information accurately over time. In contrast, active learning fosters a deeper understanding that enhances retention.

1. **Difficulty in application**: Passive learners and memorizers may find it challenging to apply their knowledge to real-world situations. Active learners, including those with a tinkerer mindset, are more adept at applying what they've learned in practical scenarios.

1. **Adaptability**: In today's rapidly changing world, the ability to adapt and learn new skills is invaluable. Active learners are better prepared for this adaptability because they have developed critical thinking, problem-solving, and learning strategies that extend beyond mere memorization.

In essence, the tinkerer mindset aligns with the principles of active learning, emphasizing engagement, exploration, and experimentation. By adopting this approach, learners can harness the science of learning to maximize their understanding and retention of new concepts and skills.

## Tinker on code

You now know that taking a more active approach to your learning through tinkering is beneficial for learning to code. But, what does tinkering with code look like? When you encounter a piece of code, especially one you're trying to learn from, don't just read it passively. Engage with it actively. Let's explore this concept with the following code example:

```javascript
// Function to calculate the sum of numbers from 1 to n
function calculateSum(n) {
  let sum = 0;
  for (let i = 1; i <= n; i++) {
    sum += i;
  }
  return sum;
}

// Calculate and display the sum of numbers from 1 to 5
const n = 5;
const result = calculateSum(n);
console.log(`The sum of numbers from 1 to ${n} is: ${result}`);
```

Now, let's explore how you can tinker with this JavaScript code:

- **Start with comments**: Read any comments that provide context or explanations within the code. In this example, there are comments explaining that this code calculates the sum of numbers from `1` to `n` using a loop.

- **Identify key components**: Break down the code into smaller parts or functions. In this code, there's a function called `calculateSum()` that calculates the sum of numbers. It also contains a `for` loop that iterates through the numbers and accumulates the sum.

- **Modify and experiment**: Now it's time to tinker! Make small changes to the code and observe how it affects the program's behavior. For instance, try changing the value of `n` to calculate the sum of numbers from 1 to a different number. Experiment with different starting values in the `for` loop and observe the results.

- **Debugging and problem solving**: When you encounter errors or unexpected behavior, embrace them as opportunities to learn. For instance, if you change the input to `calculateSum("5")`, you may be surprised to learn that the code actually functions as normal. If you change the input to `calculateSum(true)`, you'll get a return value of `1`, which might also be unexpected! This is a chance to practice debugging by understanding why the code works the way it does.

By actively engaging with code, you'll not only gain a better understanding of how it works but also develop problem-solving skills that are essential for programming and active learning.

## Ask clarifying questions

Asking questions is a fundamental skill for any learner, but tinkerers take it a step further. They not only ask questions but also pose queries that lead to new perspectives and insights. When presented with information, whether it's a text, diagram, or code snippet, take a moment to digest it. Then, instead of passively accepting it, ask yourself:

1. **What do I understand from this?** Start by summarizing what you've grasped so far. This clarifies your current understanding.

1. **What don't I understand?**: Identify gaps in your understanding. What aspects of the information are unclear or confusing?

1. **What if...?**: This is the key question for tinkerers. Consider alternative scenarios or interpretations. What if this information were applied differently? What if there were exceptions? For code, consider how different input types could affect the outcome, or whether the code is even necessary at all.

1. **How can I test my understanding?**: Formulate testable hypotheses or experiments based on your questions. This might involve experimenting with code or conducting research to find answers.

A tinkerer mindset is a valuable asset for any learner, especially in the dynamic and ever-evolving world of programming and technology. By developing the ability to ask clarifying questions and actively engage with code, you'll not only understand concepts better but also become a more confident and versatile learner. Embrace the joy of tinkering, and remember that every experiment, every question, and every mistake is a step towards deeper understanding.
