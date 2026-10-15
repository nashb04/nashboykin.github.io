---
title: "What Fusion Does to the Climate Scenarios (and When)"
date: 2026-10-15T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "climate", "modeling"]
cover:
  image: "images/co2-icon.png"
  alt: "CO2 cloud with three downward arrows icon"
---

We use the SSPs constantly in my classes, and the energy story is almost always wind and solar. Fission comes up as a share that keeps shrinking, and fusion never comes up at all. That matches the data: nuclear supplied 9% of global electricity in 2024, the lowest share in more than 45 years even with output at a record, while solar was the largest source of new electricity for the third year running ([Ember](https://ember-energy.org/latest-insights/global-electricity-review-2025/2024-in-review/)).

The standard SSP emissions files carry totals by gas and sector with no technology breakdown, so there's no fusion dial to turn. A few research groups have added fusion to full energy-system and integrated assessment models ([GCAM](https://www.osti.gov/biblio/1778647) and [DNE21+](https://www.sciencedirect.com/science/article/pii/S2211467X19301257) among them). I wanted to see what it looks like on the standard pathways, so I added it.

## What I did

I took the standard SSP2-4.5 ("middle of the road") and SSP3-7.0 (high-emission) fossil CO2 pathways and added a fusion fleet. The fleet starts building in a given year, ramps up over 20 years to a peak build rate, and holds that rate until 2100, after which it stays at its 2100 size. It displaces fossil CO2 from the power sector first, at 0.6 tonnes per MWh. Both versions then go through a climate model, FaIR, across 841 calibrated configurations, and I compare them member by member.

{{< fusion-ssp >}}

## The fleets are big

The fastest build-out is 100 GW a year starting in 2035. That is roughly five to six times the average pace of fission's biggest build-out, which added just over 100 GW between 1983 and 1988 ([World Nuclear Association](https://world-nuclear.org/our-association/publications/world-nuclear-outlook-report/chapter-4-assessment-of-overall-global-nuclear-capacity)), held for decades. By 2100 it is 5,550 GW generating about 41,000 TWh a year. Global electricity generation in 2024 was about 30,800 TWh and nuclear was 2,768 TWh ([Ember](https://ember-energy.org/latest-insights/global-electricity-review-2025/2024-in-review/); the total is derived from its low-carbon share). So this one fleet is 1.3 times today's whole grid and 15 times today's nuclear.

A slower, more fission-like build-out of 30 GW a year from 2040 still reaches 1,515 GW by 2100, and cools SSP2-4.5 by only 0.03 °C.

## Why it's small by 2100

Even so, the fast fleet cools the 2081–2100 average by about 0.10 °C in SSP2-4.5.

**It's carbon-budget arithmetic.** The IPCC's best estimate is 0.45 °C of warming per 1,000 Gt of CO2 ([AR6](https://www.ipcc.ch/report/ar6/wg1/chapter/summary-for-policymakers/)), so a full degree is roughly 2,200 Gt. The fast fleet avoids 294 Gt by 2100 in SSP2-4.5 and 708 Gt in SSP3-7.0.

**The baseline is already decarbonizing.** SSP2-4.5's power-sector emissions fall from about 15 Gt a year in 2020 to below zero by 2100. Fusion is the marginal clean source on top of a transition that is already assumed.

**It only touches part of the problem.** In SSP2-4.5, 672 of the 2,250 Gt of fossil CO2 emitted from 2035 to 2100 sit in the power-sector line. The rest is industry, transport and buildings. Removing all power-sector CO2 by 2050 would cool 2081–2100 by 0.21 °C. Removing all fossil CO2 by 2050 would cool it by 0.67 °C.

**It arrives late.** Even the fast fleet is only 600 GW in 2050, and 48% of the century's fossil CO2 has been emitted by then. Starting the same build-out in 2055 instead of 2035 leaves about a third of the effect (−0.03 °C instead of −0.10 °C) and a smaller fleet in 2100 (3,550 GW).

## After 2100

Past 2100 the picture changes. In SSP3-7.0 the same fast fleet goes from −0.15 °C at 2100 to −1.1 °C by 2300. Emissions there are still large in the 2100s, and the fleet keeps displacing about 25 Gt of CO2 a year until the baseline winds down.

After 2100 the baseline is the CMIP6 extension convention, a straight glide to zero by about 2200–2250, not model output. These numbers are what fusion does given that continuation.

## When the power gets used

In SSP2-4.5, fusion runs out of power-sector CO2 to displace before the century ends, but the fleet is still there. If the surplus electricity replaces fossil fuel in industry, transport and buildings, the same fleet goes from −0.10 °C to −0.16 °C by 2100 and −0.66 °C by 2300 (the middle scenario above).

This assumes every spare terawatt-hour finds a use at the same 0.6 t per MWh, so it is an upper bound. The 0.6 sits between the direct emissions of gas combined-cycle (370 g CO2 per kWh) and coal (760) in the [IPCC's AR5 technology table](https://www.ipcc.ch/report/ar5/wg3/).

## What it's worth

FaIR returns temperature, not dollars, so this is a separate step. Each tonne of CO2 the fleet keeps out of the air is valued at the U.S. EPA's 2023 social cost of carbon (the harm done by one more tonne): $190 for a tonne emitted in 2020, rising to $410 by 2080, at a 2% discount rate. Each year's avoided CO2 is valued at that year's figure and discounted back to 2020. Every number below is the difference between the same SSP with the fleet and without it, so it's what the fleet is responsible for and nothing else.

- **The fast fleet in SSP2-4.5 is worth about $42 trillion.** It avoids 294 Gt of CO2 by 2100, which comes to roughly $140 a tonne after discounting. At the EPA's 2.5% and 1.5% rates it is $22 to $80 trillion.
- **Starting late or slowly cuts that by about two thirds.** The 2055 start is worth $13 trillion, and the slow 30 GW a year from 2040 is also worth $13 trillion. The dollars follow the temperature results: both avoid about a third as much.
- **Putting the surplus power to use adds $38 trillion.** That scenario is worth $80 trillion by 2100, and another $46 trillion from CO2 avoided after 2100.
- **The same fleet is worth twice as much in SSP3-7.0.** It comes to $84 trillion by 2100 and $92 trillion after, because there is more fossil CO2 left to displace.

For scale, removing all power-sector CO2 by 2050 would be worth $93 trillion in SSP2-4.5 and $316 trillion in SSP3-7.0 through 2100, so the fast fleet captures a bit under half of the first and about a quarter of the second.

These are wide estimates. The study behind the EPA's central value puts its own 5th to 95th percentile at $44 to $413 per tonne around $185 ([Rennert et al., *Nature* 2022](https://www.nature.com/articles/s41586-022-05224-9)), so each figure could plausibly be a quarter to double what is shown. The EPA table stops at 2080, so I held the value flat after that, and the post-2100 figures depend more on discounting than on climate. The social cost of carbon is also built for small changes, and a fleet this size is not one.

## What I take from it

- For a 2100 temperature target, fusion at any plausible pace is a small contributor. The baselines already assume a lot of clean power, and the fleet is small while emissions are highest.
- Its case is the long game: the 2100s, and high-emission worlds where there is far more fossil CO2 left to displace.
- The bigger lever in these runs is the rest of the economy. In SSP2-4.5, removing all fossil CO2 does about three times what removing power-sector CO2 alone does, and that's where abundant clean power would have to be put to work.

## What this leaves out

- **Only direct displacement, fossil-first.** There are no cost feedbacks, rebound effects, or demand response.
- **The fleets are scenarios, not forecasts.** Whether fusion is cost-competitive depends on carbon policy and on whether fission and carbon capture are available. The [GCAM study](https://www.osti.gov/biblio/1778647) finds fusion's share swinging from marginal to dominant on those assumptions.
- **The climate model runs cool in high-emission worlds.** FaIR reproduces today's warming (1.08 °C for 2011–2020 against the IPCC's 1.09 °C) and SSP1-2.6 exactly, but runs 0.3–0.4 °C below the IPCC's best estimates for SSP3-7.0 and SSP5-8.5. It also gives 0.24–0.38 °C per 1,000 Gt against the IPCC's 0.45, so the high-SSP effects here are probably understated by roughly 1.5 to 1.7 times.
- **No retirements.** Plants are assumed to last past 2100 or be replaced one-for-one.

I also ran SSP1-2.6 and SSP5-8.5. SSP5-8.5 looks like SSP3-7.0. SSP1-2.6 is the extreme version of the "power gets used" case: its power sector is already net-negative, so fusion only matters if its output electrifies the rest of the economy.

---

*Sources: [RCMIP v5.1.0 SSP emissions](https://zenodo.org/records/4589756) · [FaIR](https://docs.fairmodel.net) and its [AR6-calibrated ensemble (fair-calibrate v1.4.1)](https://gmd.copernicus.org/articles/17/8569/2024/) · [IPCC AR6 WGI Summary for Policymakers](https://www.ipcc.ch/report/ar6/wg1/chapter/summary-for-policymakers/) · [IPCC AR5 WGIII, Annex III, Table A.III.2](https://www.ipcc.ch/report/ar5/wg3/) · [Turnbull, Glaser & Goldston, "Investigating the value of fusion energy using the Global Change Assessment Model"](https://www.osti.gov/biblio/1778647) · [Gi et al., "Potential contribution of fusion power generation to low-carbon development under the Paris Agreement", Energy Strategy Reviews (2020)](https://www.sciencedirect.com/science/article/pii/S2211467X19301257) · [World Nuclear Association, global nuclear capacity](https://world-nuclear.org/our-association/publications/world-nuclear-outlook-report/chapter-4-assessment-of-overall-global-nuclear-capacity) · [Ember, Global Electricity Review 2025](https://ember-energy.org/latest-insights/global-electricity-review-2025/2024-in-review/) · U.S. EPA, *Report on the Social Cost of Greenhouse Gases: Estimates Incorporating Recent Scientific Advances* (2023), Table ES.1 · [Rennert et al., "Comprehensive evidence implies a higher social cost of CO2", Nature (2022)](https://www.nature.com/articles/s41586-022-05224-9)*
