# BillSteady Landing

The public landing page for BillSteady — pay real Nigerian bills (DisCo,
airtime, data, school fees) straight from a Stellar wallet, in XLM or
USDC, non-custodially. Astro + Tailwind v4, deployed to Vercel.

**Live:** https://billsteady-landing.vercel.app

## Status

As of 2026-11-08, this reflects a pivot from the original "naira bill
planner, no crypto" product to a non-custodial Stellar/stablecoin bill-pay
app — see [CLAUDE.md](CLAUDE.md) for why and what carries over (the
non-custodial principle, the contracts repo's security model) versus what
doesn't (the daily-savings planning concept, the existing app UI). The app
itself (billsteady-web) has not been rebuilt to match yet — this page is
ahead of the product on purpose, to validate the new positioning first.

One page: hero, problem, how-it-works, trust/safety points, CTA. ~44KB
total page weight. No backend, no forms, no tracking.

The primary CTA currently links to the
[billsteady-web](https://github.com/BillSteady/billsteady-web) GitHub repo —
a real, working link, but a placeholder for the actual deployed app URL,
which doesn't exist yet (billsteady-web's Cloudflare Pages deploy is
pending). Swap `APP_URL` in `src/pages/index.astro` once that's live.

See [CLAUDE.md](CLAUDE.md) for the visual direction ("Sunrise Teal") and the
design-token system.

## Related repos

- [billsteady-web](https://github.com/BillSteady/billsteady-web) — the planner PWA
- [billsteady-backend](https://github.com/BillSteady/billsteady-backend) — Supabase backend
- [billsteady-contracts](https://github.com/BillSteady/billsteady-contracts) — the Soroban jar smart contract

## Development

```bash
pnpm install
pnpm dev        # start the dev server
pnpm typecheck  # astro check
pnpm build      # production build
pnpm preview    # preview the production build locally
```

## Deploy

```bash
vercel --prod
```

## License

MIT — see [LICENSE](LICENSE).
