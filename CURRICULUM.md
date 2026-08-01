# Fluent Enough to Ship — A Self-Teaching Curriculum

*A two-year spine for going from "I can vibe-code apps but can't read them" to "I understand the machine well enough to direct it." Built to be taught to you by Claude, in ~30-minute blocks, with no software to install.*

---

## The one idea behind all of this

You are **not** training to become a software engineer. You're becoming the content / SEO / architecture person who understands the system well enough to drive it instead of ride in it. Every module below serves *that* — not making you a junior dev competing with 22-year-olds and the AI.

The bar is never "can I write this from a blank page." The bar is **"can I read what the AI wrote, understand it, and fix it when it breaks."** Undeceivable, not fluent-from-scratch.

---

## How this works (read once, then never again)

**The daily ritual.** You have ~20 minutes a day, 5 days a week. A "lesson" is a ~30-minute block, so some lessons will spill across two sittings — that's fine and expected. Don't rush to finish a lesson in one go; rush nothing.

**The mechanism.** For each lesson, you paste a prompt into Claude (template below) and Claude teaches you that specific concept, checks your understanding, and gives you a tiny hands-on task. You build the task in an artifact or a web IDE. You don't move on until you can explain it back.

**The anti-cheat rule.** The entire point is understanding, not output. If you ever catch yourself copy-pasting Claude's code without reading it — stop. The discipline that makes this work: after every lesson, close the chat and **explain the concept out loud (or in a note) in your own words.** If you can't, you didn't learn it yet. This is the single habit that separates this from the last year of vibe-coding.

### Your daily prompt template

Copy this, fill in the brackets, paste into a fresh Claude chat:

```
I'm working through my self-teaching web-dev curriculum. 
Today's lesson: [Module __, Lesson __: TITLE].

Context about me: I know HTML and CSS well. I do NOT know JavaScript. 
I've had light exposure to APIs. I can't install anything on my computer, 
so I'll build in a Claude artifact or a browser IDE. I have ~25 minutes.

Please:
1. Explain the concept simply, building on what I already know.
2. Stop and ask me 1–2 quick questions to check I actually got it.
3. Give me ONE tiny hands-on task I can build in an artifact / browser.
4. Don't move ahead until I've done it and can explain it back.

Keep it conversational, not a lecture.
```

---

## Your no-install toolkit

Everything here runs in a browser tab. No admin rights, no Node, nothing to download.

- **Claude artifacts** — build and run HTML, JavaScript, and React live, right in the chat. Your primary sandbox for most lessons.
- **CodeSandbox / StackBlitz / Replit** — full browser IDEs when you want a real project structure. StackBlitz and CodeSandbox even run Node *in the browser*, so you get the "real" workflow without installing it.
- **CodePen / JSFiddle** — quick throwaway HTML/CSS/JS scratchpads.
- **Postman (web version) or Hoppscotch.io** — poke at real APIs from the browser. Zero install.
- **Learn Git Branching (learngitbranching.js.org)** — Git, taught visually, entirely in the browser.

---

## The spine (six modules, in order)

Order matters through Module 5 — skipping ahead to React before the web model is exactly the flailing you're trying to escape. Module 6 you can start braiding in early through your actual AEM work.

Time estimates are a **first-pass scaffold**, not a promise — some lessons will click in ten minutes, some you'll want to sit in for a week. At 20 min/day this is honestly a 1.5–2 year journey. It's a marathon; treat it like one.

---

### Module 0 — Setup & how to learn *(2 lessons, ~1 hour)*

Get the tools open and the habit built before any concepts.

- **0.1** — Set up your accounts (CodeSandbox, a browser IDE, Postman/Hoppscotch). Open them once so they're not friction later.
- **0.2** — The learning contract: practice the daily prompt, practice the "explain it back" habit on something you already know (explain how a webpage loads a CSS file). Build the muscle before you need it.

---

### Module 1 — The mental model of the web *(~8 lessons, ~4 hours)*

**The highest-leverage module on the list.** This is the scaffolding that makes everything the AI generates *legible* instead of magical. Do not skip it because it's not "coding."

- **1.1** — What actually happens when you type a URL and hit enter (the 30,000-ft tour).
- **1.2** — Client vs. server. Where does code run, and why does it matter?
- **1.3** — HTTP: requests and responses. Methods (GET/POST), status codes (why 404 and 500 mean different things).
- **1.4** — What a domain, DNS, and an IP address are (the address book of the internet).
- **1.5** — JSON: the language data travels in. Read it, write it, recognize it.
- **1.6** — What an API *is*, underneath the buzzword — a waiter taking your order to the kitchen.
- **1.7** — Frontend vs. backend vs. database — the three-part shape of almost every app.
- **1.8** — Recap + explain-it-back: draw the whole "URL to page" journey from memory.

**Resources:** MDN's "How the Web works" guides; *How DNS Works* (howdns.works — an illustrated comic); Julia Evans' free zines/blog for intuition.

**Project:** No build yet — the artifact is a diagram *you* draw of the request/response cycle, labeled in your own words. If you can draw it, you own it.

**Done when:** you can explain, unprompted, what happens between hitting enter and seeing a page, and where an API fits in.

---

### Module 2 — JavaScript fundamentals *(~14 lessons, ~7–8 hours)*

The big one. Bar: **read the AI's JS, understand it, fix it.** Not "become a JS developer."

- **2.1–2.3** — Variables, types, functions. The absolute grammar.
- **2.4–2.5** — Conditionals and loops (the logic the AI is always writing for you).
- **2.6–2.7** — Arrays and objects — and `map` / `filter` / `find`, the three you'll see constantly.
- **2.8–2.9** — The DOM: how JS reads and changes the page. This is where HTML/CSS knowledge pays off hard.
- **2.10** — Events: clicks, inputs, forms.
- **2.11–2.12** — **`async/await` and `fetch`.** The most important lessons in the module — this is the door to APIs. Slow down here.
- **2.13** — Errors: reading a stack trace without panic; `try/catch`.
- **2.14** — Recap: rebuild one small thing understanding every line.

**Resources:** **javascript.info** (the best free JS resource that exists — work through it in order); MDN's JS guide as reference; freeCodeCamp's JS course; Scrimba for interactive.

**Project:** rebuild ONE of your vibe-coded apps — the simplest one — *understanding every single line this time.* Same output, total comprehension. That contrast is the whole point of the year.

**Done when:** you can paste AI-generated JS into a chat and narrate what each part does before running it.

---

### Module 3 — APIs, for real *(~8 lessons, ~4 hours)*

**Your highest-*value* module.** It serves your Apps Script work today, the data stuff you like, AEO, and every AI product idea you'll ever have. Lean in.

- **3.1** — Anatomy of a request revisited: endpoints, headers, query params, body.
- **3.2** — Making real calls with Postman/Hoppscotch (no code yet — just poke a live API).
- **3.3** — Reading API documentation without fear (the actual meta-skill).
- **3.4** — Authentication: API keys, tokens, why they exist, how not to leak them.
- **3.5** — Rate limits, pagination, and why your call sometimes fails.
- **3.6** — Calling an API from JavaScript with `fetch` (ties back to 2.11).
- **3.7** — Chaining calls and handling the errors gracefully.
- **3.8** — Recap: consume a public API end-to-end in an artifact.

**Resources:** MDN Fetch docs; the "public-apis" list on GitHub (free APIs to play with); Postman/Hoppscotch learning centers.

**Project:** build a small artifact that fetches from a free public API (weather, a jokes API, whatever) and displays it on the page. Then a stretch: one that calls the Claude API (your interface supports this in artifacts — you've explored it before).

**Done when:** handed an unfamiliar API's docs, you can make a working call and display the result without hand-holding.

---

### Module 4 — Git & the developer workflow *(~5 lessons, ~2.5 hours)*

Unglamorous connective tissue. It's what turns "I can code a little" into "I work like a technical person." Cheap to learn, quietly essential.

- **4.1** — What version control is and the mental model of commits (snapshots in time).
- **4.2** — `add`, `commit`, `push`, `pull` — the daily four.
- **4.3** — Branches and merging (visually, via Learn Git Branching).
- **4.4** — What GitHub is vs. what Git is; pull requests.
- **4.5** — The command line, just enough to not be scared of it.

**Resources:** **learngitbranching.js.org** (visual, browser-based); GitHub's own "Git Handbook"; MDN's Git basics.

**Project:** put one of your rebuilt apps into a GitHub repo, with real commit messages that describe what changed.

**Done when:** you can start a repo, commit as you work, and branch without googling every command.

---

### Module 5 — One modern framework: React *(~12 lessons, ~6 hours)*

*Now* it's time — Modules 1–4 make React comprehensible instead of copied. This is what turns vibe-coding into actually-shipping.

- **5.1** — Why frameworks exist (what problem React solves that raw JS made painful).
- **5.2–5.3** — Components and JSX — HTML-in-JS, and why.
- **5.4–5.5** — Props: passing data down.
- **5.6–5.7** — State and `useState`: the concept everything hinges on.
- **5.8** — Handling events and forms the React way.
- **5.9–5.10** — `useEffect` and fetching data (Module 3 comes back).
- **5.11** — Lists and keys; conditional rendering.
- **5.12** — Recap: build and modify a small multi-component app.

**Resources:** **react.dev** (the official tutorial is genuinely excellent — start there); Scrimba's React course for interactive; build directly in Claude artifacts, which run React natively.

**Project:** rebuild a vibe-coded app of yours in React — component-based, with real state — understanding the architecture, not just the output.

**Done when:** you can build a small component-based app, explain the difference between props and state, and modify AI-generated React confidently.

---

### Module 6 — Content modeling & headless delivery *(your capstone — braid in early)*

This is where the whole plan converges: the future-proof half of your current job, the AEO skill, and the thing that makes you the rare content-*plus*-architecture person. Everything above exists to make you credible enough to own this. Start touching it early through your AEM work — you're already paid to be in there.

- **6.1** — Content as data, not pages: the core mental shift.
- **6.2** — What a content model is: types, fields, relationships, taxonomy.
- **6.3** — Headless vs. traditional CMS, concretely (map it onto AEM classic vs. Content Fragments).
- **6.4** — AEM Content Fragments hands-on — model something real at work.
- **6.5** — Querying content via AEM's GraphQL API (ties directly to Modules 1 & 3).
- **6.6** — Structured content and AEO: why clean models are what machines can read accurately.
- **6.7** — Designing a content model from scratch for a made-up product — the portfolio artifact.

**Resources:** Adobe's AEM Content Fragments & Headless/GraphQL docs; Contentful's (vendor-neutral-ish) content-modeling guides; Deane Barker's writing on content modeling.

**Project (portfolio-worthy):** take a real content type from your work — a program description, say — and design a proper structured content model for it: typed fields, taxonomy, and a sketch of how it'd be delivered via API to a website, an app, an email, *and* an AI. Write up the reasoning. **That artifact is the proof of the whole pivot** — it's you demonstrating content architecture, not CMS button-clicking.

**Done when:** you can look at any pile of content and think in models — types, fields, relationships, delivery — instead of pages.

---

## Progress tracker

Fill this in as you go. Seeing it move is most of the motivation.

```
MODULE 0 — Setup            [ ] 0.1  [ ] 0.2
MODULE 1 — Web model        [ ] 1.1 [ ] 1.2 [ ] 1.3 [ ] 1.4 [ ] 1.5 [ ] 1.6 [ ] 1.7 [ ] 1.8
MODULE 2 — JavaScript       [ ] 2.1 ... [ ] 2.14
MODULE 3 — APIs             [ ] 3.1 ... [ ] 3.8
MODULE 4 — Git              [ ] 4.1 ... [ ] 4.5
MODULE 5 — React            [ ] 5.1 ... [ ] 5.12
MODULE 6 — Content modeling [ ] 6.1 ... [ ] 6.7

Current lesson: ______________________
Last thing that finally clicked: ______________________
```

---

## A few honest reminders

- **Consistency beats intensity.** 20 minutes every weekday crushes a heroic 4-hour Sunday you'll skip half the time. The streak is the strategy.
- **Boredom is not a signal to skip ahead.** Module 1 will feel too basic. It isn't. The people who skip it are the people still confused in Module 5.
- **Explain it back, every time.** If you can't teach the lesson to an imaginary beginner, you haven't learned it — you've watched it.
- **This is means, not identity.** You're not becoming an engineer. You're becoming undeceivable, and building toward the content-architecture seam nobody else sits in well.
