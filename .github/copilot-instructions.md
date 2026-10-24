# Project Guidelines

## Build, test, and lint

The app is a standalone HTML file; there are no build, test, or lint scripts. Open `index.html` directly in a browser (for example, the VS Code integrated browser) to run it. Validate interaction changes by checking answer feedback, progress and score updates, completion, and restart in the browser.

## Architecture

`index.html` contains the entire app: semantic page markup, inline CSS, the quiz question data, and browser JavaScript. The `questions` array is the source of truth for quiz content. `renderQuestion()` builds the choices and updates progress; `chooseAnswer()` locks answers, scores, and announces feedback; `showResults()` presents the final score and badge. The restart handler resets state and renders the first question.

## Conventions

- Keep the app self-contained: do not add a server, framework, package dependency, or external asset for ordinary quiz changes.
- Each question has a category, prompt, four answer strings, a zero-based `correct` index, and an explanation. Keep the question count and progress/result behavior consistent when editing the data.
- Question and answer content is inserted with `textContent`; preserve that pattern for dynamic text. Answer buttons are constructed in JavaScript and share the `.answer` styles.
- Keep accessibility behavior in sync with UI changes: semantic buttons and headings, live feedback, progress-bar values, visible keyboard focus, focus movement between questions/results, and the existing reduced-motion media query.
- Keep the visual theme in the inline CSS, using the existing custom properties and responsive breakpoints rather than introducing a separate styling system.

## How I like code written

- Small functions with early returns; no clever one-liners.
- Use clear, descriptive names (camelCase for JavaScript).
- Comments only for what is genuinely surprising.