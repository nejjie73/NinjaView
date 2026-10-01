# NinjaView

**Run TradingView Pine Script indicators inside NinjaTrader 8.**

NinjaView lets you load a `.pine` indicator file and see it on your NinjaTrader charts, calculated live from NinjaTrader's own data. It works two ways:

- **NinjaView Pine indicator.** Add it to any NinjaTrader minute chart and point it at a Pine file. Plots, fills, levels, shapes, boxes, labels, lines and tables draw natively on the chart, and update tick by tick.
- **NinjaView window.** A standalone chart (New > NinjaView) with NinjaTrader market data and the same Pine engine.

**[Download the latest release](https://github.com/nejjie73/NinjaView/releases/latest)** · [Install guide](docs/install.md) · [What's supported](docs/supported-features.md) · [Report a script](https://github.com/nejjie73/NinjaView/issues/new/choose)

## Highlights

- Pine v5 and v6: persistent `var`/`varip` state with correct realtime rollback, user types, methods, enums, arrays, maps, tuples, switch/if/for/while, and a broad set of `ta.*`, `math.*`, `str.*` and drawing functions.
- Separate-panel (oscillator) scripts get their own panel; `force_overlay` objects draw on the price chart.
- Script inputs appear in NinjaTrader's indicator settings and are saved with your workspace.
- Public libraries (`import Owner/Library/Version`) are fetched once from TradingView by exact version, verified and cached. Local copies always take priority.
- No orders, no account access, no TradingView login.

## Requirements

- NinjaTrader 8 (tested on 8.1.8.3), Windows x64
- Time-based minute charts (tick, range, Renko and daily charts are not supported yet)

## Limits

NinjaView is an independent, partial implementation of Pine. Some scripts will not compile yet, `strategy()` scripts are not supported, and a script that loads may still calculate differently from TradingView. Check results against TradingView before relying on them. See [what's supported](docs/supported-features.md) for details.

If a script fails, [open an issue](https://github.com/nejjie73/NinjaView/issues/new/choose) with the error message and a link to the public script.

## Terms

Free to use; no warranty; not financial advice. Not affiliated with TradingView or NinjaTrader. See [TERMS.md](TERMS.md).
