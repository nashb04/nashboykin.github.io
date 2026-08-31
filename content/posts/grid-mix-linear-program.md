---
title: "Fusion's Breakeven Price: A Linear Program"
date: 2026-08-31T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "optimization", "lcoe"]
cover:
  image: "images/minimize-icon.png"
  alt: "Hand-drawn parabola minimization icon"
---

I just finished a decision sciences course that spent a good chunk of the semester on linear programming, and I wanted to use it on something real before the material faded. The [laser fusion LCOE calculator](/posts/laser-fusion-lcoe/) already gave me verified $/MWh figures for solar, wind, and nuclear fission. An LP needs exactly that: a cost per unit of something, and constraints on how much of that something you're allowed to build. So: given North Carolina's actual electricity demand, what's the cheapest way to meet it, blending solar, wind, fission, and fusion, and how does the answer change as fusion's price moves?

One word choice up front: I'm calling the incumbent reactor technology "fission," not "nuclear," on purpose. Fusion is a nuclear reaction too, so "nuclear" as a stand-in for fission is exactly the kind of loose language this blog is supposed to avoid.

{{< grid-mix-lp >}}

## The model

Four decision variables: TWh of solar (S), wind (W), fission (N), and fusion (F) built in a year. The objective is to minimize total cost:

**Minimize** 58S + 62W + 181N + P·F

where 58, 62, and 181 are [Lazard's June 2025 unsubsidized LCOE midpoints](https://www.lazard.com/research-insights/levelized-cost-of-energyplus-lcoeplus/) ($/MWh) for utility-scale solar, onshore wind, and new nuclear fission, and P is fusion's LCOE, the variable the slider above moves.

Two constraints:

**S + W + N + F ≥ 135.6** — [North Carolina generated 135.6 TWh in 2024](https://www.eia.gov/state/seds/sep_use/total/pdf_a/use_tot_NCa.pdf) (EIA). The model has to meet that, not just approach it.

**S + W ≤ 40.68** — solar and wind combined can't be more than 30% of the mix. This isn't arbitrary: [NREL's Eastern Renewable Generation Integration Study](https://www.energy.gov/node/2014117) found the Eastern Interconnection (which NC sits in) can feasibly absorb up to 30% *wind and solar together* on an energy basis, with real coordination and flexible operations, not for free. Above that, you're into a different, harder problem this model doesn't try to solve. Fission and fusion are both treated as firm, dispatchable capacity, so neither is capped.

That's it. Four variables, one cost-minimizing objective, two constraints.

## What falls out of it

Rank the four costs and the answer is almost mechanical: use the cheapest source up to its cap, then the next cheapest for the rest, and the most expensive source never gets built unless everything else is exhausted. Two variables turn out to be dominated, for two different reasons.

**Fission is dominated by price.** At $181/MWh it loses to fusion at *any* price this model considers realistic, so fission's optimal quantity is zero in every scenario on the slider. The LP would only use it if fusion crossed north of $181/MWh, worse than even the [most pessimistic LCOE estimate in the calculator](/posts/laser-fusion-lcoe/).

**Wind is dominated by a cheaper peer.** Solar ($58) and wind ($62) share the same 30% cap, since NREL's study covers them jointly. A cost-minimizing model has no reason to split that capped bucket between two options when one is strictly cheaper, so wind's optimal quantity is also zero, everywhere. Solar fills the whole 40.68 TWh on its own.

That leaves two live regimes, split at solar's price, not wind's:

**Fusion above $58/MWh:** solar stays maxed at its 30% ceiling (40.68 TWh), fusion fills the remaining 94.92 TWh. At [LLNL's realistic LIFE estimate, $91/MWh](/posts/laser-fusion-lcoe/), that's a total system cost of **$11.00B/year**.

**Fusion below $58/MWh:** fusion now undercuts solar too, so the model drops every other source and goes 100% fusion. At [Hawker's optimistic case, $25/MWh](/posts/laser-fusion-lcoe/), that's **$3.39B/year**, a 69% drop in total cost, triggered by one number crossing one threshold.

$58/MWh is the whole hinge, and it isn't a fusion number at all, it's solar's LCOE. The interesting question a linear program forces you to ask isn't "is fusion cheap enough to matter," it's "cheap enough compared to what, exactly," and the answer to that changes the entire shape of the solution, not just the price tag.

## Why this is worth doing at LP-homework scale

A real utility integrated resource plan has hundreds of variables: transmission constraints, hourly dispatch, storage, minimum-diversification rules a regulator actually imposes. This model has four variables and two constraints on purpose. It's small enough to solve by hand and still produces two real, falsifiable claims: that fission doesn't get built in this model at any realistic fusion price, and that wind doesn't either, once solar is allowed to compete for the same capped slot. Both are testable, specific claims about which variables a cost-minimizer would actually zero out, which is more than "fusion could be competitive someday" usually gets you.

---

*Sources: [Lazard, Levelized Cost of Energy+ (June 2025)](https://www.lazard.com/research-insights/levelized-cost-of-energyplus-lcoeplus/) · [EIA, North Carolina State Electricity Profile](https://www.eia.gov/state/seds/sep_use/total/pdf_a/use_tot_NCa.pdf) · [DOE/NREL, Eastern Renewable Generation Integration Study findings](https://www.energy.gov/node/2014117) · [NC Utilities Commission, Clean Energy and Energy Efficiency Portfolio Standard](https://www.ncuc.gov/Reps/reps.html)*
