# Cashfree AI Store

<img width="1191" height="837" alt="Screenshot 2026-06-03 at 11 04 28 AM" src="https://github.com/user-attachments/assets/24ac9968-5a4b-41df-8459-23ef2bd6f487" />


An AI-powered hostel booking demo with a chat agent that can answer questions, showcase listings, and trigger UPI payments via Cashfree — all from a single chat drawer.

> **Not production-ready.** This is a demonstration. For a production-grade implementation, reach out at [arjun@graycup.in](mailto:arjun@graycup.in) or [@arjunaditya\_](https://x.com/arjunaditya_) on X.

---

## Stack

- **Framework** — Next.js 16 (App Router)
- **Database** — [Turso](https://turso.tech) (libSQL / SQLite at the edge)
- **AI Agent** — Gemini 2.5 Flash with native function calling
- **Payments** — [Cashfree Payment Links API](https://docs.cashfree.com/docs/payment-links) (sandbox)
- **Encryption** — AES-256-GCM for admin session tokens
- **UI** — Tailwind CSS v4, Framer Motion

---

## Setup

**1. Clone and install**
```bash
git clone <repo>
cd cashfree-ai-store
bun install
```

**2. Environment variables**

Copy `.env.example` to `.env.local` and fill in:

| Variable | Where to get it |
|---|---|
| `TURSO_DATABASE_URL` | `turso db show --url <db-name>` |
| `TURSO_AUTH_TOKEN` | `turso db tokens create <db-name>` |
| `ADMIN_PASSWORD` | Any password you choose |
| `ENCRYPTION_KEY` | Any exactly 32-character string |
| `CASHFREE_APP_ID` | [Cashfree Dashboard](https://merchant.cashfree.com) → Payment Gateway → API Keys (Test mode) |
| `CASHFREE_SECRET_KEY` | Same as above |
| `GEMINI_API_KEY` | [Google AI Studio](https://aistudio.google.com/app/apikey) |

**3. Create database tables**
```bash
bun dev
curl -X POST http://localhost:3000/api/migrate
```

This creates both tables (`hostels`, `transactions`) and seeds the two demo listings.

**4. Run**
```bash
bun dev
```

- Frontend → `http://localhost:3000`
- Admin panel → `http://localhost:3000/admin`

---

## Cashfree Docs

- [Payment Links API](https://docs.cashfree.com/docs/payment-links)
- [Test credentials](https://docs.cashfree.com/docs/test-data)
- [Webhooks](https://docs.cashfree.com/docs/ipn-intro)
- [API Reference](https://docs.cashfree.com/reference/pg-new-apis-endpoint)
