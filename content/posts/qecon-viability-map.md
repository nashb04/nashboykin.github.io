---
title: "Fusion's Economic Lawson Criterion: A Viability Map"
date: 2026-09-03T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "lcoe", "economics"]
cover:
  image: "images/qecon-icon.png"
  alt: "Dollar sign icon"
---

Dennis Whyte (MIT's plasma physics center director) and Andrew Lo (an MIT finance professor) just got a paper accepted to the *Journal of Fusion Energy*. Their pitch: the Lawson criterion tells you when a plasma produces net energy, independent of whatever specific reactor you've built it in. Nobody had built the economic equivalent, a single framework that tells you when a plant produces net *profit*, independent of whether it's a tokamak, a stellarator, or a laser target chamber. So they built one, and called the output **Q_econ**: economic gain over economic cost. Above 1, viable. Below 1, not.

{{< qecon-map >}}

## What the map is actually showing

Every dot is a real, published fusion power plant design, plotted where the paper's own Table 3 puts it, on axes the paper itself uses: fusion power per square meter of reactor wall on the x-axis, overnight construction cost per square meter on the y-axis. That's the whole model's radical move, borrowed straight from Lawson: normalize to the surface that captures the energy, and the comparison stops caring what kind of reactor it is. A laser target chamber and a tokamak's first wall are just two answers to the same question, "how much power moves through how much area," and the economics only care about the answer, not the question.

The color isn't looked up, it's computed live: for whichever design you click, at whatever cost-of-capital and wall-replacement assumptions the sliders are set to, I run the paper's actual equations and check whether Q_econ clears 1. ITER and SPARC show up only as tick marks on the power-density axis, not dots, because neither one has an electric conversion system: they were never designed to sell power, so asking whether they're "economically viable" isn't a coherent question for them, not a data gap. Stellaris is a tick mark for the more mundane reason that its overnight cost hasn't been published.

## How Q_econ is actually calculated

Underneath the sliders, Q_econ is one ratio, in dollars per square meter of reactor wall, per year:

**Q_econ = C_gain / (C_S,rep + C_fixed)**

- **C_gain** — what the plant earns by fusing. It's (a constant folding in electricity price and each design's own conversion efficiency) × (power density) × (availability).
- **C_fixed** — the annualized capital bill. It's each design's own overnight cost per square meter, run through a capital recovery factor that spreads a lump sum into a level annual payment over a 30-year plant life at a given interest rate.
- **C_S,rep** — the annualized cost of replacing the first wall as neutrons wear it out. It's (a wall-material cost) × (power density) × (availability).
- **Availability** falls as wall swaps eat into uptime — the more often and the longer each swap takes, the less time the plant spends actually selling power.

The two sliders each move exactly one input:

**Cost of capital** feeds straight into the capital recovery factor inside C_fixed. It doesn't touch the reactor's physics or its power output at all — the same overnight cost just gets levelized into a bigger annual bill as financing gets more expensive. That's why it's the sharpest lever here: it's pure finance, not engineering. Worth knowing what "reasonable" means on this slider: the paper's own 2% starting point isn't a market rate at all, it's the Fed's long-run inflation target, essentially a risk-free floor. A real fusion plant borrowing on commercial terms, with actual technology risk on the books, is realistically looking at high single digits at best and could easily clear 10%+ — the slider's low end is the optimistic case, not the typical one.

**Wall replacement** moves two things at once, in the same design's favor or against it together: how much each swap costs (which directly raises C_S,rep), and how long each swap takes (which lowers availability, which drags down C_gain too). Since both terms move together, you'd expect the effects to partly cancel — the paper's finding is that they don't: the direct cost hit dominates, so a wall built cheap and fast to swap still beats one built expensive and durable. There's no market rate to anchor this one to the way there is for financing — think of the low end as a liquid or modular first wall built to be swapped often and cheaply, and the high end as a solid, durable component that's expensive and slow to pull when it finally wears out.

## Three things the paper found, and you can watch two of them happen

The paper's own conclusion calls out three findings it considers surprising enough to state plainly. The dashed line on the map is the first: **there's a real threshold around 2 MW/m²**, the paper's own base case, below which no combination of the other nine parameters makes a design viable. Not economically disadvantaged — economically impossible.

The other two findings, you can watch directly in the sidebar. Drag **cost of capital** up and most designs flip red well before you reach double-digit interest rates, some by 8%. That's the paper's confirmed finding: fusion, like any capital-intensive plant, lives or dies on financing terms most of the engineering conversation ignores. Drag **wall replacement** toward "resilient and expensive" and the same thing happens, for the counterintuitive reason laid out above: a wall that's cheap and fast to swap out beats one that's built to last. Durability sounds like the responsible engineering choice. The model says it's frequently the expensive one.

One design survives the longest as you drag either slider up: **ARIES-AT**, the most modern of the four ARIES studies, stays viable past 15% financing and past 3x wall-replacement cost — not because it's the cheapest (ARIES-CS is) or the most powerful (HYLIFE-II is), but because it's the most efficient, converting 58% of fusion power to electricity against 46% for the next best. Efficiency feeds C_gain directly without adding anything to C_S,rep, so more of its power turns into revenue at no extra wall cost.

---

*Source: [Whyte, Lo, et al., "Criteria for the economic viability of fusion power plants," accepted, Journal of Fusion Energy (2026)](https://arxiv.org/abs/2604.07367). Design data (ARIES-RS/ST/AT/CS, HYLIFE-II, LIFE.2, ARC-V2E, ITER, SPARC, Stellaris power densities and costs) from the paper's own Table 3. The authors' own full research-grade explorer, with all ten parameters and 2D contour maps, is at [andrewwlo.github.io/fusioneconomics](https://andrewwlo.github.io/fusioneconomics/).*
