# From reference to testable indicator

Use this reference for a chart, video, informal setup description, or a mismatch between expected and actual signals. A straightforward parameter rename does not require this workflow.

## Resolve the reference

Inspect the actual image or relevant video frame and statement. Capture context that changes interpretation: instrument and exchange, contract type, timeframe, timestamp/timezone, candle type, scale, and relevant inputs.

Separate directly readable facts, inferred semantics, and unknowns that materially change the signal. A claim from an unavailable video remains unverified. A visually similar setup is not a substitute source.

## Write the smallest sufficient contract

Before coding a new rule, connect the source to implementation decisions:

| Decision | What must be clear |
|---|---|
| Reference level | How it is selected and when it becomes available |
| Candidate | What begins a setup; whether wick, body, volume, or another input matters |
| Confirmation | Exact condition and whether bar close is required |
| Invalidation | What cancels the candidate; precedence if conditions share a bar |
| Lifetime | Expiry and the treatment of an already-triggered event |
| Output | What is drawn, its anchors, and when it is removed |
| Alert | Which transition emits it and whether repeats are allowed |

Do not invent unused lifecycle states for a continuous plot. Use only relevant fields.

When a missing detail changes the trading rule, ask one focused question or show clearly labeled alternatives. Continue independent work such as locating the source and examining tool access. Defaults suit presentation details; they must not silently invent a strategy.

## Signal time versus drawing time

A pivot needing N right-side bars belongs to an earlier candle but becomes known only after those N bars. Anchor visuals where intended while keeping signal and alert timing honest.

Do not use the final high/low/close of a developing higher-timeframe candle in a historical test as if already confirmed. Follow current Pine non-repainting rules for the requested behavior.

If both trigger and invalidation appear inside one OHLC bar, the bar may not establish their order. Use the specified precedence, inspect finer data where appropriate and supported, or report ambiguity. Do not choose the favorable sequence from the final candle alone.

## Check informative examples

Select examples distinguishing the rule from a plausible mistaken implementation:

- One matching case with the expected confirmation bar.
- One nearby case lacking a required condition, e.g. wick crossing without the required close.
- A lifecycle or timing boundary when relevant, e.g. invalidation before confirmation, an already-emitted event, or a higher-timeframe candle still open.

Record expected and observed behavior. These checks do not prove profitability. Do not optimize parameters to make only the reference screenshot match.

## Percentage and price ambiguity

For entry 100 and wick low 99.80, an entry-distance stop of 0.1% gives 99.90. A buffer of 0.1% of the wick price below that wick gives 99.7002. The distinction changes placement and distance; do not implement either until the source or user resolves it.

Verify instrument tick size. Check long/short direction, and calculate gross RR only when a target is specified. Do not equate price movement with account risk or add a default 3R target.

## Compare the visible artifact

Use the same instrument, timeframe and historical region where possible. Check candle/price anchors and signal timing first, then line extension, labels, colors, density and overlap.

Read structured drawing values when supported and inspect a real screenshot. API values establish coordinates; the render establishes readability. Neither alone proves persistence.

Keep source version, applied study version/inputs and saved layout state separate. Check each chart in the requested scope. Preserve unrelated drawings, study instances and running alerts.
