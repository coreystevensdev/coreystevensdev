# Hey, I'm Corey.

Philly-based software engineer with a focus on AI tooling and systems design. I care about where the model's boundary is: computed outputs, schema-validated responses, and structured context go in; raw user content and unvalidated LLM output stay out. That constraint shapes every design decision in my work.

## What I shipped

**[InvoiceFlow](https://github.com/coreystevensdev/invoiceflow)** ([live demo](https://invoiceflow-cs.vercel.app)) extracts structured data from PDF invoices using the Anthropic SDK with zero retention. Drop a PDF, get vendor / line items / tax / total / due date as JSON in about five seconds. No database, no auth, no stored content. Zod validates LLM output at the schema boundary so a malformed response fails loudly instead of corrupting downstream data. Next.js 16 + Anthropic SDK + Zod.

**[Tellsight](https://github.com/coreystevensdev/tellsight)** ([live demo](https://tellsight.coreystevens.dev)) is a full-stack SaaS analytics platform for small business owners. Upload a CSV or connect QuickBooks via OAuth, get charts plus plain-English AI interpretation delivered as a weekly email digest with week-over-week longitudinal context. Multi-tenant Postgres with row-level security, Stripe billing, SSE streaming, BullMQ workers.

The AI only ever sees computed statistics from a three-stage curation pipeline, never raw rows. The Anthropic SDK sits behind an in-house provider seam (retries, circuit breaker, cost gate, prompt caching) rather than a framework wrapper; the architecture decision is in an ADR. An offline eval harness grades summaries on faithfulness, completeness, and legal posture. A separate agent tier generates structured proposals with severity tiers and a routing gate that decides auto-notify vs. human approval based on confidence and financial impact. 1,635 tests (Vitest + Playwright); 5-stage GitHub Actions CI.

## Skills

**AI / LLM**: Anthropic SDK, prompt engineering, structured output validation, eval harnesses (faithfulness / completeness / legal posture), agent design, SSE streaming, RAG patterns

**Backend**: TypeScript, Node.js, Express 5, PostgreSQL, Redis, BullMQ, REST APIs, multi-tenant architecture, row-level security

**Frontend**: Next.js 16, React 19, Tailwind CSS, Playwright E2E

**Tooling**: Docker, GitHub Actions CI/CD, Drizzle ORM, Vitest, Zod, pnpm workspaces, Turborepo

**Languages**: TypeScript, JavaScript, SQL, C#

## On the side

A C# fantasy football management game I work on when the web stack gets boring. Generally drawn to systems where the architecture is the interesting problem.

## What I'm looking for

Actively looking for **AI Engineer**, **Software Engineer**, or **Full-Stack Engineer** roles. The AI tooling work above is the direction I want to go. I'm strongest in TypeScript / Node.js backend systems with LLM integration, but equally comfortable in data-layer, infrastructure, or product-focused full-stack roles where the system design is the hard part. Open to the Philadelphia / Wilmington / Princeton corridor or fully remote.

## Reach me

[LinkedIn](https://www.linkedin.com/in/coreystevensdev/) · cstevens3446@gmail.com
