---
layout: essay
type: essay
title: "Asking Real Smart Questions"
# All dates must be YYYY-MM-DD format!
date: September 10th, 2025
published: true
labels:
  - Coding
  - TypeScript
---

# Asking Real Smart Questions

## Why Smart Questions Matter

In software engineering, knowing *what* to ask is often just as important as knowing how to code. Eric Raymond’s classic essay, [*How to Ask Questions the Smart Way*](http://www.catb.org/esr/faqs/smart-questions.html), argues that the way we phrase our questions can make the difference between receiving silence, sarcasm, or genuinely useful answers. As a developer who leans on communities like StackOverflow, I’ve seen both sides of this coin. Smart questions invite collaboration; lazy or vague questions repel it.

## A Smart Example: Debugging a Promise Chain

One example of a “smart” question I found on StackOverflow involved a developer struggling with JavaScript promises. The question was titled: *“Why is my Promise chain not returning the expected value in Node.js?”* The developer included:

* A **minimal reproducible code snippet** that clearly showed the async function and the missing `return`.
* A **description of what they expected** (“I thought this would print the resolved value”) and what actually happened (“It prints `undefined`”).
* **Environment details** (Node.js version, OS).

Because of this, the answers were immediate and high-quality. One top answer explained that the developer forgot to `return` the inner Promise, and even rewrote the snippet to show the correction:

```javascript
function getValue() {
  return new Promise(resolve => resolve(42));
}

getValue().then(value => console.log(value));
```

This was a textbook example of Raymond’s principles: the asker showed effort, provided context, and made it easy for others to help. The community rewarded that with clear, educational answers. ([Link to question](https://stackoverflow.com/questions/46810512/why-is-my-promise-chain-not-returning-the-expected-value))

## A Not-So-Smart Example: “Help My Code Not Work”

Contrast that with another question I came across: *“My code not working plz help!!!”* The body simply read:

> i try to make login page in react but it dont work. can someone fix?

There was no code sample, no error messages, not even details about what “don’t work” meant. Unsurprisingly, the responses weren’t useful: one person asked for clarification, another downvoted, and one reply bluntly said, *“Read the React docs.”* This illustrates the downside of violating Raymond’s rules: without context, helpers can’t diagnose the issue, and frustration builds on both sides.

(Since vague questions often get closed quickly, here’s a [similar low-quality example](https://stackoverflow.com/questions/41889726/my-code-not-working) that captures the same problem.)

## Insights from Comparing the Two

What struck me in this exercise is how much of communication in software engineering comes down to empathy. A smart question respects the time of others by being specific, complete, and clear. A not-smart question shifts the burden onto others, effectively saying, *“Do my work for me.”*

I also realized this ties back to my own habits. I often rely on ChatGPT for coding help, but this reflection reminded me that the *quality of the question* determines the *quality of the answer*. Even AI performs better when I give precise details and context. Whether I’m asking humans or machines, the discipline of asking smart questions makes me a better engineer.

## Conclusion

The open-source community thrives on generosity, but generosity is not unlimited. Asking smart questions isn’t about gatekeeping—it’s about showing respect for other people’s time and expertise. When I put effort into how I ask, I get effort back in the answers. From now on, whether I’m posting to StackOverflow or debugging with a classmate, I want to keep Raymond’s advice in mind: be clear, be specific, and above all, be respectful.

