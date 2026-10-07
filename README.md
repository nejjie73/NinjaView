# NinjaView: TradingView Pine Script indicators in NinjaTrader 8

**Run TradingView Pine Script indicators inside NinjaTrader 8, with no conversion to NinjaScript.**

NinjaView lets you load a `.pine` indicator file and see it on your NinjaTrader charts, calculated live from NinjaTrader's own data. It works two ways:

- **NinjaView Pine indicator.** Add it to any NinjaTrader minute chart and point it at a Pine file. Plots, fills, levels, shapes, boxes, labels, lines and tables draw natively on the chart, and update tick by tick.
- **NinjaView window.** A standalone chart (New > NinjaView) with NinjaTrader market data and the same Pine engine. It draws the same plots, labels and tables as the indicator, on any minute interval from 1 to 1440, and has TradingView-style **Bar Replay** with paper trading.

**[Download the latest release](https://github.com/nejjie73/NinjaView/releases/latest)** · [Install guide](docs/install.md) · [What's supported](docs/supported-features.md) · [Report a script](https://github.com/nejjie73/NinjaView/issues/new/choose)

## Highlights

- Pine v5 and v6: persistent `var`/`varip` state with correct realtime rollback, user types, methods, enums, arrays, maps, matrices, named arguments, tuples, switch/if/for/while, and most `ta.*`, `math.*`, `str.*` and drawing functions.
- Older Pine v1–v4 scripts (many classic public indicators) are upgraded automatically.
- Every plot style (line, step, histogram, columns, area, circles, cross), linefills, and higher-timeframe `request.security`.
- Separate-panel (oscillator) scripts get their own panel; `force_overlay` objects draw on the price chart.
- Script inputs appear in NinjaTrader's indicator settings and are saved with your workspace.
- Public libraries (`import Owner/Library/Version`) are fetched once from TradingView by exact version, verified and cached. Local copies always take priority.
- **Your NinjaTrader indicators in the NinjaView window** (experimental): Add Indicator lists every installed NinjaTrader indicator next to your Pine scripts. They run on NinjaTrader's own engine with their plots, drawings and on-chart painting, and their settings are editable in NinjaView.
- **Bar Replay and paper trading** in the NinjaView window: start from any bar (or a random one), play the market forward with your Pine indicator, and trade it with a TradingView-style order panel, quick buy/sell buttons and a right-click menu. Results show P&L, win rate, profit factor and drawdown; trade logs save as CSV. Fills are simulated on one-minute bars.
- No live orders, no account access, no TradingView login.

## Requirements

- NinjaTrader 8 (tested on 8.1.8.3), Windows x64
- Time-based minute charts (tick, range, Renko and daily charts are not supported yet)

## Limits

NinjaView is an independent, partial implementation of Pine. Some scripts will not compile yet, `strategy()` scripts show their plots and drawings without backtesting their orders, replay trading is simulated on one-minute bars, and a script that loads may still calculate differently from TradingView. Check results against TradingView before relying on them. See [what's supported](docs/supported-features.md) for details.

If a script fails, [open an issue](https://github.com/nejjie73/NinjaView/issues/new/choose) with the error message and a link to the public script.

## License key

To enter a license key, use **Control Center > New > NinjaView** or the NinjaView Pine indicator's **License key** setting.

No warranty; not financial advice. Not affiliated with TradingView or NinjaTrader. See [TERMS.md](TERMS.md).
