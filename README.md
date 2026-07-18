# Hey, Im Corey!

Building AI systems and backend APIs in Python, TypeScript, Go, Java, and C#.

## Projects

**AI / LLM**

**[TaxCite](https://github.com/coreystevensdev/taxcite):** Agentic RAG over 14 IRS publications. LangGraph state machine, pgvector retrieval, Voyage AI embeddings, LangSmith tracing, Ragas eval (faithfulness / answer relevancy / context precision). HITL interrupt before generation. 62 tests.

**[Fairline](https://github.com/coreystevensdev/fairline):** Agentic NFL/NBA/MLB/NHL betting research. Removes bookmaker vig from Pinnacle sharp lines to derive no-vig fair probabilities, surfaces closing line value opportunities via Claude forced tool call, LangGraph HITL approval gate before bet slip prep. Stripe billing. 189 tests.

**[TitleTrace](https://github.com/coreystevensdev/titletrace):** LangGraph property title agent for PA and NJ. Parallel Send API fan-out across parcel, tax, lien, and zoning data (Philadelphia OPA, ATTOM Data); a FEMA flood-zone client is implemented but not yet wired into the graph. Claude synthesis via forced tool call. 40 tests.

**[Tellsight](https://github.com/coreystevensdev/tellsight):** Multi-tenant analytics SaaS for small businesses. Three-stage curation pipeline (compute stats, score by relevance, assemble prompt), SSE streaming, BullMQ weekly digest, offline eval harness, Stripe billing, row-level security. 1,671 Vitest tests + Playwright E2E.

**SWE / APIs**

**[InvoiceFlow](https://github.com/coreystevensdev/invoiceflow)** ([live demo](https://invoiceflow-cs.vercel.app)): Zero-retention PDF invoice extraction. Next.js 16, Anthropic SDK, per-field reasoning tooltips, Zod validation at the SDK boundary. No database, no stored content by design.

**[bondcalc](https://github.com/coreystevensdev/bondcalc):** Go bond calculator. YTM via Newton-Raphson iteration, Macaulay and modified duration. JWT auth, distroless container, AWS ECS Fargate + Terraform. 18 tests.

**[portfolio-rebalancer](https://github.com/coreystevensdev/portfolio-rebalancer):** ASP.NET Core 8 REST API. MediatR CQRS, drift detection, rebalancing order generation. TestContainers integration tests hit a real PostgreSQL container. EC2 + Terraform, GitHub Actions OIDC (no stored AWS credentials). 25 tests.

**titlerate-java / titlerate-dotnet (private):** Title insurance premium calculators. Spring Boot 3.3 + Spring Security JWT (Java) and ASP.NET Core 9 Minimal API + EF Core (C#). Multi-tier bracket accumulation for state-filed PA and NJ rate schedules, JWT auth, PostgreSQL.

**[rolling-cost-cap](https://github.com/coreystevensdev/rolling-cost-cap):** Published Python library on PyPI. Rolling-median anomaly cap for LLM and metered API calls. Three independent layers: rolling median, absolute ceiling, monthly budget. Zero dependencies, thread-safe, fully typed. 27 tests.

## Stack

**AI:** LangGraph, LangSmith, Anthropic SDK, pgvector, Voyage AI, Ragas, RAG, HITL, SSE streaming, eval harnesses

**Languages:** Python, TypeScript, Go, Java, C#

**Backend:** FastAPI, Express 5, Spring Boot 3, ASP.NET Core 9, Node.js

**Data:** PostgreSQL, Redis, BullMQ, SQLAlchemy, EF Core, Drizzle ORM

**Infra:** AWS ECS Fargate, Terraform, Docker, GitHub Actions OIDC, Helm

**Testing:** pytest + respx, Vitest + Playwright, TestContainers, xUnit, Ragas

## Contact

[LinkedIn](https://www.linkedin.com/in/coreystevensdev/) · cstevens3446@gmail.com
