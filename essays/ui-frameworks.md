---
layout: essay
type: essay
title: "Frameworks, not crutches: what Bootstrap 5 really buys you"
# All dates must be YYYY-MM-DD format!
date: 2025-10-08
labels:
  - UI
  - Bootstrap 5
  - Semantic UI
  - ICS 314
---

<img width="320px" class="rounded float-start pe-4" src="../img/websitebuilders.png" alt="Example UI built with a framework">

Designing a clean, responsive interface with just raw HTML and CSS is possible—but it’s rarely efficient. UI frameworks like Bootstrap 5 and Semantic UI trade some learning curve for speed, consistency, and accessibility out of the box. In ICS 314, that trade has paid off for me: I spent less time wrestling with flexbox quirks and more time focusing on the product.

## Why not just use raw HTML/CSS?

You can—and you should learn the fundamentals. But frameworks provide:

- A design system: sensible defaults for spacing, color, typography, and states.
- Layout primitives: a well-tested grid, flex helpers, and utilities for common patterns.
- Accessibility affordances: focus states, color contrast guidance, and ARIA-friendly components.
- Documentation and examples: copy/paste-able patterns that reduce time-to-first-UI.

In practice, frameworks reduce “yak shaving” so you can ship faster and with fewer layout regressions across devices.

## What you get for the investment

- Consistent spacing and typography via tokens and utilities (e.g., `p-3`, `gap-2`, `lh-lg`).
- Responsive grid and visibility helpers (`col-12 col-md-6`, `d-none d-md-block`).
- Component primitives that compose well: cards, navbars, modals, toasts, forms.
- A mature ecosystem: themes, icon sets, and a long tail of community tips for edge cases.

Here’s a tiny side-by-side to illustrate the upgrade in ergonomics.

### Raw CSS approach

```html
<!-- HTML -->
<div class="card-list">
  <article class="card">
    <h3>Project A</h3>
    <p>Short description…</p>
  </article>
  <article class="card">
    <h3>Project B</h3>
    <p>Short description…</p>
  </article>
</div>

<!-- CSS -->
.card-list { display: grid; grid-template-columns: 1fr; gap: 1rem; }
@media (min-width: 768px) {
  .card-list { grid-template-columns: 1fr 1fr; }
}
.card { border: 1px solid #ddd; border-radius: 0.5rem; padding: 1rem; }
```

### Bootstrap 5 approach

```html
<div class="row g-3">
  <div class="col-12 col-md-6">
    <div class="card h-100">
      <div class="card-body">
        <h5 class="card-title">Project A</h5>
        <p class="card-text">Short description…</p>
      </div>
    </div>
  </div>
  <div class="col-12 col-md-6">
    <div class="card h-100">
      <div class="card-body">
        <h5 class="card-title">Project B</h5>
        <p class="card-text">Short description…</p>
      </div>
    </div>
  </div>
</div>
```

You get responsive columns, spacing (`g-3`), consistent card styling, and better defaults—without writing custom media queries or borders.

## Bootstrap 5 vs. Semantic UI

My experience:

- Bootstrap 5
  - Strengths: ubiquitous examples, robust grid/utilities, strong docs, large ecosystem (themes, icons).
  - Tradeoffs: utility classes can get verbose; it’s easy to ship “Bootstrap-looking” UIs without customization.
- Semantic UI
  - Strengths: readable class names (`ui button`, `very padded segment`) and a declarative feel.
  - Tradeoffs: smaller ecosystem today; some packages lag behind modern build tooling.

I reach for Bootstrap when I need velocity and predictable responsiveness. I’d consider Semantic UI for teams who value the more “English-like” class names and are willing to invest in theming.

## Pitfalls to avoid

- Over-reliance on defaults: customize the theme (colors, spacing) to avoid a generic look.
- Deeply nested markup: keep components shallow and leverage utilities instead of custom wrappers.
- Ignoring a11y: frameworks help, but you still need semantic HTML, labels, and contrast checks.
- CSS bloat: remove unused CSS (e.g., only include needed components, or use a custom build).

## How I use frameworks in ICS 314

- Start with a quick wireframe, then translate to Bootstrap grid + utilities.
- Swap default colors/spacing to match the project’s tone.
- Use components for common patterns (navbars, cards, forms) and write custom CSS only when needed.
- Keep an “Accessibility checklist” pass before calling the page done.

Result: faster iteration, fewer layout bugs, and a UI that scales from mobile to desktop with minimal fuss.

## Conclusion

UI frameworks aren’t a crutch—they’re a leverage point. They package years of design and accessibility lessons into a toolkit you can apply in hours, not weeks. Learn the fundamentals, then let frameworks amplify them.

---

Small print on AI usage: I used GitHub Copilot Chat to brainstorm the outline and to review grammar. I wrote and edited the content to reflect my current understanding and voice.
