# Module 2 — JavaScript Fundamentals (Full Lesson Scripts)

> **For the tutor:** This is your worked script for Module 2. Each lesson gives you the substance, the analogy to lead with, the check questions, the hands-on task, and the "done when" bar — so you teach the concept rather than improvise it. Follow the teaching method from the project instructions: explain → check → one small task → explain-it-back, and never advance until Brendan can put it in his own words. Keep each lesson to ~20–25 minutes; some (2.8–2.12 especially) will legitimately spill across two sittings — that's fine, don't rush them.
>
> Brendan knows **HTML and CSS well.** He has **no JavaScript** background but finished Module 1, so he already owns: client/server, request/response, HTTP methods and status codes, DNS, JSON, what an API is, and frontend/backend/database. **Use that constantly** — JS is "the language that makes the client do things," and JSON/fetch/APIs are where this module cashes out. He can't install anything — everything below runs in a Claude artifact, the browser DevTools Console, or a browser IDE (CodePen, CodeSandbox, StackBlitz). The bar for this whole module is **not** "become a JS developer" — it's **read the AI's JS, understand it, fix it.**

---

## Lesson 2.1 — Variables & types

**Goal:** the absolute grammar. A place to store a value, and the handful of kinds of values JS cares about.

**Lead with this:** In CSS he writes things like `color: blue;` — a fixed value baked into the file forever. JavaScript's whole superpower is that values can *change while the page is running.* A **variable** is a labeled box that holds a value right now, and can hold a different value five seconds from now.

**The explanation:**
- Declare with `let` (value can change later) or `const` (value is locked once set). Default to `const`; reach for `let` only when you know the value will change.
  ```js
  const name = "Brendan";
  let clickCount = 0;
  ```
- JS's core value types (he'll recognize most from JSON in 1.5 — same vocabulary, now *alive*):
  - **String** — text, in quotes: `"hello"`.
  - **Number** — `42`, `3.14`. No separate "integer" type to worry about.
  - **Boolean** — `true` / `false`.
  - **Array** and **Object** — the container types from 1.5, coming back properly in 2.6–2.7.
  - `undefined` / `null` — "nothing here yet" (two flavors, don't stress the difference now).
- Naming: `camelCase` by convention (`clickCount`, not `click_count` or `Click Count`) — flag this since JSON examples sometimes used spaced keys.

Analogy: variables are labeled sticky notes on boxes. `const` is a sticky note taped shut — write the value once, done. `let` is a sticky note you're allowed to peel off and rewrite.

**Check understanding:**
- If a value should never change after you set it, `let` or `const`? Why default to that?
- Which type would you use to store "is the user logged in" — string, number, or boolean?

**Hands-on task:** In a Claude artifact or the browser Console (F12 → Console tab, type directly, hit Enter — zero setup), declare three variables about himself: his name (string), years in his career (number), and whether he knows JavaScript yet (boolean, and yes the honest answer is about to change). Log each with `console.log(name)`.

**Done when:** he can explain the difference between `let` and `const` in his own words, and can correctly name the type of a value someone shows him (string/number/boolean).

**If he's stuck:** skip the console and just have him predict, out loud, the type of five things you name ("my age," "is it Friday," "my job title") before writing any code — types first, syntax second.

---

## Lesson 2.2 — Functions

**Goal:** a reusable block of instructions. The single most common shape of AI-generated code.

**Lead with this:** He's written the same CSS rule for five different elements before, copy-pasted with tweaks. A **function** is JS's answer to "stop repeating yourself" — write the instructions once, run them as many times as you want, with different inputs each time.

**The explanation:**
- Anatomy of a function:
  ```js
  function greet(personName) {
    return "Hello, " + personName + "!";
  }

  greet("Brendan"); // "Hello, Brendan!"
  greet("Team");    // "Hello, Team!"
  ```
- **Parameters** (`personName`) are placeholders for input — filled in each time the function is *called*.
- **`return`** is the function handing back an answer. Not every function returns something (some just *do* a thing, like changing the page — that comes in 2.8–2.10).
- Defining a function ≠ running it. `function greet(...) {...}` just writes the recipe. `greet("Brendan")` is actually cooking it. This trips everyone up once — call it out directly.
- Also show the shorter modern shape he'll see constantly in AI output, arrow functions:
  ```js
  const greet = (personName) => "Hello, " + personName + "!";
  ```
  Same thing, different spelling. He doesn't need to write these yet, just recognize them.

Analogy: a function is a recipe card. Writing the recipe (defining it) doesn't make dinner appear. You have to actually *cook it* (call it), and the ingredients you hand in (parameters) change the result each time — same recipe, different sandwich.

**Check understanding:**
- What's the difference between *defining* a function and *calling* it?
- If `greet` takes a `personName` parameter, what happens if you call `greet("Brendan")` versus `greet("Team")`?

**Hands-on task:** Write a function `shout(sentence)` that returns the sentence in all caps with an exclamation point (hint: strings have a `.toUpperCase()` method he can Google or you can hand him). Call it three times with different sentences and `console.log` each result.

**Done when:** he can point to the parameter, the return value, and correctly distinguish "I wrote the function" from "I ran the function" in his own code.

**If he's stuck:** strip the caps/exclamation part entirely — just get `function shout(x) { return x; }` calling and returning correctly first, then layer the transformation back in.

---

## Lesson 2.3 — More functions / scope

**Goal:** where variables live and who can see them. This is what makes bugs feel mysterious until it clicks.

**Lead with this:** In CSS, styles cascade and can leak everywhere unless scoped (`!important` fights, specificity wars — he's lived this). JS variables have a similar containment rule, but stricter: **a variable declared inside a function only exists inside that function.**

**The explanation:**
- **Scope** = where a variable is visible/usable.
  ```js
  function makeSandwich() {
    const filling = "turkey"; // only exists inside makeSandwich
    return filling;
  }

  console.log(filling); // ERROR — filling doesn't exist out here
  ```
- Variables declared *outside* any function (global scope) can be seen everywhere, including inside functions.
- Variables declared *inside* a function (local scope) exist only inside that function, and disappear when it's done running.
- Why this is good, not annoying: it means two different functions can both use a variable named `total` without stepping on each other. Scope is a safety fence, not a limitation.
- Briefly mention **parameters are local too** — `personName` in 2.2's `greet` function doesn't exist outside it.

Analogy: scope is like rooms in a house. What's on the kitchen counter (local to that function) isn't visible from the bedroom. Stuff left in the hallway (global scope) is visible from every room.

**Check understanding:**
- If you declare `const x = 5` inside a function, can code *outside* that function read `x`? Why or why not?
- Why is it useful that two separate functions can each have their own variable called `count` without conflict?

**Hands-on task:** Write two small functions, each declaring a local variable with the *same name* (e.g., both use `let total = 0` internally, but each does something different with it — one adds numbers, one counts letters in a word). Run both, log both results, and confirm they don't interfere with each other.

**Done when:** he can predict, without running it, whether a variable declared in one function is visible in another, and can explain why that's a feature.

**If he's stuck:** have him deliberately trigger the "variable doesn't exist" error from the first example above — seeing the actual error message makes the boundary concrete instead of abstract.

---

## Lesson 2.4 — Conditionals

**Goal:** how code makes decisions. This is the logic the AI is *always* writing on his behalf — time to read it.

**Lead with this:** CSS has `:hover`, media queries — "if this condition, apply this style." JS's `if` statement is the general-purpose version: **if something is true, do this; otherwise, do that.**

**The explanation:**
- Basic shape:
  ```js
  const isLoggedIn = true;

  if (isLoggedIn) {
    console.log("Welcome back!");
  } else {
    console.log("Please log in.");
  }
  ```
- Comparisons produce booleans, which is what `if` checks: `===` (equals — always use the triple-equals, not double, he doesn't need to know why yet, just the convention), `!==` (not equals), `<`, `>`, `<=`, `>=`.
- Combine conditions: `&&` (and — both must be true), `||` (or — at least one must be true).
  ```js
  if (age >= 18 && hasTicket) {
    console.log("You're in.");
  }
  ```
- `else if` chains for more than two branches.
- The idea to land: **every `if` is a fork in the road, and the condition is always something that evaluates to `true` or `false`** — same boolean type from 2.1.

Analogy: a bouncer at a club checking a list. One question, one gate: if the condition holds, you go one way; if not, you go the other. Chained `else if`s are just more gates in a row.

**Check understanding:**
- If `age = 16` and the check is `age >= 18`, which branch runs?
- What's the difference between `&&` and `||` in plain English?

**Hands-on task:** Write a function `checkAge(age)` that returns `"child"` if under 13, `"teen"` if 13–17, and `"adult"` if 18 or older, using `if` / `else if` / `else`. Test it by calling it with three different ages and logging the results.

**Done when:** he can trace, by hand, which branch of an `if`/`else if`/`else` chain will run for a given input, before running the code to check himself.

**If he's stuck:** remove the chain entirely — get a single `if`/`else` working with one clean boolean first, then add the middle branch back in.

---

## Lesson 2.5 — Loops

**Goal:** doing something many times without writing it many times. The mechanical partner to functions.

**Lead with this:** If he ever wanted five `<div>`s each with slightly different content, he's hand-typed them or copy-pasted. A **loop** is "do this thing, N times, changing one detail each time" — automatically.

**The explanation:**
- The workhorse loop, `for`:
  ```js
  for (let i = 0; i < 5; i++) {
    console.log("Item number " + i);
  }
  ```
  Three parts, in order: start (`let i = 0`), keep-going condition (`i < 5`), and what happens after each pass (`i++`, "add one to i").
- Trace it out loud once, step by step, so it's not magic: i starts at 0 → is 0 < 5? yes → log it → i becomes 1 → is 1 < 5? yes → ... → i becomes 5 → is 5 < 5? no → stop.
- Briefly preview `for...of` (loop over each item in an array directly — no counter needed) since it's what he'll actually reach for once arrays land in 2.6:
  ```js
  const fruits = ["apple", "banana", "cherry"];
  for (const fruit of fruits) {
    console.log(fruit);
  }
  ```
- Land the idea: loops are how a tiny bit of code touches a lot of data. Every table, list, or feed he's ever seen rendered on a page was very likely built by a loop running once per item.

Analogy: a loop is a factory line worker doing the same motion on every box that comes down the belt, until the belt is empty. The `for` loop's three parts are: where the belt starts, when to stop, and how far it moves each time.

**Check understanding:**
- In `for (let i = 0; i < 5; i++)`, how many times does the loop body run, and what's the *last* value of `i` inside it?
- Why would you use `for...of` instead of a counting `for` loop if you already have a list of items?

**Hands-on task:** Write a `for` loop that logs the numbers 1 through 10. Then modify it to log only the *even* numbers 1 through 10 (hint: an `if` inside the loop, checking `i % 2 === 0` — introduce `%` as "remainder after dividing," useful shorthand for even/odd).

**Done when:** he can hand-trace a simple `for` loop's iterations on paper/out loud before running it, and correctly predicts how many times it will run.

**If he's stuck:** have him log `i` on every single pass with no other logic, and literally count the printed lines against his prediction — the mismatch (if any) reveals exactly where his mental model of start/condition/step is off.

---

## Lesson 2.6 — Arrays

**Goal:** ordered lists of data, properly — the container type from JSON, now something he can build and manipulate.

**Lead with this:** Back in 1.5, `[ ]` meant "an ordered list" in JSON. Same thing in JS, except now it's *alive* — he can add, remove, and read items out of it in code.

**The explanation:**
- Creating and reading:
  ```js
  const skills = ["HTML", "CSS", "SEO"];
  console.log(skills[0]); // "HTML" — indexes start at 0, not 1
  console.log(skills.length); // 3
  ```
  **Zero-indexing** is the one genuinely weird rule here — call it out explicitly and repeat it. First item is `[0]`, not `[1]`.
- Common operations he'll see constantly in AI code:
  - `.push(item)` — add to the end.
  - `.length` — how many items.
  - Looping over one with `for...of` (from 2.5) to touch every item.
- Combine with 2.5: looping over an array is *the* most common pattern in real code — "for each item in this list, do something."
  ```js
  for (const skill of skills) {
    console.log("I know " + skill);
  }
  ```

Analogy: an array is a numbered coat check rack. Item 1 hangs on hook `[0]` (annoying but true), item 2 on `[1]`, and so on. `.length` is just "how many hooks are currently full."

**Check understanding:**
- If `skills[0]` is `"HTML"`, what is `skills[1]`?
- Why does looping over an array with `for...of` save you from writing `skills[0]`, `skills[1]`, `skills[2]` by hand?

**Hands-on task:** Build an array of 5 of his real skills. Log its `.length`. Then write a `for...of` loop that logs `"Skill: " + skill` for each one. Finally, `.push()` one more skill and re-log the length to confirm it grew.

**Done when:** he can correctly read any index out of an array (including catching a zero-index mistake), and can loop over an array to touch every item without hand-writing each index.

**If he's stuck:** draw the coat-check rack literally — numbered hooks starting at 0 — and have him point to which hook `[2]` is before writing any code.

---

## Lesson 2.7 — Objects + `map` / `filter` / `find`

**Goal:** the other container type from JSON, now alive — plus the three array methods he will see in *every single* piece of AI-generated JS from here on.

**Lead with this:** `{ }` in JSON meant "one thing, described by key-value pairs." Same in JS. And once he has an *array of objects* (a list of things, each with properties) — which is basically what every API response looks like — three methods let him work with that list without writing a manual loop each time.

**The explanation:**
- Objects: a single thing with named properties.
  ```js
  const person = {
    name: "Brendan",
    role: "web author",
    yearsExperience: 8
  };
  console.log(person.name); // dot notation — "Brendan"
  ```
- Now the array-of-objects shape he'll see everywhere (this *is* what JSON from an API looks like once it lands in JS):
  ```js
  const users = [
    { name: "Ana", age: 28 },
    { name: "Sam", age: 34 },
    { name: "Lee", age: 19 }
  ];
  ```
- **`.map()`** — transform every item into something new, same number of items out as in:
  ```js
  const names = users.map(user => user.name);
  // ["Ana", "Sam", "Lee"]
  ```
- **`.filter()`** — keep only the items that pass a test, fewer (or equal) items out:
  ```js
  const adults = users.filter(user => user.age >= 21);
  // [{ name: "Sam", age: 34 }]
  ```
- **`.find()`** — get the *first single* item that matches, not a list:
  ```js
  const sam = users.find(user => user.name === "Sam");
  // { name: "Sam", age: 34 }
  ```
- The one-line distinction that matters: **map transforms, filter narrows, find grabs one.** These three, plus the loop from 2.5, cover the vast majority of "do something to a list" code he'll ever read.

Analogy: you have a box of mixed fruit (the array). `.map()` is peeling every piece (same count, transformed). `.filter()` is picking out only the ripe ones (fewer pieces, same box shape). `.find()` is reaching in and grabbing the first banana you see, then stopping.

**Check understanding:**
- If you `.filter()` an array of 10 users for `age >= 21` and only 4 qualify, how many items are in the result?
- What's the difference between what `.filter()` returns and what `.find()` returns, even when only one item matches?

**Hands-on task:** Build the `users` array from above (or his own 4–5 fake people with `name` and `age`). Use `.map()` to get an array of just their names. Use `.filter()` to get everyone 21 or older. Use `.find()` to get the first person named something specific. Log all three results.

**Done when:** he can look at unfamiliar AI-generated code using `.map()`, `.filter()`, or `.find()` and correctly say what shape of result it produces without running it.

**If he's stuck:** go back to plain `for...of` first — solve the *same* task (get names, get adults, get one person) with a manual loop and an `if`, then show the `.map()`/`.filter()`/`.find()` version doing the identical thing with less code. The loop version de-mystifies what the shorthand is actually doing under the hood.

---

## Lesson 2.8 — The DOM (part 1)

**Goal:** how JavaScript sees the page it's running on. This is where his HTML/CSS knowledge starts paying off directly.

**Lead with this:** Everything so far has lived in the Console, disconnected from any actual page. Today, JS meets the HTML he already knows. The **DOM** (Document Object Model) is the browser's live, in-memory model of the page — and JS can read and change it.

**The explanation:**
- When the browser parses HTML (recall 1.1 — the response body), it builds the DOM: a tree of every element, matching the HTML structure he already knows (`<body>` contains `<div>`s, which contain `<p>`s, etc.).
- JS can **find** elements in that tree:
  ```js
  const heading = document.querySelector("h1");
  const allParagraphs = document.querySelectorAll("p");
  ```
  `document.querySelector(...)` takes a **CSS selector** — literally the same selector syntax he's used his whole career (`"h1"`, `".my-class"`, `"#my-id"`) — and returns the *first* matching element. `querySelectorAll` returns *all* matches (as a list he can loop over, tying back to 2.5).
- Once you have an element, you can **read or change** it:
  ```js
  console.log(heading.textContent); // read the text inside it
  heading.textContent = "New Title"; // change it — the page updates live
  heading.style.color = "blue"; // change a CSS property directly
  ```
- The idea to land: **the DOM is the bridge between "the HTML I wrote" and "the JS that can change it while someone's looking at the page."** This is the first lesson where code visibly *does* something on screen.

Analogy: the DOM is a real-time, touchable model-home version of his HTML blueprint. `document.querySelector` is walking into that model home and pointing at a specific wall. Once he's pointing at it, he can repaint it (`.style`) or knock the sign off and hang a new one (`.textContent`) — and the change happens *instantly*, live, no reload.

**Check understanding:**
- If `document.querySelector("h1")` finds the *first* `<h1>` on the page, what would `document.querySelectorAll("h1")` give you instead?
- What's the connection between the CSS selectors he already knows and what goes inside `querySelector(...)`?

**Hands-on task:** In a Claude artifact (build a tiny HTML page with a heading, a paragraph, and a button — no functionality yet), open the artifact's console or add a `<script>` tag, and: select the heading, log its `textContent`, then change it to something else and watch the page update. Then change the paragraph's `.style.color`.

**Done when:** he can select an element with a selector he'd recognize from CSS, and can both read and change something about it, watching the live page respond.

**If he's stuck:** start with `document.querySelector("body")` and just change *its* background color first — one giant, undeniable visual change removes any doubt that the code is really touching the real page.

---

## Lesson 2.9 — The DOM (part 2)

**Goal:** creating and removing elements, not just editing ones that already exist. This is how JS builds UI dynamically.

**Lead with this:** Part 1 was editing existing HTML. But most real apps *generate* HTML on the fly — a list of search results, a new comment, a card for each item in an array (2.6–2.7 connection incoming). Today: making new elements appear and disappear.

**The explanation:**
- Create an element, fill it in, and attach it to the page:
  ```js
  const newItem = document.createElement("li");
  newItem.textContent = "New task";
  document.querySelector("ul").appendChild(newItem);
  ```
  Three steps, always in this order: **create** it (in memory, invisible so far) → **fill it in** (textContent, style, etc.) → **attach** it to something already on the page (`appendChild`). Skipping step 3 is the #1 "why isn't anything showing up" bug — name that explicitly.
- Remove an element: `elementToRemove.remove()`.
- Now connect it directly to 2.5–2.7: this is *why* loops and arrays matter for real pages.
  ```js
  const tasks = ["Buy milk", "Walk dog", "Ship site"];
  const list = document.querySelector("ul");

  for (const task of tasks) {
    const item = document.createElement("li");
    item.textContent = task;
    list.appendChild(item);
  }
  ```
  Say it plainly: **this exact pattern — loop over an array, create an element per item, append it — is how essentially every list, feed, and grid of cards on the modern web gets built.** He's officially not far from rebuilding the card-rendering he saw on his own Sanity-powered site back in Lesson 1.3.

**Check understanding:**
- What are the three steps, in order, to get a brand-new element to actually show up on the page?
- If you have an array of 5 items and loop over it creating one `<li>` per item, how many `<li>`s end up in the list?

**Hands-on task:** Build a small artifact: a `<ul>` (empty) on the page, and a JS array of 4–5 real tasks or grocery items. Loop over the array and append one `<li>` per item to the `<ul>`. Confirm all items show up, then add one `.remove()` call to knock one back out.

**Done when:** he can build a small list on screen entirely from a JS array and a loop, and can explain why "append" is the step people forget.

**If he's stuck:** do it with a *single* hardcoded item first (no loop, no array) — create, fill, append, watch it appear — before reintroducing the loop over multiple items.

---

## Lesson 2.10 — Events, clicks, forms

**Goal:** making the page react to the user, not just to code running top-to-bottom automatically.

**Lead with this:** Everything so far ran the instant the script loaded. But real pages wait around and respond to *the user* — a click, a typed character, a submitted form. That's an **event**, and JS "listens" for them.

**The explanation:**
- Basic pattern — pick an element, tell it what to do when something happens:
  ```js
  const button = document.querySelector("button");

  button.addEventListener("click", function () {
    console.log("Button was clicked!");
  });
  ```
  `addEventListener(eventType, function)` — "when `eventType` happens on this element, run this function." The function only runs *later*, on click — not immediately when the page loads. That timing (define now, run later, maybe never) previews the mental shift needed for 2.11's async work.
- Common event types: `"click"`, `"input"` (typing in a field, fires on every keystroke), `"submit"` (a form being submitted).
- Reading form input:
  ```js
  const nameInput = document.querySelector("input");
  console.log(nameInput.value); // whatever the user typed
  ```
- Forms specifically need one extra thing — preventing the page from doing its old-school full-page-reload submit behavior:
  ```js
  const form = document.querySelector("form");
  form.addEventListener("submit", function (event) {
    event.preventDefault(); // stop the default reload
    console.log("Form submitted with:", nameInput.value);
  });
  ```
- Tie together 2.8–2.10: this is the full loop — **listen for an event → read/change the DOM in response.** That's the recipe behind almost every interactive thing he's ever clicked.

Analogy: `addEventListener` is posting a guard at a door who does nothing all day until one specific thing happens (someone knocks a certain way), and only then springs into action. The page isn't "running" the click handler constantly — it's just waiting, cheaply, until it's needed.

**Check understanding:**
- Does the function passed to `addEventListener` run immediately when the page loads, or only later? When, exactly?
- Why does a form need `event.preventDefault()` but a plain button click usually doesn't?

**Hands-on task:** Build a tiny artifact: a text input, a button, and an empty `<p>`. When the button is clicked, read the input's `.value` and set it as the paragraph's `textContent` (reusing 2.8's DOM-editing skill). Bonus if time allows: make it clear the input afterward.

**Done when:** he can wire up a click listener from scratch, correctly read a form field's value on that click, and explain in his own words why the listener "waits."

**If he's stuck:** strip out the input entirely first — get a button that just logs `"clicked"` to the console working, cleanly, before adding the complexity of reading form values.

---

## Lesson 2.11 — `async` / `await` (the big one)

**Goal:** the most important lesson in the module. How JS handles things that take *time* — and the direct bridge to everything in Module 1 about requests and responses.

**Lead with this:** Slow down here — genuinely take two sittings if needed. Everything so far ran instantly, line by line, top to bottom. But recall 1.1: a request to a server takes *real time* to travel across the internet and come back. JS needs a way to say "go start this, and come back to it whenever it's actually done" without freezing the whole page while it waits.

**The explanation:**
- The core problem, made concrete:
  ```js
  console.log("Before");
  // imagine something here that takes 3 seconds
  console.log("After");
  ```
  If JS just *waited* 3 seconds doing nothing else, the whole page would freeze — no clicks, no scrolling, nothing — for those 3 seconds. That's unacceptable, so JS doesn't work that way.
- A **Promise** is JS's placeholder for "a value that isn't ready yet, but will be." Don't over-explain the mechanics — the practical shape is what matters:
  ```js
  async function getData() {
    console.log("Starting...");
    const result = await someSlowThing(); // pause HERE, but only this function
    console.log("Got it:", result);
  }
  ```
  - `async` in front of `function` means "this function is allowed to pause and resume."
  - `await` in front of something means "pause *this function* right here until that thing finishes — but the rest of the page keeps working normally."
- The crucial distinction to hammer: **`await` pauses that one function, not the whole browser.** Everything else — clicks, animations, other code — keeps running. This is exactly how a page can show a loading spinner while data is still in flight (the request from 1.3, still traveling).
- Directly name the connection: "Remember in Module 1, a request goes out and takes time before the response comes back? `async`/`await` is JS's way of saying 'wait for that response, but don't freeze everything else while you do.'"

Analogy: ordering at a coffee shop (a callback to 1.1's delivery analogy, now sharper). You place your order (`await someSlowThing()`), and you personally stand there paused until your coffee is ready — but everyone *else* in the shop keeps talking, ordering, sitting down. Your line is paused; the shop isn't.

**Check understanding:**
- When you `await` something, does the entire page freeze, or just that one function's next line?
- What's the actual English-language reason JS needs `async`/`await` at all — what would go wrong without it?

**Hands-on task:** No real API yet (that's 2.12) — use a fake "slow thing" to feel the pause without needing the network. In a Claude artifact:
```js
function wait(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function demo() {
  console.log("Starting...");
  await wait(2000); // pauses 2 seconds
  console.log("2 seconds later!");
}

demo();
console.log("This logs immediately, before the 2-second line!");
```
Have him run it and predict, *before* running, the order the three `console.log`s will print. The surprising order (the last line prints before "2 seconds later!") is the entire lesson landing.

**Done when:** he can correctly predict the print order of the exercise above before running it, and can explain in his own words why `await` doesn't freeze the whole browser.

**If he's stuck:** remove `async`/`await` entirely and just run `console.log("Starting"); wait(2000); console.log("done")` — show him that without `await`, "done" prints instantly too, since nothing tells JS to actually pause. Then add `await` back and contrast the two outcomes side by side.

---

## Lesson 2.12 — `fetch` (the door to APIs)

**Goal:** the payoff of the entire module. Everything from Module 1 (request, response, JSON, API) and 2.11 (async/await) clicks together into one real, working piece of code.

**Lead with this:** He made a raw API call by pasting a URL into his address bar back in 1.6. Today he makes that *exact same call*, from code, and actually does something with the data that comes back.

**The explanation:**
- `fetch(url)` sends an HTTP GET request (1.3) to that URL and returns a Promise (2.11) — because, obviously, going out to a server takes time.
  ```js
  async function getJoke() {
    const response = await fetch("https://icanhazdadjoke.com/", {
      headers: { Accept: "application/json" }
    });
    const data = await response.json(); // parse the JSON body (1.5) into a real JS object
    console.log(data.joke);
  }

  getJoke();
  ```
- Walk the two `await`s explicitly, naming the Module 1 vocabulary out loud each time:
  1. `await fetch(url)` — pause until the **response** (1.3) arrives from the **server** (1.2). `response` now holds the status code and headers.
  2. `await response.json()` — the response **body** (1.3) arrived as raw JSON text (1.5); this parses it into an actual JS object/array he can use with dot notation, `.map()`, etc. (2.7).
- This is the exact mechanism behind the Sanity calls he inspected in his own site's Network tab back in Lesson 1.3 — same GET, same JSON response, now written as code instead of watched happening.
- Briefly mention `response.status` and `response.ok` exist for checking success (2.13 covers handling failure properly).

Analogy: `fetch` is placing the phone order from the restaurant analogy (1.1/1.6) — and now he's not just describing the steps, he's *dialing the number himself.* The first `await` is holding the phone, waiting for someone to pick up (the response). The second `await` is the order actually being read out to him and written down (parsing the JSON body).

**Check understanding:**
- After `const response = await fetch(url)`, does `response` already contain the usable data, or does something else need to happen first?
- Name, out loud, every Module 1 concept you can spot inside a single `fetch` call.

**Hands-on task:** In a Claude artifact, use `fetch` to call a free, no-key public API (same kind he used in 1.6 — a dad-joke, cat-fact, or similar API), `await` the JSON, and display the result on the actual page (reusing 2.8's DOM skills — set some element's `textContent` to the fetched data) instead of just logging it. Bonus: wrap it in a button click (2.10) so a fresh fact/joke loads on demand.

**Done when:** he can write a `fetch` + `await response.json()` call from scratch for a new API, correctly narrate what each `await` is waiting for, and get the real result rendered onto the page.

**If he's stuck:** split it into two separate exercises — first just `console.log(response.status)` right after the fetch (proving the request/response cycle alone, no JSON yet), then add `.json()` parsing as its own second step once the network round-trip itself feels solid.

---

## Lesson 2.13 — Errors, stack traces, `try`/`catch`

**Goal:** reading an error without panic, and handling failure gracefully instead of letting the page silently break.

**Lead with this:** Every request from 2.12 can fail — bad URL, server down (a 5xx from 1.3!), no internet. Right now his code has no plan for that. Today: making failure a handled case instead of a crash.

**The explanation:**
- What an error actually is: JS hits a line it can't execute and stops, printing a **stack trace** — a (surprisingly readable, once you know to skip most of it) trail of where the failure happened. Teach him to read *only the top* line and the *file/line number* first — ignore the rest on a first pass.
- `try`/`catch` — attempt something risky, and have a plan if it fails:
  ```js
  async function getJoke() {
    try {
      const response = await fetch("https://icanhazdadjoke.com/", {
        headers: { Accept: "application/json" }
      });
      const data = await response.json();
      console.log(data.joke);
    } catch (error) {
      console.log("Something went wrong:", error.message);
    }
  }
  ```
  Code in `try {}` runs normally. If *anything* in there throws an error, execution jumps straight to `catch (error) {}` instead of crashing the whole script.
- Also worth a line: `fetch` itself doesn't throw on a 404/500 (a "successful" request that got a *bad* status code back, 1.3) — checking `response.ok` or `response.status` is a separate, deliberate check, not automatic. Don't over-teach this distinction, just flag it exists.
- The idea to land: **errors are information, not chaos.** A stack trace is the program telling you exactly where and often why it broke — reading the top line first turns "the AI's code is broken and I don't know why" into "line 12 says X, let's look at line 12."

Analogy: a stack trace is like a car's dashboard warning light plus a fault code — annoying, but it's pointing directly at the problem, not being cryptic on purpose. `try`/`catch` is a seatbelt: you don't expect to crash, but you wear it so a crash doesn't total the whole trip.

**Check understanding:**
- If code inside a `try` block throws an error, where does execution go next?
- Why might a `fetch` call "succeed" (get a response) but still represent a failure from your app's point of view?

**Hands-on task:** Take the working `fetch` code from 2.12 and deliberately break the URL (typo the domain) so it fails. Read the resulting console error's *top line* out loud before doing anything else. Then wrap the code in `try`/`catch` and confirm the page now logs a friendly message instead of an ugly crash.

**Done when:** he can read the first line of an unfamiliar error message and describe what it's telling him, and can wrap risky code in `try`/`catch` to handle a failure without the script dying.

**If he's stuck:** trigger a much simpler, obvious error first — call a function that doesn't exist (`typo()`) — and just practice reading *that* stack trace's top line before moving to the more layered `fetch`-failure case.

---

## Lesson 2.14 — Recap: rebuild one small thing, every line understood

**Goal:** the module's proof, matching Module 1's 1.8. Not new material — demonstrating that everything from 2.1–2.13 is actually his, working together.

**Lead with this:** No new concepts today. Pick the simplest thing he's vibe-coded before (or a small feature of one) and rebuild it here, from scratch, narrating every single line as he writes or reads it. This *is* the module's "done when."

**How to run it:**
Have him build (or pick apart and re-explain, line by line, if rebuilding from zero is too big for one session) a small, complete interactive artifact that touches most of the module:
1. An array of data (2.6) — could be objects (2.7), e.g. a small list of items.
2. Rendered onto the page via a loop that creates DOM elements (2.9), OR fetched live from a public API with `fetch` + `async`/`await` (2.11–2.12), OR both.
3. A button or input with an event listener (2.10) that changes something on screen (2.8) in response — filtering the list with `.filter()` (2.7), adding a new item, or loading fresh data.
4. Wrapped in `try`/`catch` (2.13) if it involves a `fetch` call, so a broken request doesn't crash it.

**Your job:** let him lead, and push on *why*, not just *what* — for each line, ask "why does this line need to exist / what would break without it" rather than accepting "it just works." Where he can run code correctly but can't explain a line, that's the real gap — note it, and loop back rather than moving on.

**Done when:** he can build (or fully re-explain) a small multi-part interactive page and, for every line, say what it does and why it's needed — no "the AI wrote it and it worked" answers left standing.

**End-of-module ritual:** mark all of Module 2 complete in PROGRESS.md, print the completion marker for 2.14, and tell him plainly: he can now read the shape of almost any AI-generated JavaScript — variables, functions, conditionals, loops, arrays/objects with map/filter/find, DOM manipulation, events, and (the big one) async data fetching with proper error handling. Module 3 (APIs, for real) will feel like *depth*, not a new mountain — `fetch` from 2.12 is the exact tool he'll spend that whole module getting fluent with, now against real, messier APIs with auth and pagination.
