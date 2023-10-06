# Common Algorithms

Algorithms are the heart and soul of computer programming. They are step-by-step instructions that solve specific problems or perform tasks. In the world of programming, certain algorithms are so fundamental and widely used that they can be found in virtually any programming language. In this chapter, we will explore why these algorithms are so commonplace and how they are implemented across different programming languages. Additionally, we will delve into some of the most common algorithmic themes, such as sorting and searching algorithms, which are essential tools for any programmer.

## Learning Objectives

By the end of this lesson, you should be able to:

- Describe why some algorithms are commonplace in programming and how they can appear in any programming language.
- Identify common algorithmic themes, such as sorting and searching algorithms.

---

## The universality of algorithms

An algorithm is a finite sequence of well-defined, unambiguous steps that, when executed, produce a specific result or solve a particular problem. In essence, algorithms are like recipes for computers, guiding them through a series of logical operations.

Certain algorithms are universal because they address fundamental problems or tasks that occur frequently in the realm of computer science and programming. These problems are not specific to any particular programming language, platform, or application. Instead, they are encountered across a wide range of contexts. Therefore, it makes sense to have standard algorithms that can be applied in various situations.

### Examples of Universal Algorithms

You've already learned about one universal algorithm: the accumulator pattern. The accumulator pattern is used in all kinds of programming languages to solve problems where a series of elements must be aggregated into another element. For example, the JavaScript code below filters through a list of names to find all names that start with the letter "L".

```javascript
const names = ["Lewis", "Jack", "Louie", "Lily", "Devyn", "Martha", "Matilda"];
const result = [];
const letter = "L";
for (let name of names) {
  if (name[0] === letter) {
    result.push(name);
  }
}
```

This pattern can be reproduce in other coding languages. For example, the code below is written in the Python coding language but performs the same action as the JavaScript code.

```python
names = ["Lewis", "Jack", "Louie", "Lily", "Devyn", "Martha", "Matilda"]
result = []
letter = "L"
for name in names:
    if name[0] == letter:
        result.append(name)
```

Other examples of common algorithms include the following:

- **Euclid's algorithm**: Euclid's algorithm is another universal algorithm used to find the greatest common divisor of two integers. It has applications in cryptography, data compression, and various mathematical computations.

- **Breadth-First Search (BFS) and Depth-First Search (DFS)**: Graph traversal algorithms like BFS and DFS are essential for navigating and exploring data structures like trees and graphs. These algorithms are universal because they are fundamental to tasks like network routing, web crawling, and solving puzzles, making them a core part of programming languages and libraries.

## Common algorithmic themes

There are a number of common algorithms that all revolve around a particular theme. For example, sorting is a ubiquitous operation in computer programming. Whether you're organizing a list of names, sorting data in a database, or optimizing search algorithms, you'll encounter sorting algorithms. Some of the most common sorting algorithms are as follows:

- Bubble Sort
- Selection Sort
- Insertion Sort
- Merge Sort
- Quick Sort

Each of these algorithms have their own pros and cons, and all can be implemented in multiple languages. Searching for specific data within a dataset is another fundamental task in programming. There are several searching algorithms that can be implemented in any language, such as the following:

- Linear Search
- Binary Search

It's important to note that all these algorithms _already have implementations._ So far, you've been working on problems where you don't know what the solution is. In the case of common algorithms, a solution has already been determined. In the future, you'll be asked to understand these algorithms but not necessarily come up with the implementations on your own.
