# Secure Notes — Frontend

A minimal single-page frontend for the [Secure Notes backend](https://github.com/YOUR-USERNAME/note-taker-backend), built as part of a technical assessment for a Secure Note-Taking Application.

> **Live frontend:** https://note-taker-frontend.vercel.app
> **Live backend API:** https://note-taker-backend-0jxe.onrender.com

---

## Overview

This is a deliberately minimal frontend — no framework, no build step, no design system. It exists to demonstrate that the backend API works end-to-end through a real browser interface, per the assessment instruction:

> *"DO NOT waste time improving the frontend. This is a backend task."*

It is a **single `index.html` file** with inline CSS and vanilla JavaScript. Nothing else.

---

## Features

### Authentication
- Register a new account
- Log in with existing credentials
- Log out (client-side token discard)
- Session persists across page refreshes via `localStorage`

### Notes (authenticated users)
- View a paginated list of the user's own notes
- Create a new note
- Edit an existing note (title and content)
- Delete a note

### Posts (public — Scenario 2)
- Create a post as the logged-in user
- Browse users via a public directory (names only — no email exposure)
- View any user's posts (uses the backend `$lookup` aggregation)

### Admin section (admin role only)
- List all users in the system
- View everyone's notes (not just their own)
- View users grouped by interests (Scenario 1 aggregation result)

The admin section only renders when the logged-in user has `role: "admin"`. Regular users never see it.

---

## Tech stack

| Concern | Choice | Why |
|---|---|---|
| Language | Vanilla JavaScript (ES2020) | No framework, no build step, per the assessment's "no templates" instruction |
| Styling | Inline `<style>` block | Minimal CSS for readability only; not a design deliverable |
| State | `localStorage` for JWT + user object | Session persistence across refresh without a server-side session |
| HTTP | Native `fetch` | No axios/ky — one less dependency |
| Routing | None | Single-page app; sections toggle via CSS classes |

**No dependencies. No `node_modules`. No build pipeline.**

---

## Project structure
