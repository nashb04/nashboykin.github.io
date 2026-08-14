---
title: "Stellarator vs. Tokamak: What Each Bet Buys You"
date: 2026-08-12T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "stellarator", "tokamak"]
cover:
  image: "images/magnet-icon.png"
  alt: "Horseshoe magnet icon"
---

I recently spoke with Lennart Bock at Proxima Fusion, and he got me thinking about stellarators. I'd just finished writing about [laser fusion](/posts/laser-fusion-lcoe/) — one bet on how to hold a plasma together. Stellarators and tokamaks are a different fork: both use magnetic fields, and disagree about how to shape them.

What I actually wanted to know was which one wins. Turns out that's the wrong question: the two designs aren't competing to be better at the same thing. A tokamak buys compactness by driving a current through the plasma, which does most of the confinement work for free. A stellarator refuses that current and shapes the field entirely with a far more complex coil set. Every difference below traces back to that one decision.

{{< stellarator-tokamak-table >}}

## The trade, compressed

**What a tokamak buys you:** compactness. ARC does with a 3.3 m radius what Stellaris needs 12.7 m for, using coils that are just simple rings, the same shape the industry has built for seventy years. **What it costs:** the plasma current that makes that compactness possible also creates disruption risk. SPARC's own team designs the machine around a 1-in-10 chance of one on every full-power pulse.

**What a stellarator buys you:** no disruptions, by design, and continuous operation instead of pulsing. **What it costs:** with no plasma current to help confine the plasma, you pay for that confinement entirely in coil complexity and machine size. Those twisted, individually-machined 3D coils are one of the hardest manufacturing problems in fusion.

Everything below is the case for why that trade looks the way it does.

## Why Commonwealth Fusion Systems, not ITER

I picked CFS's SPARC and ARC as the tokamak side on purpose. ITER is a government megaproject: different funding, different timeline, different mission (physics demonstration, not commercialization). CFS is the fairer match: venture-backed, betting on the same high-temperature superconducting magnets to shrink the machine, racing toward net energy this decade. Comparing Proxima to ITER is startup vs. nation-state. Comparing it to CFS is bet vs. bet.

The market is pricing both bets right now, three weeks apart. [Proxima raised €411 million ($468 million) on July 7, 2026](https://www.proximafusion.com/press-news/proxima-fusion-raises-eu411-million-to-build-europes-commercial-fusion-champion) at a €2.4 billion valuation, pushing its total raised past €650 million. [CFS raised $1 billion on July 30, 2026](https://cfs.energy/news-and-media/commonwealth-fusion-systems-raises-another-1-billion-bringing-total-capital-raised-to-4-billion/), pushing its total past $4 billion. Real investors, real money, on both sides of a roughly 5x gap in total capital raised.

## The size gap is the whole argument, in one number

Stellaris's major radius (12.7 m) is roughly 3.8x ARC's (3.3 m), at nearly the same field strength (9 T vs. 9.2 T). That's the trade-off, compressed: a tokamak's driven current does a lot of its confining for it, almost for free. A stellarator has to buy the same confinement entirely through coil shape, and that costs volume — more vessel, more blanket, more shielding, downstream.

SPARC's own physics team designs the machine assuming a [1-in-10 chance of a plasma disruption on every full-power pulse](https://www.cambridge.org/core/journals/journal-of-plasma-physics/article/mhd-stability-and-disruptions-in-the-sparc-tokamak/908C6788C0D625C5DDF335DBD9A17476). Not a skeptic's estimate — [the tokamak team's own engineering assumption](https://en.wikipedia.org/wiki/SPARC_(tokamak)), baked into how they design the vessel. A stellarator, with no net plasma current, doesn't have that failure mode at all. That's the trade Proxima is betting is worth the extra size: the compactness is real, and so is the risk that comes with it.

## Is 3.8x real physics, or extra margin?

Both concepts have published, peer-reviewed scaling laws for confinement time, fitted to thousands of real discharges: [IPB98(y,2)](https://iopscience.iop.org/article/10.1088/0029-5515/39/12/302) for tokamaks, [ISS04](https://iopscience.iop.org/article/10.1088/0029-5515/45/12/024) for stellarators. This isn't a recomputation of ARC's or Stellaris's specific numbers — I don't have either team's assumed density or heating power, and neither company has published enough to reconstruct it. It's what the published laws say happens to *any* tokamak or stellarator design as you scale it up. Do that geometrically — same field, density, and heating power, just bigger — and IPB98(y,2) says confinement improves as roughly size². Do the same to a stellarator, and ISS04 says it improves as roughly size³ (an exponent of 2.28 on minor radius alone, plus 0.64 on major radius). On paper, a stellarator gets a steeper payoff from bulking up.

But that size² number flatters the tokamak, because it assumes plasma current stays fixed while the machine grows. Real reactor studies don't do that — current scales up with size too, at a fixed safety factor. Fold in IPB98(y,2)'s own 0.93 exponent on current and the tokamak's effective size scaling jumps to size^2.9, almost exactly matching the stellarator's size^2.92. Scale both machines the way an actual design study would, and the tokamak's size advantage nearly disappears. The compactness isn't coming from some confinement-efficiency edge — it's coming from the same driven current that also causes the disruption risk above. Same source, both effects.

That's a real, sourced number, not two press releases side by side — with the caveat every scaling law like this carries: these are fits to present-day, much smaller experiments, extrapolated to reactor scale with real uncertainty (typically ±20%, even inside the fitted range). They explain the shape of the trade-off. They don't pin down Stellaris's exact radius.

## What's published isn't the same as what's built

CFS has put a number on ARC's net electric output: 270 MWe. [Proxima's Stellaris paper](https://www.proximafusion.com/press-news/proxima-fusion-and-partners-publish-stellaris-fusion-power-plant-concept-to-bring-limitless-safe-clean-energy-to-the-grid) reports fusion power (up to 2.7 GW) and thermal power (about 3.1 GW), but no net electric figure yet. That's not really a gap in ambition, it's sequencing: Stellaris is a physics and engineering concept paper, and a net electric number means committing to a specific balance-of-plant design before there's a specific site or grid connection to design it for.

Proxima's own construction timeline, meanwhile, is concrete. [In February 2026, Proxima signed a framework agreement with the Free State of Bavaria, RWE, and the Max Planck Institute for Plasma Physics](https://www.ans.org/news/2026-03-03/article-7810/proxima-fusion-signs-mou-with-bavaria-rwe-and-max-planck-ipp-to-build-german-stellarator-power-plant/) to build Alpha at Garching, a project [priced at €2 billion](https://neutronbytes.com/2026/07/07/proxima-fusion-funding-targets-2030s-for-power-plant/). SPARC is further along, [about three-quarters built as of April 2026 with first plasma targeted for 2027](https://blog.cfs.energy/our-sparc-fusion-facility-is-now-about-75-done-take-a-virtual-tour-of-the-progress/). Alpha's next milestone, the Stellarator Model Coil, is due the same year, ahead of Alpha's own target of reaching net energy in 2031.

## Both bets are still bets

Neither SPARC nor Alpha makes electricity yet. SPARC exists to prove a compact, high-field tokamak can hit strong energy gain despite the disruption risk. Alpha exists to prove a stellarator can hit net energy without ever taking that risk on. Whoever proves their machine works first gets to build the commercial plant with a straight face. Until then, stellarator vs. tokamak isn't a verdict — it's two bets on which problem is worth solving first.

---

*Sources: [Proxima Fusion, Stellaris power plant concept announcement (Feb 2025)](https://www.proximafusion.com/press-news/proxima-fusion-and-partners-publish-stellaris-fusion-power-plant-concept-to-bring-limitless-safe-clean-energy-to-the-grid) · [World Nuclear News on the Stellaris design](https://www.world-nuclear-news.org/articles/german-stellarator-fusion-design-concept-unveiled) · [Wikipedia, SPARC (tokamak)](https://en.wikipedia.org/wiki/SPARC_(tokamak)) · [Wikipedia, ARC fusion reactor](https://en.wikipedia.org/wiki/ARC_fusion_reactor) · [Sweeney et al., "MHD stability and disruptions in the SPARC tokamak," Journal of Plasma Physics](https://www.cambridge.org/core/journals/journal-of-plasma-physics/article/mhd-stability-and-disruptions-in-the-sparc-tokamak/908C6788C0D625C5DDF335DBD9A17476) · [ITER Physics Expert Group, "Chapter 2: Plasma confinement and transport," Nuclear Fusion 39 (1999)](https://iopscience.iop.org/article/10.1088/0029-5515/39/12/302) · [Yamada et al., "Characterization of energy confinement in net-current free plasmas using the extended International Stellarator Database," Nuclear Fusion 45 (2005)](https://iopscience.iop.org/article/10.1088/0029-5515/45/12/024) · [Proxima Fusion, €411M funding announcement (July 2026)](https://www.proximafusion.com/press-news/proxima-fusion-raises-eu411-million-to-build-europes-commercial-fusion-champion) · [CFS, $1B funding announcement (July 2026)](https://cfs.energy/news-and-media/commonwealth-fusion-systems-raises-another-1-billion-bringing-total-capital-raised-to-4-billion/) · [ANS/Nuclear Newswire on the Proxima/Bavaria/RWE/IPP Alpha agreement](https://www.ans.org/news/2026-03-03/article-7810/proxima-fusion-signs-mou-with-bavaria-rwe-and-max-planck-ipp-to-build-german-stellarator-power-plant/) · [Neutron Bytes on Alpha's €2B cost](https://neutronbytes.com/2026/07/07/proxima-fusion-funding-targets-2030s-for-power-plant/) · [CFS, SPARC construction progress (April 2026)](https://blog.cfs.energy/our-sparc-fusion-facility-is-now-about-75-done-take-a-virtual-tour-of-the-progress/)*
