---
title: "Pricing Laser Fusion: A Live LCOE Calculator"
date: 2026-08-07T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "lcoe", "laser-fusion"]
cover:
  image: "images/supply-chain-icon.png"
  alt: "Broken supply chain icon"
---

Everyone who covers fusion eventually gets asked the same question: what would the electricity actually cost? Almost nobody answers it, because almost nobody can. There's no operating laser fusion power plant, so there's no bill to point to. What exists instead is a handful of assumptions about lasers, targets, and plants that don't exist yet, wired together into a spreadsheet.

So I built the spreadsheet. Then I turned it into something you can play with.

{{< lcoe-calculator >}}

## Where the numbers come from

The math underneath is [Nicholas Hawker's 2020 model](https://royalsocietypublishing.org/doi/10.1098/rsta.2020.0053), published in the Royal Society's *Philosophical Transactions A*. Hawker co-founded [First Light Fusion](https://firstlightfusion.com/), the same company whose tritium breeding numbers I wrote about [last time](/posts/fusion-supply-chain-map/), and he built this specifically to be technology-agnostic: fourteen parameters that describe *any* inertial fusion concept, laser-driven or otherwise, without assuming a particular reactor design. That's the equation chain the calculator reruns live in your browser on every slider drag: driver energy through efficiency to target energy, through gain to fusion yield, through the blanket multiplier to thermal power, minus recirculating power, through thermal efficiency to net electric output, then capital and operating costs annualized against that output. I collapsed his year-by-year discounted cash flow into a standard capital-recovery-factor form (30-year plant life, fixed) so it updates instantly instead of re-solving on every keystroke. Plugging in his own published optimistic case reproduces his $24.6/MWh result to within a few percent, about as much confidence as a rewritten model deserves.

For the default view, I wanted a design point I could actually attribute to a real engineering study rather than a plausible-sounding guess, so it's built on [LLNL's LIFE program](https://www.osti.gov/servlets/purl/964088), the fullest laser-IFE power plant costing exercise that's been published. Their Market Entry Plant design point (2.2 MJ of laser light on target, gain around 60, 8.3 shots a second, 45% thermal efficiency, 18% driver wall-plug efficiency) reproduces their own headline numbers, roughly 1,100 MW of fusion power and 390-440 MWe net, when I run it through Hawker's equations. Two numbers in the calculator are lifted straight from LLNL's report rather than guessed: their own target-cost goal of **25 cents a target** (they note current target manufacturing runs into the thousands of dollars each, which is the whole ballgame for the fuel-cycle supply chain I wrote about [last time](/posts/fusion-supply-chain-map/)), and a plant-cost figure backed out of their own $6.4B capital estimate. Run that combination and the calculator lands at $90.5/MWh, essentially matching LLNL's own projected 9.1 cents/kWh. Everything else on that preset (driver lifetime, O&M, target-factory infrastructure cost) is Hawker's generic constant, not LLNL's, because their report doesn't break costs down to that level publicly.

LIFE itself dates to around 2011 and was eventually shelved. But LLNL is back in this business: after NIF's ignition results, the lab stood up the [Livermore Institute for Fusion Technology](https://lift.llnl.gov/) in 2025, and it just released [GEM](https://lift.llnl.gov/resources/gem), a "Generalized Economics Model" that does more or less what this calculator does, for the same class of design (diode-pumped laser driver, indirect-drive targets, liquid-lithium chamber), built on the same LIFE lineage. GEM ships as a licensed Excel tool for industry rather than a public equation set, which is the practical reason I built this from Hawker's math instead. But it's a good sign that the lab everyone treats as the most credible source on laser-IFE costing is still actively working the same problem this calculator is toy-modeling.

## Gain is not the same as a power plant

The "Today's laser" preset is deliberately close to what the National Ignition Facility has actually demonstrated, and it's worth clicking before anything else. NIF fired 2.05 MJ of laser light at a target in [December 2022](https://lasers.llnl.gov/science/achieving-fusion-ignition) and got 3.15 MJ of fusion energy back: gain greater than one, a genuine first, front-page news everywhere. What made fewer headlines is that [NIF drew roughly 300 MJ from the electrical grid](https://bigthink.com/the-future/fusion-power-nif-hype-lose-energy/) to fire that shot, because its lasers are only about 1% wall-plug efficient. Fusion energy out over grid energy in, the number that actually determines whether a plant makes electricity, is closer to 1/130.

That's why the calculator flags this preset as "not net electric" instead of giving it a price. There's no LCOE for a plant that's a net energy sink; the question isn't well-formed yet. Target gain is necessary but nowhere near sufficient, and conflating the two is the single most common misreading of fusion news.

## The sensitivity panel is the actual point

The "what's driving the price" panel at the bottom recomputes live: nudge each of the fourteen parameters 10% toward cheaper, one at a time, holding everything else fixed, and rank by how much LCOE moves. On the LLNL-grounded default, gain and driver energy top the list, because that Market Entry Plant design point is nowhere near Hawker's high-gain, low-frequency optimum, so there's real room to buy the LCOE down with better target physics. Drag gain up toward Hawker's own optimistic value and watch that leverage shrink: once gain stops being the binding constraint, the panel reorders and the cost constants take over.

That reordering is the point, and it echoes something Hawker found running his model across the whole 14-parameter space rather than one design at a time: averaged over many candidate designs, the *strongest* correlations with LCOE weren't the physics parameters that get all the press coverage. They were the discount rate, the plant cost constant, and the target cost constant. Gain mattered, but less on average than the interest rate on the debt used to build the thing.

That tracks with how every other capital-intensive energy technology has actually gotten cheap. Nuclear fission's history is as much about financing risk and regulatory certainty as it is about reactor physics. Solar's cost curve is as much about manufacturing scale-up as photovoltaic efficiency gains. If laser fusion ever gets built at scale, the discount rate a utility or a government is willing to offer it, and the confidence with which the tenth plant can be costed against the first, will probably matter as much as the gain curve on some target physicist's whiteboard.

Which is a strange thing to say about a technology that still needs a genuine physics miracle to work at all. Both things are true at once: the miracle is necessary, and it isn't the part that sets the price.

---

*Sources: [Hawker, "A simplified economic model for inertial fusion," Phil. Trans. R. Soc. A (2021)](https://royalsocietypublishing.org/doi/10.1098/rsta.2020.0053) · [LLNL, "Systems Modeling for the Laser Fusion-Fission Energy (LIFE) Power Plant"](https://www.osti.gov/servlets/purl/964088) · [Livermore Institute for Fusion Technology / GEM](https://lift.llnl.gov/resources/gem) · [LLNL on the December 2022 ignition shot](https://lasers.llnl.gov/science/achieving-fusion-ignition) · [Big Think on NIF's overall energy balance](https://bigthink.com/the-future/fusion-power-nif-hype-lose-energy/)*
