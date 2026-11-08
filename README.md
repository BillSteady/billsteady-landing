# BillSteady Landing

The public landing page for BillSteady — a bill planner for people short on
cash in Nigeria (then Kenya, Ghana). Astro + Tailwind v4, deployed to Vercel.

**Live:** https://billsteady-landing.vercel.app

## Status

Shipped. One page: hero, problem, how-it-works, trust/safety points, CTA.
~44KB total page weight. No backend, no forms, no tracking.

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
