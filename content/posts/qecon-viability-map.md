---
title: "Fusion's Economic Lawson Criterion: A Viability Map"
date: 2026-09-03T12:00:00-04:00
draft: false
tags: ["analysis", "fusion", "lcoe", "economics"]
cover:
  image: "images/fusion3.png"
  alt: "Atom icon"
---

Lennart's other suggestion, after he corrected the stellarator post, was a paper by Dennis Whyte (MIT's plasma physics center director) and Andrew Lo (an MIT finance professor), just accepted to the *Journal of Fusion Energy*. Their pitch: the Lawson criterion tells you when a plasma produces net energy, independent of whatever specific reactor you've built it in. Nobody had built the economic equivalent, a single framework that tells you when a plant produces net *profit*, independent of whether it's a tokamak, a stellarator, or a laser target chamber. So they built one, and called the output **Q_econ**: economic gain over economic cost. Above 1, viable. Below 1, not.

{{< qecon-map >}}

## What the map is actually showing

Every dot is a real, published fusion power plant design, plotted where the paper's own Table 3 puts it, on axes the paper itself uses: fusion power per square meter of reactor wall on the x-axis, overnight construction cost per square meter on the y-axis. That's the whole model's radical move, borrowed straight from Lawson: normalize to the surface that captures the energy, and the comparison stops caring what kind of reactor it is. A laser target chamber and a tokamak's first wall are just two answers to the same question, "how much power moves through how much area," and the economics only care about the answer, not the question.

The color isn't looked up, it's computed live: for whichever design you click, at whatever cost-of-capital and wall-replacement assumptions the sliders are set to, I run the paper's actual equations and check whether Q_econ clears 1. ITER and SPARC show up only as tick marks on the power-density axis, not dots, because neither one has an electric conversion system: they were never designed to sell power, so asking whether they're "economically viable" isn't a coherent question for them, not a data gap. Stellaris is a tick mark for the more mundane reason that its overnight cost hasn't been published.

## Three things the paper found, and you can watch two of them happen

The paper's own conclusion calls out three findings it considers surprising enough to state plainly. The dashed line on the map is the first: **there's a real threshold around 2 MW/m²**, below which no combination of the other nine parameters makes a design viable. That overturns the intuitive assumption that a gentler, lower-power reactor should be the cheaper one to build. It isn't. Below the line, you're not economically disadvantaged, you're economically impossible.

The other two, you can watch directly. Drag **cost of capital** up and most of the dots flip red well before you reach double-digit interest rates, some of them by 8%. That's the paper's confirmed finding: fusion, like any capital-intensive plant, lives or dies on financing terms most of the engineering conversation ignores. Drag **wall replacement** toward "resilient and expensive" and the same thing happens, for a reason the paper flags as its most counterintuitive result: a wall that's cheap and fast to swap out beats one that's built to last. Durability sounds like the responsible engineering choice. The model says it's frequently the expensive one.

One design survives both stress tests: **ARIES-AT**, the most modern of the four ARIES studies, holds Q_econ above 1 even at 15% financing and 3x wall-replacement cost, while five of the other six flip to red under either. It isn't the most powerful design in the set (HYLIFE-II runs nearly 3x its power density) or the cheapest (ARIES-CS is). It's just the one that doesn't have a single parameter close to its own limit, which, in a model built entirely out of thresholds, might be the actual lesson.

---

*Source: [Whyte, Lo, et al., "Criteria for the economic viability of fusion power plants," accepted, Journal of Fusion Energy (2026)](https://arxiv.org/abs/2604.07367). Design data (ARIES-RS/ST/AT/CS, HYLIFE-II, LIFE.2, ARC-V2E, ITER, SPARC, Stellaris power densities and costs) from the paper's own Table 3. The authors' own full research-grade explorer, with all ten parameters and 2D contour maps, is at [andrewwlo.github.io/fusioneconomics](https://andrewwlo.github.io/fusioneconomics/).*
