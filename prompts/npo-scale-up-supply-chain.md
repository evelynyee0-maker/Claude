# Research Prompt: NPO (Near-Packaged Optics) Supply Chain for AI Scale-Up

> Copy everything below the line into your research assistant (works best with web search / deep-research mode enabled).
> Edit the `[PARAMETERS]` block first.

---

## [PARAMETERS]
- **Technology:** NPO, Near-Packaged Optics: optical engines mounted next to the switch/XPU package (on the same substrate or the host board, usually through a high-density socket or flyover connector) instead of co-packaged (CPO) or pluggable.
- **Application focus:** AI **scale-up** fabric, meaning GPU/XPU-to-GPU/XPU and GPU-to-switch links inside one coherent domain (e.g., NVLink, UALink, Scale-Up Ethernet / ESUN). Scale-out (front-end/back-end Ethernet, InfiniBand) only as comparison.
- **Time horizon:** 2025 (current) → 2028 (volume ramp), with a view to 2030.
- **Geography:** Global. Flag US / Taiwan / China / Japan / Korea / EU exposure and export-control relevance.
- **Output language/format:** English. **One self-contained HTML file**, tables-first, diagrams wherever possible. **No cover page.**

## ROLE
You are a senior semiconductor and optical-interconnect supply-chain analyst. You have worked on silicon photonics, advanced packaging, and hyperscale data-center procurement. You write for an investment and strategy audience who want evidence, not hype.

## OBJECTIVE
Build a verified, end-to-end map of the NPO supply chain for AI scale-up. Identify the **highest value-add parts and processes**, name the **upstream and downstream players** at each, and show where the **bottlenecks, chokepoints and margin pools** are.

## STEP 1: Define the technology precisely (short)
1. One paragraph each: pluggable vs. LPO/LRO vs. **NPO** vs. CPO. Then a comparison table with these rows: distance from ASIC, electrical channel (XSR/VSR/LR SerDes), power (pJ/bit), serviceability/field-replaceability, bandwidth density (Tb/s per mm of shoreline), thermal coupling, yield/rework risk, and maturity (TRL).
2. Why NPO matters **specifically for scale-up**: copper reach limits at 200G/lane and above, rack/multi-rack coherent domains, and the power budget.
3. Name the standards and industry bodies that shape it: OIF (e.g., CEI-224G, external laser ELSFP, co-packaging frameworks), OCP, UALink Consortium, Ethernet scale-up efforts, COBO, IEEE 802.3dj. **Cite the actual document or announcement for each claim.**

## STEP 2: Decompose the bill of materials and process flow
Break NPO into the value-chain nodes below (add or split nodes if the evidence supports it). Show the flow as a **Mermaid flowchart** from raw materials to the hyperscaler rack.

| # | Node | Examples of what belongs here |
|---|------|-------------------------------|
| 1 | Compound-semiconductor substrates & epi | InP / GaAs wafers, epitaxy |
| 2 | Laser sources | CW DFB / high-power lasers, external laser source (ELS/ELSFP) modules, on-chip vs. remote laser |
| 3 | Photonic IC (PIC) design & foundry | SiPh platforms (MZM, micro-ring modulators, Ge PD, mux/demux), PDKs, wafer foundries |
| 4 | Electronic IC (EIC) | Drivers, TIAs, CDR/DSP or DSP-less (linear) designs, SerDes IP |
| 5 | 3D/2.5D integration of PIC + EIC | Hybrid bonding, Cu-Cu, micro-bump, wafer-level optics (e.g., foundry photonic-stacking platforms) |
| 6 | Optical I/O & fiber attach | Fiber array units, edge vs. grating couplers, lenses, detachable fiber connectors, polarization-maintaining fiber, fiber shuffles/routing |
| 7 | Package substrate, sockets & interconnect | ABF/glass substrates, LGA/compression sockets, flyover cables, high-density board connectors |
| 8 | Optical engine assembly & OSAT | Active alignment, assembly, burn-in, hermeticity/reliability |
| 9 | Test & metrology equipment | Wafer-level optical probe, known-good-die (KGD) testing, high-speed BERT/scope |
| 10 | Host silicon | GPU/XPU, scale-up switch ASICs, retimers |
| 11 | System integration | Switch trays, compute trays, rack ODM/OEM, liquid cooling interaction |
| 12 | Downstream demand | Hyperscalers, AI clouds/neoclouds, sovereign AI, national labs |

## STEP 3: Player mapping (core deliverable)
For **every node**, produce a table with these exact columns:

| Company | HQ / listing (ticker) | Role (upstream supplier / node leader / downstream customer) | Specific NPO-relevant product or process | Evidence of NPO/CPO/scale-up engagement (customer, demo, design win, qualification) | Est. market position (leader / challenger / emerging) | Capacity & expansion plans | Key customers & suppliers | Geographic / export-control exposure | Source(s) + date | Confidence (High/Med/Low) |

Rules:
- Include **incumbents, challengers, and start-ups** (e.g., venture-funded photonics/optical-I/O companies), as well as **Chinese domestic alternatives**.
- Separate **confirmed** relationships (from filings, press releases, official conference presentations) from **reported/rumored** ones (sell-side notes, trade press, supply-chain media). Never mix them in one cell without a label.
- If a company is believed to be relevant but you cannot verify an NPO link, list it under *"Watchlist: unverified"* instead of the main table.

## STEP 4: Value-add and margin analysis
1. Estimate the **cost breakdown of an NPO optical engine** (and an 800G/1.6T/3.2T-equivalent port) by node. Give it as a table **and** a stacked-bar or waterfall chart. State assumptions and ranges; do not give single-point guesses.
2. Score each node from 1 to 5 on: **technical difficulty, IP/know-how moat, supplier concentration (HHI or top-3 share), capex intensity, gross-margin potential, qualification lead time, substitution risk.** Show the result as a **heatmap table** and pick the **top 3–5 highest value-add nodes**.
3. For each top node, explain *why* value accrues there and who captures it.

## STEP 5: Bottlenecks, risks, and scenarios
- A **chokepoint table** with columns: node, single/dual-source dependency, lead time, capacity constraint, geopolitical risk, mitigation.
- Critical technical risks: laser reliability and field replacement, fiber-attach yield, thermal crosstalk with a >1 kW ASIC, test/KGD economics, serviceability vs. CPO.
- **Competing paths:** NPO vs. CPO vs. LPO vs. copper (incl. active electrical cables) for scale-up. Give a timeline/Gantt chart of expected adoption per path through 2030, and state which scenario favors which suppliers.
- **Triggers to watch:** product launches, OFC/ECOC/Hot Chips/ISSCC/IEDM disclosures, hyperscaler RFQs, standards milestones.

## STEP 6: Upstream ↔ downstream relationship map
- A **Mermaid graph** (or Sankey-style table) linking suppliers → integrators → host-silicon vendors → hyperscalers. Mark confirmed links with solid lines and reported links with dashed lines.
- A **"Who depends on whom"** matrix: the top 10 downstream buyers against the top 15 upstream suppliers.

## STEP 7: Investment / strategy takeaways
- 5–8 bullet conclusions, each tied to evidence above.
- Public companies with the **highest NPO revenue sensitivity** (what % of revenue could be exposed, with reasoning).
- Private companies or start-ups worth tracking (latest funding round, investors, product status).

## SOURCING & VERIFICATION RULES (mandatory)
1. **Source priority:** (a) company filings (10-K/20-F, annual reports, earnings-call transcripts, investor-day decks); (b) official press releases and product pages; (c) peer-reviewed or conference papers (OFC, ECOC, ISSCC, VLSI, ECTC, Hot Chips); (d) standards-body documents (OIF, OCP, IEEE, UALink); (e) established market research (LightCounting, Yole, Cignal AI, TrendForce, Dell'Oro); (f) reputable trade press. Use social media or anonymous supply-chain chatter only if it is labeled *"unverified"*.
2. Cite **every factual claim** inline with source name, title, date, and URL.
3. Give the **date of each data point**. Flag anything older than 12 months as possibly stale.
4. If sources conflict, show both values and explain which you trust and why.
5. Do not invent market-share numbers. If no reliable figure exists, say *"no public data"* and give a reasoned range labeled as an estimate.
6. End with a **"Known unknowns"** section: the questions the public evidence cannot answer, and how to answer them (expert calls, teardown, channel checks).

## OUTPUT FORMAT: a single self-contained HTML file
Deliver the whole report as **one `.html` file** that opens straight in a browser. Output only the HTML, in one code block, with no commentary before or after it.

**Structure**
- No cover page. The page opens with a slim header (title, "as of" date, scope line), then a 150-word **Executive Summary** and a one-glance **value-chain diagram**.
- Put a sticky table of contents (sidebar on desktop, collapsible on mobile) with one `<section id="step-N">` and one `<h2>` per step.
- Appendix: a numbered source list with access dates. Make every inline citation a clickable superscript (`<sup><a href="#src-12">[12]</a></sup>`) that jumps to its entry, and make every source entry link to the original URL.

**Libraries** (load from CDN only, with no other external files)
- **Mermaid** (`https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js`): value-chain flowchart, supplier → customer relationship graph, and adoption Gantt. Use solid edges for confirmed links and dashed edges for reported links.
- **Chart.js** (`https://cdn.jsdelivr.net/npm/chart.js@4`): stacked bar of the cost breakdown and the scenario/adoption charts. Put chart data in inline `<script>` JSON so it can be edited.
- Keep all CSS inline in one `<style>` block, with no CSS framework.

**Tables**
- Use real `<table>` elements with `<thead>`, sticky headers and zebra rows, wrapped in a horizontally scrollable container on small screens.
- Make the player-mapping tables **sortable by column and filterable with a search box**, using about 30 lines of vanilla JS (no library).
- Render the **Confidence** column as colored badges (High = green, Med = amber, Low = red), and add a "Confirmed" or "Reported" tag to every relationship cell.
- Build the value-add **scoring heatmap** as a table whose cell backgrounds are shaded from the 1–5 score, with a legend.
- Put the "Watchlist: unverified" and "Known unknowns" sections in visually distinct callout boxes.

**Design**
- Clean, simple and modern: a system font stack, max content width of about 1100px, generous whitespace, one accent color, and colors defined as CSS variables.
- Support light and dark mode with `prefers-color-scheme`.
- Make it responsive down to phone width, with no horizontal page scroll.
- Add a `@media print` stylesheet that hides the TOC and search boxes, avoids page breaks inside table rows and diagrams, and prints link URLs in the source list.
- Keep the prose tight. Every number in a table must carry its citation.
