# Unlimited Bandwidth VPS: What "Unmetered" Really Promises, Which Plan You Actually Need, and What Happens If You Exceed It (Full Plan Table)

Every VPS on AVA Hosting's price list carries the line "Unlimited Bandwidth", and that line buys you exactly one thing: the traffic counter never turns into an invoice. It does not raise the speed of your connection. On this lineup the port speed is what separates one plan from the next, 100 Mbps on the entry box against 1 Gbps on everything above it, and that single number decides how much the word "unlimited" is worth to you.

Below you get the full plan table with prices, the three limits buried inside "unlimited", how to test them before you commit, and which plan to buy for a VPN node, a website, or a file server.

> VPS One at **€5.00/month** (1 vCPU, 2 GB ECC RAM, 25 GB NVMe, 1 Gbps port, unlimited traffic) handles a VPN node, a bot, or a small site. Step up to **VPS Basic at €10.00/month** if you want 4 GB RAM and a second core. 👉 [See the current AVA Hosting VPS plans and prices](https://my.ava.hosting/aff.php?aff=15562)

## The full AVA Hosting VPS lineup

Seven plans are on the store page today, all KVM-virtualised on NVMe storage. Every one of them lists unlimited bandwidth, so the bandwidth column tells you nothing about which to choose. The port speed column does.

| Plan | vCPU / RAM | Storage | Port speed | Price | Order |
| --- | --- | --- | --- | --- | --- |
| VPS Nano | 1 vCPU / 512 MB ECC | 20 GB NVMe | 100 Mbps | €11.00 / year | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS One | 1 vCPU / 2 GB ECC | 25 GB NVMe | 1 Gbps | €5.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS Basic | 2 vCPU / 4 GB ECC | 50 GB NVMe | 1 Gbps | €10.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS Lucky | 2 vCPU / 6 GB ECC | 70 GB NVMe | 1 Gbps | €15.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS Power | 4 vCPU / 8 GB ECC | 90 GB NVMe | 1 Gbps | €20.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS Extra | 6 vCPU / 12 GB ECC | 120 GB NVMe | 1 Gbps | €30.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |
| VPS Ultra | 8 vCPU / 16 GB ECC | 160 GB NVMe | 1 Gbps | €40.00 / month | [Order](https://my.ava.hosting/aff.php?aff=15562) |

Prices are the ones printed on the store page, shown there as starting prices in euros. Two things in that table are easy to miss. VPS Nano is billed **annually**, not monthly, which is why €11.00 looks cheaper than a €5.00 monthly plan until you compare twelve months against twelve months. And the jump from 100 Mbps to 1 Gbps happens between Nano and VPS One, so the cheapest monthly plan already sits on the full-speed port.

Included on every plan, per the same page:

- Intel Xeon E5 hosts with NVMe storage
- Free DDoS protection (no mitigation capacity figure is published)
- Weekly backups
- Full root access and a control panel
- 99.9% uptime SLA and 24/7 support
- Each instance gets its own IPv4 address
- Port 25 is marked closed on the plan card, so plan on sending mail through a relay or an external mail service rather than straight from the VPS

## What "unlimited bandwidth" promises, and the three things it does not

The term has an industry meaning, and it is narrower than the marketing suggests. OVHcloud spells it out in its own FAQ: an unmetered VPS is one where "the volume of data transferred (traffic) is not measured and has no limit", so you are not charged by usage and the monthly bill stays predictable. The next question in that same FAQ is "Is bandwidth truly unlimited?", and the answer is yes for volume, with a catch: the maximum speed of the network connection is set by the plan you choose.

That catch is the whole game. Three boundaries sit inside the word, and only the first one is stated on the pricing table.

### 1. Traffic volume is not metered

On AVA Hosting this is simple: all seven plans list unlimited traffic, and no overage rate appears anywhere on the store page. If your worry is a surprise bill after a front-page spike or a popular upload, unmetered billing removes it. This is the part the phrase genuinely delivers.

### 2. Port speed is the real ceiling

A 1 Gbps port moves about 125 MB per second. Held at full tilt for thirty days that is roughly 324 TB, and a 100 Mbps port tops out around 32 TB. Those are theoretical ceilings, since nobody saturates a link around the clock, but they tell you where the wall is. On AVA Hosting the wall is 1 Gbps on every plan from VPS One upward, and 100 Mbps on VPS Nano. Paying for VPS Ultra does not widen the pipe; it buys CPU, RAM and disk, and the network stays at 1 Gbps.

If a single server needs more than a gigabit of sustained throughput, no plan here gets you there, and a dedicated machine is the honest answer.

### 3. Monthly quotas and throttling exist in some regions

This is the clause that hides in a footnote rather than the price table. OVHcloud publishes an exception for its Mumbai, Singapore and Sydney datacentres: those VPS plans come with a set monthly traffic quota measured in hundreds of gigabytes to a few terabytes depending on the tier, and once the quota is used up the connection is capped at 10 Mbps. A plan that reads "unlimited" on the product page can therefore behave like a metered plan in one region and an unmetered one in another.

AVA Hosting does not publish a regional quota on its store page. Ask support directly whether the datacentre your plan lands in carries a monthly allowance, and get the answer in writing before you migrate anything.

### Port speed and guaranteed speed are two different numbers

A port speed is a cap, not a promise. ZetServers illustrates the distinction on its own product page: its VPS plans sit on 25 Gbps unmetered ports with a guaranteed rate of 1 to 8 Gbps depending on the tier, and it states there are no traffic caps and no overage billing. Two figures, one ceiling and one commitment.

AVA Hosting lists the ceiling only. The plan cards say 100 Mbps or 1 Gbps and stop there, with no guaranteed-throughput figure alongside. For a VPN node or a website that is fine. For anything where sustained throughput is the product, ask what rate they will stand behind at peak hours, not just what the port negotiates at.

## How to check the bandwidth before you commit

Speedtest.net will lie to you on a gigabit port. Its public endpoints frequently have less than 1 Gbps of capacity themselves, so a healthy 1 Gbps link tests at 600 or 700 Mbps and you spend an evening chasing a problem that does not exist. Use iperf3 against a well-connected target with parallel streams instead:


iperf3 -c ping.online.net -p 5201 -P 30


Run it from the VPS to an external host and from an external host back to the VPS. Single-stream tests under-report on long-distance routes; the `-P 30` flag spreads the test across thirty connections, which is closer to how real traffic behaves. Test at the hour your users are awake, not at 4 a.m. on a Sunday.

Three questions to put to support before you pay, on any host, including this one:

1. **Port speed.** What is the physical cap on my plan, and is it shared with other tenants?
2. **Guaranteed rate.** What throughput do you commit to at peak, as opposed to what the port allows?
3. **What happens at the limit.** Throttle to a fixed speed, bill the overage, or suspend? Get the number, not the adjective.

👉 [Check AVA Hosting's port speeds on each plan](https://my.ava.hosting/aff.php?aff=15562)

## Which plan fits which job

The gap between VPS One and VPS Ultra is €35 a month and seven vCPUs, and most buyers searching this term land far closer to the bottom of that range. Working through the common workloads:

**VPN or proxy exit node.** VPS One at €5.00. WireGuard or Xray needs almost no RAM, and the 1 Gbps port is the part that matters. 2 GB is more than enough, and a second core buys you nothing here.

**A Telegram bot, a cron job runner, a monitoring node, a DNS resolver.** VPS Nano at €11.00/year is built for this, with one caveat: 512 MB of RAM and a 100 Mbps port mean no control panel, no Docker stack with five services, and no room for a database that grows. It is billed yearly, so treat it as a fixed annual commitment rather than something you spin up for a fortnight.

**One or two small sites with a database.** VPS Basic at €10.00. A LEMP stack with MySQL fits in 2 GB, and 4 GB gives you headroom for traffic peaks, backups and the occasional rebuild without the OOM killer visiting.

**A handful of containers, staging environments, a CI runner.** VPS Power at €20.00, where 4 vCPU and 8 GB start to matter. Below this you will be tuning swap instead of shipping.

**Static file distribution or video.** Every plan above Nano shares the same 1 Gbps port, so buying more CPU does not serve more concurrent downloads. Take VPS Basic for the disk and RAM, put a CDN in front of the large files, and the port stops being the constraint your users feel.

**VPS Extra and VPS Ultra.** 6 to 8 vCPU and 12 to 16 GB of RAM at €30 to €40. These are for database servers, build farms, game servers with many slots, or several production apps on one box. A single WordPress site on VPS Ultra is €40 a month spent on hardware that will sit idle.

## Who should not buy an unlimited bandwidth VPS here

Three cases where the answer is a different product, not a bigger plan:

- **You need to run a mail server.** Port 25 is closed on the plan card. Inbound mail through a relay works; direct outbound SMTP does not, and no amount of RAM fixes it.
- **You need more than 1 Gbps on one machine.** The top plan stops at 1 Gbps. A dedicated server is the route, and AVA Hosting sells those separately.
- **You need a contractual throughput guarantee.** The uptime SLA is 99.9%, but no guaranteed bandwidth figure is published. If your contract with your own customers depends on a committed rate, that has to be negotiated first.

If none of those apply, the "unlimited" part is genuinely useful and the rest is a normal VPS purchase.

## Before you order

Two things to settle before you enter card details. First, which datacentre your plan is provisioned in and whether that location carries a monthly traffic allowance, since regional quota rules are the most common way "unlimited" turns out to be limited. Second, the billing cycle and the renewal price: VPS Nano is annual, the rest are monthly, and the store page shows starting prices rather than a renewal figure, so confirm what the second year costs.

My default recommendation for this search: **VPS One at €5.00/month** for anything network-bound but small, and **VPS Basic at €10.00/month** the moment a database or a control panel enters the picture. Everything above Basic is a decision about CPU and RAM, not about bandwidth, because the port is already at 1 Gbps.

👉 [Start with VPS One on the AVA Hosting order page](https://my.ava.hosting/aff.php?aff=15562)
