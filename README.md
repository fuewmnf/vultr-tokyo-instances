# vultr tokyo: what the NRT datacenter actually offers, how instance pricing works, and the reseller pages to ignore

Search *vultr tokyo* and the results get confusing fast. Sitting between genuine questions about Vultr's cloud servers in Japan, you'll find pages titled "Vultr Cloud Hosting Tokyo" selling ¥628-a-month cPanel plans — products that have nothing to do with deploying a Vultr cloud server. So here's the short answer first: yes, Vultr runs a real cloud datacenter in Tokyo, listed as the **NRT** region, and it has been part of the company's map since at least May 2015, when Vultr's own blog announced Storage plans for the Tokyo datacenter. You deploy there on hourly billing, across several instance families, and it's the sensible region when your users sit in Japan, Korea, or coastal China.

What follows: which instance families actually run in Tokyo, tracked per-instance prices with rough monthly figures, how the billing behaves, what those lookalike hosting pages really are, and a short guide to picking a plan.

> **Quick verdict:** Tokyo (NRT) is a legitimate Vultr region with hourly-billed instances. Most projects should start with a Cloud Compute plan in the size they need and scale up only if usage demands it; among the larger tracked Tokyo instances, prices run **$0.877–$5.26 per hour**. If a search result promises "Vultr hosting from ¥319/year", that's a cPanel reseller, not Vultr. 👉 [Check the live Tokyo region pricing on Vultr](https://www.vultr.com/pricing/?ref=7268283)

## Does Vultr have a datacenter in Tokyo?

Yes, and it's not new. Vultr's blog was announcing plans for the Tokyo datacenter back in May 2015 — the launch of its Storage Series there — which makes Tokyo one of the longer-running Asian locations in its network. Today the region (`nrt` in Vultr's naming) hosts several distinct instance families, and Vultr also operates Osaka, which matters if you're thinking about redundancy inside Japan. That combination — two Japanese cities from the same provider — is more useful than it sounds, and I'll come back to it.

One honest caveat before the numbers: instance prices and availability shift over time, so treat everything below as a snapshot and confirm the live figure on the plan page before you order.

## What you can deploy in Tokyo: the instance families

Three families currently show up in the Tokyo lineup, and you can decode most of what you need from the instance names.

**Cloud Compute** (`vc2` prefix) is the standard line — shared virtual servers for ordinary workloads. The tracked Tokyo rows include a 24-core / 96 GB Intel box, and the family extends down to much smaller plans that suit typical websites and apps.

**VX1** is a separate family whose tracked Tokyo rows span 32–64 cores and 128–512 GB of RAM. The suffix tells you the flavor: `-g` for general purpose, `-m` for memory-heavy configurations.

**Optimized Cloud** (`voc` prefix) splits into four subtypes you can read straight off the name:

- `voc-c` — dedicated CPU. The tracked Tokyo rows pair 32 cores with only 64 GB of RAM, which is the signature of a compute-focused box.
- `voc-g` — general purpose, with a balanced ratio (roughly 2–4 GB of RAM per core across the tracked rows).
- `voc-m` — memory optimized, around 8 GB of RAM per core (32 cores / 256 GB).
- `voc-s` — storage optimized; the tracked row pairs 256 GB of RAM with a 5,760 GB NVMe disk.

Two more naming details: the number before the `s` is the NVMe disk size (`500s` = 500 GB, `1280s` = 1,280 GB), and `-amd` marks AMD processors. Most Optimized Cloud and VX1 rows in Tokyo are AMD; the Intel option in this snapshot is the 24-core Cloud Compute machine.

## Vultr Tokyo instance pricing: a tracked snapshot

Vultr prices instances by the hour, and an independent instance-price tracker (Daestro) currently logs per-hour rates for the Tokyo region. The table below collects the tracked rows — the heavier end of Tokyo's catalog, since the tracker's list continues below this cut with smaller plans in the same families. Monthly figures are simple hourly × 720 conversions, rounded; treat them as an estimate for a server that runs all month, and let the plan page's monthly price be the deciding number.

| Instance | Family | vCPU | RAM | Tracked price | Deploy |
| --- | --- | --- | --- | --- | --- |
| vc2-24c-96gb | Cloud Compute | 24 | 96 GB | $0.877/hr · ≈$630/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-g-32c-128g | VX1 | 32 | 128 GB | $0.96/hr · ≈$690/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-g-32c-128g-1920s | VX1 | 32 | 128 GB | $1.223/hr · ≈$880/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-m-32c-256gb | VX1 | 32 | 256 GB | $1.28/hr · ≈$920/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-m-32c-256g-1920s | VX1 | 32 | 256 GB | $1.543/hr · ≈$1,110/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-g-48c-192g | VX1 | 48 | 192 GB | $1.44/hr · ≈$1,040/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-m-48c-384gb | VX1 | 48 | 384 GB | $1.92/hr · ≈$1,380/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-g-64c-256g | VX1 | 64 | 256 GB | $1.92/hr · ≈$1,380/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| vx1-m-64c-512gb | VX1 | 64 | 512 GB | $2.56/hr · ≈$1,840/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-g-24c-96gb-480s-amd | Optimized Cloud | 24 | 96 GB | $0.986/hr · ≈$710/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-c-32c-64gb-500s-amd | Optimized Cloud (dedicated CPU) | 32 | 64 GB | $0.877/hr · ≈$630/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-c-32c-64gb-1000s-amd | Optimized Cloud (dedicated CPU) | 32 | 64 GB | $0.986/hr · ≈$710/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-g-32c-128gb-640s-amd | Optimized Cloud (general) | 32 | 128 GB | $1.315/hr · ≈$950/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-m-32c-256gb-1600s-amd | Optimized Cloud (memory) | 32 | 256 GB | $1.753/hr · ≈$1,260/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-m-32c-256gb-3200s-amd | Optimized Cloud (memory) | 32 | 256 GB | $2.144/hr · ≈$1,540/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-s-32c-256gb-5760s-amd | Optimized Cloud (storage) | 32 | 256 GB | $2.74/hr · ≈$1,970/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-g-40c-160gb-768s-amd | Optimized Cloud (general) | 40 | 160 GB | $1.644/hr · ≈$1,180/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-g-64c-192gb-960s-amd | Optimized Cloud (general) | 64 | 192 GB | $2.63/hr · ≈$1,890/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| voc-g-96c-256gb-1280s-amd | Optimized Cloud (general) | 96 | 256 GB | $5.26/hr · ≈$3,790/mo | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |

A few things worth pulling out of the table. The cheapest tracked row — $0.877/hour for 32 dedicated cores and 64 GB of RAM — is already a server-grade machine, which tells you the true entry point for small projects sits in the smaller plans below this snapshot. There's also a tidy tradeoff at the same price point: VX1's 48-core / 384 GB memory row and its 64-core / 256 GB general row both track at $1.92/hour, so the right pick depends entirely on whether RAM or cores is your bottleneck. And at the very top, the tracker lists a 192-core / 768 GB machine around $5.76/hour for workloads that genuinely need that much metal. 👉 [Open Vultr's pricing page for the full current Tokyo catalog](https://www.vultr.com/pricing/?ref=7268283)

One expectation-setting note: a reseller that carries multiple providers in Japan points out that some plans price higher in Japan than in the cheapest regions, so a Tokyo deployment can carry a modest regional premium over, say, a US location. Budget accordingly.

## How Vultr's hourly billing works in practice

Vultr accrues charges by the hour while an instance is running. A $0.877/hour server costs roughly $21 per day; keep it up for a full month and you land near the monthly figures in the table. Destroy the instance and the meter stops — which is the entire appeal of hourly billing for anything short-lived.

That behavior fits a few Tokyo-specific use cases nicely. A staging server you spin up for two days of APAC load testing costs a couple of days' worth of hours, not a month. A game server for a weekend event, a migration rehearsal, or a temporary node for a launch all become round-trip expenses measured in dollars rather than monthly commitments. For the permanent stuff — your production app, your mail relay — just pick the plan size and let it run; the hourly rate converges on the monthly cost.

## The "Vultr cloud hosting Tokyo" pages in your results usually aren't Vultr

This is the part most articles about this search term skip, and it's the part most likely to waste your money. Two of the visible results for this exact query — Kibo Web Host and Lilder — run pages titled "Vultr Cloud Hosting Tokyo," and the two pages are near-identical: same three plans, same prices, same "since 2011" and "50,000+ websites" marketing claims, same layout. Both were updated as recently as August 2026, so they're active, not stale leftovers.

Here's what they actually sell:

| Plan | Monthly | Billed yearly | What you get |
| --- | --- | --- | --- |
| Starter Cloud | ¥628 | ¥287/mo (¥3,454/yr) | 30 GB storage, 5 websites, 30 email accounts, cPanel |
| Business Cloud | ¥785 | ¥405/mo (¥4,867/yr) | 50 GB storage, 10 websites, 150 email accounts |
| Professional Cloud | ¥1,413 | ¥694/mo (¥8,321/yr) | 100 GB storage, 20 websites, 1,000 email accounts |

That's cPanel shared hosting — websites, email accounts, daily backups — with no Vultr account, no cloud console, and no server you can rebuild, snapshot, or destroy. Buying it means renting hosting space; it does not give you a Vultr Tokyo VPS. The headline pricing adds to the confusion: both pages promise hosting "from ¥317–319 a year" at the top while their own plan lists start at ¥3,454–3,504 a year, numbers the pages never reconcile.

To be fair to the category: if all you want is managed hosting for a small blog and you never intend to touch a terminal, that kind of plan is a legitimate product. The problem is only the framing — a reader searching for Vultr's cloud servers lands on these pages and can reasonably assume they're looking at Vultr's own offering. They aren't. There are also more transparent resellers in this space: one, Initech, openly sells Vultr Tokyo and Osaka VPS from $10/month on its own retail floor, plus Windows Server on Vultr from $52/month and fractional NVIDIA A16 GPU time in Tokyo from $90/month, with PayPal and crypto accepted. That's a valid route if you specifically want to pay in crypto or juggle multiple providers on one balance — just remember you're paying a reseller's layer on top of the hardware.

## Tokyo or Osaka: which Vultr location makes sense?

Tokyo, in almost every case. If your audience is in Japan, Korea, or coastal China, Tokyo is the location that keeps round trips short — that's the whole reason to deploy in-country rather than routing Asian users across the Pacific. Osaka exists on Vultr as well, and the two cities on one account make a straightforward same-provider failover pair: run production in Tokyo, keep a warm standby in Osaka, and a single regional outage doesn't take you offline.

If you need a hyperscaler ecosystem instead — managed Kubernetes with specific integrations, for instance — AWS and Google Cloud both operate Tokyo regions, and Alibaba Cloud runs one too. Those are the alternatives to compare against; for plain VPS workloads, Vultr's hourly model is the simpler one to reason about and turn off.

## How to deploy a Vultr server in Tokyo

The whole process takes a few minutes:

1. Create a Vultr account and add a payment method.
2. From the Products page, start a new deployment and pick the server type — Cloud Compute for general use, Optimized Cloud when you need dedicated CPU, extra RAM, or a large NVMe disk.
3. In the location list, choose **Tokyo** (the `nrt` region). Osaka is listed separately, so double-check you've grabbed the right city if you're building a failover pair.
4. Select an OS image — Linux distributions give you full root access — and a plan size.
5. Deploy. Hourly billing starts once the server is up; destroy the instance when you no longer need it and the charges stop.

👉 [Create a Vultr account and deploy your first Tokyo server](https://bit.ly/VulTR)

## Frequently asked questions

**Does Vultr have servers in Japan?**
Yes — Tokyo (NRT) and Osaka, both, from the same account. Tokyo has been part of the network since at least 2015.

**How much does a Vultr Tokyo server cost?**
By the hour, per instance. The large machines tracked above run $0.877–$5.26/hour (roughly $630–$3,790 if
