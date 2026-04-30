# Hey, I'm Corey.

Software engineer based in Philadelphia. Recent CS grad shipping AI-assisted tools solo while looking for my first full-time SWE role. I build things that actually work — not just hello-world demos, but applications with real architecture, real tests, and real edge cases handled.

## What I've shipped

### [InvoiceFlow](https://github.com/coreystevensdev/invoiceflow) — [live demo](https://invoiceflow.vercel.app)

Drop a PDF invoice and get vendor, line items, tax, total, and due date back as structured JSON in about five seconds, each field annotated with the source text Claude pulled it from. No login, no database — PDFs process in memory and disappear when the request ends. Next.js 16, React 19, the Anthropic SDK, and Zod. Strict nonce-based CSP, an 8-category typed error taxonomy, and a 3× rolling-median cost ceiling that catches runaway extractions.

### [TellSight](https://github.com/coreystevensdev/tellsight) — _live demo coming 2026-05-04_

Full-stack SaaS analytics for small businesses. Upload a CSV, see charts, get plain-English AI interpretation of trends and anomalies. Multi-tenant with PostgreSQL row-level security, Stripe billing with webhook lifecycle management, SSE streaming for AI summaries, and a curation pipeline that sends computed statistics to Claude rather than raw rows. 781 tests across unit, integration, and E2E. Clone it, run `docker compose up`, and see it work.

Both projects share an architectural bias: customer data shouldn't have to leave the customer's control for AI to be useful. That tradeoff drove most of the interesting decisions.

## Tech I reach for

TypeScript and Next.js 16 on the frontend, Express and PostgreSQL on the backend, Drizzle ORM for type-safe queries, Tailwind for styling. The Anthropic SDK with Zod for structured-output AI integration. Vitest and Playwright for tests. Docker and GitHub Actions for the build and deploy loop. Comfortable picking up other stacks when a problem fits.

## What I'm looking for

A team that ships often and lets junior engineers write real code from day one. Particularly drawn to teams using AI to make tools for non-technical users, where getting the data-handling story right matters as much as getting the model right. Open to full-stack, backend, or frontend roles.

## Get in touch

- [LinkedIn](https://www.linkedin.com/in/coreystevensdev/)
- [cstevens3446@gmail.com](mailto:cstevens3446@gmail.com)
