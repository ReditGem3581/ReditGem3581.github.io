# Typescript: Power in Coding

## My Background Before TypeScript

I came into this module with about a year of computer engineering under my belt. In that time, I learned JavaScript, C, and C++. Each language had its own quirks: C felt low-level and unforgiving, while C++ gave me more tools but also more complexity. JavaScript, by contrast, was flexible and fun, but sometimes a little *too* loose. I could write code quickly, but debugging strange type errors later felt like detective work.

That’s why TypeScript caught my attention. At first it looked like JavaScript in a stricter suit — the same syntax, but with the “grown-up” requirement of types. My first impression was that it slowed me down. But after writing a few WODs (Workouts of the Day), I started to see how catching mistakes early in the editor could save me from spending hours later.

## Comparing TypeScript With What I Know

Compared to C and C++, TypeScript is obviously more forgiving. You don’t worry about memory management, pointer errors, or segmentation faults. At the same time, it’s stricter than JavaScript in a way that feels balanced. In C, I felt boxed in; in JavaScript, I felt too free. TypeScript sits somewhere in the middle: it guides you without chaining you.

Here’s a small example that really clicked for me:

```typescript
function temperatureConverter(temp: number, degree: string): number | string {
  if (degree === 'F' || degree === 'f') {
    return (temp - 32) * 5/9;
  } else if (degree === 'C' || degree === 'c') {
    return (temp * 9/5) + 32;
  }
  return 'Illegal temperature type';
}
```

In plain JavaScript, I could accidentally pass a boolean or an object and not know until runtime. In TypeScript, the editor catches it instantly. That immediate feedback loop is where I think the language shines.

## On ChatGPT and “the Thing Made of Code”

I’ll be honest: I lean heavily on ChatGPT when I code. To me, that feels natural. The thing made of code understands code in the same way humans understand our own bodies. Just as we instinctively know how our muscles and organs work, ChatGPT “instinctively” knows code. Why wouldn’t I learn from something that has that depth of knowledge?

That said, this module has pushed me to balance AI support with my own understanding. TypeScript is teaching me to think more rigorously about function signatures, object structures, and data flow. Even if I ask AI for help, I now catch myself reading the type definitions to make sure I actually understand why the code works.

## Athletic Software Engineering: Stressful but Effective

The WODs felt like gym workouts for my brain. They were stressful at first — I made silly mistakes under the time pressure. But over time, I noticed something: just like lifting weights, the repetition builds skill. The more I practiced, the more comfortable I became with TypeScript syntax and ES6 features. The pressure was real, but the improvement was real too.

For me, this style of learning works because it forces me out of passive learning mode. Watching videos or reading docs doesn’t stick nearly as well as sprinting through a WOD with the clock ticking.

## Final Thoughts

So, is TypeScript a good language for software engineering? I’d say yes. It’s not as bare-bones as C or as chaotic as plain JavaScript. It gives me structure without robbing me of creativity. Combined with practice through WODs, it feels like a toolset that’s actually sharpening my thinking.

I did use ChatGPT while reflecting on my experiences and shaping this essay. The AI helped me with organization and grammar, but the thoughts and examples are my own.
