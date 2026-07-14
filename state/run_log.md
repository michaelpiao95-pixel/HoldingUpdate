# Earnings Memo Agent — Run Log

## Run 2026-07-09 (pilot: META, WFC, MTY, HME, ZC)
- META | new earnings Q1 FY2026 (2026-04-29) | memo: memos/META/META_2026-04-29_memo.md | SEC direct fetch 403 → used PRNewswire mirror of same release
- WFC  | new earnings Q1 FY2026 (2026-04-14) | memo: memos/WFC/WFC_2026-04-14_memo.md | official PDF saved but no local pdftoppm to text-extract; headline via release, capital/buyback detail via slide summary [slides]. Q2 reports 2026-07-14.
- MTY  | new earnings Q1 FY2026 (2026-04-10, qtr ended 2026-02-28) | memo: memos/MTY/MTY_2026-04-10_memo.md | primary via GlobeNewswire release. Q2 FY2026 expected ~mid-July 2026.
- HME  | new earnings Q1 2026 (2026-05-13, qtr ended 2026-03-31) | memo: memos/HME/HME_2026-05-13_memo.md | primary via company IR press release (good disclosure for a TSXV name). Net income not captured; AFF/netback used.
- ZC   | latest = FY2025 annual (year ended 2025-11-30, MD&A eff. 2026-03-26) | memo: memos/ZC/ZC_2026-03-26_memo.md | no press releases; pulled MD&A+FS PDFs from company site, text-extracted via local pdftotext. FLAG: Q1 FY2026 interim (Feb 28 2026) not on site — needs SEDAR+ manual check.

## Run 2026-07-11 (full run, remaining 35 tickers — Batch 1)
- BAC  | Q1 FY2026 (2026-04-15) | memo: memos/BAC/BAC_2026-04-15_memo.md | PRIMARY: presentation PDF downloaded via curl + pdftotext. Beat; NII guide raised.
- AXP  | Q1 FY2026 (2026-04-23) | memo: memos/AXP/AXP_2026-04-23_memo.md | PRIMARY: release PDF via curl + pdftotext. Guidance reaffirmed. (CET1/buyback $ not in release text — noted.)
- EBAY | Q1 FY2026 (2026-04-29) | memo: memos/EBAY/EBAY_2026-04-29_memo.md | PRIMARY: release PDF via curl + pdftotext. GMV +18%, margins compressed.
- BABA | March Qtr FY2026 (2026-05-12) | memo: memos/BABA/BABA_2026-05-12_memo.md | PRIMARY: results PDF via curl + pdftotext. Investment-mode qtr; adj EBITA -84%, FCF negative.
- STLA | Q1 FY2026 (2026-04-30) | memo: memos/STLA/STLA_2026-04-30_memo.md | PRIMARY: official press-release page (PDF link served HTML). Return to thin profit; FCF -€1.9B.

## Run 2026-07-11 — Batch 2
- RIG  | Q1 FY2026 (2026-05-04) | memo: memos/RIG/RIG_2026-05-04_memo.md | PRIMARY: deepwater.com release (WebFetch). Swing to GAAP profit; adj loss. Backlog $7.1B.
- SD   | Q1 FY2026 (2026-05-06) | memo: memos/SD/SD_2026-05-06_memo.md | SECONDARY: SEC 8-K blocked; figures via release summaries (stocktitan/minichart). Div raised + special.
- SRG  | Q1 FY2026 (2026-05-13) | memo: memos/SRG/SRG_2026-05-13_memo.md | Businesswire + 10-Q summaries. GOING CONCERN flag ($50M loan due 2026-07-31). Liquidation est is 3rd-party [UNVERIFIED].
- BHM  | Q1 FY2026 (2026-05-07) | memo: memos/BHM/BHM_2026-05-07_memo.md | SECONDARY: SEC 8-K/10-Q blocked; figures via summaries. NAV/FFO not captured — FLAG for next run.
- GNE  | Q1 FY2026 (2026-05-13) | memo: memos/GNE/GNE_2026-05-13_memo.md | SECONDARY: SEC 8-K blocked; figures via summaries. FY guidance CUT.

## Run 2026-07-11/13 — Batch 3
- NC   | Q1 FY2026 (2026-05-05) | memo: memos/NC/NC_2026-05-05_memo.md | PRIMARY (PRNewswire mirror of 8-K). Profit +80% on margin/cost.
- MOV  | Q1 FY2027 (2026-05-27, qtr ended 2026-04-30) | memo: memos/MOV/MOV_2026-05-27_memo.md | PRIMARY (Businesswire). FY ends Jan 31. Recovery qtr; div raised.
- B    | Q1 FY2026 (2026-05-11) | memo: memos/B/B_2026-05-11_memo.md | PRIMARY: PDF via curl + pdftotext. Beat; new $3.0B buyback.
- AAUC | Q1 FY2026 (2026-05-14) | memo: memos/AAUC/AAUC_2026-05-14_memo.md | PRIMARY (GlobeNewswire). Zijin Gold acquisition pending — deal-driven. GAAP loss vs adj profit gap [UNVERIFIED driver].
- VLE  | Q1 FY2026 (2026-05-13) | memo: memos/VLE/VLE_2026-05-13_memo.md | PRIMARY (company release). Lifting-timing distortion; net cash US$261.6M.

## Run 2026-07-13 — Batch 4
- IWG    | Q1 FY2026 trading update (~2026-05-13) | memo: memos/IWG/IWG_2026-05-13_memo.md | LSE RNS; revenue-only TU. Asset-light fees +41%. FY guide maintained. [Q1 date approximate]
- TIG    | FY2025 results + 2026 YTD TU (~2026-06) | memo: memos/TIG/TIG_2026-06_memo.md | AIM RNS. FY25 losses on $41.7M impairments; DIS/Comparison growing. DIS-disposal review live. [dates approximate]
- FRVIA  | Q1 FY2026 sales update (2026-04-24) | memo: memos/FRVIA/FRVIA_2026-04-24_memo.md | PRIMARY: Forvia sales PDF/press release. Sales-only update; guidance reaffirmed.
- IIP.UN | Q1 FY2026 (2026-05-04) | memo: memos/IIP.UN/IIP.UN_2026-05-04_memo.md | ⚠ PRIVATIZATION COMPLETED 2026-07-09 ($13.55/unit cash, CLV+GIC). DELISTED — remove from monitoring.
- FOOD   | Q2 FY2026 (2026-04-21, 13wks to 2026-03-07) | memo: memos/FOOD/FOOD_2026-04-21_memo.md | PRIMARY (GlobeNewswire). CFIA suspension; back to EBITDA/FCF loss.

## Run 2026-07-13 — Batch 5
- SEC   | Q1 FY2026 (2026-05-15) | memo: memos/SEC/SEC_2026-05-15_memo.md | PRIMARY: Senvest PDF via curl + pdftotext. Net loss much smaller than Q1'25. BVPS extraction ambiguous — flagged [EST].
- OTCM  | Q1 FY2026 (~2026-05-07) | memo: memos/OTCM/OTCM_2026-05-07_memo.md | Release mirrors. Rev +14%. Adj-EPS $0.93 [UNVERIFIED]. [date approximate]
- RET.A | Q1 FY2027 (2026-06-16, qtr ended 2026-05-02) | memo: memos/RET.A/RET.A_2026-06-16_memo.md | PRIMARY (mediaroom). Seasonal loss narrowed.
- GO.U  | Q1 FY2026 (~2026-05-13) | memo: memos/GO.U/GO.U_2026-05-13_memo.md | PRIMARY (Newswire). Beat IPO forecast; 4 acquisitions. [date approximate]
- URL   | Q1 FY2026 (2026-06-02) | memo: memos/URL/URL_2026-06-02_memo.md | PRIMARY (PRNewswire). Record revenue; diversifying.

## Run 2026-07-13 — Batch 6 (TSXV micro-caps)
- MMY | Q3 FY2026 (2026-06-01, qtr ended 2026-03-31) | memo: memos/MMY/MMY_2026-06-01_memo.md | PRIMARY (GlobeNewswire + WebFetch). Strong gold profit; ~US$102M cash. FY ends Jun 30.
- LTC | Q1 FY2026 (2026-04-27) | memo: memos/LTC/LTC_2026-04-27_memo.md | PRIMARY (Newsfile). Early-stage oil ramp; detailed Q1 financials [not captured].
- AEP | Q1 FY2026 (~2026-05-28) | memo: memos/AEP/AEP_2026-05-28_memo.md | PRIMARY (Newswire). Weak seasonal Q1; robotic facility July. [date approximate]
- TMG | Q3 FY2026 (~2026-04, qtr ended ~2026-02-28) | memo: memos/TMG/TMG_2026-04_memo.md | Company/SEDAR+; Q3 profit detail [not captured]. FY ends May 31. [date approximate]
- GVC | Q1 FY2026 (2026-05-07) | memo: memos/GVC/GVC_2026-05-07_memo.md | PRIMARY (GlobeNewswire). Print-to-data pivot; EBITDA positive.

## Run 2026-07-13 — Batch 7 (thinnest OTC/TSXV)
- RW   | Q1 FY2026 (2026-05-27) | memo: memos/RW/RW_2026-05-27_memo.md | PRIMARY (renoworks.com). SaaS transition; recurring +36%.
- IDWM | Q2 FY2026 (~2026-06-15, qtr ended 2026-04-30) | memo: memos/IDWM/IDWM_2026-06-15_memo.md | SEC filing + trade-press. Turnaround near breakeven. [date approximate]
- HYFT | Q3 FY2026 (2026-03-12, qtr ended 2026-01-31) | memo: memos/HYFT/HYFT_2026-03-12_memo.md | PRIMARY (Businesswire/6-K). ⚠ Trades NASDAQ not OTC (csv discrepancy); rebranded from ImmunoPrecise. FY26 results due 2026-07-22.
- IMI  | FY2025 annual (filed 2026-04-13); Q1 interim DELAYED | memo: memos/IMI/IMI_2026-04-13_memo.md | ⚠ MANAGEMENT CEASE TRADE ORDER (2026-04-30). Figures [UNVERIFIED]. MANUAL SEDAR+ check.
- JTC  | latest UNVERIFIED | memo: memos/JTC/JTC_2026-status_memo.md | ⚠ FLAG: no press releases, SEDAR+ only. Aggregator figures [UNVERIFIED]. MANUAL SEDAR+ check.

### FULL-RUN SUMMARY (2026-07-11 to 2026-07-13): 35 remaining tickers processed, 35 memos written (40/40 holdings now covered incl. the 5 pilot).
Manual-follow-up flags: JTC & IMI (thin/cease-trade — verify on SEDAR+); HYFT (NASDAQ vs csv OTC; FY-end results 2026-07-22); IIP.UN (privatized/delisted 2026-07-09 — remove from monitoring). Corporate events: AAUC (Zijin acquisition pending), IIP.UN (privatization completed), SRG (going concern). Not-yet-reported (skipped, no new earnings): WFC Q2 (2026-07-14), HYFT FY (2026-07-22), MTY Q2, plus half-yearly reporters (IWG/FRVIA/STLA H1 ~late July/Aug).

## Step 4 — ZC SEDAR+ follow-up (2026-07-13)
- Attempted to close the ZC Q1 FY2026 interim gap. Findings: interim (period ended 2026-02-28) almost certainly filed ~2026-04-20 (per investing.com "latest earnings release date"), but (a) still not on zimtu.com, (b) SEDAR+ (sedarplus.ca) redirects bots to a ShieldSquare/PerfDrive CAPTCHA wall — not fetchable, (c) aggregators carry only annual data. Updated ZC memo + state with revised flag: MANUAL SEDAR+ download required. Memo remains on FY2025 audited annual pending retrieval. No material change to the memo's substance (Zimtu = MTM of portfolio; interim would update NAV).

### Quality review pass (2026-07-09):
- WFC: upgraded from secondary→PRIMARY. Text-extracted the saved release PDF with pdftotext; confirmed ROE 12.2%/ROTCE 14.5%/efficiency 67%/CET1 10.3%/$4.0B buyback. Corrected a misattributed CEO quote (the "operational leverage" line was a secondary paraphrase, not in the release) → replaced with verbatim Scharf quote. Added EPS +15% YoY ($1.60 vs $1.39) and the $135M/$0.04 discrete tax benefit that was in the headline EPS.
- MTY: clarified that the $605.1M "long-term debt" IS the revolver draw (not additive); net debt ~$549M, ~2.3x [EST].
- META, HME, ZC: numbers reconciled internally (EPS×shares ≈ net income; netback×volume ≈ total; NAV math); flags appropriate; no corrections needed.

### Pilot summary (2026-07-09): 5 tickers checked, 5 memos written (META, WFC, MTY, HME all had new quarterly earnings; ZC latest was FY2025 annual). Tooling notes: SEC.gov + streetinsider return 403 to WebFetch (use official IR/newswire mirrors); local env has pdftotext (mingw64) but NOT pdftoppm, so Read-on-PDF fails — use `pdftotext -layout` via Bash for PDF filings. Open follow-up: verify ZC Q1 FY2026 interim on SEDAR+.

## Run 2026-07-14
- WFC  | Q2 FY2026 (2026-07-14) | memo: memos/WFC/WFC_2026-07-14_memo.md | PRIMARY: press release PDF downloaded via curl + pdftotext; presentation PDF also saved. EPS $2.00 (+25% YoY), ROTCE 17.7%, efficiency ratio 60%, loans +12% YoY, Q3 div raised to $0.50.
- BAC  | Q2 FY2026 (2026-07-14) | memo: memos/BAC/BAC_2026-07-14_memo.md | PRIMARY: investor presentation PDF downloaded via curl + pdftotext. EPS $1.21 (+34% YoY, beat est.), ROTCE 17.0%, NII $16.0B (+9% YoY), FY2026 NII guidance raised to upper end of 6-8%.
- MTY  | Q2 FY2026 (2026-07-10) | memo: memos/MTY/MTY_2026-07-10_memo.md | PRIMARY: GlobeNewswire press release (2026-07-10). Revenue -8.2% YoY, EPS $0.67 (vs $2.49), FCF $32.2M solid; 68 corporate stores to close.

Skipped (no new earnings since last check): META, GO.U, SRG, IWG, EBAY, BABA, AXP, SD, GNE, NC, MOV, TIG, RIG, B, HYFT, STLA, OTCM, IDWM, BHM, FRVIA, AAUC, URL, LTC, FOOD, SEC, VLE, HME, MMY, RET.A, AEP, TMG, RW, GVC (33 tickers).
Skipped (manual monitoring): JTC, IMI, ZC.

Notable non-earnings events:
- SRG: $50M term loan due 2026-07-31 — refinancing discussions ongoing as of Q1; no resolution confirmed by 2026-07-14. URGENT watch.
- VLE: Q2 2026 ops update (2026-07-09) — record revenue US$259.8M, cash US$316.5M, anticipated FCF ~US$100M; full Q2 financials due 2026-08-06.
- AXP: Q2 2026 reports 2026-07-24. EBAY/META: both report 2026-07-29. FRVIA H1: 2026-07-31. HYFT FY2026: 2026-07-22.

### Run 2026-07-14 Summary: 36 auto tickers checked, 3 new memos written (WFC, BAC, MTY). 33 tickers had no new earnings. 3 manual tickers skipped as designed.
