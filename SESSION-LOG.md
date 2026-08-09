# SESSION LOG — Fluent Enough to Ship

> After each lesson, the AI appends a short entry here capturing what was covered, key connections made, and any tangents worth remembering. This gives future sessions richer context than the checkbox alone.

---

## Lesson 1.1 — What happens when you type a URL and hit enter
**Date:** Prior session  
**Key takeaway:** The full journey from URL to rendered page — DNS lookup, request to server, response with HTML, browser renders it.

---

## Lesson 1.2 — Client vs. server
**Date:** Prior session  
**Key takeaway:** Client = browser (visible, runs on user's device). Server = remote machine (hidden, holds secrets). Where code runs determines what's visible and what's secure.

---

## Lesson 1.3 — HTTP: requests, responses, methods, status codes
**Date:** 2026-08-01  
**Key takeaways:**
- GET = "give me this." POST = "here, take this."
- Status code buckets: 2xx success, 3xx redirect, 4xx client error, 5xx server error.
- 4xx means the *request* was wrong (you asked for the wrong thing); 5xx means the server broke trying to fulfill a valid request. This clicked when framed as "who needs to fix it."
- 301 = permanent redirect (already familiar from SEO work).

**Hands-on:** Inspected Network tab on brendanbockes.com (his own site).  
**Connections made:**
- His site uses React + Sanity (headless CMS). The Network tab showed two GET requests to `2fx5od72.apicdn.sanity.io` — one for work projects (on page load), one for side projects (on toggle click). Both returned 200 + JSON.
- He articulated the full chain: browser requests HTML from his server → React runs → React makes GET requests to Sanity's server → Sanity responds with JSON → browser renders cards.
- Connected this to headless CMS architecture: content as data on a separate server, presentation decoupled, multiple clients can consume the same API. Tied it to a prior Claude conversation about content being stored as data and delivered to multiple channels via APIs.

**Tangents worth remembering:**
- He's already thinking about the "content as structured data" paradigm and multi-channel delivery — this maps directly to Module 6 (content modeling & headless delivery). He'll arrive there with strong technical grounding.
- His personal site is a great reference point for future lessons — real React, real API calls, real JSON responses he can inspect.

---

## Lesson 1.4 — Domains, DNS, and IP addresses
**Date:** 2026-08-02  
**Key takeaways:**
- Domain name = human-friendly label; IP address = the machine location; DNS = the phone book that translates name → IP before any HTTP request can be sent.
- Runtime sequence: domain → DNS lookup → IP → HTTP request → response.
- Configuring a domain is publishing answers in that phone book — not the same job as buying the name or hosting the site.

**Hands-on:** DNS lookup for `brendanbockes.com` → resolved to `71.126.156.42`.  
**Connections made:**
- Mapped his real setup: **registrar** (iwantmyname) vs **DNS provider** (nameservers — kept at registrar or handed to Netlify) vs **host** (Netlify, where the site actually runs).
- Walked end-to-end: buy name → set A/CNAME (or change nameservers) → Netlify serves at an IP → every visit does the silent DNS lookup he just did manually.
- Tied forward to Module 6 / headless thinking: the name is just a label; where traffic goes is whatever the DNS records say.

**Tangents worth remembering:**
- He recognized record types (A, AAAA, CNAME, MX) from a prior specialist role but hadn’t owned what they meant. Covered: A = IPv4 for web, AAAA = IPv6, CNAME = alias to another name, MX = email servers — different jobs, so one record type isn’t enough.
- “DNS server” dropdown in lookup tools = which resolver you’re asking (e.g. Google), not the same as “my DNS provider” that holds authoritative records.
- Strong mental model already of registrar → DNS → host; good to reuse his personal site as the concrete example in later lessons.

---

## Lesson 1.5 — JSON
**Date:** 2026-08-03
**Key takeaways:**
- JSON = JavaScript Object Notation, but it's not JavaScript — it's a plain-text, language-agnostic data format. Named after JS object syntax because that's where `{ }` / `[ ]` came from, but any language (Python, Java, PHP...) can read/write it with no JS involved.
- `{ }` = object (one thing), `[ ]` = array (ordered list). The bracket type is the real signal — not commas, since objects use commas too.
- HTML/CSS/JS render pages for humans to see; JSON carries data for programs to act on. That's the purpose split.
- Landed cleanly on: JSON is a text format for moving data between systems, not a coding language — no logic, no functions, inert until something else (JS's `JSON.parse`, Python's `json` module) reads and acts on it.

**Hands-on:** Wrote his own JSON object (name, job title, skills array, nested `learning` object) and validated it in a browser JSON validator — passed on first try.
**Connections made:**
- Noted `"job title"` (with a space) is valid JSON but awkward once you get to JS property access — real-world JSON usually uses `jobTitle` or `job_title`. Flagged as a forward-looking convention note, not a rule.

**Tangents worth remembering:**
- He asked good clarifying questions unprompted (JSON vs. JS relationship, "is JSON a language?") rather than just accepting the material — a good sign for how he engages with new concepts. Keep leaving room for him to interrogate definitions before moving on.

---

## Lesson 1.6 — What an API actually is
**Date:** 2026-08-04
**Key takeaways:**
- An API = a published contract letting one program request data/functionality from another over the web: HTTP request to an endpoint → HTTP response, usually JSON, back. Every API buzzword resolves to that sentence.
- Menu analogy landed well: fixed set of endpoints (the menu) removes guesswork for the person ordering (the client).
- Cleared up a GET/POST mix-up: responses are never labeled by method — only requests are GET (retrieve) or POST (submit/create). "POST request back" isn't a thing; it's just "the response."
- Extended the concept himself to AI chat interfaces: chat UI = client, sends a POST (submitting a prompt) to the model's API endpoint, gets JSON back, renders it as a message bubble. Correctly reasoned POST vs. GET based on "sending data" vs. "just asking for something."

**Hands-on:** Made real zero-code API calls by pasting public endpoint URLs into the browser address bar — a random dog-image API (name as a URL slug/path parameter) and a nationality-prediction API (name in the URL, JSON prediction back). Correctly identified the variable part of the URL as a parameter telling the API which specific thing to fetch/process.
**Connections made:**
- Walked his own Sanity-powered blog through the full pipeline unprompted: DNS → server → GET request to Sanity's endpoint → JSON response with per-field key-value pairs (title, slug, body, image) → browser renders it. Used this as his own explain-back example before the formal one.
- Defined API in his own words: "an interface that lets browsers/programs programmatically access data elsewhere on the web" — accurate and concise.

**Tangents worth remembering:**
- He continues to test his understanding by extending concepts to new domains unprompted (AI chatbots as API clients) rather than waiting to be told — reinforce this by letting him reason it out before confirming, as done here.

---

## Lesson 1.7 — Frontend vs. backend vs. database
**Date:** 2026-08-09  
**Key takeaways:**
- Marked complete by request so we could move into the Module 1 recap (1.8). Core idea: frontend (what the user sees, client-side) → backend (server-side logic, secrets, decisions) → database (persistent data the backend reads/writes; frontend never talks to it directly).

**Hands-on:** Skipped formal exercise; will be exercised inside 1.8's full URL-to-page journey (frontend/backend/database as the bottom layer).  
**Connections made:**
- Already demonstrated this shape in earlier sessions via his Sanity/React site (browser/React = frontend, Sanity API = backend-ish delivery, content store = database role).

**Tangents worth remembering:**
- If gaps show up in 1.8 on "who talks to the database," revisit the restaurant pantry analogy briefly rather than re-teaching the whole lesson.

---

## Lesson 1.8 — Recap: draw the URL-to-page journey from memory
**Date:** 2026-08-09  
**Key takeaways:**
- Produced an unaided hand-drawn diagram covering: client/browser, DNS (WWW → IP), HTTP GET/response, response payloads (JSON or HTML/CSS/JS), datacenter/server scale, and frontend → backend → database.
- Filled gaps verbally: status codes come with the response; page assembly happens in waves of follow-up GETs after HTML arrives; only the backend talks to the database (frontend never directly); third-party services (Clerk, Sanity, Stripe) are reached via APIs.
- Minor precision note: he initially said status codes live "in the header" — clarified that status code is its own part of the response (alongside headers and body).

**Hands-on:** Hand-drawn architecture diagram + verbal walkthrough of the three gap questions.  
**Connections made:**
- Reused Sanity/Clerk/Stripe as concrete examples of "backend talks to another service/database on the frontend's behalf via an API" — consistent with 1.3/1.6 sessions.
- Module 1 complete; next is Module 2 (JS). Cash-in moments flagged: async/await + fetch (2.11–2.12).

**Tangents worth remembering:**
- Drawing + explain-back worked well for him — prefer that over pure prose for architecture recaps.
- Speech-to-text sometimes turns GET → "Git"; treat as GET unless context is version control.

---

<!-- TEMPLATE FOR FUTURE ENTRIES

## Lesson X.Y — Title
**Date:** YYYY-MM-DD  
**Key takeaways:**
- Bullet points of core concepts that landed

**Hands-on:** What they built or explored  
**Connections made:**
- Links to prior lessons, real-world experience, or forward curriculum topics

**Tangents worth remembering:**
- Anything discussed beyond the lesson that future sessions should know

-->
