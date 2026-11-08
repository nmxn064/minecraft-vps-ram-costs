# Minecraft VPS: How Much RAM 5–20 Players Need, What the Second Year Costs, and Where SpinServers' $12–$89 KVM Plans Fit (Full Plan Table)

A Java server for 5–20 friends runs on 2–4 GB of RAM, and single-core speed decides whether it holds 20 ticks per second. SpinServers sells KVM VPS from **$12/month** for 2 vCPU and 2 GB up to 32 vCPU and 32 GB for **$89/month**, billed monthly with no promotional rate that expires after the first term. What follows is the full plan list, the RAM-to-player math, what year one and year two actually cost against the providers people usually shortlist, and the parts of running a Minecraft server that SpinServers leaves to you.

## Quick pick

> For a Paper server with 10–20 players and a few plugins, the **8 GB / 6 vCPU plan at $39/month** (120 GB RAID-10 SSD, 8 TB transfer) is the smallest tier here that leaves headroom for a modpack. A vanilla world for 3–5 friends is fine on the **$12 two-gig plan**. Neither includes a game panel; you get root SSH and install Java yourself.
>
> 👉 [See SpinServers' current KVM VPS plans and prices](https://bit.ly/Spinservers)

## Every SpinServers VPS plan, with prices

| Plan | RAM · vCPU · SSD | Monthly transfer | Price (USD) | Order |
| --- | --- | --- | --- | --- |
| KVM 2 vCPU / 2 GB | 2 GB DDR4 · 2 vCPU · 40 GB RAID-10 | 4 TB @ 1 Gbps | **$12.00/mo** | [View plan](https://bit.ly/Spinservers) |
| KVM 4 vCPU / 4 GB | 4 GB DDR4 · 4 vCPU · 80 GB RAID-10 | 8 TB @ 1 Gbps | — (see plan page) | [View plan](https://bit.ly/Spinservers) |
| KVM 6 vCPU / 8 GB | 8 GB DDR4 · 6 vCPU · 120 GB RAID-10 | 8 TB @ 1 Gbps | **$39.00/mo** | [View plan](https://bit.ly/Spinservers) |
| KVM 8 vCPU / 8 GB | 8 GB DDR4 · 8 vCPU · 160 GB RAID-10 | 10 TB @ 1 Gbps | **$45.00/mo** | [View plan](https://bit.ly/Spinservers) |
| KVM 12 vCPU / 12 GB | 12 GB DDR4 · 12 vCPU · 160 GB RAID-10 | 10 TB @ 1 Gbps | — (see plan page) | [View plan](https://bit.ly/Spinservers) |
| KVM 16 vCPU / 16 GB | 16 GB DDR4 · 16 vCPU · 320 GB RAID-10 | 15 TB @ 1 Gbps | **$74.00/mo** | [View plan](https://bit.ly/Spinservers) |
| Hybrid KVM 32 vCPU / 32 GB | 32 GB RAM · 32 vCPU · 500 GB SSD | 20 TB @ 1 Gbps | **$89.00/mo** | [View plan](https://bit.ly/Spinservers) |

Two of the seven tiers (4 GB and 12 GB) appear on the plans page without a "starting from" figure in the summary, so their current rate has to be read on the plan page itself. Everything else above is the listed monthly price.

What every plan includes:

- KVM virtualisation with full root access
- 1 IPv4 and 1 IPv6 address (useful for an SRV record, so players can join on a domain without typing a port)
- 1 Gbps network port
- RAID-10 SSD storage
- Monthly billing; no hourly option

## What SpinServers actually is

SpinServers has operated since 2018 under Majestic Hosting Solutions LLC. Dedicated servers and hybrid dedicated boxes are the main business, and the KVM VPS line is the smaller product alongside it. The company owns its hardware and IP space and runs its own facilities in Dallas and San Jose, which is why the VPS plans can carry 4–20 TB of monthly transfer on a 1 Gbps port at these prices.

For Minecraft specifically, there is no preinstalled game image, no Pterodactyl panel, and no per-slot pricing. You pick an OS, get root, install a JDK, drop in a server jar. That suits anyone who has run a Linux box before and frustrates anyone who wants a web panel for restarting the server and editing `server.properties`.

There is also **no published refund or trial policy on the VPS page**, which is worth resolving before money changes hands. Monthly billing is the smallest commitment on offer, so the cheapest test of whether this host suits your world is one month on the $12 tier rather than a prepaid year.

## How much RAM does a Minecraft VPS need?

The community numbers line up closely across sources, and they are a reasonable planning baseline:

| Players | RAM | What's running |
| --- | --- | --- |
| 1–5 | 1–2 GB | Vanilla survival |
| 5–15 | 2–4 GB | Light plugins (EssentialsX, LuckPerms) |
| 15–30 | 4–6 GB | Forge/NeoForge modpacks, moderate plugin sets |
| 30+ | 6–8 GB+ | Heavy modpacks, large public servers |

Two anchors support this: RackNerd's own guidance of at least 1 GB and 2 cores for roughly four players, and Cloudzy's FAQ, which puts vanilla survival for a few friends at 2 GB, FTB/ATM/Create-style modpacks at 4–8 GB, and a busy Spigot or Paper network at 8–16 GB.

One number gets misread constantly. Cloudzy's marketplace image for Minecraft lists a **4 GB minimum RAM**, and that figure is the recommended floor for a 10-player community server running that specific image with Java, Paper's start script and Docker Compose preloaded, not a hard requirement of the game. Vanilla Minecraft will boot and hold a handful of players on 2 GB. Plan 2 GB for vanilla, 4 GB for a light modpack or plugin set, 8 GB once you are past 20 players or running something like All The Mods.

On SpinServers' ladder, that maps cleanly: $12 tier for vanilla, the 8 GB tiers at $39–$45 for plugin servers and light modpacks, and the 16 GB or 32 GB plans for a heavy pack or a multi-server network.

## vCPU count is the wrong number to shop by

Minecraft is single-thread heavy. One core does the tick loop, and if that core can't finish its work in 50 ms, the server stutters no matter how many other cores sit idle. Since 1.18 the per-tick workload has grown enough that clock speed matters more than it did on 1.12-era servers. A 4-core box at 4.5 GHz will outrun an 8-core box at 2.4 GHz on the same world.

SpinServers' VPS page lists Intel Xeon processors and vCPU counts but does not publish clock speeds per plan, and the vCPU counts climb fast: 12, 16 and 32 cores. Before paying for cores Minecraft cannot use, ask support what the base and boost clocks are on the tier you're considering, or deploy the cheapest plan for a month and run `lscpu` plus a short world-load test. For a 10-player Paper server, 4 fast cores beat 12 slow ones.

That is the honest caveat on the 32 vCPU / 32 GB hybrid plan at $89. The RAM and the 500 GB SSD are the reason to buy it (a big modpack plus Dynmap renders plus backups), not the core count.

👉 [Compare the 8 GB and 16 GB tiers on SpinServers' plan page](https://bit.ly/Spinservers)

## What year one and year two actually cost

This is where most comparisons stop short: they quote the advertised monthly rate and never check what happens at renewal.

| Configuration | Monthly | Year 1 | Year 2, same rate |
| --- | --- | --- | --- |
| SpinServers 2 GB / 2 vCPU | $12.00 | $144.00 | $144.00 |
| SpinServers 8 GB / 6 vCPU | $39.00 | $468.00 | $468.00 |
| SpinServers 32 GB / 32 vCPU | $89.00 | $1,068.00 | $1,068.00 |
| Cloudzy 2 GB / 1 vCPU (50% off) | $7.48 | $89.76 | $179.40 if the list price of $14.95 applies |
| Cloudzy 8 GB / 4 vCPU (50% off) | $26.48 | $317.76 | $635.40 if the list price of $52.95 applies |

Cloudzy's page shows struck-through list prices next to a "currently 50% off" rate and does not state what renewal costs, so the year-two figure is a range, not a certainty. SpinServers quotes a single monthly price with no discount attached, which makes its second year identical to its first.

Cost per gigabyte of RAM, using the rates above:

- SpinServers 2 GB: $6.00/GB · 8 GB: $4.88/GB · 16 GB: $4.63/GB · 32 GB: $2.78/GB
- Cloudzy at promo rates: 2 GB $3.74/GB · 4 GB $3.62/GB · 8 GB $3.31/GB · 12 GB $2.92/GB (list rates are roughly double)

Read together, the entry tiers favour Cloudzy on price and the 32 GB tier is where SpinServers becomes hard to beat at $89/month for 32 GB and 500 GB of storage. A 10–20 player Paper server at 8 GB costs $468/year at SpinServers against $317.76–$635.40 at Cloudzy depending on whether the discount holds, which is a real spread and worth a support ticket before you commit either way.

## How the alternatives compare

**Cloudzy** lists 13 regions (six in North America, four in Europe, plus Dubai, Singapore and Sydney), AMD EPYC cores, DDR5, NVMe, 40 Gbps uplinks, 60-second provisioning, live resizing without moving the world, and a 14-day money-back guarantee. Listed plans are 2 GB at $7.48, 4 GB at $14.48, 8 GB at $26.48 and 12 GB at $34.98 per month, all at the current 50% discount. It is the better fit if you want many region choices and a refund window; the trade-off is that the pricing is promotional.

**RackNerd** sells prepaid annual KVM plans, with promotional pricing that lands somewhere in the $10–$65 per year range for 1–8 GB of RAM. That is a different product category from monthly billing, and its published tables are revised often enough that quoted figures on roundup pages disagree with each other, so treat any specific number as needing a check at checkout. Its draw is the annual price; its risk is that you're paying a year up front.

**MonoVM** sells 1–8 GB app VPS plans on AMD EPYC 7532 hardware and publishes Geekbench 6 multi-core scores from its Amsterdam location: 2,724 for 2 GB, 4,952 for 4 GB, 5,973 for 8 GB, 8,288 for 16 GB. Those are multi-core figures, which is exactly the metric that tells you least about Minecraft performance, so use them to judge throughput headroom rather than tick stability. Per-plan pricing wasn't verifiable, so treat its advertised "from" figure with caution.

**Rainyun** is a Chinese provider worth knowing about if most of your players are in mainland China. It bills in RMB, runs mainland datacenters plus Tokyo, Los Angeles and Hong Kong, and prices 2-core/4 GB game cloud from ¥12 to ¥45 per month depending on the CPU (up to an i9-14900K at 6.3 GHz). Latency to Chinese players is the reason to consider it; the interface and documentation are in Chinese.

## Getting the server running on a bare VPS

SpinServers gives you an OS and root, so the setup is the standard one and takes about 20 minutes on Ubuntu:

1. Deploy Ubuntu 22.04 or 24.04, connect over SSH as root.
2. Install Java 21: `sudo apt install openjdk-21-jdk-headless -y`
3. Create a directory for the server, download `paper-1.21.4-latest.jar` (or your chosen jar) into it.
4. Start it once to generate `eula.txt`, accept the EULA, then launch with a memory cap that leaves room for the OS: `java -Xmx6G -Xms6G -jar paper.jar nogui` on an 8 GB plan.
5. Run it inside `screen -S mc` so it survives a disconnect: `Ctrl+A` then `D` detaches, `screen -r` reattaches.
6. Open the port: **25565/TCP** for Java Edition, **19132/UDP** if you run a Bedrock dedicated server. GeyserMC bridges Bedrock clients into a Java server if you need both.

Give the server its own user rather than running as root, and set a nightly backup to somewhere off the box. A 40 GB disk on the $12 plan holds a lot of world, but not a copy of itself.

## Questions people ask before buying

**Is 2 GB enough for a Minecraft server?**
For vanilla survival with 1–5 players, yes. Add plugins or a modpack and it becomes tight fast; chunk generation and world saves are where a 2 GB box starts to show its limits.

**Do modpacks really need 8 GB?**
A pack like All The Mods or a Pixelmon server will run on 4 GB for a small group, but 6–8 GB is the comfortable range once several players load chunks in different dimensions. Budget for RAM before cores.

**Will the SpinServers price go up on renewal?**
The listed rates have no discount attached and no expiry date, so there is no promotional price to lapse. Confirm the renewal rate shown in the cart during checkout, since that is the number that governs year two.

**Can I get a refund?**
SpinServers' VPS page doesn't publish a trial or money-back policy. Ask support in writing before ordering, and if you can't get a clear answer, start with one month rather than a longer prepay.

**Which location should I pick?**
SpinServers' own facilities are in Dallas and San Jose. Confirm the location attached to the specific plan at checkout, then have a player in your main timezone ping it before you migrate an existing world.

**Do I need Linux experience?**
To install Java and run a jar from the command line, yes, at a basic level. If you'd rather click a panel, a managed Minecraft host is the better spend even at a higher monthly price.

## Which plan to buy, and two things to check first

- **3–5 friends, vanilla survival:** the $12 2 GB plan. Nothing above it buys you a smoother vanilla tick loop.
- **10–20 players, Paper with plugins:** the $39 8 GB / 6 vCPU plan. The extra $6 for the 8 vCPU version buys cores Minecraft won't use, so spend it on RAM instead if you're near the limit.
- **ATM/FTB-scale modpack, 20+ players, Dynmap:** 16 GB at $74 or the 32 GB hybrid at $89. Storage and RAM are the reasons, not the core count.

Before you order, confirm two things: the renewal rate and term shown in the cart, and the clock speed of the tier you're buying, since that is the number that decides whether your world ticks at 20 TPS.

👉 [Open SpinServers' VPS page and check the plan that matches your player count](https://bit.ly/Spinservers)
