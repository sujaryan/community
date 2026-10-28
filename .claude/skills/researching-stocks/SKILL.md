---
name: "researching-stocks"
description: "Research and analyze mainboard IPOs and listed stocks for investment. ALWAYS delivers two angles for IPOs: short-term (listing day) AND long-term (business quality). Triggers on \"should I buy X\", \"analyze this IPO\", \"is X a good investment\", \"help me research X\", RHP/DRHP uploads, or any request to assess a company/IPO. Covers mainboard IPO assessment (anchor allocation, P/E vs peers, institutional demand, OFS analysis) and full long-term research funnels with India/NSE-BSE focus. Frames output as education, never personalized financial advice."
---

# Researching Stocks

This skill turns a vague "should I buy this?" into a disciplined research process. The single most common and expensive retail mistake is judging price before understanding the business — so this workflow deliberately delays valuation until the business, industry, and financials are understood.

**Scope: Mainboard IPOs (NSE+BSE) and listed stocks only.** No SME IPOs (NSE Emerge / BSE SME). If the user uploads an SME RHP, flag it as out of scope and explain why mainboard-only.

## Operating principles

1. **This is education, never personalized advice.** Analyze the business, surface strengths and risks, and assess whether valuation looks stretched or sane — but the buy/sell/hold call belongs to the user (or a SEBI-registered adviser). Never give a clean "yes, buy it." State this framing naturally, not as a disclaimer dump.
2. **Search before asserting.** Prices, holders, ratings, NPAs, and "latest" anything change constantly and post-date training. For any present-day figure (current price, market cap, latest results, who's selling in an IPO), use web search and prefer primary sources (RHP/DRHP, exchange filings, company IR, rating rationales) over aggregators. Treat surprising numbers from a single source skeptically and cross-check.
3. **Don't look at the price chart first.** It anchors judgment. Understand the business and what it's worth, *then* compare to price.
4. **Match the lens to the sector.** A bank/NBFC is analyzed on asset quality and capital, not EV/EBITDA. Applying the wrong lens produces confident nonsense. See `references/sector-lenses.md`.
5. **Cash flow is the lie detector.** When reported profit and operating cash flow diverge over years, that's the earliest reliable red flag. Always reconcile them.
6. **Fetch live data from Groww before making any suggestion on a listed stock.** When the user asks for a suggestion, recommendation, or "should I buy/hold/sell" on any listed stock, always pull live price, OHLC, and recent historical data from the Groww API (Section C) before forming a view. Live price anchors the valuation; historical trend context is essential. Ask for the Groww token if it has not been provided in this conversation.
7. **The Commodity P/E Trap — cyclicals are valued backwards.** For commodity and cyclical stocks (metals, mining, chemicals, oil & gas, sugar, shipping), a low P/E often signals *peak* earnings and danger, not a buying opportunity. A high P/E (or losses) at the bottom of the cycle is often the best time to buy. Never apply compounder logic ("low P/E = cheap") to a cyclical without first asking: where are we in the earnings cycle? See "Cyclical / Commodity Stock Valuation" section below.

---

## Cyclical / Commodity Stock Valuation

This is the single most common and expensive mistake in commodity investing: treating a low P/E as cheap. For compounders (HDFC Bank, TCS, Asian Paints), a low P/E relative to history *is* a buying signal because their earnings are stable or growing. For cyclicals, it's often a sell signal.

**Why cyclical P/E works backwards:**
- At cycle peak: earnings are at all-time highs → P/E looks low (say 8x) → market is pricing in earnings falling → the stock looks "cheap" but is actually expensive relative to normalized earnings
- At cycle trough: earnings are near zero or negative → P/E is infinite or 100x+ → market is pricing in the eventual recovery → the stock looks "expensive" but is actually cheap relative to where earnings will go

**The test before applying any P/E-based valuation to a cyclical:**
1. Where is the commodity price (LME aluminium, steel HRC, crude oil, sugar, freight rates) relative to its 10-year range?
2. Are current margins at historical highs, lows, or mid-cycle?
3. Is the industry at peak or trough capacity utilization?
4. If current earnings halved, what would the P/E be? If it would be >20x, the "low P/E" is an illusion.

**What to use instead of trailing P/E for cyclicals:**
- **P/B (Price to Book)** — book value is more stable across cycles; compare to historical P/B range
- **EV/EBITDA on mid-cycle earnings** — normalize EBITDA to the 5-year or 10-year average, not the latest year
- **Replacement cost** — what would it cost to build this capacity from scratch? If market cap < replacement cost, there's a floor
- **Dividend yield at cycle peaks** — high dividend yield at peak earnings often means the dividend gets cut when earnings fall

**NALCO case study (Oct 2026):**
- P/E 8.6x on Rs 6,751 Cr profit looked cheap vs peers
- But LME aluminium was near multi-year highs, margins were at cycle peak (EBITDA margin ~30%+), and ROCE was 39.6% (vs 10-year average ~15%)
- If aluminium corrected and earnings halved, the effective P/E would be ~17x — not cheap at all
- The market wasn't ignoring NALCO; it was correctly pricing cyclical peak earnings at a low multiple
- The investment question becomes: will the 0.5 MTPA smelter expansion create a structurally higher earnings floor? That expansion kicker is what separates this from a pure cycle play
- FIIs had actually doubled their holding to 22% — smart money was already positioned, but at a disciplined multiple

**Key rule: For cyclicals, buy on high P/E (trough earnings), sell on low P/E (peak earnings).** This is the inverse of everything that works for quality compounders.

**PSU discount compounds the effect:** PSU cyclicals like NALCO, Coal India, NMDC get a double discount — cyclical peak earnings compression PLUS the structural PSU governance/efficiency discount. This makes them look absurdly cheap on paper, but both discounts are rational and persistent.

---

## MANDATORY: Always deliver BOTH angles for IPOs

**Every mainboard IPO analysis must present two distinct verdicts:**

1. **Short-term (listing day)**: Should you apply for listing gains? Use the Mainboard IPO Assessment (Section B). This is about institutional demand (anchor allocation, QIB subscription), valuation vs peers, GMP signal, and whether you'll make money in the first week.

2. **Long-term (business quality)**: Is this a business worth owning for 1-3+ years? Use a compressed version of the Section A research funnel — business model clarity, industry tailwinds, financial health (margins, ROCE, D/E, OCF), valuation vs peers, and key risks. This answers: if you get allotted and the listing is flat or negative, should you hold or cut?

**These two verdicts can diverge — and that's the whole point:**
- Behari Lal Engineering: CAUTIOUS for listing (69% OFS, promoter WACA ₹1-3), but SOLID long-term (27% ROCE, 0.06x D/E, P/E 18.6x vs 31x peer avg, margin expansion story).

**The divergence tells the user what to do**: If both say skip → stay away completely. If listing = skip but long-term = interesting → watch for post-listing dip entry. If listing = apply but long-term = weak → sell on listing, don't hold.

---

# SECTION A: The long-term research funnel — follow in order

Resist jumping ahead. Each stage feeds the next.

### Step 1 — Understand the business
Answer in plain English: What does it sell? Who pays, and why? How does revenue become profit (the unit economics)? Write a 2-3 sentence description a 12-year-old would follow. If you can't, you don't understand it well enough to judge it yet — keep reading the "Our Business" / MD&A sections of the annual report or RHP.

The label is not the engine. "Fintech" can mean a commission-earning distribution platform (Turtlemint) or a spread-earning lender (Kissht) — utterly different businesses needing different analysis.

### Step 2 — Map the industry
Use a five-forces frame: rivalry, new-entrant threat, supplier power, buyer power, substitutes. Estimate the market size, the company's share, and the structural tailwind or headwind. Read DRHP industry-report exhibits *skeptically* — they're commissioned and optimistic. Note regulatory dependence (e.g. IRDAI for insurance, RBI for lenders).

### Step 3 — Analyze the financials *together*
Never read the P&L alone. Pull 5-10 years of all three statements side by side and reconcile them. Profit without cash is suspect; growth not funded by cash must be funded by debt or dilution. Full method, ratios, and forensic red-flag checks: `references/financial-analysis.md`.

### Step 4 — Value the business
Only now form a view on price. Use relative multiples (P/E, P/B, EV/EBITDA, PEG) anchored to genuine peers *and* the stock's own history, sense-checked against simple intrinsic-value thinking and a margin of safety. The question is never "is the P/E low?" but "is the price low relative to the cash this business will durably generate?" Methods and sector nuances: `references/valuation.md`.

**CRITICAL for cyclicals/commodities:** If the stock is in a cyclical sector (metals, mining, oil & gas, chemicals, sugar, shipping, cement), do NOT use trailing P/E as the primary valuation metric. Apply the Cyclical / Commodity Stock Valuation framework above — normalize to mid-cycle earnings, use P/B and replacement cost as anchors, and explicitly state where the company is in its earnings cycle.

### Step 5 — Run a pre-mortem on risks
Assume it's three years later and the position has halved — write down what went wrong. Force the bear case. This counters confirmation bias. Cover business risks, governance/promoter risks, and (for recent listings) IPO-specific risks. See `references/red-flags-and-process.md`.

### Step 6 — Write the thesis
One page: (1) what the business is, (2) why it will do well (2-3 core drivers), (3) the valuation you'd pay and expected return, (4) key risks, (5) **invalidation conditions** — the specific events that would prove the thesis wrong. When price later moves, return to this and ask: did the *business* change, or just the price?

### Compressed long-term assessment (for IPO dual-angle output)
When presenting alongside the listing assessment, compress the long-term view into these bullets:
- **Business**: 1-2 sentence plain-English description
- **Moat/edge**: What protects margins? (niche position, switching costs, scale, regulatory license)
- **Financial health**: ROCE, D/E, OCF/PAT, margin trajectory (improving/stable/declining)
- **Valuation**: P/E vs listed peers, EV/EBITDA if available
- **Key risk**: The single biggest thing that could go wrong
- **Long-term verdict**: BUY ON DIPS / HOLD IF ALLOTTED / EXIT ON LISTING / AVOID

---

# SECTION B: Mainboard IPO Assessment

Mainboard IPOs (NSE+BSE) are institutional-driven markets with deep liquidity. The assessment framework focuses on what drives mainboard listing performance.

## Pre-screening gate

### Gate 0 — Is this actually assessable?
1. **DRHP vs RHP**: If the document is a DRHP, it does NOT have final dates set. You cannot apply yet. Still provide the long-term assessment and flag for re-evaluation when RHP drops.
2. **Confirm mainboard**: Dual NSE+BSE listing, issue size typically >₹200 Cr, top-tier or mid-tier BRLMs, anchor investor allocation present.
3. **Subscription window open?** If the IPO hasn't opened yet, pre-assess all factors except subscription. Flag for re-assessment once Day 1-2 data is available.

## How mainboard IPOs work (key differences from smaller IPOs)

- **QIBs dominate**: 50%+ allocation goes to qualified institutional buyers who typically bid on Day 3. Their participation is the strongest signal.
- **Anchor investors** (T-1 day): 30% of QIB portion allocated to anchors before the IPO opens. Anchor quality and size is visible pre-open and is the earliest institutional confidence signal.
- **Listing day liquidity is deep**: No circuit-lock traps. You can always exit. This means negative listings hurt less (you can cut quickly) but also means GMP can evaporate fast.
- **OFS-heavy structures are common**: Established businesses monetizing promoter stakes. OFS >50% isn't automatically bad — check promoter post-IPO stake and WACA (weighted average cost of acquisition).
- **Subscription multiples are lower**: 5-20x total is good for mainboard (vs 50-100x for smaller IPOs). QIB subscription >10x is strong. Retail subscription matters less.

## The mainboard assessment framework

### Factor 1: Anchor allocation (critical signal)
- **₹100 Cr+ from top-tier MFs/FIIs** (SBI MF, HDFC MF, ICICI Pru, Fidelity, GIC, etc.): Strong positive. These firms do deep due diligence.
- **₹50-100 Cr from reputable institutions**: Positive but moderate.
- **<₹50 Cr or mostly unknown/offshore entities**: Weak signal. Proceed with caution.
- **No anchor allocation**: Red flag for a mainboard IPO. Why couldn't they attract institutions?

### Factor 2: Valuation vs listed peers
- **P/E at 15%+ discount to peer average**: Attractive. Room for re-rating post-listing. (Behari Lal: 18.6x vs peer avg 31.4x — genuine discount)
- **P/E at par with peers**: Fairly priced. Listing gain depends on market sentiment and demand.
- **P/E at premium to peers**: Needs a strong growth story to justify. Higher risk of flat/negative listing.
- **Also check**: EV/EBITDA, P/B (for asset-heavy businesses), PEG ratio if growth is the narrative.

### Factor 3: BRLM (Book Running Lead Manager) quality
- **Top-tier** (Kotak, ICICI Sec, Axis Capital, JM Financial, Emkay, SBI Cap): Reputation at stake. They won't take a terrible deal to market (usually).
- **Mid-tier on mainboard**: Not a red flag by itself but check other factors more carefully.
- **Unknown/tiny BRLMs on a mainboard IPO**: Red flag. Why couldn't they get a reputable banker?

### Factor 4: Issue structure & promoter intent
- **Fresh issue majority (>60%)**: Growth capital. Positive signal — the company needs money to expand.
- **OFS majority (>60%)**: Promoter monetization. Check:
  - **Promoter WACA**: If promoter acquired shares at ₹1-10 and IPO price is ₹300+, they're sitting on massive gains regardless. Not inherently bad but means they're primarily cashing out.
  - **Promoter post-IPO stake**: >50% retained = still aligned with the business. <30% retained = potential dump, especially if WACA is near-zero.
  - **PE/VC exit**: If PE investors are selling, check their entry date. If they entered <2 years ago, they're flipping too — weaker signal.
- **Mixed (40-60% fresh + OFS)**: Balanced. Usually fine.

### Factor 5: Financial quality (the fundamentals filter)
- **ROCE >20%**: Institutional magnet. These tend to get re-rated post-listing as more analysts initiate coverage.
- **D/E <0.5x**: Clean balance sheet. Low refinancing risk.
- **OCF/PAT >60%**: Real cash earnings, not accounting profit. Cross-check with working capital trends.
- **Margin trajectory**: Improving margins over 3 years = operating leverage narrative = premium valuation justified.
- **Revenue CAGR**: >15% over 3 years for growth story. <10% needs margin expansion or re-rating thesis.

### Factor 6: Market timing & sentiment
- **GMP (Grey Market Premium)**: Mainboard GMP of +15-25% with strong anchor = reasonably reliable. But GMP can vanish overnight with market corrections.
- **Market conditions**: IPOs launched in bull markets get 20-30% premium just on sentiment. Same IPO in a correction might list flat.
- **Sector narrative**: Hot sectors (defence, EV, renewables, AI/tech, specialty chemicals) attract retail enthusiasm and higher subscription.

### Red flags (any one = seriously reconsider)
- No anchor allocation or very weak anchor participation
- Promoter exiting to <25% post-IPO stake with near-zero WACA
- P/E at >20% premium to peer average without superior growth
- Declining revenue or margins over 3 years
- Negative OCF in latest year despite reported profits
- Pre-IPO bonus dilution in last 12 months
- Heavy related-party transactions (>20% of revenue)
- SEBI complaints, auditor resignations, or qualified audit opinions
- Customer concentration >40% from single client
- Revenue spike >100% in latest year with declining OCF (manufactured growth)

## Mainboard verdict framework

| Signal combination | Verdict |
|---|---|
| Anchor >₹100Cr + P/E discount to peers + ROCE >20% + QIB sub >10x | **STRONG APPLY** — apply for max retail lots |
| Anchor >₹50Cr + P/E at par or slight discount + decent financials + sub >5x | **APPLY** — apply for 1-2 lots |
| Some positives but OFS-heavy or tepid subscription or premium valuation | **CAUTIOUS APPLY** — apply half, be ready to exit on listing |
| Weak anchor + premium valuation + declining metrics | **SKIP** |
| Any red flag triggered | **SKIP** unless overwhelmingly strong on other factors |

## Post-listing discipline (mainboard)
- Listing gain >20%: Consider selling 50-100% on listing day (lock in gains, re-evaluate for re-entry)
- Listing gain 5-20%: Hold 1-2 weeks if long-term thesis is strong. Sell if long-term = weak.
- Listing flat to -5%: If long-term = solid, hold. This is often the best entry for long-term holders.
- Listing <-10%: Cut if long-term = weak. Hold only if thesis is truly strong and decline is market-driven, not company-specific.

---

---

# SECTION C: Live Market Data (Groww API)

Use this section whenever the user asks for a suggestion, recommendation, or price-based view on any **listed stock**. Live data makes valuation concrete — replace "peer average P/E is 25x" with "HDFCBANK is currently trading at ₹1,842, down 4% from its 52-week high, with the 30-day trend showing consolidation."

## Authentication

All Groww API calls require:
```
Authorization: Bearer {GROWW_TOKEN}
Accept: application/json
X-API-VERSION: 1.0
```

The token is a daily session JWT. If the user has not provided their Groww token in this conversation, ask: *"To pull live prices from your Groww account, I need your Groww API token — you can find it in Groww → Settings → Trading APIs."* Do not proceed without it.

## What to fetch and when

### For a single listed stock (suggestion / hold-or-sell analysis)

**Step 1 — Full quote** (live snapshot: price, OHLC, 52-week range, volume, market depth)
```
GET https://api.groww.in/v1/live-data/quote
  ?exchange=NSE
  &segment=CASH
  &trading_symbol={SYMBOL}
```
Key fields to extract: `last_price`, `open`, `high`, `low`, `close`, `volume`, `week_52_high`, `week_52_low`, `upper_circuit`, `lower_circuit`

**Step 2 — Historical candles** (daily, last 180 days — price trend and momentum)
```
GET https://api.groww.in/v1/historical/candles
  ?exchange=NSE
  &segment=CASH
  &groww_symbol={GROWW_SYMBOL}
  &start_time={DATE_180_DAYS_AGO}
  &end_time={TODAY}
  &candle_interval=1day
```
Response format: `[timestamp, open, high, low, close, volume, open_interest]`

Use the 180-day candle history to assess:
- **Price trend**: Is it in an uptrend, downtrend, or range-bound?
- **Distance from 52-week high/low**: Context for entry timing
- **Recent volume pattern**: Volume expanding on up-days = accumulation; on down-days = distribution

**Note on `groww_symbol`**: This is Groww's internal symbol identifier, different from `trading_symbol`. If not known, fall back to the deprecated range endpoint which accepts `trading_symbol` directly:
```
GET https://api.groww.in/v1/historical/candle/range
  ?exchange=NSE
  &segment=CASH
  &trading_symbol={SYMBOL}
  &start_time={DATE}
  &end_time={DATE}
  &interval_in_minutes=1440
```

### For multiple stocks (portfolio review / peer comparison for IPO)

**Bulk LTP** — up to 50 symbols in one call
```
GET https://api.groww.in/v1/live-data/ltp
  ?segment=CASH
  &exchange_symbols=NSE_{SYMBOL1},NSE_{SYMBOL2},...
```
Use this for: comparing live prices of IPO peers, pulling current prices of all portfolio holdings at once.

**Bulk OHLC** — same structure as LTP but returns O/H/L/C
```
GET https://api.groww.in/v1/live-data/ohlc
  ?segment=CASH
  &exchange_symbols=NSE_{SYMBOL1},NSE_{SYMBOL2},...
```

## How to use live data in the analysis

| What you fetched | How to use it |
|---|---|
| `last_price` | Anchor the current valuation — compute live P/E = `last_price / (annual_EPS)` |
| `week_52_high / week_52_low` | Assess where price sits in its range: near 52-week high = momentum but risk of pullback; near 52-week low = beaten-down but check if thesis is broken |
| 180-day candle trend | Describe price behavior plainly: "HDFCBANK has been consolidating between ₹1,750-1,900 for 3 months after a 15% rally" |
| Volume pattern | Rising volume on recent up-days suggests institutional accumulation |
| Bulk LTP for peers | Compute live P/E for each peer → compare to IPO's offer price P/E |

## Output block for listed stocks (add after valuation section)

```
━━ LIVE MARKET DATA (Groww) ━━
Price: ₹[last_price] | Today: O [open] H [high] L [low]
52-week range: ₹[week_52_low] — ₹[week_52_high] | Currently at [X]% of range
30-day trend: [Uptrend / Downtrend / Consolidation — one sentence description]
Volume: [today's volume vs avg — normal/above/below]
Live P/E: [calculated from last_price and latest EPS]
```

## Rate limits to respect
- Live data endpoints: 10 calls/sec, 300 calls/min — no issue for single-stock analysis
- Historical candles: same limits — fetch once, reuse in the analysis

---

## Validated case studies

### Behari Lal Engineering (Aug 2026, Mainboard)
- **Short-term**: CAUTIOUS APPLY. ₹90Cr anchor allocation. P/E 18.6x vs peer avg 31.4x (genuine discount). QIB sub 3.89x Day 2. GMP +24%. BUT: 69% OFS with promoter WACA ₹1-3 (massive gain for promoter).
- **Long-term**: SOLID. Manufacturer of steel rolls for rolling mills — niche position covering 10-11.5% of India demand. ROCE 27%, D/E 0.06x, EBITDA margin expanded 13.7%→19% over 3 years. P/E at 40% discount to peer average. Revenue FY26 ₹5,340M, PAT ₹646M.
- **What this means**: Apply cautiously (OFS concern is real but anchor backing and valuation discount provide support). If allotted and listing is flat, the fundamentals support holding — this is a genuine value play vs listed peers.

### NALCO — National Aluminium Company (Oct 2026, Commodity Cyclical)
- **The trap**: P/E 8.6x, ROCE 39.6%, zero debt, Rs 10,500 Cr net cash, 3.64% dividend yield. On paper, screaming cheap.
- **The reality**: LME aluminium near multi-year highs, margins at cycle peak. ROCE of 39.6% vs 10-year average ~15% = classic peak earnings. If earnings halved, effective P/E would be ~17x — fairly valued, not cheap.
- **Why the market "ignored" it**: FIIs actually doubled their stake (9% → 22%). The market was fully aware — it just correctly priced peak cyclical earnings at a compressed multiple + applied the structural PSU discount.
- **The real question**: Does the 0.5 MTPA smelter expansion (from 0.46 to 0.96 MTPA) create a higher earnings floor even in a downturn? That capacity-expansion kicker is the only thesis that justifies entry at peak-cycle prices.
- **Lesson**: Never call a commodity stock "cheap" just because trailing P/E is low. Always normalize to mid-cycle earnings and ask what the P/E would be if the commodity corrected 25-30%.

## Key patterns for mainboard IPOs

1. **Anchor allocation is the #1 signal** — strong anchors (top MFs, sovereign funds, reputable FIIs) do deep diligence. Their presence de-risks the IPO significantly.
2. **P/E discount to peers = room for re-rating** — the market eventually prices mainboard stocks at peer multiples. A 30-40% discount at IPO often closes within 6-12 months.
3. **ROCE >20% + low D/E = institutional magnet** — post-listing, as analyst coverage begins, high-ROCE low-debt companies attract sustained buying.
4. **OFS-heavy isn't automatically bad on mainboard** — unlike smaller IPOs, mainboard OFS is often PE/VC exit or legitimate wealth diversification. Check post-IPO promoter stake and WACA for intent.
5. **QIB subscription matters more than retail** — on mainboard, QIB sub >10x with strong anchor = likely positive listing regardless of retail demand.
6. **GMP is directional but not precise** — mainboard GMP with anchor backing is more reliable than without. But market corrections can wipe GMP overnight.
7. **The flip/long-term divergence is the most actionable insight** — when listing verdict = skip but long-term = solid, the IPO often presents a better buying opportunity 2-4 weeks post-listing when price stabilizes.
8. **Receivables ballooning is the earliest OCF warning** — trade receivables growing 2x+ faster than revenue over 2 years almost always precedes negative OCF.
9. **The Commodity P/E Trap** — for cyclical stocks (metals, chemicals, oil, shipping), a low P/E signals peak earnings, not cheapness. The market deliberately keeps the multiple low because it prices in earnings mean-reverting downward. Always normalize earnings to mid-cycle before comparing P/E to compounders. Buy cyclicals on high P/E (trough), sell on low P/E (peak).

## Key patterns for listed stock analysis

1. **Compounder vs cyclical — know which you're analyzing.** A compounder (consistent ROCE >15%, growing earnings, pricing power) deserves a stable or expanding multiple. A cyclical (earnings swing with commodity/cycle) deserves a compressed multiple at peak and an expanded one at trough. Mixing these frameworks is the most expensive analytical error.
2. **PSU discount is structural and rational.** Government-owned companies trade at 30-50% discount to private peers due to: dividend extraction policy, limited management autonomy, social obligation mandates, and capex decisions driven by national interest rather than ROI. This discount rarely closes permanently.
3. **"Smart money is already there" doesn't mean the opportunity is gone.** FII accumulation confirms the thesis but doesn't mean the stock is fully priced. Watch for the *rate of change* in institutional holding — acceleration = conviction building.

---

## Practical tips for reading RHP/DRHP PDFs

1. **Start with the KPI table**, not the full financial statements. It's in the "Basis for Offer Price" section (typically pages 155-165 in mainboard RHPs) and gives Revenue, EBITDA, PAT, margins, ROCE, ROE, Cash Profit, D/E, working capital days, and operational metrics in a single table.
2. **Peer comparison table** is on the same pages — shows the company's P/E, EPS, RONW vs listed peers. This is your quickest valuation check.
3. **Financial statements location**: Balance Sheet, P&L, and Cash Flow are in the "Summary of Financial Information" section. Full detail in "Restated Financial Statements" (often page 384+).
4. **When the PDF reader struggles with financial table pages**, try: (a) the KPI summary table instead, (b) different page ranges, (c) web search for "[Company] IPO financials" — indmoney, chittorgarh.com, ipogyani extract key numbers.
5. **Risk factors section** (pages 24-60) often contains financial metrics in text — RPT percentages, customer concentration %, subsidy dependence — easier to extract than formatted tables.
6. **For OCF estimation when cash flow statement is hard to extract**: Cash Profit (from KPI table) minus the increase in working capital (trade receivables + inventories - trade payables, year over year) gives a rough OCF proxy.
7. **Anchor investor details** are in an addendum or on the exchange website (NSE/BSE). Search "[Company] anchor allocation" for the list.

---

## When to read which reference

- `references/data-sources.md` — India-specific sources. Read when sourcing data.
- `references/financial-analysis.md` — three-statement analysis, ratios, forensic checks. Read at Step 3 (long-term) or financial quality deep-dive (IPO assessment).
- `references/valuation.md` — relative and intrinsic valuation. Read at Step 4 (long-term only).
- `references/sector-lenses.md` — sector-specific metrics. Read when sector is identified.
- `references/red-flags-and-process.md` — governance flags, behavioral traps, process toolkit. Read at Step 5 (long-term) or red flag check (IPO assessment).
- **Section C (this file)** — Groww API live data. Read whenever the user asks for a suggestion or recommendation on a listed stock. Always fetch live price + 180-day candles before valuation.

## Output formats

### MANDATORY: Dual-angle mainboard IPO scorecard
**Every IPO analysis must use this format. Never deliver just one angle.**

```
[Company name]

━━ SHORT-TERM (Listing Day) ━━
Anchor: [₹X Cr from Y investors — name top 3-5]
P/E: [X.Xx vs peer avg Y.Yx] ([discount/premium] of Z%)
QIB subscription: [X.Xx] | Retail: [X.Xx] | Total: [X.Xx]
GMP: [₹X (+Y%)]
Issue structure: [Fresh X% / OFS Y%] | Promoter post-IPO: [X%]
BRLM: [Names]
Red flags: [NONE / list any triggered]

Listing verdict: [STRONG APPLY / APPLY / CAUTIOUS APPLY / SKIP]

━━ LONG-TERM (Business Quality) ━━
Business: [1-2 sentence plain-English description]
Moat: [What protects margins]
Financials: ROCE [X%] | D/E [X.Xx] | OCF/PAT [X%] | Margin trend [↑/→/↓]
Valuation: P/E [X.Xx] vs peer avg [Y.Yx] | EV/EBITDA [X.Xx]
Key risk: [Single biggest threat]
Long-term verdict: [BUY ON DIPS / HOLD IF ALLOTTED / EXIT ON LISTING / AVOID]

━━ WHAT THIS MEANS ━━
[One paragraph connecting the two verdicts into a clear action plan.]
```

### For long-term research only (already-listed stocks) — the research note
```
[Business in plain English — 2-3 sentences]
[Industry & structural position]
[Financial health — three statements, cash-flow reconciliation]

━━ LIVE MARKET DATA (Groww) ━━
Price: ₹[last_price] | Today: O [open] H [high] L [low]
52-week range: ₹[week_52_low] — ₹[week_52_high] | Currently at [X]% of range
30-day trend: [Uptrend / Downtrend / Consolidation — one sentence]
Volume: [today vs avg — normal/above/below]
Live P/E: [last_price / latest annual EPS]

[Valuation — vs peers and own history, anchored to live price above]
[The real risks]
[Honest synthesis — NOT a buy call]
```

## Adapting to the user

If the user has shared a screenshot or a single data point, work with it but search for the rest rather than asking them to retype. If they ask a narrow question, answer directly without forcing the whole funnel. If they mention "listing gains" or "should I apply", still provide both angles but lead with the listing assessment. Calibrate emphasis to what they asked, but never omit either verdict for IPO analysis.

**When processing multiple IPOs simultaneously**: Assess all of them and present a comparative scorecard (visual widget preferred). For each IPO, show both the listing verdict and long-term verdict side by side. Prioritize: red flag checks first (eliminates quickly), then anchor/subscription data, then financial deep-dive only for survivors.

