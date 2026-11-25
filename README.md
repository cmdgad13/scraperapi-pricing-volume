# Crawlbase Alternative: What ScraperAPI Costs per 1,000 Pages, Which Plan Fits Your Volume, and When Switching Isn't Worth It

If your Crawlbase bill swings with domain complexity and your hardest targets still come back as blocks, ScraperAPI is the closest like-for-like swap: request-volume plans starting at **$49/month for 100,000 credits**, a standard page costing 1 credit, and a 7-day trial with 5,000 credits that doesn't ask for a card.

The catch is that "one page" isn't one price. A JavaScript-rendered page on the Hobby plan costs 10 credits, so the same $49 buys 100,000 plain pages or 10,000 rendered ones. Below you'll find every plan ScraperAPI publishes, the effective cost per 1,000 pages at each tier, how the major providers differ on failed requests, and the cases where staying on Crawlbase or picking a different tool is the better call.

## Quick answer: which plan most people actually need

> **Hobby, $49/month for 100,000 credits and 20 concurrent threads**, if you scrape plain HTML or a light mix of rendered pages. Move to **Startup, $149/month for 1,000,000 credits**, once plain-page volume passes roughly 100,000 a month, because the per-credit price drops from $0.00049 to $0.000149. If more than half your requests need rendering, premium proxies or bot-protection bypass, price your own URL mix before choosing a tier.

👉 [Check the current ScraperAPI plans and per-request credit costs](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## Every ScraperAPI plan on the pricing page

| Plan | Credits / month | Concurrent threads | Price / month | Best for | Start |
| --- | --- | --- | --- | --- | --- |
| Free | 1,000 | 5 | $0 | Testing one endpoint or a small scheduled job | [Start free](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Hobby | 100,000 | 20 | $49 | Plain HTML at low volume; US and EU geotargeting only | [Open Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | 1,000,000 | 50 | $149 | First tier where plain pages fall under $0.15 per 1,000 | [Open Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | 3,000,000 | 100 | $299 | Country-level geotargeting outside the US and EU | [Open Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | 5,000,000 | 200 | $475 | Volume that spikes; pay-as-you-go overage applies | [Open Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | 10,500,000 | 300 | Custom quote | Steady high volume with auto-upgrade | [Ask for Professional pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 | 500 | Custom quote | High concurrency jobs | [Ask for Advanced pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | 22,000,000+ | 500+ | Custom quote | Custom terms and volume | [Talk to sales](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

Three plan features decide more purchases than the credit number:

- **Geotargeting.** Hobby and Startup cover the US and EU. Country-level targeting elsewhere starts at Business, which is the $299 line item people miss when they budget $49.
- **Analytics history.** 30 days on Hobby and Startup, unlimited from Business up.
- **What happens when credits run out.** The pricing FAQ describes two mechanisms: auto-upgrade, which moves you up a tier when the allowance is spent (Hobby through Professional), and pay-as-you-go at a fixed per-credit rate up to a cap you set (Scaling and above). Running past your concurrency limit returns a 429 rather than queueing the request, and exceeding credits pauses scraping until renewal unless one of those two mechanisms is on. Third-party reviews report a 10% discount for annual billing; confirm it at checkout rather than assuming.

Credits don't roll over, and overage billing only exists from Scaling upward. On Hobby through Business, the practical choice is auto-upgrade or waiting for renewal.

## What a request actually costs

ScraperAPI prices every request in credits, and the credit cost depends on the target and the parameters you send. The multipliers are published, and the dashboard has a Domain Cost Estimator plus a `max_cost` setting to cap any single scrape.

| Request type | Credits | Per 1,000 at Hobby | Per 1,000 at Startup | Per 1,000 at Business |
| --- | --- | --- | --- | --- |
| Standard page | 1 | $0.49 | $0.15 | $0.10 |
| E-commerce (Amazon, Walmart, eBay) | 5 | $2.45 | $0.75 | $0.50 |
| Google or Bing SERP | 25 | $12.25 | $3.73 | $2.49 |
| LinkedIn | 30 | $14.70 | $4.47 | $2.99 |
| Bot-protection bypass | 10 | $4.90 | $1.49 | $1.00 |
| JS rendering (`render=true`) | 10 | $4.90 | $1.49 | $1.00 |
| Premium proxy (`premium=true`) | 10 | $4.90 | $1.49 | $1.00 |
| Premium proxy plus rendering | 25 | $12.25 | $3.73 | $2.49 |
| Ultra premium | 30 | $14.70 | $4.47 | $2.99 |
| Ultra premium plus rendering | 75 | $36.75 | $11.18 | $7.48 |

Geotargeting, sessions, device type, output format and auto parsing add nothing to the credit cost.

The spread is the whole story. A rendered premium-proxy page costs 25 times a plain one, so a plan that looks generous at $49 covers 4,000 hard pages, not 100,000. Two conclusions follow. First, estimate the share of your URLs that need `render=true`, premium proxies or bypass before comparing plan sizes, because that ratio, not total volume, decides your tier. Second, the volume discount is real but modest on the low end: moving Hobby to Startup cuts the per-credit price by about 70%, while Startup to Business cuts it by another third.

## Why people leave Crawlbase

Crawlbase's own comparison content lists four reasons teams shop around: targets that need heavier JavaScript execution, a billing model that's hard to forecast, sites with stronger anti-bot defenses, and a wish for a second provider to benchmark against. ScraperAPI addresses the first and fourth directly: rendering is a request flag rather than browser code you maintain, and the pricing unit is a fixed credit count rather than a domain tier.

The Crawlbase mechanics worth knowing before you compare quotes:

- **Billing runs on success.** A request is charged when Crawlbase returns `cb_status` 200 and the site answered with real content or a genuine 404/410. Blocks, timeouts and 5xx responses are free, and blocked requests are retried server-side until one gets through.
- **Rendered requests cost double.** A JavaScript-rendered request is billed at twice the domain's complexity tier, so the same URL costs different amounts depending on the parameters you send.
- **Domain complexity sets the price.** There's no flat per-page rate. Third-party listings reflect that: one tools directory puts Crawlbase at "from $3 per 1,000" while a competitor's comparison page cites about $0.21 per request on entry tiers. Those figures describe different request types, and neither converts cleanly to a per-page cost without knowing your domain mix.
- **The proxy products are separate.** Smart AI Proxy subscriptions run $149 to $449 per month on top of API usage.
- **The network size claim is disputed.** Crawlbase's site advertises 140M residential plus 98M datacenter IPs and a 99% success rate. Bright Data's comparison page, citing an independent review, puts the usable pool closer to 2M+ IPs across roughly 45 countries. Both numbers come from parties with an interest in the answer, so treat the marketed figure as a claim and test block rates on your own targets.
- **Same competitor page lists gaps:** no city-level geotargeting, no mobile or ISP proxy product, no SOCKS5, GDPR/CCPA compliance but no published SOC2 or ISO 27001, and roughly 35 managed scrapers. Those are a direct competitor's findings, not a neutral audit.

## Failed requests, 404s and the 70-second trap

This is where budgets actually diverge, and almost nobody compares providers on it.

| Provider | Charged | Not charged | Rendering cost |
| --- | --- | --- | --- |
| Crawlbase | 200 with real content, genuine 404/410 | Blocks, timeouts, 5xx | 2× the domain tier |
| ScraperAPI | 200, 404, and requests cancelled after 70 seconds | Other failures | 10 credits with `render=true` |
| ScrapingBee | 200, 404, 410 | Other failures | On by default at 5 credits, 1 with `render_js=false` |
| Bright Data Web Unlocker | Per 1,000 successful requests by default | — | Every request billed once custom features are on |

Two details in that table change real invoices. ScraperAPI's pricing FAQ states plainly that failed requests aren't charged, except for 200 and 404 responses and for requests you cancel after 70 seconds. Combine that with a documented behavior: protected domains can take up to 60 seconds, which is why the docs recommend a 70-second timeout. If your client gives up at 60 and cancels, you've paid for a page you never got. Set your timeout above the documented ceiling, or use the Async API for volume so a slow target doesn't turn into a cancellation.

ScrapingBee and Bright Data come at the same problem from opposite ends. ScrapingBee bills 200, 404 and 410 responses and turns rendering on by default at 5 credits, so a forgetful `render_js=false` can cost you five times the expected rate. Bright Data's Web Unlocker bills per thousand successful requests until you switch on custom features, after which every request is billable.

The comparison method that survives all of this comes from Crawlbase's own evaluation guide: run a few thousand requests of your real workload through each candidate, measure the block rate yourself, and convert every provider to cost per successful request including retries. Advertised success rates are averages over easy sites and can't be compared across vendors.

👉 [Run your own URL list through ScraperAPI's trial and check the credit math](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## How the trials compare

ScraperAPI gives you a 7-day trial with 5,000 credits and no credit card, then a permanent free plan with 1,000 credits a month and 5 concurrent threads. Five thousand credits is 5,000 plain pages, but only 500 rendered ones or 66 ultra-premium renders, so spend them on your hardest domains rather than a full backfill.

The alternatives structure trials differently. Crawlbase offers up to 5,000 requests without a card, expanding to 10,000 once payment details are added, according to Bright Data's comparison page. Apify's free plan includes $5 of monthly credit, no card, and stops when it's spent. ScrapingBee gives a one-time 1,000-credit trial, which at its default 5 credits per rendered request is 200 pages.

## The other options, in one table

| Tool | Billing unit | Entry point | Failure billing | Where it wins |
| --- | --- | --- | --- | --- |
| ScrapingBee | Monthly credits, 1 to 75 per request | $19 for 75,000 credits, up to $599 for 8M | 200/404/410 billed | Scripted browser interaction: scrolling, clicking, waiting |
| Bright Data | Per request, record or GB depending on product | Free tier of 5,000 monthly credits, proxies excluded | Per 1,000 successful by default | ISP and mobile proxies, city-level targeting, SOC2/ISO 27001/CSA STAR, 120+ scrapers |
| Apify | Compute units (1 GB × 1 hour) plus proxy traffic | Free, $19, $199, $999 per month | Usage-based | Ready-made Actors and a hosted runtime |
| Zyte | Bandwidth for proxies, usage for extraction | Usage-based | — | Teams already inside the Scrapy ecosystem |
| Firecrawl | Credits per page | Usage-based | 403/404 pages billed | One-call crawl, map, search and schema extraction; AGPL-3.0 core |
| Jina Reader | Output tokens | Free tier labelled non-commercial | — | Turning a single URL into clean Markdown with no setup |
| Crawl4AI | Free library, hosted cloud per credit | Open source | — | Self-hosting with Playwright and no copyleft requirement |

## Where ScraperAPI is the wrong choice

Three situations come up repeatedly.

**You need city or ASN-level targeting.** The plan grid tops out at country-level geotargeting from Business upward, and US/EU only on the two cheapest tiers. Reviewers flag the same limit. Ad verification, localized SERP checks and account management work need city-level control, which means Bright Data rather than ScraperAPI.

**Your pipeline consumes Markdown.** ScraperAPI returns HTML or JSON, and reviewers note there's no built-in Markdown conversion. If you moved to Crawlbase for its `format=md` output to feed an LLM, switching to ScraperAPI adds a conversion step, and Firecrawl or Jina Reader may be the shorter path.

**You need agent tooling today.** Reviews published in 2026 disagree on whether ScraperAPI ships an MCP server, with one saying the current product added it and another saying MCP integration is absent. Verify the current status before you buy on that basis.

Two more practical limits: structured endpoints cover roughly ten major sites, against Crawlbase's ~35 managed scrapers, and credits reset rather than accumulate, so a burst month followed by a quiet one doesn't get cheaper.

## Migrating without losing a week

The switch is mostly mechanical if you test in the right order.

1. **Pull 50 URLs across your hardest domains.** Run them through both tools and diff the extracted text. Check that boilerplate is stripped and that tables and code blocks survive.
2. **Count how many need rendering.** That ratio times 10 credits is your real plan size, not your total URL count.
3. **Run 2,000 to 3,000 requests against your worst domain** and record attempts per success. This is the only block-rate number worth trusting.
4. **Convert to cost per successful request:** credits per attempt × attempts × your tier's per-credit price. Compare that figure, not the sticker price.
5. **Check structured output coverage.** Auto parsing only helps on supported sites; the rest still needs your own selectors.
6. **Re-test geotargeting, sessions and output format.** These are free extras on ScraperAPI, but confirm they behave the way your code expects.
7. **Set `max_cost` per scrape and watch the 70-second cancellation rule** on any target that routinely takes a minute.

## Which one to buy

Plain HTML under 100,000 pages a month: Hobby at **$49**. Plain or lightly rendered work between 100,000 and 1,000,000 pages: Startup at **$149**, where the per-credit price falls about 70%. Country-level geotargeting outside the US and EU: Business at **$299**, no way around it. Above 5 million credits with spiky traffic: Scaling at **$475** with pay-as-you-go turned on. City-level targeting, mobile proxies or an audited compliance pack: not ScraperAPI. Clean Markdown for an LLM pipeline with no conversion code: Firecrawl or Jina Reader.

Two things to confirm before you enter payment details. Your trial needs no card, so any charge is a deliberate step rather than an automatic one; check whether your chosen plan uses auto-upgrade or pay-as-you-go before your first heavy month. And remember that 404s in a crawl are billable, which matters if you're crawling link-heavy sites where a chunk of URLs are dead.

👉 [Start with the 5,000-credit trial and price your own URL mix against each tier](https://www.scraperapi.com/pricing/?fp_ref=coupons)
