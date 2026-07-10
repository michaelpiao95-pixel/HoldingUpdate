# Earnings Memo Agent — Run Log

## Run 2026-07-09 (pilot: META, WFC, MTY, HME, ZC)
- META | new earnings Q1 FY2026 (2026-04-29) | memo: memos/META/META_2026-04-29_memo.md | SEC direct fetch 403 → used PRNewswire mirror of same release
- WFC  | new earnings Q1 FY2026 (2026-04-14) | memo: memos/WFC/WFC_2026-04-14_memo.md | official PDF saved but no local pdftoppm to text-extract; headline via release, capital/buyback detail via slide summary [slides]. Q2 reports 2026-07-14.
- MTY  | new earnings Q1 FY2026 (2026-04-10, qtr ended 2026-02-28) | memo: memos/MTY/MTY_2026-04-10_memo.md | primary via GlobeNewswire release. Q2 FY2026 expected ~mid-July 2026.
- HME  | new earnings Q1 2026 (2026-05-13, qtr ended 2026-03-31) | memo: memos/HME/HME_2026-05-13_memo.md | primary via company IR press release (good disclosure for a TSXV name). Net income not captured; AFF/netback used.
- ZC   | latest = FY2025 annual (year ended 2025-11-30, MD&A eff. 2026-03-26) | memo: memos/ZC/ZC_2026-03-26_memo.md | no press releases; pulled MD&A+FS PDFs from company site, text-extracted via local pdftotext. FLAG: Q1 FY2026 interim (Feb 28 2026) not on site — needs SEDAR+ manual check.

### Quality review pass (2026-07-09):
- WFC: upgraded from secondary→PRIMARY. Text-extracted the saved release PDF with pdftotext; confirmed ROE 12.2%/ROTCE 14.5%/efficiency 67%/CET1 10.3%/$4.0B buyback. Corrected a misattributed CEO quote (the "operational leverage" line was a secondary paraphrase, not in the release) → replaced with verbatim Scharf quote. Added EPS +15% YoY ($1.60 vs $1.39) and the $135M/$0.04 discrete tax benefit that was in the headline EPS.
- MTY: clarified that the $605.1M "long-term debt" IS the revolver draw (not additive); net debt ~$549M, ~2.3x [EST].
- META, HME, ZC: numbers reconciled internally (EPS×shares ≈ net income; netback×volume ≈ total; NAV math); flags appropriate; no corrections needed.

### Pilot summary (2026-07-09): 5 tickers checked, 5 memos written (META, WFC, MTY, HME all had new quarterly earnings; ZC latest was FY2025 annual). Tooling notes: SEC.gov + streetinsider return 403 to WebFetch (use official IR/newswire mirrors); local env has pdftotext (mingw64) but NOT pdftoppm, so Read-on-PDF fails — use `pdftotext -layout` via Bash for PDF filings. Open follow-up: verify ZC Q1 FY2026 interim on SEDAR+.
