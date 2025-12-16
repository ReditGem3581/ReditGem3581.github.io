---
layout: essay
type: essay
title: "Design Patterns: The blueprints we reuse to build better software"
# All dates must be YYYY-MM-DD format!
date: 2025-12-05
labels:
  - Design Patterns
  - Software Engineering
  - ICS 314
---

When you walk into a bookstore, the shelves are organized the same way regardless of which store you visit. Fiction on one side, non-fiction on another, checkout near the exit. You don't have to ask where things are—the pattern is familiar. If a bookstore owner invented a completely novel layout every time, customers would be frustrated and lost. Instead, they follow a proven blueprint: a *pattern* that works.

Software design is no different. A design pattern is a reusable solution to a common problem that arises during software design. It's not code you copy-paste; it's a template for *how* to structure your code to solve a recurring challenge elegantly.

## Why patterns matter

Imagine I'm building a budgeting app called Tithr without any patterns in mind. I'd write code ad hoc, inventing solutions on the fly. The code might work, but it would likely be:

- **Repetitive**: I'd write similar logic for user authentication in three different places.
- **Fragile**: Change the way expenses are calculated, and I'd hunt through a dozen files looking for where else that logic lives.
- **Hard to collaborate on**: My teammates wouldn't know where to add new features or how the architecture is organized.
- **Difficult to test**: Tightly coupled components would make unit testing a nightmare.

Design patterns solve these problems by giving us a shared vocabulary and proven structures.

## The patterns in Tithr

Building Tithr, I found myself reaching for specific patterns—not because I memorized them, but because they emerged as natural solutions to real problems.

### The Singleton Pattern: One Source of Truth for Config

Tithr needs to manage user preferences—budget percentages, color themes, Bible verse sources—globally across the app. I use the **Singleton pattern**: a single, globally accessible instance that ensures only one configuration object exists at a time.

```javascript
class BudgetConfig {
  static instance = null;

  constructor() {
    if (BudgetConfig.instance) {
      return BudgetConfig.instance;
    }
    this.tithePercent = 0.1;
    this.needsPercent = 0.5;
    this.savingsPercent = 0.2;
    this.wantsPercent = 0.2;
    BudgetConfig.instance = this;
  }

  static getInstance() {
    if (!BudgetConfig.instance) {
      BudgetConfig.instance = new BudgetConfig();
    }
    return BudgetConfig.instance;
  }
}

// Anywhere in the app:
const config = BudgetConfig.getInstance();
console.log(config.tithePercent); // 0.1
```

This prevents chaos: no accidental duplication of config, no conflicting updates, one authoritative source.

### The Observer Pattern: Watching for Changes

When a user logs an income transaction, Tithr needs to update the dashboard chart, refresh the category balances, and maybe send a notification—all automatically. The **Observer pattern** decouples the event (income logged) from the actions that follow.

```javascript
class TransactionManager {
  constructor() {
    this.observers = [];
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  logTransaction(transaction) {
    // Log the transaction...
    // Then notify all observers:
    this.observers.forEach(obs => obs.update(transaction));
  }
}

// Observers can be added or removed without changing TransactionManager
class DashboardObserver {
  update(transaction) {
    // Re-render the pie chart
  }
}

class NotificationObserver {
  update(transaction) {
    // Send a congratulatory verse if user tithed
  }
}
```

Now, if I want to add a new observer later (like logging to analytics), I just create a new class and subscribe it. The transaction manager doesn't need to change.

### The Factory Pattern: Creating Budget Categories

Tithr supports different budget categories (Tithe, Needs, Savings, Wants) with different validation rules and display logic. Rather than cluttering the code with conditionals like `if (category === 'tithe') { ... }`, I use the **Factory pattern** to create the right category object.

```javascript
class CategoryFactory {
  static createCategory(type, percentage) {
    switch (type) {
      case 'tithe':
        return new TitheCategory(percentage);
      case 'needs':
        return new NeedsCategory(percentage);
      case 'savings':
        return new SavingsCategory(percentage);
      case 'wants':
        return new WantsCategory(percentage);
      default:
        throw new Error('Unknown category');
    }
  }
}

class TitheCategory {
  constructor(percentage) {
    this.name = 'Tithe';
    this.percentage = percentage;
    this.icon = '✝️';
    this.requiresApproval = true; // Custom business logic
  }
}

class NeedsCategory {
  constructor(percentage) {
    this.name = 'Needs';
    this.percentage = percentage;
    this.icon = '🏠';
    this.requiresApproval = false;
  }
}
```

When the app initializes, it simply calls `CategoryFactory.createCategory('tithe', 0.1)` and gets back a fully-fledged TitheCategory with all its specific logic. Clean, extensible, and easy to test.

### The Strategy Pattern: Flexible Calculation Rules

Not every user wants to use the 10-50-20-20 split. Some might prefer 15-40-25-20, others might have custom rules entirely. The **Strategy pattern** lets each user pick their calculation strategy without changing the core budgeting engine.

```javascript
class BudgetCalculator {
  constructor(strategy) {
    this.strategy = strategy;
  }

  allocate(income) {
    return this.strategy.calculate(income);
  }
}

class TraditionalStrategy {
  calculate(income) {
    return {
      tithe: income * 0.1,
      needs: income * 0.5,
      savings: income * 0.2,
      wants: income * 0.2,
    };
  }
}

class StudentStrategy {
  calculate(income) {
    return {
      tithe: income * 0.05,
      needs: income * 0.6,
      savings: income * 0.15,
      wants: income * 0.2,
    };
  }
}

// User picks their strategy at signup:
const calculator = new BudgetCalculator(new StudentStrategy());
calculator.allocate(800); // { tithe: 40, needs: 480, ... }
```

Each strategy encapsulates its own rules. Adding a new strategy is as simple as creating a new class; the calculator never has to change.

## The bigger picture

These four patterns—Singleton, Observer, Factory, and Strategy—are just a few of the dozens out there (Model-View-Controller, Dependency Injection, Decorator, etc.). But they illustrate why design patterns matter:

1. **Reusability**: These solutions have been battle-tested by thousands of developers. You're not inventing from scratch.
2. **Communication**: When I tell a teammate "we use the Observer pattern here," they immediately understand the architecture without needing me to explain a hundred lines of logic.
3. **Maintainability**: Adding a new category type or changing a calculation rule becomes a localized change, not a hunt-and-replace across the codebase.
4. **Scalability**: Well-patterned code is easier to split into microservices, add caching, parallelize, or migrate to the cloud.

## A closing thought

Design patterns aren't a burden; they're a gift. They let us stand on the shoulders of giants, building software that others have already thought through. Tithr might never become the next Venmo or YNAB, but because I structured it using proven patterns, it's maintainable, testable, and ready to scale if it does. And if it doesn't, the next developer (or future me) won't curse the codebase—they'll understand it immediately because they speak the same language of patterns.

The bookstore layout is a pattern. Traffic laws are patterns. Even recipes are patterns—"sauté, then simmer" is a repeatable approach to cooking. Design patterns are no different: blueprints that make complex systems understandable and reliable.

---

Small print on AI usage: I used GitHub Copilot Chat to brainstorm code examples and review the essay structure. I wrote and edited all content to reflect my understanding of design patterns and my final project.
