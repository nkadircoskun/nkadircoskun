# Kadir Coşkun

**I build the software I needed on the restaurant floor.**

Vienna, Austria.

Twenty years in gastronomy — fifteen as Chef de Rang, the last five as Restaurant
Manager. The back office was always the same picture: the same numbers written
down in three places, and none of them arriving in time to change anything. In
April 2026 I started writing the program I had spent years wishing for. I have
been writing it every day since.

---

## GASTRORIX

A desktop application for the back office of a restaurant. Not another sales
dashboard — it covers the work that happens after service:

- **the nightly close**, in a form a tired closer will actually finish
- **stock** that moves with each delivery, not at month-end
- **rosters and hours** in the same file as everything else
- **one screen** for what needs attention today, instead of last month

Desktop rather than web, deliberately: a restaurant's numbers stay on the
restaurant's own machine, and the program has to work when the connection does not.

Closed source. Alpha, one user — me. Everything below is measured from the repo.

### Scale

| | |
|---|---|
| First commit | 8 April 2026 |
| Commits | 1,811 |
| Tracked files | 1,667 |
| TypeScript / TSX | ~133,000 lines |
| Unit test files | 198 (Vitest) |
| End-to-end specs | 7 (Playwright) |

### Stack

Electron · React · TypeScript · Vite · Tailwind · Zustand ·
SQLite via `better-sqlite3-multiple-ciphers`, encrypted at rest

### Security

The program holds wages, sales figures and supplier prices. So the security model
was written down and locked before it was implemented — a decision matrix dated
the day after the first commit.

- Renderer is not trusted: `contextIsolation: true`, `nodeIntegration: false`
- Passwords hashed with Argon2
- TOTP multi-factor login, with BIP39 recovery codes
- Encrypted database, guarded schema, versioned migrations
- Login lockout, session boundary, audit trail
- Offline licence tokens signed with Ed25519 — the private key never enters the repo

About 7,800 of those lines are the security layer alone.

### Data in

POS exports are read directly — CSV, XLSX and a vendor-specific format. Nothing
gets retyped, because everything that gets retyped eventually gets retyped wrong.

### How I work

Significant decisions go into a dated record before they are implemented: the
reasoning, the alternatives, and what was rejected and why. There are around
fifteen such records so far. Working documentation is in German — the product is
built for kitchens in Austria.

---

## Background

Twenty years in gastronomy. Fifteen of them as Chef de Rang; the last five as
Restaurant Manager — the one who has to answer for the numbers at the end of the
month.

Everything I know about how a kitchen's numbers actually get written down, I
learned standing in one. That is the part I could not have read in a book, and it
is the reason this program looks the way it does rather than like the ones sold to
restaurants by people who have never closed one.

---

## Certificates

**[Google Data Analytics Professional Certificate](https://coursera.org/verify/professional-cert/BXVW3FETPH0C)** — Coursera

Spreadsheets, SQL, R, and how to present a number someone will act on.

---

## Elsewhere

- [nkadirc.com](https://nkadirc.com) — writing and projects
- [Gastrorix](https://nkadirc.com/gastrorix/)
- mail@nkadirc.com
