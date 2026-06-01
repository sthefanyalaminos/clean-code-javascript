# Clean Code JavaScript — Thematic Study Notebook with NotebookLM

Exploring AI as an active learning tool: source curation, prompt engineering, and building a study guide on JavaScript best practices.

<div align="right"> 
<a href="https://notebooklm.google.com/notebook/0ad614a6-a63c-4813-81f5-11412e79173c">Click here to access the notebook!</a>
</div>

## Context and Objectives
 
### Why Clean Code in JavaScript?
 
JavaScript is one of the most widely used languages in the world — and for that very reason, it's also one of the most commonly written in a messy way. When starting out, it's natural to focus on making code work, but it's equally necessary to learn how to make it communicate.

### Study Goals
 
- Understand the **core principles** of clean code applied to JavaScript;
- Learn to **name variables and functions** semantically and intentionally;
- Know when and how to **refactor** code that works but is hard to maintain;
- Build a **personal glossary** of the most relevant concepts;
- Create a **reusable prompt library** for future AI-assisted review.

---
## Source Curation
 
The sources below were selected for being open, reliable, and complementary. All were uploaded to NotebookLM to ground the generated responses.
 
| # | Title | Type | Link |
|---|-------|------|------|
| 1 | **Clean Code JavaScript** — ryanmcdermott | GitHub repository (text) | [github.com/ryanmcdermott/clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript) |
| 2 | **Eloquent JavaScript** — Ch. 4 & 5 (Functions and Data Structures) | Open book (online) | [eloquentjavascript.net](https://eloquentjavascript.net/) |
| 3 | **MDN Web Docs — JavaScript Guide** | Official documentation | [developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide) |
| 4 | **Refactoring Guru — Refactoring in JS** | Technical articles | [refactoring.guru/refactoring](https://refactoring.guru/refactoring) |
| 5 | **Google JavaScript Style Guide** | Official style guide | [google.github.io/styleguide/jsguide.html](https://google.github.io/styleguide/jsguide.html) |
 
---
## Prompt Engineering & Lessons Learned
 
This section documents the real exploration process inside NotebookLM — what worked, what didn't, and how prompts were adjusted along the way.
 
### Round 1 - Starting point
 
**Initial prompt:**
```
What is Clean Code?
```
 
**Problem:** The response was too broad. Even though it was grounded in the sources, the concepts weren't explored in depth.
 
**Adjustment:**
```
Based on the notebook sources, what are the main Clean Code principles applied specifically to JavaScript?
```
 
**Result:** The AI listed principles with direct references to the sources and went deeper into each one, including code examples.
 
**Lesson learned:** Specifying "based on the sources" and "applied to JavaScript" completely changes the quality of the response.
 
---
### Round 2 - Variable naming
 
**Prompt:**
```
What are the best practices for naming variables and functions in JavaScript according to the sources?
```
 
**Result:** A solid response with naming examples, rules, and formatting conventions.
 
**Variation tested:**
```
Give me 5 real examples of bad variable names in JS and how to rewrite them using Clean Code.
```
 
**Result:** The AI also covered naming rules and conventions, and added a before/after format that is very useful for review.
 
---
### Round 3 - Code comments
 
**Prompt:**
```
When should and shouldn't I comment my JavaScript code? What do the sources say about this?
```
 
**Result:** The response drew a clear distinction between comments that explain *what* (unnecessary when the code is clear) vs. comments that explain *why* (valid when the context isn't obvious).
 
---
### Round 4 - Prompts for future review
 
**Prompt:**
```
Based on everything we discussed, create a list of questions I can use to review Clean Code in JavaScript in the future.
```
 
**Result:** Generated over 10 review questions. The best ones were used in the reusable prompts section below.
 
---
## Study Mini-Guide
 
### 1. Structured Summaries
 
#### Naming (Variables and Functions)
 
- Use names that **reveal intent**. If you need a comment to explain the name, the name is wrong.
- Boolean variables should start with `is`, `has`, `can` → `isActive`, `hasPermission`
- Avoid obscure abbreviations: `usr` → `user`, `calc` → `calculateTotal`
- Functions should use **verb names**: `getUser()`, `sendEmail()`, `validateInput()`
```js
// ❌ Bad
const d = new Date();
const u = getU();
function proc(x) { ... }
 
// ✅ Good
const currentDate = new Date();
const activeUser = getActiveUser();
function processPayment(order) { ... }
```
 
---
#### Functions
 
- **One function, one responsibility.** If you need "and" to describe what it does, it does too much.
- Prefer **fewer parameters**: more than 3 is a warning sign. Use a configuration object instead.
- Avoid undeclared **side effects**: functions shouldn't modify external variables without making it obvious.
- Prefer **returning values** over directly modifying state.
```js
// ❌ Bad — does two things and has a side effect
function saveAndNotify(user) {
  db.save(user);
  sendEmailNotification(user.email);
}
 
// ✅ Good — separated responsibilities
function saveUser(user) { return db.save(user); }
function notifyUser(email) { return sendEmailNotification(email); }
```
 
---
#### Comments
 
- **Good code explains itself.** A comment is not a substitute for a bad name.
- Comment the **why**, not the **what**.
- Remove outdated comments — they're worse than no comment at all.
- TODO comments are acceptable while learning, but not in production without a planned resolution.
```js
// ❌ Bad — the comment just repeats the code
let age = 25; // sets age to 25
 
// ✅ Good — the comment explains a non-obvious decision
// Using index 1 because the API returns 1-based, not 0-based
const firstItem = items[1];
```
 
---
#### Structure and Formatting
 
- Use **ESLint** and **Prettier** to automate consistency.
- Keep **lines short** (max ~80–100 characters).
- Group related code together; separate groups with a blank line.
- Avoid deep nesting (more than 2–3 levels of `if`/`for`): use **early return** or function extraction.
```js
// ❌ Bad — deep nesting
function processOrder(order) {
  if (order) {
    if (order.items.length > 0) {
      if (order.isPaid) {
        // process
      }
    }
  }
}
 
// ✅ Good — early return
function processOrder(order) {
  if (!order) return;
  if (order.items.length === 0) return;
  if (!order.isPaid) return;
  // process
}
```
 
---
### 2. Concept Glossary
 
| Term | Definition |
|------|------------|
| **Clean Code** | Code written to be read by humans — clear, simple, no surprises |
| **Naming** | The practice of choosing names that reveal intent without needing comments |
| **Single Responsibility** | Principle that each function/module should have only one reason to change |
| **Side Effect** | When a function modifies external state beyond returning a value |
| **Early Return** | Technique of returning early in functions to avoid unnecessary nesting |
| **Refactoring** | Rewriting existing code to improve readability without changing behavior |
| **Magic Number** | A literal number in code with no name or context — should be replaced with a named constant |
| **DRY (Don't Repeat Yourself)** | Principle of avoiding logic duplication — extract repeated code into reusable functions |
| **KISS (Keep It Simple)** | Prefer the simplest solution that works — unnecessary complexity is a potential bug |
| **Linter** | A tool (e.g. ESLint) that automatically analyzes code for style issues and errors |
| **Prettier** | A code formatter that standardizes indentation, quotes, commas, etc. automatically |
| **Code Smell** | A signal in the code that indicates a potential design problem, even if the code works |
 
---
