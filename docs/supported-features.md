# NinjaView: supported features and limits

NinjaView is an independent, partial Pine v5/v6 implementation; Pine v1–v4 scripts are upgraded to v5 automatically before they run. It runs accessible local source; it does not use TradingView's compiler or your TradingView account. A script loading successfully is not proof of matching calculations.

| Area | Current beta scope |
| --- | --- |
| NinjaView add-on | Separate WebView2 chart, NT market history/streaming, instrument and any 1–1440 minute interval, Pine loading and inputs, chart appearance and open/close timestamp display |
| NinjaView Pine indicator | Standard NT time-based minute charts; chart's primary bars plus a fixed one-minute secondary series; multiple instances, input persistence, custom native graphics |
| Pine | v5/v6 syntax and APIs implemented by this engine: most of the `ta`, `math`, `str`, `array`, `map` and `matrix` namespaces, named arguments, persistent state, objects/methods/enums, `once`, `if`/`switch` expressions, inputs (including `input.enum`, `input.time`, `input.price`) and imports. Pine v1–v4 sources are upgraded automatically. Support remains incomplete |
| Output | Plots in every style (line, step, histogram, columns, area, circles, cross, broken variants), plot offsets, fills, linefills, markers, arrows, candles/bars, lines, boxes, labels, polylines and tables; native typography and exact pixel parity remain approximate |
| Requested data | Same-symbol requests at minute, daily, weekly and monthly timeframes (aggregated from one-minute data), one-minute lower-timeframe data, `gaps_on`, `lookahead_on` and Heikin Ashi tickers. Other symbols, Renko/Kagi/line-break/point-and-figure tickers, and fundamental, economic and footprint data are not supported |
| Live calculation | Developing-bar previews, rollback between updates and confirmation on rollover; consistency tests cover selected scripts and datasets |
| Bar Replay (NinjaView window) | Start from a clicked or random bar; play, pause and step by chart bar or 1/5/15 minutes at 0.5x to 60x. Pine replays without seeing future bars (higher-timeframe requests show the developing bar, as on TradingView). Replay covers the window's loaded history days |
| NinjaTrader indicators (NinjaView window, experimental) | Any installed NinjaTrader indicator from Add Indicator, run on NinjaTrader's own engine against the window's bars, live. Plots and lines, `Draw.*` objects (rectangles, lines, text, fixed-position text, dots, squares, diamonds, triangles, arrows) and the indicator's own `OnRender` painting; extra data series (`AddDataSeries`) load over the chart's days. Not yet: Bar Replay, strategies, colour and other non-basic settings, painting positioned by time. Tested on NinjaTrader 8.1.8.3 |
| History (NinjaView window) | Counts like NinjaTrader's "Days to load": that many trading days before today plus today's session |
| Replay trading | Market, limit and stop orders with take profit and stop loss, from a docked order panel, chart buttons or right-click menu; draggable order lines. Simulated fills on one-minute bars using TradingView's intrabar rule (open→high→low→close if the high is nearer the open, otherwise open→low→high→close), gaps fill at the open, stop before target in the same move, optional commission and slippage. P&L, win rate, profit factor, average R, intrabar drawdown, MAE/MFE; CSV/JSON trade logs |
| Trading (NinjaView window) | Trade the chart on a NinjaTrader account you choose, through NinjaTrader (like Chart Trader). Market, limit and stop orders from the order panel, quick buttons or right-click menu; one take profit and stop loss for the whole position (linked, resized as you add), draggable, with their dollar value; draft limit/stop orders shown on the chart before sending; cancel, Flatten, Reverse. Starts switched off in every window; live accounts labelled LIVE; prices far from the market, stops on the wrong side and typo quantities are refused; contract limits are your broker's. Trading involves substantial risk of loss: try a simulation account first |
| Diagnostics | Local editable report, version, chart/session context, effective inputs and recent events; source excluded by default |

## Restrictions

- Native host rejects tick, range, Renko and daily charts, and rejects Tick Replay. It currently requires minute bars. Separate-panel scripts may require selecting the appropriate panel in NT settings.
- Native plots are custom-rendered, not published NT `Values[]` series. Native Data Box values and strategy-readable output series are not exposed.
- Strategy scripts run as indicators: their plots and drawings appear, but orders and trades are not simulated (position values read as flat). No Pine strategy backtester or automated strategy orders (trading is manual, from the trading panel), TradingView login, protected/invite-only source retrieval, or production alert delivery service.
- Libraries resolve from `PineLibraries/Owner/Library/Version.pine` beside the script first. Missing open-source public libraries are fetched once from TradingView by exact owner/name/version, verified, and cached (SHA-256) under `%LOCALAPPDATA%\NinjaView\PineLibraries`; private or ambiguous libraries must still be supplied locally.
- Pane (oscillator) scripts draw their `force_overlay=true` boxes, lines, labels and shapes on the price panel in both the native indicator and the add-on window. In the native indicator, choose Panel "New panel" when adding a pane script.
- Unsupported language constructs or API overloads can fail compilation or execution. Resource limits apply; expensive scripts and long histories may load slowly. There is no claim of full v5 or v6 coverage.
- During ambiguous DST clock changes the timestamp adapter can reject data; UTC as NT's display timezone avoids ambiguous local timestamps for those datasets.
- Visual equivalence, reconnect behavior and performance across all NT versions/providers remain beta test areas.

## Comparing TradingView and NinjaTrader

Use the same contract, timeframe, session coverage, date range, warm-up history and inputs. Record provider, rollover/merge policy and delayed/live status. NT close-stamped bars are converted internally to Pine open/close timestamps. The add-on's open/close display toggle does not change calculation semantics; the native chart retains NT's axis labels.

Different source OHLCV, volume, session boundaries or history can produce different indicator outputs even when execution is correct. Compare completed bars first and distinguish data differences from engine differences. Do not treat a displaced axis label alone as a shifted signal.

## How it is tested

Each release runs the engine, host and web-interface test suites (700+ automated checks), including realtime rollback of `var`/`varip` state through the live data path, and replays a fixed set of real-world indicators to confirm historical and live updates produce identical results. Selected public scripts are also compared against TradingView on matching data.

These checks are evidence, not a compatibility percentage or a guarantee that any particular script matches TradingView. If a script fails or differs, please [open an issue](https://github.com/nejjie73/NinjaView/issues/new/choose); reports of scripts that work are welcome too.
