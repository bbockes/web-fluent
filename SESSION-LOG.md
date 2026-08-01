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
