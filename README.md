# EU CBAM 出口碳關稅試算器
**Taiwan Exporter's CBAM Cost Calculator**

Live demo → [部署後填入 Netlify URL]

---

## Assignment 3 — AI Collaboration Documentation

### What I Built

A single-page web tool that helps Taiwan manufacturers quickly estimate their annual EU CBAM (Carbon Border Adjustment Mechanism) costs. Users input their export volume and product type, and the tool calculates how much they'll pay under the 2026 CBAM enforcement — and how much they could save by hitting EU benchmark emission levels.

**Covered products:** Steel (4 subcategories), Fasteners (CN 7318), Aluminium (3 subcategories), Cement, Fertiliser/Hydrogen

**Key features:**
- Product applicability checker (keyword → CBAM status)
- Real-time calculation with scenario comparison
- Product-specific decarbonization recommendations
- Clear usage disclaimer and data sourcing

---

## AI Collaboration Process

### Phase 1 — Problem Definition (Claude)
Started with a broad question: *"What digital tool would generate real business value for an ESG consultant?"*

Claude helped me reframe from a generic ESG tool to a specific pain point: **Taiwan exporters don't know how much CBAM will cost them in 2026.** This focus came from AI-assisted analysis of:
- Taiwan's CBAM exposure (~2,600–3,500 affected companies)
- The gap between the government information platform (no calculator) and what companies actually need
- Product scope: steel and fasteners as Taiwan's primary EU exports

### Phase 2 — Technical Research (Claude)
Used AI to research:
- Official CBAM Annex I product list and CN codes
- EU benchmark emission factors from JRC (Joint Research Centre)
- Taiwan-specific emission intensity data (e.g., fastener industry avg 1.85 tCO₂/t)
- API options for EU ETS carbon price (OilPriceAPI, Sandbag, Trading Economics)
- Deployment strategy: Netlify free tier vs. Vercel vs. Zeabur

Key AI insight: *OilPriceAPI requires a backend proxy for CORS — for a standalone HTML file, a manual-override input is more practical and transparent.*

### Phase 3 — CBAM Formula Validation (Claude)
AI helped verify the calculation logic:

```
CBAM Cost (€) = Export Volume (t) × Emission Intensity (tCO₂/t) × (EU ETS Price − Taiwan Carbon Fee)
```

- Taiwan carbon fee: NT$300/tCO₂e ≈ €8 (confirmed EU recognizes this as deductible)
- Benchmark comparison: AI sourced EU benchmark values from Regulation (EU) 2023/956 Annex I

**Test case:** 1,000t steel (HRC, BF/BOF route) at €75 ETS price:
`1000 × 1.370 × (75 − 8) = €91,790/year`

### Phase 4 — UX & Disclaimer Design (Claude)
Key design decisions made with AI guidance:

1. **Usage disclaimer placement** — AI suggested putting it *above* the form (not just in footer) so users encounter it before calculating, reducing misuse risk

2. **"適合/不適合" split** — AI recommended clear two-column layout showing what the tool IS and IS NOT for, protecting against users treating estimates as official compliance data

3. **Product applicability checker** — AI suggested adding this after noting that many Taiwan exporters (machine tools, electronics) are NOT directly subject to CBAM — important to clarify before they waste time calculating

4. **Language correction** — AI flagged that "合規" is mainland Chinese usage; correct Taiwan term is "法規遵循"

### Phase 5 — Iteration & Refinement
Iterated on:
- Scope: Started with CBAM as an ESG consulting tool → refined to focus on Taiwan's actual exposure (steel + fasteners as priority, not cement/fertiliser)
- Footer disclaimer: Expanded from one line to full data sourcing + legal disclaimer after feedback that users might misuse the numbers
- CTA: Changed from generic "contact ESG consultant" to specifically "覺心營 ESG 顧問"

---

## Technical Stack

- **Frontend:** Vanilla HTML + CSS + JavaScript (no build tools, no dependencies)
- **Deployment:** Netlify (free tier, HTTPS, custom domain support)
- **Data sources:** EU CBAM Regulation (EU) 2023/956 Annex I, JRC benchmark values
- **Carbon price:** User-configurable reference value (default €75/tCO₂)

---

## Data Sources

| Data | Source |
|------|--------|
| CBAM product list & CN codes | EU Regulation 2023/956 Annex I |
| Emission intensity benchmarks | JRC (Joint Research Centre) official values |
| Steel production route factors | CarbonChain CBAM Guide |
| Aluminium benchmarks | Climatiq CBAM Dataset |
| Taiwan fastener emission intensity | Industry average, ~22% above EU benchmark |
| Taiwan carbon fee | Environmental Protection Administration, NT$300/tCO₂e |
| EU ETS price range | OilPriceAPI / Trading Economics (reference) |

---

## Disclaimer

This tool provides estimates for internal evaluation only. It does not constitute legal, financial, or regulatory compliance advice. See full disclaimer in the tool footer.

---

*Built with AI collaboration (Claude) as part of Asia Impact Nexus Assignment 3 — Vibe Coding Project*
*© 2026 覺心營股份有限公司 Awakening Heart Base Corporation*
