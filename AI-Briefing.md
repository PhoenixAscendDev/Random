# 🧠 AI Briefing – CheeseBag Project

**Version:** 2025-08-08
**Primary Rule:** This document is the ONLY valid source for project details. If it’s not here, it doesn’t exist. No assumptions.

---

## 💜 Project Snapshot

* **Name:** Cheese Bag
* **Description:** A culinary web app centered on grilled cheese sandwiches, with room for future cheese-related expansions.
* **Architecture Model:** "Dumb / Façade / Dumber" with a centralized **Domain Core**

  * **Presentation Tier – Dumb:** React UI; renders, handles user input, calls façades; **no business rules.**
  * **API Façade (Transport/Contract):** `/apps/api-server` exposes HTTP/GraphQL endpoints; **no domain decisions.** Delegates to Domain.
  * **Domain Core – Mastermind:** `/domain` holds all business logic (DDD: entities, value-objects, domain-services, repositories); **the single source of truth for decisions** (e.g., the grilled-cheese randomizer service).
  * **Data Source Tier – Dumber:** `/database` + external stores; storage/retrieval only; **no interpretation.**

---

## 🛠️ Tech Stack Overview

| Layer             | Technologies                 | Languages             |
| ----------------- | ---------------------------- | --------------------- |
| Presentation Tier | React, SCSS, Bootstrap       | HTML, CSS, TypeScript |
| API Façade        | Node.js, Express.js, GraphQL | TypeScript, GraphQL   |
| Domain Core       | DDD modules in `/domain`     | TypeScript            |
| Data Source Tier  | PostgreSQL, MongoDB, Neo4j   | SQL, NoSQL, Cypher    |

**Tools:** PowerShell (not Bash) for CLI
**Libraries:** Bootstrap v5.3.7, Font Awesome v7.0.0

---

## 📂 Project Structure (from README)

/apps
  web-client/      # Frontend (Presentation)
  api-server/      # API Façade (transport/contract only)
/docs              # Project documentation
/branding          # Logos, fonts, theme
/packages          # Aerie core utilities
/database          # Schema, seeds, migrations
/domain            # Domain Core (DDD business logic)
/libraries         # External library references
/tests             # Unit and integration tests
```
---

## 📏 Code & Placement Rules (Authoritative)

* **All business logic lives in `/domain`.**

  * Example: `domain/services/GrilledCheeseRandomizerService.ts` exports pure functions used by façades.
* **API Façade** (`/apps/api-server`) is transport-only: routing, auth, validation, mapping; **no decisions**.
* **Presentation** (`/apps/web-client`) renders UI and calls façades; **no business rules**.
* **Data access** occurs behind **Domain repositories**; data tier remains passive.
* **Static data for MVP** may be read in Presentation for speed, but MUST be migrated behind Domain APIs when available.
* **One README per feature** under `/docs` (or `/docs/features`).

---

## 🚫 AI Do / Don’t

**Do:**

* Use only details from this document.
* Resposes are to the point and are direct to the request.
* Ask before adding anything not in the project files.
* Enforce **Presentation = Dumb**, **API = Façade**, **Domain = Mastermind**, **Data = Dumber**.
* Only ever respond to the very last prompt I send. Never go back to older ones, even if unanswered. Treat them as expired.”

**Don’t:**

* Invent file paths, tools, libraries, or rules not listed here.
* Embed business rules in Presentation or API Façade.
* Provide suggestions at end of responses
* No Fluff in responses

---

---

## 🧾 Change Log

* **2025-08-08:** Updated to Façade pattern; clarified Domain as the master logic layer; added AI checklist.
