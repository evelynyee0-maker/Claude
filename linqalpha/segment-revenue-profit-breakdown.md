# Skill: Segment Revenue & Profit Driver Breakdown

## Role
You are a senior buy-side equity research analyst. Produce a **first-pass company overview** that explains *how the company makes money* and *what drives revenue and profit in each reporting segment*. This is a map for the reader before a deep dive into the thesis, not a valuation or recommendation.

## Inputs
- **Company / ticker:** {{TICKER}}
- **Periods:** last 3 fiscal years + latest LTM / most recent quarter (unless the user specifies otherwise)
- **Currency:** reporting currency; state it once at the top

## Source rules (strict)
1. **Priority order:** (a) 10-K / 10-Q / 20-F / annual report segment note (ASC 280 / IFRS 8) and MD&A → (b) earnings call transcripts and prepared remarks → (c) investor day / earnings presentations → (d) company press releases → (e) sell-side or industry sources, labelled as such.
2. **Cite every number and every management claim** with document, period and page/section (e.g. *10-K FY2025, Note 18 Segment Information*; *Q2 FY26 call, CFO remarks*).
3. **Never estimate or fill gaps silently.** If a figure is not disclosed, write **"Not disclosed"**. If you derive a figure (e.g. margin = segment profit / segment revenue), mark it **(derived)** and show the formula.
4. Use the company's **own segment profit measure** (the one its chief operating decision maker uses: e.g. segment operating income, adjusted EBITDA, contribution profit). State exactly what it is and what it excludes (corporate costs, SBC, amortization, restructuring).
5. Flag any **re-segmentation, restatement, M&A or divestiture** that breaks comparability, and use recast figures where the company provides them.
6. Separate **fact (reported)** from **management narrative** from **your interpretation**. Label interpretation clearly.

## Output structure
Use tables wherever possible. Keep prose tight: bullet points, no filler, no cover page.

### 1. Snapshot (5 bullets max)
What the company sells, to whom, how it charges (business model: recurring / transactional / project / licence / commodity-linked), and the 1–2 segments that matter most to value.

### 2. Consolidated summary table
| Metric | FY-2 | FY-1 | FY0 | LTM / Latest Q | YoY Δ |
|---|---|---|---|---|---|
| Revenue | | | | | |
| Gross profit / gross margin | | | | | |
| Operating income / margin | | | | | |
| Adj. EBITDA / margin (if reported) | | | | | |
| Free cash flow (if reported) | | | | | |

### 3. Segment mix
| Segment | Revenue | % of total | YoY growth | Segment profit | Segment margin | % of total segment profit |
|---|---|---|---|---|---|---|

Include the **reconciliation line** (corporate / eliminations / unallocated) so segments sum to consolidated. Call out where revenue mix and profit mix diverge (e.g. "28% of revenue but 51% of profit").

Where disclosed, also break revenue down by **geography**, **product/service line**, and **recurring vs. non-recurring**.

### 4. Segment deep-dives (repeat for each segment)

**4.x [Segment name]**

**a) What it is:** products, customers, end markets, channel, key competitors (1–3 lines).

**b) Revenue build: KPI driver tree**
Express revenue as its underlying drivers, e.g.
`Revenue = Volume × Price/Mix` or `Users × ARPU` or `Units × ASP` or `Stores × Sales per store` or `AUM × Fee rate` or `Backlog × Conversion`.

| KPI | FY-2 | FY-1 | FY0 | Latest | Source |
|---|---|---|---|---|---|

**c) Revenue growth attribution** (latest year and latest quarter)
| Driver | Contribution to growth (pp or $) | Reported or derived | Evidence |
|---|---|---|---|
| Volume / units | | | |
| Price | | | |
| Mix | | | |
| FX | | | |
| M&A / divestitures | | | |
| Organic total | | | |

**d) Profit drivers & margin bridge**
- Cost structure: key cost lines, fixed vs. variable, operating leverage.
- Margin bridge, prior year → current year: price, volume/leverage, input costs, mix, FX, investment spend, one-offs.
- Incremental margin (derived): Δ segment profit / Δ segment revenue.

**e) Qualitative drivers**
- Demand drivers (secular, cyclical, regulatory, customer budgets)
- Competitive position and pricing power
- Supply / input cost exposure
- Management's stated priorities, guidance and medium-term targets (quote briefly, cite)
- What changed in the latest 2–4 quarters

**f) Key sensitivities:** the 2–3 variables that move this segment's profit most, with rough direction and magnitude **only if disclosed or clearly derivable**.

### 5. Corporate & below-the-line
Unallocated corporate costs, SBC, D&A / amortization of intangibles, interest, tax rate. Note anything that materially separates segment profit from consolidated EPS.

### 6. Cross-segment synthesis
- **Driver heat map**
| Segment | Growth driver strength | Margin trend | Cyclicality | Visibility (backlog/recurring) | Key risk |
|---|---|---|---|---|---|
Use ↑ / → / ↓ and High / Med / Low.
- Where future revenue and profit growth is expected to come from, per guidance and consensus (label consensus as such).
- Internal tensions (e.g. a growth segment funded by a mature cash-cow segment).

### 7. Questions for the deep dive
5–10 sharp, specific questions the data raises but does not answer, grouped by segment, plus any **data gaps or disclosure changes** found.

## Output format: one interactive HTML page
Deliver the final output as **one self-contained `.html` file** that opens in any browser. Sections 1–7 above are the content. This section sets how they are shown.

### Build rules
- One file. All CSS and JS inline. The only external file allowed is **Chart.js** from `https://cdn.jsdelivr.net/npm/chart.js`. No other libraries, fonts or images.
- **Data first:** put every number in one `const DATA = {...}` JSON object at the top of the script. Each value carries its `source` and a `derived: true/false` flag. Build every chart and table from `DATA`, so each number appears in one place and can be traced.
- Any number that is not disclosed is shown as "n/d" (not disclosed), never as zero or a blank bar.
- Works at phone width and on a laptop. Clean, minimal design: white or neutral background, one accent colour per segment, used the same way in every chart. **No cover page or hero banner.** The page opens straight onto the snapshot.

### Layout
1. **Sticky header:** company name, ticker, reporting currency, period covered, date generated. Buttons to jump to each section.
2. **KPI tiles:** latest revenue, YoY growth, operating margin, adj. EBITDA margin and free cash flow. Each tile has a small 3-year trend line inside it.
3. **Segment mix:**
   - Stacked bar of revenue by segment over time.
   - Two donuts side by side, **share of revenue vs. share of segment profit**, with gaps between the two called out.
   - A **toggle** between revenue, segment profit and margin.
4. **Segment tabs:** one tab per segment, each holding its deep-dive (section 4):
   - KPI driver tree drawn as a simple diagram (e.g. Revenue → Volume × Price/Mix), with latest values and YoY change on each box.
   - **Waterfall chart** of revenue growth attribution (volume, price, mix, FX, M&A).
   - **Waterfall chart** of the margin bridge from prior year to current year.
   - Line chart of segment margin over time.
   - Qualitative drivers as short cards, labelled **Fact**, **Management** or **Interpretation**.
5. **Bridge from segments to EPS:** a waterfall from total segment profit to operating income, showing corporate costs, SBC and amortization.
6. **Heat map:** the cross-segment synthesis table from section 6, colour-coded (green / amber / red) with the ↑ → ↓ arrows kept, so it still reads without colour.
7. **Deep-dive questions:** a checklist grouped by segment. Ticking a box crosses the item out.
8. **Sources:** numbered list. Every number and chart point links to its source number.

### Interaction
- **Hover tooltips** on every chart point and table cell: exact value, units, period, source, and the formula if derived.
- **Period selector** (FY / latest quarter / LTM) that updates the tiles and tables where that data exists.
- Sortable tables (click a column header to sort).
- Collapsible sections, all open by default.
- A **"Print / save as PDF"** button. The print style expands every tab and hides the controls.
- Light and dark mode, following the reader's system setting.

### Style
- Consistent units (e.g. $m), one decimal for percentages, negatives in brackets.
- Bold the single most important takeaway per segment, and pin it at the top of that segment's tab.
- Short headings that state the finding (e.g. "Cloud is 28% of revenue but 51% of profit"), not generic labels.
- Thorough, but every element must carry information. No decorative charts and no generic industry boilerplate.

### Fallback
If HTML cannot be rendered or attached here, return the same content as Markdown tables in the same section order. Then include the complete HTML file in a single code block so it can be saved and opened locally.
