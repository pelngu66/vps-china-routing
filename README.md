# VPS for China: Do You Need Mainland Hosting, a CN2 GIA Route, or Just a $2.99/Month Box? (Full Evoxt Plan Table and Route Cheat Sheet)

Two different products get sold under the same phrase. A server inside mainland China gives a Beijing visitor single-digit milliseconds, but your domain needs an ICP license before it resolves properly. An overseas server with a premium China route skips the paperwork and lands at roughly 30–60 ms from Shanghai, at a much higher price per gigabyte of RAM.

Price anchors, all from current provider pages: overseas optimized plans start at $52/year (ZgoCloud, Los Angeles, 1 GB) or $49.99/quarter (BandwagonHost, Los Angeles DC9, 1 GB). Mainland hosting starts at $24.99/month (NeteronHost, Beijing). Evoxt, the subject of the plan table below, starts at $2.99/month, and its Kuala Lumpur optimized-network plans reportedly start at the same figure. Those three numbers describe three different machines, and this article is mostly about telling them apart.

> **Quick pick for most readers:** Evoxt VM-1.5 at $6.95/month — 2 cores, 2 GB RAM, 20 GB storage, 500 GB monthly transfer — ordered in Kuala Lumpur on the optimized network rather than Frankfurt. It is the cheapest point in the lineup where a small site or a proxy node has enough RAM to breathe. If you only need a tunnel endpoint or a DNS box, VM-0.75 at $4.99/month is enough and you should not pay more.
>
> 👉 [See Evoxt's current plan list and monthly prices](https://bit.ly/EvoXt)

## The full Evoxt lineup, at listed monthly prices

Every plan below appears on Evoxt's pricing page. The listed CPU frequency is "up to 6.0 GHz" across the board, and weekly offsite backup is included at no extra cost on all of them.

| Plan | Cores / RAM | Storage | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 core / 512 MB | 5 GB | 250 GB | $2.99/mo | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 core / 1 GB | 10 GB | 250 GB | $4.99/mo | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 core / 2 GB | 20 GB | 500 GB | $5.99/mo | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 cores / 2 GB | 20 GB | 500 GB | $6.95/mo | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 cores / 4 GB | 30 GB | 1,000 GB | $11.99/mo | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 cores / 4 GB | 30 GB | 1,000 GB | $14.99/mo | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 cores / 8 GB | 60 GB | 2,000 GB | $23.99/mo | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 cores / 8 GB | 60 GB | 2,000 GB | $29.99/mo | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 cores / 16 GB | 80 GB | 3,000 GB | $47.99/mo | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 cores / 16 GB | 80 GB | 3,000 GB | $60.95/mo | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 cores / 32 GB | 100 GB | 5,000 GB | $95.99/mo | [Deploy VM-16](https://bit.ly/EvoXt) |

Three things in that table matter more than the core counts. Transfer allowances are modest: 250 GB on the two cheapest plans, and a site with images or a busy API will eat through that. The plan ladder is priced monthly with no advertised annual discount; you can prepay up to three years and top up account credits, but the page shows one price per plan either way. And the two 16-core plans cost roughly 20× the entry plan while offering 64× the RAM, which tells you the markup sits in memory, not in CPU time.

Payments accepted are credit and debit cards, PayPal, Bitcoin and USDt on Tron. The control panel covers monitoring, firewall rules set outside the guest OS, floating IP reassignment, VM cloning, browser VNC and per-resource upgrades, so you can add RAM to VM-1.5 without migrating to VM-2. Windows RDP images and the usual Linux templates are both offered.

## What "China optimized" actually means, in AS numbers

Ignore the label. Ask which tier of China Telecom's international network the provider bought, because that single fact predicts peak-hour behavior better than any spec sheet.

China Telecom's options, cheapest to most expensive:

- **AS4134 (ChinaNet/163)** is the default for most clouds outside China. Large capacity, lowest cost, and it degrades badly in the evening when residential traffic peaks.
- **CN2 GT (AS4809 Global Transit)** was built to relieve that congestion. Since around 2019 it has performed close to AS4134 during peak hours while still costing noticeably more, which makes it the worst value in the set.
- **CN2 GIA (AS4809 Global Internet Access)** is the premium tier. Fewer routes, higher cost, and the one tier that holds up for video calls, VOIP, gaming and serving content to Chinese users.
- **CTGNet (AS23764)** is the newer option and performs in roughly the same class as CN2 GIA. Some provider pages describe CTGNet as "formerly CN2 GIA," which is imprecise: AS23764 and AS4809 are different identifiers, so treat the two as siblings rather than the same product.

China Unicom's premium path is **AS9929**, sometimes written alongside AS10099. China Mobile's is **CMIN2 (AS58807)**. A "three-network optimized" plan means Telecom, Unicom and Mobile each enter and exit through their own premium path, instead of one carrier being optimized and the other two routed wherever capacity was cheap.

That is the whole test. A provider that says "China optimized" but cannot name AS4809, AS9929 or AS58807 is usually reselling AS4134 with better copy.

## Where Evoxt actually fits, and where it doesn't

Evoxt is not a China-route specialist, and its pricing page doesn't present itself as one. Its pitch is clock speed: single-core performance at prices where most competitors give you a shared vCore. For a China-facing workload, that matters less than the route, so the honest framing is that Evoxt gives you a very cheap machine to run on, and the route depends entirely on which location you pick.

Third-party testing published on VPS review sites reports that Evoxt's Kuala Lumpur optimized-network plans return China Telecom traffic over CN2 GIA (AS4809) and China Unicom traffic over AS9929, with China Mobile connecting directly via CMI. That testing also lists a 1 Gbps port and AMD EPYC Genoa hardware, with entry pricing from $2.99/month. Two caveats apply: the routing was measured by a reviewer, not published as a routing table by Evoxt, and "optimized network" needs to be the option you select at checkout. Confirm both before you pay.

The contrast inside Evoxt's own catalog is instructive. A separate review of the Frankfurt location on the $2.99 VM-0.5 recorded the provider's network as AS149440, with China Unicom traffic leaving via AS4837, the budget transit path, and measured latency of 243 ms to Tokyo and 160 ms to Singapore. Frankfurt is fine for European visitors and wrong for this article's purpose.

👉 [Open the Evoxt order page and select Kuala Lumpur](https://bit.ly/EvoXt)

## Mainland, Hong Kong/Taiwan, or overseas optimized

| Where the server sits | ICP license | Typical China latency | Fits whom |
| --- | --- | --- | --- |
| Mainland China (Beijing, Shanghai) | Required; the application has to come from a company or an authorized local representative | Under 10 ms for Beijing users, under 40 ms for Shanghai, Guangzhou, Shenzhen, Chengdu and Wuhan, per NeteronHost's own figures | Businesses with a Chinese legal entity, or anyone whose users are all mainland and whose domain can be filed |
| Hong Kong or Taiwan | Not required | Cross-border, roughly 40–80 ms slower than a Beijing box in the same provider's comparison | Chinese-language audiences you also want reachable from outside, anyone who cannot file an ICP |
| Overseas optimized (Los Angeles, Tokyo, Singapore, Kuala Lumpur) | Not required | Depends on the route tier, not distance | Everyone else, including proxies, APIs, game nodes and sites that just need to be usable from China |

LightNode's own FAQ states the rule plainly: hosting a website in mainland China requires an ICP license, otherwise the domain may be filtered, while its Hong Kong and Taiwan locations do not. That is not a marketing position; it is how the filing system works out there. No hosting provider can file it for you.

The latency gap is the price of skipping that paperwork. NeteronHost quotes under 10 ms for users in Beijing and describes Hong Kong or Singapore as adding 40–80 ms of cross-border latency on top. For a text-heavy site, that difference is invisible. For a game server or a trading interface, it's the whole experience.

## How the alternatives compare on paper

Five providers show up repeatedly in this search. Their entry numbers are not directly comparable because the billing periods differ, which is the point of the column.

| Provider | Location | Route | Entry price and period | Refund | Main limitation |
| --- | --- | --- | --- | --- | --- |
| BandwagonHost | Los Angeles DC9 | CN2 GIA + CMIN2 + Unicom AS10099 | $49.99/quarter (2 cores, 1 GB, 20 GB, 1 TB) | 30 days | CN2 GIA capacity is limited and the network doesn't absorb DDoS; attacked IPs get nullrouted. Hong Kong/Japan "Ultra" plans are a separate, far pricier line from $89.99/month |
| ZgoCloud | Los Angeles, Hong Kong | LA: GIA + 9929 + CMIN2 at 200 Mbps. HK: BGP only | $52/year (1 core, 1 GB, 10 GB, 500 GB) | Special offers non-refundable | Founded around 2021, small community footprint; the Hong Kong line carries no premium route branding |
| LightNode | Hong Kong, Taiwan | HK: CN2/BGP. Taiwan: BGP | $7.71/month (1 vCPU, 2 GB, 50 GB, 1 TB) | Not stated on the plan page | Page lists two conflicting uptime figures (99.95% and 99.5%), so treat the SLA as unclear |
| sa.net | Tokyo, Singapore | CTGNet + AS9929 + CMIN2, 1 Gbps | $49/month (2 vCPU, 4 GB, 40 GB, 1 TB) | 14 days, under 10 GB used, IP not blacklisted | No Windows; upgrades require a ticket and downgrades are impossible |
| NeteronHost | Beijing | Domestic, not a cross-border route | $24.99/month | 30 days | ICP required for any website; month-to-month only, no annual option |

Evoxt's position in that table is the cheap end. VM-1.5 costs $83.40/year for 2 cores and 2 GB, which is less than two quarters of the BandwagonHost entry plan, and it includes weekly offsite backups. It does not include a guaranteed premium route on every location, so if three-network optimization is your hard requirement, BandwagonHost, ZgoCloud and sa.net are the ones that name all three AS numbers in their product copy.

## The real annual cost, converted

Mixing $49.99, $52 and $2.99 in one sentence is how people end up disappointed. Converted to a year:

- BandwagonHost EC-1GB: $49.99/quarter = **$199.96/year**, about $16.66/month. The EC-2GB at $89.99/quarter is $359.96/year, and from EC-4GB upward the same line switches to monthly billing at $56.99/month.
- ZgoCloud LA AMD Optimised Starter: **$52/year**, about $4.33/month, for 1 GB and 500 GB of transfer at 200 Mbps.
- NeteronHost: $24.99/month = **$299.88/year**, before any ICP work.
- sa.net Premium: $49/month = **$588/year**.
- Evoxt VM-0.5: $2.99/month = **$35.88/year**. VM-1.5: $6.95/month = **$83.40/year**. VM-2: $11.99/month = **$143.88/year**.

Read that list again with the specs next to it. Evoxt's $35.88/year buys 512 MB of RAM and 250 GB of transfer; ZgoCloud's $52/year buys 1 GB and 500 GB on a named three-carrier route. The $16 difference is not the story. The story is that a 250 GB monthly cap disappears fast if you're serving pages with images, and 5 GB of disk leaves no room for logs.

Renewal pricing deserves its own check at every provider. Promotional first-term pricing is common in this market, and the listed price on a plan page is not always the price on the second invoice. Evoxt's pricing page shows a single monthly rate per plan with no separate renewal figure, which is the cleaner arrangement, but confirm it in the cart before you commit to a multi-year prepay.

## Picking by what you're running

**A personal proxy or tunnel endpoint.** Buy the smallest plan that has a route you trust. Evoxt VM-0.75 at $4.99/month (1 GB, 10 GB disk) covers it, and the 250 GB transfer cap is usually the binding limit, not the CPU. Do not buy VM-8 for this.

**A small site or blog aimed at Chinese readers.** You want RAM for the database and PHP workers, plus transfer headroom. Evoxt VM-1.5 (2 GB, 500 GB) or VM-2 (4 GB, 1 TB) is the range; anything above VM-3 is for concurrent users you don't have yet. If page-load consistency during the 8–11 pm peak matters more than the monthly bill, paying $199.96/year for a named CN2 GIA line is a defensible upgrade over $83.40/year for a machine on a route you had to verify yourself.

**APIs and SaaS with Chinese users.** Latency variance hurts more than average latency, because a p99 spike shows up as a timeout in someone's integration. This is where a three-network plan (Telecom, Unicom, Mobile each on their own premium path) earns its premium over a single-carrier optimization.

**Game servers, trading interfaces, anything real-time.** Mainland hosting if you can file. Otherwise CN2 GIA or CTGNet, and accept the cost.

**A business that must be compliant inside China.** None of the overseas options apply. You need a mainland data center and an ICP filing held by a Chinese entity; NeteronHost's model, where the provider supplies the local IP and infrastructure but the customer handles the filing through a company or local representative, is the shape of that arrangement.

## Six ways this purchase goes wrong

1. **Comparing a quarter to a year to a month.** The BandwagonHost entry plan is a quarterly charge for 1 GB; the ZgoCloud entry plan is an annual charge for 1 GB. Same-looking numbers, different commitments.
2. **Buying port speed instead of route quality.** A 1 Gbps port on AS4134 loses to a 200 Mbps port on CN2 GIA at 9 pm every day of the week.
3. **Assuming CN2 GIA survives a DDoS.** It doesn't. BandwagonHost says outright that its CN2 GIA network doesn't absorb attacks and will nullroute a targeted IP. If you need always-on mitigation, a cheaper transit line with filtering is the better engineering choice.
4. **Treating Hong Kong or Taiwan as mainland.** No ICP needed, but traffic still crosses a border and picks up 40–80 ms in the process.
5. **Assuming a refund exists.** Terms range from 30 days (BandwagonHost, NeteronHost) to 14 days with a 10 GB usage cap and an IP-blacklist condition (sa.net) to nothing at all on promotional plans (ZgoCloud special offers). Evoxt's pricing page doesn't publish a refund window, so if that matters, ask support in a ticket before prepaying three years.
6. **Expecting the host to handle ICP.** They can't. It's your filing, tied to your entity.

## FAQ

**Do I need an ICP license for a Hong Kong VPS?** No. Hong Kong and Taiwan locations don't require one, which is why they're the standard workaround for sites that need to be fast in China without a mainland entity. Mainland hosting is the case that requires the filing.

**Is CN2 GIA always faster?** Not in raw milliseconds. From Los Angeles you'll still see 150 ms or more to Shanghai. What CN2 GIA buys is consistency: fewer peak-hour spikes, lower packet loss, and routing that doesn't get reworked when transit congestion hits. If your users complain about a specific 9 pm slowdown rather than average speed, that's the tier that addresses it.

**Why is a $52/year plan cheaper than a $49.99/quarter plan?** Because one is an annual commitment on 200 Mbps of premium-routed bandwidth and the other is a quarterly charge on a 2.5 Gbps port with a different route mix and a much larger provider behind it. Divide both by twelve before comparing: $4.33/month against $16.66/month.

**Can I host a Chinese-facing site on a normal overseas VPS?** Yes. No filing is required for a server outside the mainland, and users in China can reach it. What you give up is peak-hour stability, and the amount you give up depends on which transit tier the host bought. Ask for the AS number before you order.

**Does Evoxt provide CN2 GIA?** Its Kuala Lumpur optimized-network plans have been tested by third parties as returning Telecom traffic over CN2 GIA (AS4809) and Unicom over AS9929. That's a location-level option rather than a lineup-wide guarantee, so verify the network selection and the current route at the point of order.

## The decision, in one pass

If you cannot file an ICP and your users are in China, buy an overseas server on a named premium route, and treat the route as the specification. If you can file one, a Beijing or Shanghai box at $24.99/month upward beats every overseas option on latency and you should stop reading route tables.

If you need a cheap machine with high single-core speed and are willing to select the right location yourself, Evoxt's VM-1.5 at $6.95/month in Kuala Lumpur is the plan most people should start with, and VM-0.75 at $4.99 covers proxy and DNS duty. Two things to confirm in the cart before paying: that "optimized network" is selected for the Kuala Lumpur location, and what the refund terms are, since the pricing page doesn't state them.

👉 [Check Evoxt's plans and start with VM-1.5 in Kuala Lumpur](https://bit.ly/EvoXt)
