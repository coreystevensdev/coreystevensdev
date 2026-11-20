I build AI systems and backend APIs in Python, TypeScript, Go, Java, and C#.

Based in Philadelphia, open to Software Engineer and AI Engineer roles, remote or around PA, DE, NJ and DC. Everything linked below is live. [Get in touch](#contact).

## Try these first

All of these run in a browser right now, no signup:

- **[Tellsight](https://tellsight.coreystevens.dev)** reads your business numbers and tells you what changed, in plain English. Upload a CSV or connect QuickBooks; the dashboard loads with sample data so you can see it work before signing up. [Source](https://github.com/coreystevensdev/tellsight)
- **[InvoiceFlow](https://invoiceflow-cs.vercel.app)** turns a PDF invoice into structured JSON in about five seconds. Drop a file, or hit "Use sample". Every field shows the text it was read from. [Source](https://github.com/coreystevensdev/invoiceflow)

- **[bondcalc](https://bondcalc.coreystevens.dev/)** prices a bond: yield to maturity, duration, current yield. The strip under the form draws one coupon per remaining payment. [Source](https://github.com/coreystevensdev/bondcalc)
- **[TitleRate](https://titlerate.coreystevens.dev/)** quotes a title insurance premium for PA or NJ and shows which bracket each part of the price landed in. [Source](https://github.com/coreystevensdev/titlerate-java)
- **[Fairline](https://fairline.coreystevens.dev/)** grades sports bets on whether the price beat where the market closed, not on whether the bet won. The pages run on seeded sample data and say so, because a betting record that is not real is a claim about performance. [Source](https://github.com/coreystevensdev/fairline)
- **[TitleTrace](https://titletrace.coreystevens.dev/)** takes a PA or NJ address and assembles what the public record says: owner, deeds, liens, zoning, FEMA flood zone. The page shows the agent's five lookups running in parallel and the drill-down branch skipping itself when nothing is encumbered. [Source](https://github.com/coreystevensdev/titletrace)
- **[TaxCite](https://taxcite.coreystevens.dev/)** answers tax questions from IRS publications and cites the page it used. The page opens on the eval: 50 real questions with the answer given, the passages retrieval pulled, and what each one scored, sorted worst first. [Source](https://github.com/coreystevensdev/taxcite)
- **[Portfolio Rebalancer](https://rebalancer.coreystevens.dev/)** shows which holdings have drifted from your target allocation and what to trade to fix it, sells first so their proceeds fund the buys. The page holds a real bearer token: open a second tab and it gets a different user who cannot read the first one's holdings. [Source](https://github.com/coreystevensdev/portfolio-rebalancer)

## AI and LLM

**[TaxCite](https://github.com/coreystevensdev/taxcite)** ([live](https://taxcite.coreystevens.dev/)) answers a tax question and cites the IRS publication and page the answer came from, so you can go check it.

Agentic RAG over 14 IRS publications: LangGraph state machine, pgvector retrieval, voyage-3 embeddings reranked by a `rerank-2` cross-encoder, LangSmith tracing, a human approval step before generation. Scored with Ragas over 50 questions: faithfulness 0.945, answer relevancy 0.633, context precision 0.857. Per-question scores are committed next to the aggregates, so a retrieval change is a paired comparison rather than two means that might differ by noise. 110 tests.

**[Fairline](https://github.com/coreystevensdev/fairline)** ([live](https://fairline.coreystevens.dev/)) finds sports bets priced better than the sharp market, and makes a human approve each one before it goes anywhere.

Bookmaker odds carry a built-in margin called vig. Fairline strips it from Pinnacle's lines to recover the market's true implied probability, then surfaces prices that beat it. A LangGraph `interrupt()` pauses the graph for approval before any bet slip is prepared, and state persists in Postgres so an approval survives a restart. Picks are graded on closing line value rather than win rate, which is the harder standard. NFL, NBA, MLB, NHL. Stripe billing. 376 tests.

**[TitleTrace](https://github.com/coreystevensdev/titletrace)** ([live](https://titletrace.coreystevens.dev/)) takes a PA or NJ street address and assembles a property title report from county, lien, and federal flood records.

A LangGraph agent fans five lookups out in parallel via the Send API (parcel, ownership, liens, zoning, FEMA flood zone), then conditionally drills into lienholder detail and tax delinquency based on what comes back. Philadelphia routes through the free OPA and OpenDataPhilly APIs; everything else uses ATTOM. Claude synthesizes the report through a forced tool call and names the gaps in the data rather than filling them in. 106 tests.

**[Tellsight](https://github.com/coreystevensdev/tellsight)** ([live](https://tellsight.coreystevens.dev)) is multi-tenant analytics for small businesses, with a weekly email that explains what moved and why.

Three-stage curation pipeline: compute statistics, score them for relevance, assemble the prompt. The function that builds the prompt accepts computed statistics and not data rows, so raw customer transactions cannot reach the model; the privacy boundary is enforced by the type system rather than by code review. Row-level security lives in PostgreSQL rather than the application layer. SSE streaming, a four-queue BullMQ digest pipeline, an offline eval harness, Stripe billing. Running on EC2 and RDS. 5,506 tests.

## Backend and APIs

**[InvoiceFlow](https://github.com/coreystevensdev/invoiceflow)** ([live](https://invoiceflow-cs.vercel.app)) extracts vendor, line items, tax, total and due date from a PDF invoice, and shows the source text behind each one.

Next.js 16 and the Anthropic SDK with a Zod schema enforced at the SDK boundary. Nothing is stored: no database, no file persistence, no log line containing invoice content, which is a property of the codebase rather than a policy, since no database dependency exists in it at all. Eight typed error codes, each mapped to a title and a next step. 160 tests.

**[bondcalc](https://github.com/coreystevensdev/bondcalc)** ([live](https://bondcalc.coreystevens.dev/)) prices a bond: what it yields if you hold it to maturity, and how much its price moves when rates move.

Yield to maturity has no closed form for most payment schedules, so it solves by Newton-Raphson, converging in about ten iterations. Duration discounts each cash flow at the solved yield. Go, no database, distroless container, JWT auth, deployed to EC2 by Terraform with GitHub Actions OIDC and no stored AWS credentials. 36 tests.

**[titlerate-java](https://github.com/coreystevensdev/titlerate-java)** ([live](https://titlerate.coreystevens.dev/)) quotes a title insurance premium for PA or NJ from the state's filed rate schedule.

Rates are tiered, so the premium accumulates across brackets the way income tax does, and a lender policy issued alongside an owner policy takes a discount off the accumulated base. Spring Boot 3.3, stateless Spring Security JWT, Spring Data JPA, Testcontainers Postgres throughout. An unset `JWT_SECRET` signs with a random per-process key and warns, rather than falling back to one committed in the repo. 38 tests. Runs beside bondcalc on one EC2 instance, behind Caddy.

**[portfolio-rebalancer](https://github.com/coreystevensdev/portfolio-rebalancer)** ([live](https://rebalancer.coreystevens.dev/)) tells you which holdings have drifted from your target allocation and what to buy or sell to get back.

ASP.NET Core 10, MediatR vertical slices, EF Core 10. Sells are always sequenced before buys so the proceeds fund the purchases. Every query filters by the caller's user id at the EF level, so authentication and authorization are never separated. TestContainers integration tests run against a real PostgreSQL container. 41 tests.

**[rolling-cost-cap](https://github.com/coreystevensdev/rolling-cost-cap)** is a published Python library that stops a runaway API bill.

"Expensive" is relative: ten cents is an anomaly when your median call costs two, and normal when it costs eight. So it tracks a rolling median and trips when a call exceeds a multiple of it, backed by an absolute per-call ceiling and a monthly budget. The median layer stays dormant until enough samples exist, so one cheap first call cannot set a hair-trigger baseline. Zero dependencies, thread-safe, fully typed. `pip install rolling-cost-cap`. 29 tests.

## Open source

**[langchain4j #5708](https://github.com/langchain4j/langchain4j/pull/5708)**: RAG chunking overlaps on purpose, which makes adjacent retrieved segments repeat text, and the model pays for that repetition twice. `OverlapRemovingContentAggregator` trims the duplicated span where two adjacent segments of the same document meet, and reads the splitter's own index metadata to decide adjacency instead of guessing from content. A decorator over any `ContentAggregator`, so the stock retriever is untouched. 15 tests. Open, 8/8 checks green, awaiting review.

## Stack

- **AI:** LangGraph, LangSmith, Anthropic SDK, pgvector, Voyage AI, Ragas, RAG, SSE streaming, eval harnesses
- **Languages:** Python, TypeScript, Go, Java, C#
- **Backend:** FastAPI, Express 5, Spring Boot 3, ASP.NET Core, Node.js
- **Data:** PostgreSQL, Redis, BullMQ, SQLAlchemy, EF Core, Drizzle ORM
- **Infra:** AWS EC2, RDS, ECR, Terraform, Docker, Kubernetes, Helm, GitHub Actions OIDC, CloudWatch
- **Testing:** pytest + respx, Vitest + Playwright, TestContainers, xUnit, Ragas

## Contact

[LinkedIn](https://www.linkedin.com/in/coreystevensdev/) · cstevens3446@gmail.com
