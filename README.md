# Sidhi Florals

Billing, inventory and bouquet management for Sidhi Florals, a flower shop. Ring up flowers and bouquets, build custom bouquets, track stock and margins, manage customer credit and print or WhatsApp receipts. It installs as a PWA and talks to Supabase directly, with no API server, so it opens in about a second.

## Features

| Area | What it does |
| --- | --- |
| Dashboard | Today's revenue, stems sold, monthly revenue, bouquets this month, revenue chart |
| Billing | Flowers and ready bouquets (with "can make N" from current stock), custom bouquet builder, discounts, credit sales, quick bill generator |
| Inventory | Stock levels, bouquet recipes, profit margins |
| Customers | Customer list, purchase history, archiving |
| Sales | Sales history with void and audit trail |
| Reports | Five sales and margin charts |
| Credits & Dues | Outstanding balances and repayments |
| Receipts | Print, or share as a PDF over WhatsApp |
| Extras | Built-in calculator, data backup, offline-ready PWA install |

## Tech stack

React + TypeScript + Vite, Tailwind CSS, TanStack Query, Supabase (Postgres, SQL functions and views), Vitest, Vercel.

## Getting started

```bash
git clone https://github.com/rajivagarwal221/Sidhi-Florals.git
cd Sidhi-Florals
npm install
cp .env.example .env     # VITE_SUPABASE_URL and VITE_SUPABASE_ANON_KEY (Supabase > Project Settings > API)
npm run dev              # http://localhost:5173
```

## Database

SQL migrations are in `supabase/migrations/`. On a new Supabase project, run them in the SQL editor in this order: `0001_schema.sql`, `0003_views.sql`, `0002_functions.sql`, then `0005` to `0009` in numeric order.

## Shop details on receipts

Edit `src/config/shop.ts` (name, tagline, address, phone, GSTIN, footer).

## Scripts

| Command | What it does |
| --- | --- |
| `npm run dev` | Start the dev server |
| `npm run build` | Typecheck and build to `dist/` |
| `npm run preview` | Preview the production build |
| `npm test` | Vitest: cart, bouquet and checkout rules, BouquetBuilder |
| `npm run typecheck` | TypeScript check |
| `node scripts/make-icons.mjs` | Regenerate PWA icons |

## Deploy (Vercel)

Import the repo with framework "Vite", add the two `VITE_*` environment variables and deploy. `vercel.json` sends every path to `index.html`.

## Security

The app has no login, and the Supabase anon key can read and write every table. Anyone who opens the deployed site can extract that key from the page. Before sharing the URL, add Supabase Auth (even a single shop login) and Row Level Security policies that only allow signed-in users.
