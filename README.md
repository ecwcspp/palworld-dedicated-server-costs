# palworld dedicated server hosting: requirements, real costs, setup steps, and when bare metal beats a $12 game panel

Palworld's built-in co-op tops out at four players. That's fine for a weekend of base-building with friends, but the moment your group grows past that, or you want a world that stays online while you're asleep, you start looking into dedicated server hosting — and quickly run into a wall of jargon, wildly different prices, and providers that all claim to be the best.

This guide sticks to what's verifiable: Palworld's official server requirements, what hosting actually costs at each tier, how a dedicated server gets installed, and when it makes sense to skip the game-panel providers entirely and rent raw hardware from a bare-metal host like Sharktech. The short version: most friend groups should not buy a bare-metal server. Some communities absolutely should. Knowing which group you're in is worth ten minutes of reading.

## What a dedicated server actually changes in Palworld

A dedicated server is a standalone instance of the game world that runs independently of any player's PC. Instead of the host's machine keeping the save alive, the world runs on a server that stays on around the clock.

Three things come with that:

- **The 32-player cap.** Palworld hard-caps a server at 32 concurrent players via the `ServerPlayerMaxNum` setting. Some hosts advertise "unlimited slots," but that's marketing — the game itself enforces the limit. For most groups, 32 is more headroom than you'll ever use.
- **Crossplay.** Since the v0.5.0 update, dedicated servers support crossplay between Steam, Xbox, PS5, and Mac on a unified cross-platform layer. If your friends are split across PC and console, a dedicated server is the only way to get everyone into one world.
- **Community server listing.** A dedicated server can be registered as a community server, which makes it discoverable in Palworld's in-game server browser instead of requiring players to type an IP address. Useful if you're running something semi-public rather than a private friends-only world.

The 1.0 release also added a wave of new server settings (guides count around 30 new options), so if you last looked at server config a year ago, the settings file has grown.

## Official requirements: what Palworld actually needs

These numbers come straight from the official Palworld server documentation, so treat them as the floor, not marketing:

| Component | Official requirement |
| --- | --- |
| CPU | 4 cores or more (recommended) |
| RAM | 16 GB recommended; 8 GB will boot but raises crash risk from out-of-memory errors |
| Storage | Fast SSD recommended; slow storage can corrupt save data |
| Network | UDP port 8211 by default (changeable), with port forwarding possible |
| OS | Windows 64-bit or Linux 64-bit (Ubuntu, AlmaLinux, etc.) |

Two practical notes on top of that. First, no GPU is needed — the server never renders anything. Second, RAM is the resource that actually decides whether your server stays up. Community experience and hosting guides line up roughly like this:

- **1–4 players:** 8 GB is workable, 6 GB is pushing it
- **5–16 players:** 8–16 GB for stable performance, especially once bases grow and players hoard Pals
- **17–32 players:** 16 GB minimum, more if you're running mods

CPU matters differently than you'd expect. Palworld leans on single-thread performance more than raw core count — a high clock speed on a few cores generally beats a pile of slow cores. Keep that in mind later when we look at server hardware, because not all dedicated servers are equal here.

## Three ways to host, and what each really costs

**Option 1: your own PC.** The server tool is free on Steam, and if you have a machine with 16 GB of RAM, you can host tonight. The downsides are the classic ones: your PC has to stay on 24/7 for the world to stay up, your home upload bandwidth becomes everyone's ping, friends can only play when your machine is running, and residential IPs are notoriously bad at absorbing even small DDoS attacks — which public game servers do attract. Fine for testing, miserable for a persistent world.

**Option 2: a game-panel host.** This is what most people searching "palworld dedicated server hosting" end up buying. You pay roughly $7–$22 per month, get a web panel, one-click install, automatic backups, and DDoS protection, and never touch a config file unless you want to. Entry plans around $7.49–$12 typically include 8 GB of RAM, which covers small groups; 16 GB plans run roughly $20–$22 at the budget end. This is the right answer for the majority of friend groups and small communities.

**Option 3: a VPS or bare-metal server.** You rent an entire machine (or a large slice of one), get root access, and run the server yourself. VPS options in the 8–16 GB range exist at game-host prices. True bare metal starts at a completely different price point — the plans on Sharktech's dedicated server page, for example, begin at $259/month — but you get the whole box: no CPU throttling, no shared noisy neighbors, enterprise networking, and the ability to run several game server instances on one machine.

The jump from ~$12/month to ~$259/month is not subtle, so the honest question is: who is bare metal actually for?

## When a bare-metal server makes sense for Palworld

Bare metal stops being overkill and starts being rational in a few specific situations:

- **You're running a public community server.** Public Palworld servers get targeted. Sharktech publishes a customer testimonial from a game network operator whose servers regularly absorb DDoS attacks in the 3–8 Gbit range without going down — that's the use case their in-line DDoS protection is built for. A $12 panel plan with shared protection is a different animal than a dedicated box sitting on a network designed to filter attacks.
- **You're running multiple worlds.** A 64–128 GB bare-metal server can host several Palworld instances (plus a voice server, a website, whatever else your community needs) simultaneously. At that point you're comparing one $259–$299 server against four separate $20/month panel plans, and the math changes.
- **You're heavily modded or at the 32-player cap.** Modded servers and busy 32-player worlds eat RAM and disk I/O. On shared panel hosting you're subject to the host's throttling rules; on bare metal there's no one to throttle you.
- **You want the hardware, not a service.** Bare metal means root access, your own OS, your own config. If you're comfortable with Linux and SteamCMD, that's freedom. If you're not, it's a liability — more on that below.

Sharktech itself is a long-established bare-metal and cloud host (operating since 2003) with data centers in Las Vegas, Los Angeles, Denver, Chicago, and Amsterdam, a 99.99% uptime guarantee, and DDoS protection included on every service rather than sold as an add-on. Their game-server page pitches custom game hosting from $7.95/month at the VPS end of their range, with dedicated bare-metal plans above that. They're a hardware provider, though — nobody there is going to click "install Palworld" for you. That's your job.

If any of those situations describe you, 👉 check out Sharktech's bare-metal dedicated server lineup and the current configurations.

## Sharktech's current dedicated server plans

The following table is the complete set of dedicated bare-metal configurations listed on Sharktech's site right now, with pricing as displayed. All plans include free setup, DDoS protection, 24/7 support, and the option to upgrade RAM (up to 1 TB on most configs), storage, or network (up to 100 Gbps) at order time or later. Billing is monthly by default, with discounts for quarterly, semi-annual, or annual prepayment — the "effective monthly" column shows what annual billing works out to per month.

| Configuration | RAM | Storage | Network | Monthly price | Effective $/mo (annual billing) | Order |
| --- | --- | --- | --- | --- | --- | --- |
| Dual Xeon E5-2695v4 (36 × 2.1 GHz), 6× 2.5" SATA/SAS bays | 64 GB DDR4 | 2 TB M.2 NVMe + SATA options | 10 Gbps, 300 TB/mo | $259 | ~$220 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=741) |
| Dual Xeon E5-2695v4 (36 × 2.1 GHz), 6× 3.5" SATA/SAS bays | 64 GB DDR4 | 2 TB M.2 NVMe + SATA/HDD options | 10 Gbps, 300 TB/mo | $269 | — | [ Contact sales about this config](https://bit.ly/SharKTech) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 3× 3.5" bays | 128 GB DDR4 | 2 TB M.2 NVMe | 10 Gbps, 300 TB/mo | $299 | ~$254 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=660) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 6× 2.5" bays | 128 GB DDR4 | 2 TB M.2 NVMe | 10 Gbps, 300 TB/mo | $309 | ~$263 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=636) |
| Dual Xeon Gold 6246 (24 × 3.3 GHz), 3× 3.5" bays | 128 GB DDR4 | 2 TB M.2 NVMe | 10 Gbps, 300 TB/mo | $309 | ~$263 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=814) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 6× U.2 NVMe bays | 128 GB DDR4 | 2 TB M.2 NVMe, expandable to 15.36 TB U.2 | 10 Gbps, 300 TB/mo | $329 | ~$296 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=766) |
| AMD EPYC 7702P (64 × 2 GHz), 10× U.2 NVMe bays | 128 GB DDR4 | 2 TB M.2 NVMe, expandable to 15.36 TB U.2 | 10 Gbps, 300 TB/mo | $499 | ~$424 | [ Order this server](https://portal.sharktech.net/aff.php?aff=1611&pid=729) |
| Dual AMD EPYC 7702 (128 × 2 GHz), 10× U.2 NVMe bays | 128 GB DDR4 | 2 TB M.2 NVMe, expandable to 15.36 TB U.2 | 10 Gbps, 300 TB/mo | $699 | — | [ Contact sales about this config](https://bit.ly/SharKTech) |

A few honest observations about this lineup, because a spec sheet alone won't tell you what fits Palworld:

**The E5-2695v4's 2.1 GHz base clock is modest by game-server standards.** Palworld cares about single-thread speed, and older Xeons running at 2.1 GHz will feel it under load more than a modern high-clock desktop CPU would. If you go this route, the Dual Xeon Gold 6246 configuration at $309/month is the more Palworld-appropriate pick of the bunch — 24 cores at 3.3 GHz is a meaningfully better fit for a game that wants fast individual threads.

**The EPYC boxes are for multi-server operations, not one Palworld world.** A single Palworld server, even full at 32 players with mods, cannot use 128 threads. Where those machines earn their price is running many instances — a network of community servers, other games, and infrastructure on one box.

**64 GB of RAM is generous for one world.** The $259 entry config comfortably covers a full 32-player server (which wants 16 GB+) with room for a second instance, a backup routine, and overhead. If your plan is strictly one world, you're paying for headroom you'll use eventually or never.

Sharktech also notes on the page that due to hardware shortages they can't guarantee sub-24-hour delivery on bare-metal deployments, so if you're standing one up before a launch weekend, order early. Their Trustpilot presence is real but small — a 3.5/5 average across a modest number of reviews — so if third-party validation matters a lot to you, weigh that alongside the uptime guarantee and the included DDoS protection.

## Getting Palworld running on your own hardware

This is the part panel hosts do for you. On a bare-metal box, it's yours, and per the official deployment docs it looks like this:

1. **Install the server tool.** On Windows, you can grab "Palworld Dedicated Server" directly from the Steam library (it appears under Tools). On Linux, use SteamCMD — the server is a free download and doesn't require an active game license on that account.
2. **Open the port.** UDP 8211 by default, changeable. On your own server you control the firewall, so open the port in the OS firewall (and in any cloud/security group if applicable).
3. **Configure the world.** Server settings live in `PalWorldSettings.ini`, found under the `Pal/Saved/Config` directory inside the server files (create it from the sample if it isn't there on first run). This is where player cap, password, EXP rate, and the batch of new 1.0 options get set.
4. **Run it persistently.** On Linux, run the server under a systemd service or in tmux/screen so it survives disconnects. On Windows, the Steam tool handles launching. Keep regular backups of the `Saved` folder — save corruption from slow storage is a documented failure mode, which is why SSDs are in the official requirements.
5. **List it as a community server (optional).** The official docs describe registering the server so it shows up in the in-game community browser. Skip this if you want a private, invite-only world.

None of this is hard if you've administered a Linux box before. If you haven't, that's the real cost of bare metal — not the monthly bill, but the evenings spent learning systemd and debugging a config file at midnight while your friends ask why the server is down.

## Sizing it to your actual situation

Putting the pieces together, the decision looks like this:

- **Friends-only world, under ~16 players, no mods:** a $7–$22/month game panel or an 8–16 GB VPS. Bare metal is wasted money here, full stop.
- **Semi-public community server, crossplay crowd, occasional DDoS concern:** a 16 GB+ panel plan with strong DDoS protection is still the first thing to try. If your community gets big enough that throttling, RAM ceilings, or repeated attacks become the bottleneck, that's the trigger to move up.
- **Public server network, multiple worlds, heavy mods, or you're done with shared hosting limits:** this is where Sharktech's plans make sense. The $309 Dual Xeon Gold 6246 config is the best hardware match for Palworld's single-thread preference; the $259 entry config is the value pick if you'll run two instances on one box; the EPYC machines are for operators running a fleet.

👉 If that middle-or-top tier sounds like your situation, configure a dedicated server through Sharktech and pick the data center closest to most of your players — Los Angeles, Denver, Chicago, Las Vegas, or Amsterdam — since latency to your player base matters more than almost any other spec.

## The bottom line

"Palworld dedicated server hosting" covers two very different purchases. For most people it means a ~$12/month managed panel where someone else handles the boring parts — and that's genuinely the right call for a friends' world. For operators running public or multi-server communities, it means hardware, and the things that matter shift to DDoS protection that actually absorbs attacks, guaranteed uptime, RAM headroom, and network quality — the exact bundle Sharktech has sold to game server operators since 2003, with dedicated plans from $259/month and DDoS protection included on everything.

Figure out which buyer you are first. Then spend accordingly — whether that's twelve dollars or three hundred.
