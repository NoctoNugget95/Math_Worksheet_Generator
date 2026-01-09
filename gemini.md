# 🧭 AI Developer Protocol: Universal Adaptive

## 🎯 Prime Directive
**Goal:** Adapt to the existing project structure immediately.
**Platform Target:** **Universal (Seamless Desktop <-> Mobile).**
**Constraint:** The application must offer a **Seamless Transition** between devices. It must look native on a 4K monitor and be fully functional on a phone without horizontal scrolling or "chunky" layout shifts.

---

## 🔍 Phase 1: Pattern Recognition (RUN THIS FIRST)
**Scan the file structure to identify the "Source of Truth" for logic:**

### 🟢 Pattern A: Data-Driven / Config-Based
* **Signs:** Logic/Structure defined in `.json` files (e.g., `levels.json`, `questions.json`).
* **Rule:** **RESPECT THE JSON.** Do not hardcode values into JS if a JSON file exists.
* **Action:** Check if changes belong in the JSON config or the JS interpreter.

### 🔵 Pattern B: The Monolith (No-Build)
* **Signs:** Single `index.html` or `.js` file. No build tools.
* **Rule:** Keep it simple. No `import`/`export`. No `npm`. Use Global State.

### 🟣 Pattern C: The Full Stack (Future)
* **Signs:** `/server` folder, `package.json`, `requirements.txt`.
* **Rule:** Enforce strict separation of concerns. Use modules.

---

## 🛠 Phase 2: Universal Coding Standards

### 1. 📱 Universal Viewport & Interaction
* **Viewport Integrity:**
    * **ALWAYS** ensure this tag is present: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.
    * **NEVER** use fixed pixel widths on root containers (e.g., `body { width: 1000px }` is forbidden). Use `width: 100%`, `max-width`, or `min-height`.
* **The "Co-Existence" Rule:**
    * **Inputs:** Interactive elements must work with **BOTH** Mouse Click and Finger Tap.
    * **Hover:** Never hide critical functionality behind `:hover` alone. Always provide a click/tap alternative.
    * **Target Size:** Interactive elements must have a minimum touch target of **44x44px** (use padding to achieve this without ruining visual density).

### 2. 📐 Layout & Continuity (Desktop <-> Mobile)
* **The "Stacking" Strategy:**
    * **Mobile Default:** Always build layouts as `flex-col` (vertical stack) by default.
    * **Desktop Enhancement:** Use media queries (`@media (min-width: 768px)`) to switch to `flex-row`. This prevents "squashed" columns on phones.
* **Handling Fixed Content (e.g., Worksheets/Canvas):**
    * If an element *must* be a fixed size (e.g., `8.5in` paper), **DO NOT squish it.**
    * **Solution:** Wrap the fixed element in a container with `overflow-x: auto` (scrollable) OR use `transform: scale(...)` to fit it to the screen width dynamically.

### 3. 🧠 Logic & Architecture
* **Separation of Concerns:**
    * **Math/Logic:** Must be **Pure Functions** (Input -> Output). Do not reference DOM inside calculation functions.
    * *Why?* Allows logic to move to Backend/Python later without rewriting.
* **State Management:**
    * **Centralized State:** Use a single state object (e.g., `const AppState = { ... }`) rather than scattered variables.

### 5. 🧩 Understanding the Layers: HTML, CSS, JS Interplay
*   **The "Concentric Circles" Analogy:**
    *   **HTML (Outer Circle - Structure):** The foundation, the nouns, the content. It defines *what* is on the page.
    *   **CSS (Middle Circle - Presentation):** The adjectives, how the HTML elements *look*. It styles the structure.
    *   **JavaScript (Bullseye - Behavior/Interaction):** The verbs, *what* the HTML elements *do* and how they change. It can dynamically manipulate both HTML and CSS.
*   **The "Why" in Coding Decisions:**
    *   **Purpose-Driven:** Every line of code, every design choice, must have a clear "why."
    *   **Interconnectedness:** Understand how changes in one layer (e.g., a JavaScript function) impact another (e.g., the CSS styling of an HTML element). This is crucial for debugging and making informed architectural decisions.


### 4. ⚡ Async & Data Safety
* **The "Spinner" Rule:** Never initiate a fetch without visually indicating "Loading".
* **Error Resilience:** **ALWAYS** implement `.catch()` for Promises and handle empty data states.

### 5. 🖨️ Print & Visual Fidelity
* **Physical Constraints:** If fixed dimensions exist (e.g., `8.5in`), **PRESERVE THEM** for the print layout.
* **Print Styles:** **NEVER** remove `@media print` blocks. Do not force Dark Mode on print containers.

---

## 🛡️ Phase 3: The "Anti-Hallucination" Check
**Before outputting code, verify:**

1.  **Viewport Check:** "Did I include the `<meta viewport>` tag?"
2.  **Layout Check:** "If I shrink the window to 375px, will the sidebar squash the content?" (If yes, move sidebar to bottom or hamburger menu).
3.  **Input Check:** "Did I handle `touchstart` alongside `mousedown`?"
4.  **JSON Safety:** "Did I leave a trailing comma in a JSON block?"
5.  **Syntax Closure:** "Did I close every bracket `}` and tag `</div>`?"

---

## 📝 Tone & Protocol
* **Ask Before Refactoring:** If code looks "ugly" (monolithic), assume it is intentional.
* **Backend Prep:** Write logic decoupled from the view (ready for server migration).