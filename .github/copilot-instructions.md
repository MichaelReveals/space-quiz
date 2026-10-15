# Repository instructions

## Run and validate

- Open `index.html` directly in a browser; the quiz uses no server, package manager, or external dependencies.
- There are no configured build, test, or lint commands. For a browser smoke check, start the quiz, answer both correctly and incorrectly, advance through all 10 questions, and check the score, progress, feedback, and results screen. Also verify keyboard focus moves to the question after each advance and to the next action after answering.

## Architecture

- This is a static, single-file web app. `index.html` contains all markup, CSS, quiz data, and JavaScript; keep it runnable from a `file://` URL with no network access or build step.
- The UI has three mutually exclusive screens: welcome, quiz, and results. `startQuiz`, `showQuestion`, `chooseAnswer`, and `showResults` drive screen state and update the DOM.
- The `questions` array is the quiz content source. Each entry supplies its category, prompt, four options, zero-based correct-option index, and explanatory fact; score and progress derive from the current question and user answers.

## Project conventions

- Keep the experience dependency-free and self-contained. Do not introduce a framework, module loader, external assets, or runtime network requests without changing the static/offline requirement.
- Use CSS custom properties for shared colors and surfaces. The base variables define the dark theme; `prefers-color-scheme: light` overrides them. Keep additions compatible with both schemes.
- Preserve semantic buttons and headings, the live feedback status, the labeled progress bar, and intentional focus movement: question on start/advance, next-question action after answering, and restart action on results.
- Render question and feedback strings with `textContent`, and retain the `prefers-reduced-motion` override when changing animations.
