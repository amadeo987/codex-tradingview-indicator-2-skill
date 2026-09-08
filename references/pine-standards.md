# Pine standards reference

Use official TradingView sources as the authority and refresh them when building a new script or migration:

- Manual: https://www.tradingview.com/pine-script-docs/
- v6 migration: https://www.tradingview.com/pine-script-docs/migration-guides/to-pine-version-6/
- Style guide: https://www.tradingview.com/pine-script-docs/writing/style-guide
- Limitations: https://www.tradingview.com/pine-script-docs/writing/limitations/
- Alerts: https://www.tradingview.com/pine-script-docs/concepts/alerts/
- Repainting: https://www.tradingview.com/pine-script-docs/concepts/repainting/
- Other timeframes and data: https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/
- Strategies: https://www.tradingview.com/pine-script-docs/concepts/strategies/
- Publishing: https://www.tradingview.com/pine-script-docs/writing/publishing/

## Implementation checklist

- Put the version annotation first and use one `indicator()`, `strategy()`, or `library()` declaration.
- Use confirmed bars for close-dependent setups.
- For confirmed higher-timeframe data, request the previous completed HTF expression with lookahead configured so historical and realtime bars agree. Document the resulting one-HTF-bar delay.
- Never enable future leakage to improve historical appearance.
- Bound persistent arrays and drawing objects. Recycle or delete objects when their state expires.
- Prefer plots for continuous series and drawing objects for sparse levels/zones.
- For dynamic multi-event alerts, prefer `alert()` so one running alert can route several event types.
- Remember that alerts run only on realtime bars and store a snapshot of script, inputs, symbol, and timeframe.
- In strategies model commission and slippage, avoid synthetic chart types, and separate development data from unseen evaluation or forward testing.
- Before public publication, show default behavior on a clean standard-candle chart and document logic, usage, inputs, alerts, limitations, and repainting.
