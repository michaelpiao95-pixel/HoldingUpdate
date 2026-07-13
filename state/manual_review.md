# Manual Review List (quarterly)

Tickers **excluded from automated polling** (`Monitoring = manual` in `holdings.csv`) because
their filings can't be pulled reliably by the automated agent. Review these **by hand once per
quarter** (and after any known reporting date).

**How to review:** go to SEDAR+ (https://www.sedarplus.ca) → search the issuer → download the
latest interim/annual financial statements + MD&A → update the memo in `/memos/{TICKER}/` and the
ticker's entry in `state/last_checked.json` (set `last_earnings_date`, `last_period`, `last_run`).

| Ticker | Company | Why manual | What to pull / notes |
|--------|---------|------------|----------------------|
| ZC  | Zimtu Capital Corp. | No press releases; SEDAR+ bot-walled; company site lags. | Q1 FY2026 interim (period ended **2026-02-28**) likely filed **~2026-04-20** but not retrievable by bot — download FS + MD&A from SEDAR+; updates NAV vs. the FY2025 annual. Then Q2 (May 31), etc. FY ends **Nov 30**. |
| IMI | Ironman International Ltd. | **Management Cease Trade Order** (BCSC, effective 2026-04-30); delayed interim; opaque disclosure. | Check MCTO status; pull the delayed **Q1 FY2026 interim** (period ended 2026-02-28). Next update expected **~2026-08-31**. FY ends **Nov 30**. Figures currently `[UNVERIFIED]`. |
| JTC | JEMTEC Inc. | No earnings press releases; SEDAR+ only; only aggregator data available. | Pull latest interim/annual FS + MD&A from SEDAR+. Confirm fiscal year-end (**~Jul 31**). Tiny but profitable (offender-monitoring tech). |

**Also removed from automated monitoring (not manual — fully dropped):**
- **IIP.UN** (InterRent REIT) — privatized/delisted 2026-07-09 at $13.55/unit cash. Row removed
  from `holdings.csv`; no longer tracked. (Historical memo retained at `memos/IIP.UN/`.)

---
Last manual review: _(none yet — list created 2026-07-13)_
