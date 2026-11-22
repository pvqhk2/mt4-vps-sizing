# VPS for MT4: How Much RAM One Terminal Needs, Which City to Pick, and What It Costs (€5 to $50 a Month)

A working MT4 VPS costs between €5 and $50 a month. The spread follows location and Windows licensing more than quality: at the low end you rent a small Windows server in a European datacentre, at the high end you pay for a box in the same building as your broker's matching engine, or for a broker-hosted VPS that is "free" only while you keep $2,000 on deposit.

Two numbers settle most of the decision. Budget 0.5–1 GB of RAM per MT4 terminal, and pick the datacentre city from your broker's server list rather than from where you live.

What follows covers both, along with the parts of MT4 hosting that spec sheets leave out: what happens when you close the Remote Desktop window, why a backtest starves the EAs on the same machine, and when the free broker option genuinely beats paying.

## What a VPS does that your laptop can't

MT4 trades only while the terminal is open and connected. Run it on your own machine and every Windows update reboot, sleep timer, Wi-Fi dropout and power cut becomes a window where a stop-loss sits unmanaged and an EA misses ticks. A VPS moves the terminal into a datacentre with redundant power and a fixed network path, and you connect over Remote Desktop from any PC, Mac or phone.

Latency matters less than the marketing implies. Order routing from home crosses your ISP and the public internet before it reaches the broker; from a server in the broker's city it crosses a metro network. That narrows requotes and the slippage on stops and pending orders, which is worth real money to a scalper and close to nothing to a swing system that trades twice a week.

## Quick pick

> - **One account, one or two terminals, a couple of EAs:** the smallest Windows-capable AvaHost plan. The range starts at **€5.00/mo**, billed monthly in EUR.
> - **Three to eight terminals, a trade copier, or indicator-heavy templates:** the 8 GB tier (4 vCPU, 90 GB NVMe).
> - **Ten or more terminals, signal distribution, client accounts:** the 16 GB tier at **€40.00/mo**, top of the range.
>
> 👉 [See AvaHost's VPS plans and current EUR prices](https://my.ava.hosting/aff.php?aff=15562)

## AvaHost's VPS range, tier by tier

AvaHost has run hosting since 2002, and its VPS line uses KVM virtualisation with a dedicated IPv4 per instance, isolated vCPU and RAM allocations, and NVMe storage on every tier. DDoS protection is included, support runs 24/7 by ticket and chat, and payment covers cards, PayPal, bank transfer, WebMoney and a long list of cryptocurrencies. Prices are quoted in EUR on a monthly cycle.

The range is sold in six configurations between €5.00 and €40.00 a month. These are the four with published specifications:

| Plan | vCPU / RAM / NVMe | Windows | Price | Order |
| --- | --- | --- | --- | --- |
| Linux VPS One | 1 / 2 GB / 25 GB | Linux only | €5.00/mo | [Choose the 2 GB plan](https://my.ava.hosting/aff.php?aff=15562) |
| Linux VPS Power | 4 / 8 GB / 90 GB | Available | in plan selector | [Choose the 8 GB plan](https://my.ava.hosting/aff.php?aff=15562) |
| Linux VPS Extra | 6 / 12 GB / 120 GB | Available | in plan selector | [Choose the 12 GB plan](https://my.ava.hosting/aff.php?aff=15562) |
| Linux VPS Ultra | 8 / 16 GB / 160 GB | Available | €40.00/mo | [Choose the 16 GB plan](https://my.ava.hosting/aff.php?aff=15562) |

Two things to check before paying. The tiers carry Linux names, but MT4 needs Windows Server, which is an option on the larger configurations. One third-party review of the range reports Windows only from 4 GB of RAM upward, so confirm the operating system at checkout if you are ordering the €5.00 size. And the whole range sits in a single datacentre in Moldova, which is fine for uptime and EA persistence and not fine if your strategy depends on single-digit milliseconds.

## How much RAM does one MT4 terminal actually use?

Less than most buyers assume. A terminal with four or five charts and an EA or two settles in the few-hundred-megabyte range. You approach 1 GB with indicator-heavy templates, long chart histories or tick-level EAs. Hosts that publish sizing guidance quote 0.5–1 GB per terminal, and 1 GB is the number to plan with. MT4 is a 32-bit application, so a single terminal will not touch several gigabytes however you configure it.

CPU counts for less than memory in live trading. MT4 executes each chart's code on a single thread and spends most of its life waiting for the next tick, so a faster core helps less than having enough memory to keep every terminal resident.

| Terminals you'll run | RAM to plan for | AvaHost tier |
| --- | --- | --- |
| 1–2 | 2 GB | One, if Windows is available on it |
| 3–8 | 8 GB | Power |
| 10 or more | 16 GB | Ultra |

One terminal logs into one account. Three broker accounts means three terminals, each installed in its own folder, each an independent process that won't take the others down if it crashes. Launch a terminal with the `/portable` switch if you want its data to stay beside the executable instead of in the user profile.

👉 [Check the 8 GB plan for a multi-terminal setup](https://my.ava.hosting/aff.php?aff=15562)

## The city matters more than the plan

Retail MT4 servers cluster in a handful of Equinix campuses: New York (NY4), London (LD4/LD5), Frankfurt and Singapore. A host that maps brokers to datacentres from their published server information lists IC Markets, FP Markets, Axi and Global Prime in NY4; FxPro, Admirals, Darwinex and BlackBull in LD4 or LD5; FXTM in Frankfurt; Exness in Amsterdam, where the choice between Frankfurt and London comes down to a ping test.

The payoff is measurable when the host sits in the right building. One provider quotes under 1 ms to brokers in New York, Frankfurt and Singapore and under 10 ms to London ones. Those are its own figures for its own locations, but the direction holds: same-campus beats same-continent by an order of magnitude.

AvaHost doesn't play that game. Its VPS range runs out of Moldova, several countries from every hub above. That is a reasonable trade for a trader who wants a terminal that never sleeps, an EA that keeps managing positions, DDoS protection and crypto payment at €5–€40 a month. It is the wrong product for a London or New York scalper counting milliseconds, who should be looking at a host with a node in LD4 or NY4 and paying three or four times as much for it.

Whichever you choose, verify before ordering. Open MT4 on your own machine, read the server name in the login dialog, and ping it. Brokers move servers between datacentres, and some run different entities in different cities.

👉 [Look at AvaHost's Windows VPS options before you compare routes](https://my.ava.hosting/aff.php?aff=15562)

## Free broker VPS vs paying €5–€40

IG and tastyfx both bundle an MT4 VPS hosted by Beeks in London. Both make it free while your MT4 account balance stays at $2,000 or more, and both charge $50 a month below that. Both give 30 GB of disk and let you run multiple MT4 instances on the same box. Their RAM figures don't agree with each other (1,300 MB on one page, 2,560 MB on the other), which tells you how much weight to put on the spec sheet.

Brokers that hand out a VPS against monthly trading volume offer something different again: usually a small shared instance in one location, withdrawn when your volume drops. That suits a single account running light EAs. A paid VPS gets you the size you chose, administrator rights, an OS you control, and no balance requirement.

Run the arithmetic against your own account. $50 a month is $600 a year, more than twelve months of AvaHost's top €40.00/mo tier at €480. The $2,000 you park to qualify isn't free either if that capital could be working somewhere else. If you already keep that balance with the broker and you trade from London, the bundled box is competitive. If you don't, paying is cheaper than qualifying.

## Setup mistakes that cost real money

**Disconnect, don't sign out.** Closing the Remote Desktop window leaves your Windows session and terminals running. Choosing Sign out from the Start menu ends the session and closes MT4, and the EA stops with it.

**Put each terminal in the startup folder.** Then tick "Keep personal settings and data at startup" in MT4's settings. If the host migrates your VM to another node after a hardware fault, the terminal comes back logged in instead of waiting for you to notice it's flat.

**Download MT4 from your broker, not MetaQuotes.** MetaQuotes no longer distributes MT4 from its own site; the installer that carries your broker's server list comes from the broker. Open the broker's site inside the VPS and install from there.

**Leave Windows on UTC.** MT4 displays the broker's server time, not the VPS clock, so changing the Windows timezone accomplishes nothing except confusing your own logs.

**Keep backtests off the live box.** The Strategy Tester runs a single-threaded backtest, so extra vCPUs don't speed up one test at all; they let you run several at once. Backtests also compete with live terminals for CPU, so run them on a separate server or outside your EA's trading hours. Heavy optimisation belongs on MT5, which uses every core.

## How the alternatives price out

| Provider | Entry price | Entry configuration | Locations |
| --- | --- | --- | --- |
| AvaHost | €5.00/mo | 1 vCPU / 2 GB / 25 GB NVMe | Moldova |
| MassiveGRID | $2.87/mo | 1 vCPU / 2 GB / 32 GB NVMe, 1–2 terminals | New York, London, Frankfurt, Singapore |
| LightNode | $7.71/mo | 1 vCPU / 2 GB / 50 GB NVMe, 1 TB traffic | 40+ |
| is*hosting | $10.19 (billing term stated unclearly on its page) | 2 GB / 30 GB SSD / 3 TB | 40+ |
| Broker VPS (IG, tastyfx) | $50/mo unless $2,000 balance | 30 GB disk, Beeks London | London |

MassiveGRID's $2.87 buys its smallest tier, not the whole line: the 8 vCPU / 16 GB plan lists at $38.32/mo and the 12 vCPU / 32 GB at $65.16/mo, with dedicated-core plans from $9.73/mo including a Windows Server licence and a 15-day refund window. LightNode scales to $52.70/mo for 8 vCPU / 16 GB and bills hourly at $0.012 if you need a server for a week. is*hosting lists 4 GB at $21.24, 8 GB at $33.99 and 16 GB at $50.99.

That table maps prices; which row wins depends on where your broker sits. The three hosts with nodes in NY4, LD4 or Frankfurt charge for the location. AvaHost charges less and puts you in Moldova. Whether the difference shows up in your results depends on how long you hold a position.

## What to order, and what to confirm first

- One MT4 account, a couple of EAs, no millisecond dependency: the smallest Windows-capable AvaHost plan, €5.00/mo and up.
- Three to eight terminals or a copier: the 8 GB tier.
- Ten-plus terminals: the 16 GB tier at €40.00/mo.
- Scalping or news trading against a London or New York broker: a host with a node in that city, even at several times the price.

Confirm two things at checkout. That the plan has Windows Server available, since the €5.00 entry may be Linux-only, and what the renewal rate and billing term are. Independent price trackers following this range show 12-month commitments lowering the effective monthly rate while the renewal rate after the first term climbs above it, so the headline figure is rarely what you pay in year two.

A review aggregator also lists AvaHost at 2.1 on Trustpilot from 13 reviews. That's a small sample, and it's the reason to open a support ticket in your first week rather than discover the response time after your EA has been flat for three days.

👉 [Start with the AvaHost plan that matches your terminal count](https://my.ava.hosting/aff.php?aff=15562)
