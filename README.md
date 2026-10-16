# The Busy Café Paradox ☕

**A café gets busier, but its profit shrinks. Why?** You play the business strategist and change price, staffing, food waste and wait time to find out.

> ⚠️ **All data is fictional.** Pour Decision Café is an invented business. Every figure is illustrative and is not real café data.

**▶ Live demo:** https://santhoshashokkumar.github.io/busy-cafe-paradox/dashboard.html

## What's inside

| File | What it is |
|---|---|
| `index.html` | Interactive web simulator. Works on phones, no install, no server. |
| `busy_cafe_paradox_model.xlsx` | Same model in Excel: scenario dropdown, scoreboard, weekly trend chart, raw data, assumptions. |
| `cafe_raw_data.csv` | 91 days of synthetic daily records, ready for Power BI, Tableau, Qlik or Python. |

## The idea

More orders do not automatically mean more profit. Cutting prices can fill the café, but if staffing doesn't keep up, waits grow, guests get unhappier and the extra sales barely cover the extra cost. Squeezing food waste too hard causes stock-outs. The simulator makes these trade-offs visible.

## How to use

- **Web:** move the four sliders or tap *Grow Sales*, *Protect Profit* or *Delight Customers*. Read the advisor panel, then *Reset to Baseline*.
- **Excel:** open the *Simulator* tab, choose a scenario or edit the yellow cells.
- **Data:** load `cafe_raw_data.csv` into your BI tool of choice. Profit columns can be rebuilt with the formulas below.

## Model (transparent and deterministic)

- Demand = 470 × (6 ÷ price)^1.2
- Capacity = staff hours × 10 orders/hour; wages = hours × $20
- Natural wait = 2 + 7 × (demand ÷ capacity)³ minutes (max 25); the line limit caps the wait and guests beyond it leave
- Happiness = 88 − 3 per wait minute over 4 − 4 per $1 above $6 − stock-out penalty + small staffing bonus (20–98)
- Orders scale by 1 + 0.004 × (happiness − 80), limited to −15% / +10%, and cannot exceed 105% of capacity
- Waste under 10% causes stock-outs: lost orders = 1.2 × (10% − waste)
- Food cost $1.55 per order served plus wasted food; card fees 3%; rent and utilities $650/day

The "AI Business Advisor" is a rule-based explainer that reads the calculated results. No AI model runs inside the app or the workbook.

## Limitations

A teaching model, not a forecast. Coefficients are assumptions, not estimates from real data. The wait calculation uses demand before the happiness effect, a deliberate simplification.

## Built with

Created with [Claude](https://claude.ai) and reviewed by me. 

## License

MIT. See `LICENSE`.
