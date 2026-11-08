# BillSteady Landing

Marketing/landing page for BillSteady, deployed separately from the product
itself. Astro (static, ships near-zero JS) + Tailwind v4.

## Product pivot (2026-11-08)

BillSteady pivoted from "naira bill planner, no crypto" to a non-custodial
Stellar/stablecoin bill-pay app, for two personas: Nigerians who already
hold crypto, and diaspora senders paying a relative's bill from abroad.
Decided and reasoned through with the user before this rewrite:
- **Pay-now, not save-first.** The original "save a little daily before the
  bill is due" planning concept is dropped for this persona — someone who
  already holds XLM/USDC isn't short on cash, they just want to spend what
  they have on a real bill without an off-ramp detour.
- **Both assets, XLM and USDC.**
- **Stay non-custodial.** This was a deliberate carry-over, not a given —
  the original PRD's whole regulatory strategy (never hold money, route
  through licensed partners, avoid looking like a VASP) was built to avoid
  exactly the exposure a "stablecoin bill pay app" invites. The fix is
  architectural, not cosmetic: every payment is signed by the user's own
  wallet, same principle already proven in billsteady-contracts' jar
  contract (`require_auth` on every fund-moving call, no admin path that
  moves user funds) — that still holds even though the "jar" itself
  (locking, time-delay) is no longer the right UI for a pay-now flow.
- billsteady-web's existing planner UI (30 tests, Bills/Planner/Ask-for-time
  screens) was built for the dropped persona and is not a starting point
  for the new app UI — expect that repo to need a comparable rewrite, not
  an extension, when that work starts.

This repo is one of four:
- [billsteady-web](https://github.com/BillSteady/billsteady-web): the planner PWA
- [billsteady-backend](https://github.com/BillSteady/billsteady-backend): Supabase backend
- [billsteady-contracts](https://github.com/BillSteady/billsteady-contracts): the Soroban jar contract
- **billsteady-landing** (this repo): the public-facing landing page

## Visual direction: "Sunrise Teal"
Warm consumer-fintech optimism (Wise/Revolut-style), built on BillSteady's
existing brand teal so the landing page and the live app read as one
product. Tokens live in `src/styles/global.css` (`@theme` block).
- **Brand teal** (`--color-brand-*`): same scale as billsteady-web, the
  product's identity.
- **Sunrise amber** (`--color-sunrise-*`): the one accent — CTAs, coins,
  highlights. Never a whole section background.
- **Cream, not white** (`--color-cream`): warmer than stark white.
- **Type**: Plus Jakarta Sans only, varying weight (no second typeface).
- **Shape**: large radii (rounded-2xl/3xl+), soft colored shadows
  (`--shadow-soft*`), never gray drop-shadows, never glass/blur-morphism.
- **Illustration**: flat line-art SVG (wallet, direct-payment flow, phone
  mockup), brand teal + one amber accent. No stock photography — it
  wouldn't represent the actual audience, and there isn't any on hand that
  would.

## Stack
- Astro (static output) + Tailwind v4 (CSS-first `@theme`, no config file)
- Deployed to Vercel

## Commands
- pnpm install | pnpm dev | pnpm build | pnpm preview | pnpm typecheck

## Rules
- No stock photos of people — illustration only, matching the direction above.
- The primary CTA currently points at the billsteady-web GitHub repo
  (`src/pages/index.astro`, `APP_URL` constant) — swap it to the real
  deployed app URL once billsteady-web is live on Cloudflare Pages.
- Keep this page light — it's often the first thing a user on a cheap
  Android phone over 3G loads, before they've decided BillSteady is worth
  their data. Current build: ~44KB total.
