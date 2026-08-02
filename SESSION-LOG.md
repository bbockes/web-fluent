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
