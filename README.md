# VANTAGE — Research Intelligence Platform

AI-powered market research for every business. Plans from £19/month.

Built with Next.js 14, Supabase, Stripe, and Claude (Anthropic).

---

## Setup

### 1. Clone and install
```bash
git clone https://github.com/YOUR_USERNAME/vantage.git
cd vantage
npm install
```

### 2. Environment variables
```bash
cp .env.local.example .env.local
```
Fill in all values — see `.env.local.example` for the full list.

### 3. Database
Run `lib/schema.sql` in your Supabase SQL editor.

Then seed sample data:
```bash
npx ts-node lib/seed.ts
```

### 4. Run locally
```bash
npm run dev
# Open http://localhost:3000
```

---

## Deploy to Vercel

1. Push to GitHub
2. Import repo at vercel.com
3. Add all env vars from `.env.local.example` in Vercel project settings
4. Deploy — auto-deploys on every push to `main`

---

## Project Structure

```
app/
  page.tsx                      # Marketing homepage
  login/page.tsx                # Login
  signup/page.tsx               # Signup + plan selection
  dashboard/page.tsx            # Query interface
  result/[id]/page.tsx          # Query result
  boards/page.tsx               # Research boards list
  boards/[id]/page.tsx          # Board detail + export
  account/page.tsx              # Plan + billing
  team/page.tsx                 # Team workspace
  api/
    query/route.ts              # Claude AI synthesis
    boards/route.ts             # Boards CRUD
    boards/[id]/route.ts        # Board items CRUD
    webhooks/stripe/route.ts    # Stripe billing events

components/layout/AppLayout.tsx # Sidebar nav
lib/
  supabase.ts                   # Supabase client
  stripe.ts                     # Stripe client
  schema.sql                    # Run in Supabase SQL editor
  seed.ts                       # Sample data (13 research chunks)
types/index.ts                  # TypeScript types + plan config
```

---

## Plans

| Feature | Starter £19/mo | Professional £49/mo | Team £149/mo |
|---|---|---|---|
| Queries/month | 5 | Unlimited | Unlimited |
| Research Boards | — | 5 | Unlimited |
| Export | — | ✓ | ✓ |
| Team workspace | — | — | ✓ (10 users) |
| API access | — | — | ✓ |

---

## Services Required

- [Supabase](https://supabase.com) — database + auth (free tier)
- [Anthropic](https://console.anthropic.com) — Claude API for AI synthesis
- [Stripe](https://dashboard.stripe.com) — subscription billing
