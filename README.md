# Hey, I'm Corey.

Actively looking for **AI Engineer**, **Software Engineer**, or **Full-Stack Engineer** roles. Fully remote.

AI / software engineer (recent CS grad). I build production LLM systems where inputs are structured and validated -- raw user data never reaches the model.

## Projects

**[Tellsight](https://github.com/coreystevensdev/tellsight)** ([live demo](https://tellsight.coreystevens.dev)) -- AI-powered analytics SaaS for small business owners. Upload a CSV or connect QuickBooks via OAuth, get charts and a plain-English AI interpretation delivered weekly with longitudinal context built from prior digests.

Under the hood: three-stage curation pipeline (compute stats, score by relevance, assemble prompt), Anthropic SDK behind an in-house provider seam (retries, circuit breaker, cost gate, prompt caching), an agent tier that generates structured proposals with severity levels and routes each one to auto-notify or human approval based on confidence and financial impact, and an offline eval harness grading summaries on faithfulness, completeness, and legal posture. Multi-tenant Postgres with row-level security, Stripe billing, SSE streaming, BullMQ workers. 1,635 tests (Vitest + Playwright); 5-stage GitHub Actions CI.

**[InvoiceFlow](https://github.com/coreystevensdev/invoiceflow)** ([live demo](https://invoiceflow-cs.vercel.app)) -- zero-retention PDF invoice extraction. Drop an invoice, get structured JSON (vendor, line items, tax, total, due date) in about five seconds. Zod validates LLM output at the schema boundary so a malformed response fails loudly instead of silently corrupting data. No database, no stored content. Next.js 16 + Anthropic SDK + Zod.

## Skills

**AI / LLM**: Anthropic SDK, prompt engineering, structured output validation, eval harnesses (faithfulness / completeness / legal posture), agent design, SSE streaming, RAG patterns

**Backend**: TypeScript, Node.js, Express 5, PostgreSQL, Redis, BullMQ, REST APIs, multi-tenant architecture, row-level security

**Frontend**: Next.js 16, React 19, Tailwind CSS, Playwright E2E

**Tooling**: Docker, GitHub Actions CI/CD, Drizzle ORM, Vitest, Zod, pnpm workspaces, Turborepo

**Languages**: TypeScript, JavaScript, SQL, C#

## On the side

A C# fantasy football management game I work on when the web stack gets boring. Generally drawn to systems where the architecture is the interesting problem.

## Reach me

[LinkedIn](https://www.linkedin.com/in/coreystevensdev/) · cstevens3446@gmail.com
