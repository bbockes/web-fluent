# Module 1 — The Mental Model of the Web (Full Lesson Scripts)

> **For the tutor:** This is your worked script for Module 1. Each lesson gives you the substance, the analogy to lead with, the check questions, the hands-on task, and the "done when" bar — so you teach the concept rather than improvise it. Follow the teaching method from the project instructions: explain → check → one small task → explain-it-back, and never advance until Brendan can put it in his own words. Keep each lesson to ~20–25 minutes.
>
> Brendan knows **HTML and CSS well but no JavaScript.** Anchor every new idea to that. He can't install anything — all tasks below run in a browser tab or a Claude artifact. Module 1 has almost no coding on purpose; the artifact is *understanding*.

---

## Lesson 1.1 — What happens when you type a URL and hit enter

**Goal:** the 30,000-foot map of the whole journey. Everything else in the module zooms into one piece of this.

**Lead with this:** He already knows that when he writes an HTML file and opens it, a page appears. Today's question is: when the page lives on the *internet* instead of his desktop, what actually happens in the two seconds between pressing Enter and seeing it?

**The explanation (keep it a story, not a spec):**
Walk the journey once, naming the players without going deep — each gets its own lesson later:
1. He types `example.com` and hits Enter. The browser needs the page, but first it needs to know *where* that page lives — it has a name, not an address yet. (→ that's DNS, Lesson 1.4.)
2. Once it has the address, the browser sends a **request** across the internet to a **server** — a computer somewhere that holds the site. (→ client/server, 1.2.)
3. The server sends back a **response**: the HTML for the page. (→ HTTP, 1.3.)
4. The browser reads that HTML and sees it needs more things — a CSS file, some images, maybe JavaScript — so it fires off *more* requests for each.
5. As the pieces arrive, the browser **renders** them into the page he sees.

The one big idea to land: **a webpage is not a single thing sitting somewhere — it's assembled, on the spot, out of many request-and-response round trips.**

Analogy that works: ordering delivery. You don't walk into the kitchen. You send an order (request) to a restaurant (server), and food comes back (response). The webpage is the meal, assembled from several orders.

**Check understanding (ask, wait for answers, one at a time):**
- In your own words, what are the two main characters in this story, and which one is your browser?
- Is the whole webpage delivered in one single response, or several? Why?

**Hands-on task:** No code. Ask him to write out — in a note or an artifact — the five steps above *from memory, in his own words*, as if explaining to a coworker. The artifact is his retelling.

**Done when:** he can narrate the URL-to-page journey loosely, naming request, response, and server, and can say that a page is assembled from multiple round trips.

**If he's stuck:** drop back to the delivery analogy and have him map each step to it (order = request, restaurant = server, food = response).

---

## Lesson 1.2 — Client vs. server

**Goal:** the single most important distinction in the whole module. Where code runs.

**Lead with this:** The HTML and CSS he's written his whole career — where does it actually *run*? (Answer he'll arrive at: in the browser, on whoever's computer is looking at it.) That's the **client**. Today is about the other half.

**The explanation:**
- The **client** is the program making requests — almost always the browser, running on the user's own device. It's the "head": the part that displays things.
- The **server** is a computer, somewhere else, whose job is to *wait for requests and respond to them.* It holds the files, the data, and often runs code to decide what to send back.
- Two machines, two different jobs, talking over the internet.

Now the payoff idea, because it matters enormously later: **code runs in one place or the other, and it makes a real difference.**
- Client-side code (the HTML/CSS he knows, and soon JavaScript) runs *in the user's browser*. Anyone can right-click → "View Source" and see it. Nothing there is secret.
- Server-side code runs on the server, out of sight. The user never sees it. This is why passwords get checked and secret API keys get stored on the server, never in the browser.

Connect it forward: "When you learn JavaScript in Module 2, it'll mostly run client-side, in the browser. When you learn APIs in Module 3, you'll be talking *to* a server. This distinction is the hinge for both."

Analogy: a restaurant. The dining room (client) is where you sit and see everything. The kitchen (server) is out back — you never go in, you just send orders and receive plates. The secret recipes stay in the kitchen.

**Check understanding:**
- If you right-click a webpage and choose "View Source," are you looking at client-side or server-side code? How do you know?
- Why would it be a terrible idea to put a secret password directly in client-side code?

**Hands-on task:** Have him open any website, right-click → **View Source** (works in every browser, no install). Ask him to notice: that HTML was *sent to his browser by a server.* Then have him state which parts of what he sees are client-side. The "artifact" is him articulating that everything in View Source is client-side and was delivered from a server.

**Done when:** he can define client and server in his own words and explain why "where code runs" affects what's visible and what's secret.

**If he's stuck:** the restaurant analogy — ask him "could a customer read the secret recipe from their table?" No → that's why secrets live on the server.

---

## Lesson 1.3 — HTTP: requests, responses, methods, status codes

**Goal:** the *language* clients and servers speak. This is where "request" and "response" stop being vague.

**Lead with this:** In 1.1 the browser "sent a request" and "got a response." What's actually *in* one of those? HTTP is the agreed-upon format for both.

**The explanation:**
A **request** has a few parts:
- A **method** — the *kind* of request. The two he'll use constantly: **GET** (give me something) and **POST** (here, take this / do something). There are others (PUT, DELETE) but GET and POST carry most of the load.
- A **URL** — what he's asking about.
- **Headers** — extra info about the request (like "I can accept JSON," or who he is).
- Sometimes a **body** — data he's sending along (mostly with POST).

A **response** comes back with:
- A **status code** — a three-digit number saying how it went. He only needs the shape of it:
  - **2xx** = success (200 is the classic "OK").
  - **3xx** = redirect ("it moved, look over here" — 301 will be familiar from his SEO work).
  - **4xx** = *you* messed up (404 = not found; 401 = not allowed in).
  - **5xx** = the *server* messed up (500 = something broke on their end).
- Headers, and usually a **body** (the actual HTML, or JSON, or image).

The idea to land: **every single thing on the web is this pattern — a request with a method, a response with a status code.** Once he sees it, he can't unsee it.

SEO hook: he already knows 301s and 404s from audits. Tell him — that *is* HTTP. He's been reading HTTP status codes for years without naming them.

**Check understanding:**
- If you want to *fetch* a page, which method? If you're *submitting* a signup form, which?
- A response comes back `404`. Whose "fault" is that, roughly — the client's or the server's? What about `500`?

**Hands-on task (this one's great, no install):** Open any website, open the browser's **DevTools** (F12 or right-click → Inspect), click the **Network** tab, and reload the page. Have him watch the flood of requests appear. Ask him to click one and find: its **method** (GET), its **status code**, and whether it returned HTML, an image, or something else. This makes the invisible visible — real requests and responses, live.

**Done when:** he can look at a Network tab entry and read off the method and status code, and he can explain what 2xx / 3xx / 4xx / 5xx mean without looking them up.

**If he's stuck:** anchor on the two he already knows — 301 (redirect, from SEO) and 404 (not found) — and build the 2/3/4/5 buckets outward from there.

---

## Lesson 1.4 — Domains, DNS, and IP addresses

**Goal:** fill in the "first, the browser needs to know where the page lives" gap from 1.1.

**Lead with this:** In Lesson 1.1 we skipped a step — the browser had a *name* (`example.com`) but computers don't find each other by name. How does a name become a findable location?

**The explanation:**
- Every server on the internet has an **IP address** — a numeric address, like `93.184.216.34`. That's how machines actually locate each other. Numbers, not names.
- Humans are terrible at remembering numbers, so we use **domain names** (`example.com`) instead.
- **DNS** (Domain Name System) is the translator — the internet's phone book. The browser asks DNS "what's the IP for example.com?", DNS answers with the number, and *then* the browser can send its request there.

So the true first step of 1.1 is: name → (DNS lookup) → IP address → now we can actually knock on the server's door.

Analogy: the Contacts app on his phone. He taps "Mom" (domain name); the phone looks up the actual number (IP) and dials it. He never memorizes the number — the contacts list (DNS) does it for him.

**Check understanding:**
- Why can't the browser just send a request straight to `example.com` without DNS first?
- In the phone analogy, what plays the role of DNS?

**Hands-on task:** Have him visit a free browser-based DNS lookup tool (search "DNS lookup" — many run entirely in the browser) and look up a domain he knows, like his employer's site. Ask him to notice: a friendly name resolved to a raw IP address. That resolution *is* what his browser does silently every time.

**Done when:** he can explain, in order, that a domain name gets translated by DNS into an IP address before any request is sent — and why that translation step has to exist.

**If he's stuck:** stay on the contacts analogy; have him walk through "tap name → look up number → dial" and map each to domain / DNS / IP.

---

## Lesson 1.5 — JSON

**Goal:** the format data travels in. His first real look at how programs (and APIs, next lesson) pass information around.

**Lead with this:** He knows HTML — tags that describe a *document* for a browser to display. JSON is a cousin, but with a totally different job: it describes **data** for a *program* to use. Not for display — for logic.

**The explanation:**
- JSON is just structured text. Its whole vocabulary:
  - **Key–value pairs:** `"name": "Brendan"` — a label and its value. (He'll recognize the shape from CSS-ish `property: value` thinking, though the syntax differs.)
  - **Objects:** a set of pairs wrapped in `{ }` — one "thing."
  - **Arrays:** an ordered list wrapped in `[ ]` — many things.
  - Values can be text (`"strings"`, in quotes), numbers, true/false, or *other objects and arrays* nested inside — which is how it describes complex things.
- Example to show him:
  ```json
  {
    "name": "Brendan",
    "role": "web author",
    "skills": ["HTML", "CSS", "SEO"],
    "learning": { "module": 1, "lesson": "1.5" }
  }
  ```
- The idea to land: HTML is for humans to *read*; JSON is for programs to *pass around and act on*. When an API sends data back (next lesson), it almost always sends JSON.

Contrast that sharpens it: HTML says "here's a document to render." JSON says "here's some data — you figure out what to do with it."

**Check understanding:**
- What's the difference in *purpose* between HTML and JSON?
- In the example above, is `skills` a single value or a list — and how can you tell from the punctuation?

**Hands-on task:** Have him write a small JSON object describing *himself* (or a product — tie it to his CPG interests if he likes): a few key–value pairs, one array, one nested object. Then paste it into a free browser JSON validator (search "JSON validator") to confirm it's valid. Getting a "valid" checkmark means he wrote well-formed data. If it errors, debugging the missing comma or quote *is* the lesson.

**Done when:** he can read a block of JSON and describe what data it holds, and can hand-write a small valid object with an array and a nested object.

**If he's stuck:** most early JSON errors are missing commas, missing quotes around keys/strings, or mismatched brackets. Have him fix his own validator errors one at a time — that's the real skill.

---

## Lesson 1.6 — What an API actually is

**Goal:** the payoff lesson. This is where client/server + HTTP + JSON click together into one idea. This lesson is why Module 3 will feel easy.

**Lead with this:** He's now met all the pieces — a client that makes requests, a server that responds, HTTP as the format, JSON as the data. An **API** is just those pieces working together on purpose, with a published menu of what you're allowed to ask for.

**The explanation:**
- An **API** (Application Programming Interface) is a **defined way for programs to talk to each other.** A server publishes a list of requests you're allowed to make (the "endpoints") and promises what it'll send back.
- Concretely, using everything he's learned: you send an **HTTP request** (usually a GET) to a specific URL (an **endpoint**) on a **server**, and it sends back a **response** — almost always **JSON**. That's it. That's an API call. Every buzzword he's heard resolves to that sentence.
- Why it matters to *him*: this is how his Apps Script automations pull data, how any AI-powered app talks to Claude, and — tie back to the earlier conversations — how **headless content gets delivered.** When content lives in a repository and travels over an API as JSON, *this* is the machinery underneath it.

Analogy (the classic, because it's good): a restaurant menu. He doesn't walk into the kitchen and cook. He reads the **menu** (the API — the list of things he's allowed to order), places an **order** (the request), and gets a **dish** back (the response). The menu is a *contract*: order item #4 and you know what arrives. An API is a menu for programs.

**Check understanding:**
- Put it together: what four things you've learned this module are all happening in a single API call?
- In the restaurant analogy, what's the "menu," and why does having a fixed menu make life easier for the person ordering?

**Hands-on task (the satisfying one):** Many public APIs answer a plain GET request right in the browser. Give him a public API endpoint URL that returns JSON (search "free public API no key" — e.g. a jokes, cat-facts, or public-data API), and have him **paste it straight into his browser's address bar.** Raw JSON appears on screen. Point out: he just made an API call. The browser was the client, that URL was the endpoint, and what came back is the JSON from 1.5. No code at all.

**Done when:** he can define an API as "a defined way to request data from a server and get a structured response back," walk through the four pieces of a call, and he's seen real JSON come back from a real endpoint.

**If he's stuck:** slow down on the restaurant menu and have him name each part (menu / order / kitchen / dish → API / request / server / response). Then re-do the browser task and narrate each piece as it happens.

---

## Lesson 1.7 — Frontend vs. backend vs. database

**Goal:** the three-part shape of nearly every app — so he has a place to file everything he'll learn next.

**Lead with this:** He now understands the *conversation* (request/response). Zoom out: what are the *parts of an application* having that conversation? Almost every app has three.

**The explanation:**
- **Frontend** — everything the user sees and touches. Runs client-side, in the browser. This is HTML, CSS, and (soon) JavaScript — his home turf. The "head."
- **Backend** — the server-side code. It handles logic, checks who you are, decides what data to send, keeps secrets. The user never sees it.
- **Database** — where data *persists* between visits. When he logs in tomorrow and his stuff is still there, that's the database. The backend talks to the database; the frontend never touches it directly.

The flow to land: frontend makes a request → backend receives it, applies logic, asks the database for data → backend sends a response (JSON) back → frontend displays it. Every piece from this whole module has a home in this shape now.

Analogy: restaurant again, extended. Dining room = frontend (what you see). Kitchen = backend (where the work happens, out of sight). Pantry/walk-in fridge = database (where ingredients are stored between services). You (frontend) never rummage in the pantry — you ask the kitchen (backend), which fetches from the pantry (database).

**Tie to his world:** map it onto AEM if it helps — the authored, rendered page is the frontend; AEM's delivery/logic layer is backend-ish; the content repository (where the fragments and data live) plays the database role. This is also exactly the "content as data, delivered over an API" idea from your earlier conversations, seen from the architecture side.

**Check understanding:**
- Which of the three parts is the only one the user can actually see?
- If you refresh a page tomorrow and your saved settings are still there, which part made that possible?

**Hands-on task:** Have him pick an app he uses daily (his email, a shopping site, even AEM) and write out — in an artifact or note — which parts of his experience are frontend, what the backend is probably doing that he can't see, and what's likely stored in the database. Labeling a real, familiar app is the exercise.

**Done when:** he can name the three parts, say which runs where, and trace a request through all three and back.

**If he's stuck:** the extended restaurant analogy, and have him place a food order mentally through dining room → kitchen → pantry → back.

---

## Lesson 1.8 — Recap: draw the URL-to-page journey from memory

**Goal:** assemble every piece of the module into one picture he can produce unaided. This *is* the module's proof.

**Lead with this:** No new material today. Today he proves the scaffolding is his. You're going to have him rebuild the whole journey from memory, and you'll only fill gaps.

**How to run it:**
Ask him to narrate or sketch the full story from "I type a URL and hit Enter" to "I see the finished page," out loud or in an artifact, using the real vocabulary. A complete answer should naturally include:
1. Types domain → **DNS** translates it to an **IP address** (1.4).
2. Browser (**client**) sends an **HTTP request** — a **GET** — to the **server** (1.2, 1.3).
3. Server sends a **response** with a **status code** and the HTML **body** (1.3).
4. Browser reads the HTML, fires **more requests** for CSS/images/JS (1.1).
5. If the page needs data, it may call an **API** and get **JSON** back (1.5, 1.6).
6. Under it all: **frontend** (what he sees) talks to **backend**, which talks to the **database** (1.7).
7. Browser **renders** the assembled page.

**Your job:** let him lead. Where he skips or fuzzes a step, ask a pointed question ("okay — but before the request goes out, how did the browser know *where* to send it?") rather than telling him. Only explain outright if a prompt doesn't recover it. Note the specific gaps — those are what to revisit.

**Done when:** he can produce the full journey unaided, using correct terms, and correctly place frontend/backend/database underneath it. When he can do this, the "everything the AI generates is magic" feeling is gone — and that's the entire point of Module 1.

**End-of-module ritual:** mark all of Module 1 complete in PROGRESS.md, print the completion marker for 1.8, and tell him plainly: the scaffolding is built. Module 2 (JavaScript) will now land on structure instead of fog — and remind him that async/await and fetch in 2.11–2.12 are where he cashes in everything he just learned about requests, responses, and APIs.
