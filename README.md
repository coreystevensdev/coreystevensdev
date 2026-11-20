I build AI systems and backend APIs in Python, TypeScript, Go, Java, and C#.

Based in Philadelphia, open to Software Engineer and AI Engineer roles, remote or around PA, DE, NJ and DC. Everything linked below is live and runs in a browser with no signup. [Get in touch](#contact).

## Start here

Three that show the most. All nine are listed further down.

**[TaxCite](https://taxcite.coreystevens.dev/)** answers a tax question from the IRS publications and names the page it used, so you can go read the source instead of trusting the model. [Source](https://github.com/coreystevensdev/taxcite)

The hard part is not producing an answer, it is making sure the answer came from the right passage. Searching by meaning alone scores a question and a passage separately, which measures what a passage is *about* rather than whether it answers *this* question, so retrieval pulls 24 candidates and a second model reads each question-passage pair together to pick the 8 worth sending. Quality is measured rather than asserted: 50 questions scored for faithfulness (0.945), context precision (0.857) and answer relevancy (0.633), with every question's individual score committed beside the aggregate so a change to retrieval is a paired comparison rather than two averages that might differ by luck. The page opens on that eval, worst question first. LangGraph, pgvector, Voyage embeddings, Ragas, and a human approval step before anything is generated. 121 tests.

**[Tellsight](https://tellsight.coreystevens.dev)** reads a small business's numbers and says what changed and what it means, then emails that explanation weekly. Upload a CSV or connect QuickBooks; the dashboard loads with sample data so you can see it work first. [Source](https://github.com/coreystevensdev/tellsight)

The model never sees a customer's transactions. The function that builds the prompt accepts computed statistics and will not accept data rows, so the privacy boundary is a type signature rather than a code-review habit. Tenant isolation lives in PostgreSQL itself rather than in application code, which means a missing `WHERE` clause in a query cannot leak another business's data. Three-stage pipeline: compute the statistics, score them for what an owner would actually care about, then assemble the prompt. Streaming summaries, a four-queue background pipeline for the weekly digest, an offline eval harness with a judge model deliberately different from the one being graded, Stripe billing. Running on EC2 and RDS. 5,782 tests.

**[InvoiceFlow](https://invoiceflow-cs.vercel.app)** turns a PDF invoice into structured JSON in about five seconds. Drop a file or hit "Use sample", and every extracted field shows the source text it was read from. [Source](https://github.com/coreystevensdev/invoiceflow)

Nothing is stored. No database, no file persistence, no log line containing invoice content, and that is a property of the codebase rather than a policy: no database dependency exists in it at all. The schema is enforced where the model's response arrives, so a malformed reply never reaches application code, and ten typed error codes each map to a title and a next step so a failure explains itself. Measured against 150 ground-truth invoices across nine fields each. 160 tests.

## Six more, all live

- **[Fairline](https://fairline.coreystevens.dev/)** grades sports bets on whether the price beat where the market closed, not on whether the bet won, which is the harder standard. A human approves every pick before it goes anywhere. [Source](https://github.com/coreystevensdev/fairline)
- **[TitleTrace](https://titletrace.coreystevens.dev/)** takes a PA or NJ address and assembles what the public record says: owner, deeds, liens, zoning, flood zone. An agent fires five record lookups at once rather than in sequence, then chases detail only where there is something to chase. [Source](https://github.com/coreystevensdev/titletrace)
- **[Portfolio Rebalancer](https://rebalancer.coreystevens.dev/)** shows which holdings have drifted from your target allocation and what to trade to fix it, sells sequenced first so their proceeds fund the buys. Open a second tab and you get a different user who cannot see the first one's holdings. [Source](https://github.com/coreystevensdev/portfolio-rebalancer)
- **[TitleRate](https://titlerate.coreystevens.dev/)** quotes a title insurance premium for PA or NJ. Rates are tiered, so the premium accumulates across brackets the way income tax does, and the page shows which bracket each part of the price landed in. [Source](https://github.com/coreystevensdev/titlerate-java)
- **[bondcalc](https://bondcalc.coreystevens.dev/)** prices a bond: what it yields if held to maturity, and how much its price moves when rates move. Yield to maturity has no closed-form solution for most payment schedules, so it is solved by iteration. [Source](https://github.com/coreystevensdev/bondcalc)
- **[rolling-cost-cap](https://github.com/coreystevensdev/rolling-cost-cap)** is a published Python library that stops a runaway API bill. "Expensive" is relative: ten cents is an anomaly when your median call costs two, and normal when it costs eight. So it tracks a rolling median and trips on a multiple of it, behind an absolute per-call ceiling and a monthly budget. `pip install rolling-cost-cap`

## How I work with AI assistants

These are built with AI assistance, which is worth saying plainly because the interesting work is what has to exist around a model to make its output safe to ship. Each repo has a "How this was built" section naming what the model got wrong and what caught it. The short version: AI output is validated against a known-good set before it is stored, prompts are graded by a judge model that is deliberately not the model being graded, and published numbers get revised in public when a larger sample disagrees with them.

## Open source

**[langchain4j #5708](https://github.com/langchain4j/langchain4j/pull/5708)**: RAG chunking overlaps on purpose, which makes adjacent retrieved segments repeat text, and the model pays for that repetition twice. `OverlapRemovingContentAggregator` trims the duplicated span where two adjacent segments of the same document meet, and reads the splitter's own index metadata to decide adjacency instead of guessing from content. A decorator over any `ContentAggregator`, so the stock retriever is untouched. 15 tests. Open, 8/8 checks green, awaiting review.

## Stack

- **AI:** LangGraph, LangSmith, Anthropic SDK, pgvector, Voyage AI, Ragas, RAG, SSE streaming, eval harnesses
- **Languages:** Python, TypeScript, Go, Java, C#
- **Backend:** FastAPI, Express 5, Spring Boot 3, ASP.NET Core, Node.js
- **Data:** PostgreSQL, Redis, BullMQ, SQLAlchemy, EF Core, Drizzle ORM
- **Infra:** AWS EC2, RDS, ECR, Terraform, Docker, Kubernetes, Helm, GitHub Actions OIDC, CloudWatch
- **Testing:** pytest + respx, Vitest + Playwright, Testcontainers, xUnit, Ragas

## Contact

[LinkedIn](https://www.linkedin.com/in/coreystevensdev/) · cstevens3446@gmail.com
