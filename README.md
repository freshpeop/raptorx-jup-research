# Jupiter ($JUP) — Stress-Testing the "Buyback Floor"

**Bounty:** RaptorX Research Challenge — Ask Better Questions. Find Better Alpha.
**Asset:** Jupiter ($JUP), Solana
**Tool:** RaptorX Claw AI 5.0 — [raptorx.trade/claw-v5](https://raptorx.trade/claw-v5)
**Format:** one AI research report + a three-turn interrogation of REX AI 5.0

---

## Why this angle

The generated report called JUP "leading infrastructure" with a "fundamental floor" from a program that routes ~50% of protocol revenue into buybacks. The obvious question is "will it go up". The useful question is whether the floor is real — so I tested the three numbers the thesis actually rests on: the fully diluted valuation, the buyback flow, and the liquidity that flow has to trade through.

Each question feeds the model its own previous answer. The conversation moves from an arithmetic inconsistency, to a methodological error in the model's own metric, to a market-microstructure constraint that bounds the whole thesis.

---

## Q1 — The FDV range is internally inconsistent

> The report quotes FDV of "$1.9B to $2.9B depending on the circulating supply model", while also stating a $0.28 price and a 10B max supply — which implies $2.8B, not $1.9B. Which supply assumption produces the low bound, and if the true fully diluted base is 10B, does the "50% of revenue to buybacks" floor still hold once you normalize buybacks against the ~6.7B tokens still to be released? Show the arithmetic for both cases.

**What came back:** the low bound reflects the post-J4J governance vote that burned 30% of supply (7B base → $1.96B FDV). The model then computed buyback absorption of **4.89%** against the 10B base versus **8.88%** against the 7B base, and called the 8.88% figure "comparable to or exceeding the burn rates of major Layer 1 assets".

## Q2 — That 8.88% is the wrong kind of number

> Your 8.88% is a flow divided by a stock: $91.25M of annual buyback over a $1.03B total overhang is a years-to-absorb ratio, not an annual absorption rate, so it cannot be compared to an L1 burn rate. Redo it flow-versus-flow. At $0.28, $91.25M buys roughly 326M JUP a year, which is about 9.8% of the 3.33B float. How many tokens does the actual unlock and emission schedule release over the next twelve months, and is the buyback larger or smaller than that flow? Then stress the revenue assumption: at $100M annual revenue instead of $182.5M, does net float still shrink or does it expand?

**What came back:** a rebuilt flow table. Baseline emissions of 641.6M–841.6M JUP/year versus 0–200M under the current DAO regime; buyback of ~326M JUP at $182.5M revenue; at $100M revenue the buyback buys ~179M JUP and the float *expands* by ~21M. The model's own conclusion: "the 'deflationary' status of JUP is not a fixed property but a function of DAO Governance."

## Q3 — The buyback may not be executable at the size assumed

> The deepest JUP spot pair prints about $350k of 24h volume, which at $0.28 is roughly 1.25M JUP per day, or ~456M JUP a year. Your buyback needs ~326M JUP a year — about 71% of all secondary volume on the deepest pair — and the same pair shows 670 sells against 497 buys. Is a 71%-of-volume buyer executable without repricing the asset upward, and if not, does the "floor" only work because the buyback is assumed to transact at a price that its own size would destroy? Which liquidity or depth threshold makes this arithmetic break, and what would you monitor to know the buyback has stopped being accretive?

**What came back:** the sharpest answer of the three. The model distinguished single-venue from consolidated liquidity (~$50M/24h globally, so ~0.5% participation), described TWAP routing across its own aggregation engine, and named a self-limiting mechanism: *the better the buyback supports price, the fewer tokens each dollar retires.* Its stated break conditions — buyback above 5–10% of global daily volume, above 50% of ±2% depth, or TWAP slippage beyond 2–3% — are the falsifiable part of the thesis.

---

## Takeaway

The buyback is a volatility dampener, not a floor. Its efficiency is inversely related to its success, and its constraint is liquidity, not budget. The monitor that matters is not the burn amount but **buyback dollars ÷ consolidated 24h volume**, together with realized slippage against TWAP.

## Evidence

| Screenshot | Contents |
|---|---|
| [shots/rx-q1.png](shots/rx-q1.png) | Report + Q1 and answer |
| [shots/rx-q2.png](shots/rx-q2.png) | Q2 and answer |
| [shots/rx-q3.png](shots/rx-q3.png) | Q3 and answer |
| [shots/rx-full.png](shots/rx-full.png) | Full thread |

All interactions captured on [raptorx.trade/claw-v5](https://raptorx.trade/claw-v5/cmvp61yzt0016jp08rz3eqqst), 2026-10-26.

## External data used

- DexScreener token endpoint for `JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN`: deepest pair by liquidity (Meteora), 24h volume ~$350k, 24h txns 497 buys / 670 sells, price $0.2796, market cap ~$928M, FDV ~$1.96B.

*Not financial advice.*
