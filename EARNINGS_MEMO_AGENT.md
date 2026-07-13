# Earnings Memo Agent — Instructions for Claude Code

## Purpose
Monitor the IR (Investor Relations) pages of every company in `holdings.csv`.
Whenever a company reports **new** quarterly/annual earnings, pull the primary
source materials and produce an updated investment memo. Never regenerate a
memo for a quarter that's already been covered — only act on genuinely new
releases.

## Setup (run once)
1. Read `holdings.csv` (columns: Ticker, Company Name, Exchange, Monitoring).
2. Create this folder structure if it doesn't exist:
   ```
   /memos/{TICKER}/                <- one folder per holding
   /memos/{TICKER}/sources/        <- raw press releases, transcripts, slides you pull
   /state/last_checked.json        <- tracks last processed earnings date per ticker
   ```
3. For each ticker, if `state/last_checked.json` has no IR URL saved yet, find
   the official investor relations page (search "<Company Name> investor
   relations" — prefer the company's own domain over third-party aggregators
   like Yahoo Finance or Simply Wall St). Save it to the state file so future
   runs don't need to re-search.

## Monitoring exceptions & filing-source routing
- **Monitoring column.** In automated/unattended runs, only poll rows where
  `Monitoring = auto`. **Skip rows where `Monitoring = manual`** — these are thin-traded
  or cease-trade names whose filings can't be pulled reliably by the bot (e.g., SEDAR+
  anti-bot walls). They live on the quarterly manual-review list in
  `state/manual_review.md`, where a human pulls the filings by hand.
  (Currently manual: **ZC, IMI, JTC**.)
- **Delisted / acquired names are removed from `holdings.csv` entirely** — do not keep a
  "delisted" tombstone row. If a holding is taken private/acquired, drop its row.
  (Removed 2026-07-13: **IIP.UN** — privatized at $13.55/unit, delisted from TSX.)
- **Route the primary filing source by `Exchange`:**
  - `NASDAQ` / `NYSE` / `NYSE American` / `OTC` / `OTCQX` → **SEC EDGAR** (10-Q/10-K/8-K)
    + company IR. Foreign private issuers (e.g., BABA, HYFT) file **6-K/20-F** on EDGAR.
  - `TSX` / `TSXV` / `CSE` → **SEDAR+** (sedarplus.ca) + company IR. SEDAR+ blocks automated
    fetches, so prefer the company's own IR press release / posted PDF; if only SEDAR+ has
    it, that's a signal to route the ticker to manual review.
  - `LSE` (AIM) → **RNS** via LSE/Investegate; reports half-yearly + trading updates.
  - `Euronext Paris` → company IR; reports half-yearly + quarterly sales updates.

## Every time you're run (this is the repeatable step)
For each ticker in `holdings.csv` **with `Monitoring = auto`**:

1. Visit its saved IR URL (or the earnings/press-release/news subpage).
2. Identify the most recent quarterly or annual earnings release date.
3. Compare it to `state/last_checked.json[TICKER].last_earnings_date`.
   - **If unchanged**: skip this company. Log "no new earnings" and move on.
   - **If new**: proceed to step 4.
4. Pull primary sources for that release, in order of preference:
   - Official press release / earnings release PDF
   - Earnings call transcript (if posted, or via a transcript aggregator)
   - Investor presentation / slide deck
   - 10-Q / 10-K or equivalent (6-K, MD&A, interim financials for
     non-US/foreign private issuers) from SEC EDGAR / SEDAR+ / company site
   Save whatever you pull into `/memos/{TICKER}/sources/{date}_*`.
5. Extract the numbers you'll need before writing anything:
   - Revenue, YoY and QoQ growth
   - EPS (GAAP and adjusted/non-GAAP if both reported), vs. consensus if
     stated in the release
   - Margins (gross, operating, EBITDA — whichever the company reports)
   - Segment-level detail if the company breaks out segments
   - Balance sheet highlights: cash, debt, net debt, buybacks, dividend
   - Guidance: what management said for next quarter/year, and how it
     compares to prior guidance
   - Management commentary: 2-3 direct quotes or paraphrases on strategy,
     headwinds, tailwinds
6. Write the memo (see format below) to
   `/memos/{TICKER}/{TICKER}_{YYYY-MM-DD}_memo.md`.
7. Update `state/last_checked.json[TICKER]` with the new earnings date and a
   timestamp of when you last ran.
8. Log a one-line summary to `/state/run_log.md` (ticker, date found, memo
   path, any sources you couldn't access).

At the end, print a short summary: how many tickers had new earnings, how
many memos were written, and any tickers you couldn't find/reach (e.g. thin
IR pages for small-cap TSXV/OTC names — flag these so I can point you to the
right source manually).

## Memo format
Use this structure for every memo. Flag anything you couldn't verify from a
primary source as **[EST]** (your own estimate) or **[UNVERIFIED]** — never
present an unsourced number as fact. Cite the source document/date for every
key figure.

```
# {Company Name} ({TICKER}) — Earnings Memo
Period: Qx FY{yyyy} | Report Date: {date} | Prepared: {today's date}

## 1. Snapshot
- Revenue: $X (YoY +/-X%, QoQ +/-X%) — source: [press release]
- EPS: GAAP $X | Adjusted $X — vs. prior quarter $X
- One-line takeaway: [beat/miss/inline] on [revenue/EPS], guidance [raised/
  cut/maintained]

## 2. What happened this quarter
2-4 short paragraphs: results vs. prior quarter and prior guidance, key
drivers (segment/product/geography), anything unusual or one-time.

## 3. Guidance & management commentary
What management said about next quarter/year. Direct read on tone
(confident, cautious, defensive). Note any strategic shifts (M&A,
capital allocation, restructuring, leadership changes).

## 4. Balance sheet & capital allocation
Cash, debt, net debt/EBITDA if calculable, buybacks, dividends, any
covenant or liquidity flags.

## 5. Thesis check
- Did this quarter support, weaken, or not change the investment thesis?
- Any new risks introduced this quarter?
- Valuation context if easily available (P/E, EV/EBITDA vs. history — mark
  [EST] if calculated rather than sourced)

## 6. Watch items for next quarter
2-3 specific things to track next release.

## Sources
List every document used with links/dates.
```

## Rules
- Always work from primary sources (company IR site, SEC/SEDAR filings,
  official press releases) over secondary aggregators. Secondary sources are
  fine as a fallback for thin small-cap coverage, but flag them as such.
- Never fabricate a number. If you can't find something, write
  "[not disclosed]" rather than guessing.
- Keep tone analytical and neutral — no promotional language.
- For TSXV/OTC micro-caps in this list (GO.U, LTC, HME, MMY, AEP, TMG, RW,
  JTC, IMI, ZC, and similar), IR pages are often sparse — check SEDAR+
  (sedarplus.ca) for filings if the company site doesn't have a dedicated
  press release archive.
- Keep memos concise — this is a working note for a personal portfolio, not
  a full sell-side initiation report. Aim for something a busy person can
  read in 3-4 minutes.

## How to re-run me
Run this same prompt again any time (I'd suggest weekly, or right after you
know a company you hold has reported). I will only touch companies with a
release newer than what's in `state/last_checked.json`, so re-running is
cheap and safe.
