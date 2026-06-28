# LA Sim — v3 Research & Engine Design

Distilled from sourced research (mid-2026). This is the build spec for v3: a real simulation engine where decisions produce **lagged, contingent, sometimes-failing** outcomes. Figures are real; see inline notes.

---

## The core idea: a city-state engine

Today, passing a bill just nudges approval and ends. In v3, the city has **live metrics that evolve every turn**, and your decisions feed **pipelines** that deliver over months/years, can be **cut by other actors**, and carry **reversal risk**.

### City metrics (tracked, shown on dashboard as trends)
- **Homeless (unsheltered / sheltered)** — start ~43,700 city (2025 PIT, −3.4% trend).
- **Housing pipeline & completions** — RHNA need ~57,000/yr; LA actually permits ~17,000/yr (~30% of pace). Affordable unit cost ~$600k (HHH audit; up to $837k).
- **LAPD sworn** — ~8,620 (≈30-yr low), attrition ~550/yr; a hire-class adds slowly.
- **Crime** — homicides ~230 (2025, fewest since 1966); property ~102k.
- **Budget** — $14.85B total / $8.59B General Fund; reserve target 5% (2.75% emergency floor).
- **Approval (by bloc), capital, scandal, war chest** — existing.

### The engine rules (what makes it "real, not easy")
1. **Lag.** A housing bill adds to a *pipeline*; units complete over ~6–12 turns. Inside Safe houses people gradually at ~$3,300/room/mo with a **~40% return-to-street** rate. LAPD hiring nets only after attrition.
2. **Contingent money.** The Mayor often doesn't control the cash: **Council can cut your program** (Inside Safe $46M→$29M), the **County can pull funding** (~$300M from LAHSA, 2025), the **State conditions grants** (HHAP), the **feds can freeze** (HUD froze ~$200M, 2026). Model funding as pledges that can be revoked.
3. **Reversal risk.** Executive Directives are fast but **not law** — they can be struck in court (ED1 lost 3×) or undone by audit (Controller found ~$513M unspent). Each unilateral move plants a delayed risk event.
4. **Noise & revision.** Counts arrive yearly, undercount ~32% (RAND vs LAHSA), and get revised. Outcomes should be noisy.
5. **Disasters convert past neglect into catastrophe.** Underfund LAFD → a fire becomes a fired chief + recall + stalled rebuild (the real 2025 arc).

---

## Detailed budget (real dollars)

**Revenue (General Fund $8.59B):** Property tax $2.95B (most stable, ~3–5%/yr), Departmental receipts $1.86B, Business tax $0.90B, UUT $0.77B, Sales tax $0.68B (cyclical), TOT/hotel $0.31B (most volatile, ±30–50% in tourism shocks), DWP transfer $0.22B.

**Spending (total cost of services):** LAPD ~$3.53B (24%), LAFD ~$1.46B, Public Works ~13.8%, LADOT ~$396M, Housing $125M, Rec & Parks $372M, Library $280M, plus benefits ~$1.0B, debt service, liability claims $210M.

**Pressures:** ~$1B structural deficit closed FY25-26 via labor deals; civilian COLA ~22%/5yr; LAPD MOU 6/4/5/5% (~$994M); reserve dipped to ~4% in the crunch.

---

## More bills (target ~30+, real policies)
Codify ED1 (make affordable streamlining permanent), defend/expand Measure ULA, 41.18 anti-camping enforcement, oil-drilling phase-out, short-term-rental crackdown, Olympic/tourism $30 wage, GRYD gang prevention, Vision Zero, LADWP clean-energy + rate hike, sanctuary/immigration protections, mansion-tax-funded eviction defense, Sixth-Street/park bonds, sidewalk-vending expansion, FAIR-plan/insurance advocacy, Metro/transit packages, plus the existing SB 79, Inside Safe, RSO, LAPD-hiring, austerity, council-expansion, wildfire-rebuild.

## More events (target ~30+, from real LA)
Palisades insurance/FAIR-plan crisis; DWP empty-reservoir liability suit (billions); ULA statewide repeal threat (Nov 2026); HUD funding freeze; County pulls LAHSA money; 41.18 sweep backlash (Echo Park / MacArthur Park / Venice); ICE raids hit street vendors; Olympics displacement protests (NOlympics); redistricting-scandal echo; labor strike / COLA crunch; film runaway-production exodus; Valley heat wave; oil-well blowout; short-term-rental fight; Skid Row surge; council corruption probe (PLUM); state preemption (builder's remedy); port automation labor fight; homeless-count revision (data shock); mansion-tax-slow-spend audit.

## Districts & demographics (texture)
City ~3.84M, **64% renters**, 47% Latino, 36% foreign-born, median rent ~$1,933, poverty 16.5%. District flavors: CD1 Latino NE/renters; CD4 affluent Westside/hills; CD8/CD9 South LA (Black/Latino, environmental burden); CD11 Westside/coastal + Palisades; CD13/CD14 Eastside/DTLA immigrant; CD15 Harbor/port/Watts. Problem geography: Skid Row + Valley homelessness; South LA rent burden (73%); port pollution (Wilmington); Valley heat; NE-to-Crenshaw gentrification.

## Rules corrections (from charter research)
- **§409 vacancy:** Council (not Mayor) fills it — appointment until the next even-year 2nd Monday of December, **plus** a special election if substantial term remains; or a special election outright. **No 30-day deadline.** (Game models the player backing a candidate.)
- **Ballot timing:** ordinary ordinances/measures can use special elections; **charter amendments are effectively even-year November only** (Elec. Code §1415/§9255). So council-expansion/ethics charter measures should schedule to the next even-year November; bonds/taxes have more flexibility.
- **Mayor traits (shipped):** Raman → +1 AP, warmer progressive bloc (younger, organizer). Bass → +2 capital/turn, warmer establishment (institutional clout).

---

## Build order for v3
1. **Engine core** — city-metric state + per-turn update + pipelines + lagged outcomes + contingent funding + reversal-risk events. (Centerpiece.)
2. **Dashboard outcomes** — clean trend charts: homes built, homeless, crime, LAPD staffing, budget/reserve.
3. **Detailed budget** — real dollars, revenue elasticity, reserve mechanics, labor costs.
4. **Content expansion** — ~30 bills, ~30 events, district/neighborhood texture, ballot-timing realism.
5. **Polish & balance** — playtest tuning so it's deep but still playable.
