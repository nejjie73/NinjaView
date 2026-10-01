---
name: Bug report or compatibility result
about: Report a script that fails, renders differently, or works
labels: report
---

# NinjaView beta report

## Summary

- Category: compile / calculation / rendering / performance / installation / successful compatibility test
- Short description:
- NinjaView build ID (from diagnostic report):
- NinjaTrader version:
- Host: add-on / native NinjaView Pine

## Script

- Title and Pine version:
- Public TradingView script URL and author, if available:
- Script revision/date or source hash:
- Unmodified source? If changed, describe changes:
- Imports and exact versions:
- Attach source only if you own it or have permission to share it. Do not include protected or private third-party code without permission.

## Reproduction

1. Chart and script setup:
2. Inputs changed:
3. Action that triggers the issue:
4. How often it occurs; whether it survives reload/restart:

## Expected versus actual

- Expected behavior/value, and how verified:
- Actual behavior/value and complete error message:
- Exact affected candle date/time, timezone, and whether using open or close timestamps:
- Historical/confirmed candle or developing candle:
- Earliest bar where results diverge, if known:

## Data context

- Exact contract/symbol on both platforms (not just the root):
- Interval/bar type:
- Trading-hours/session template; ETH/RTH:
- Platform and exchange timezone:
- History start/end, days loaded and warm-up:
- Provider, delayed/live status and merge/rollover settings:
- NT Break at EOD and Tick Replay settings:
- Did underlying OHLCV match on the affected bars?

## Attachments

- Reviewed diagnostic JSON (remove private paths/values as needed).
- Screenshots showing both results with symbol, timeframe and matching affected bars. Native Data Series settings screenshot if relevant.
- Minimal permitted script or public source link; library files only with permission.
- Optional small OHLCV/reference export, when permitted, to reproduce calculations.

For a successful test, state exactly what you checked: compile only, historical calculation, live rollover, rendering, input persistence, or matching reference values. Include timeframe, inputs and date range; avoid marking the whole script universally compatible based on one view.
