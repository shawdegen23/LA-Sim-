# LA Sim — A Hyperrealistic Los Angeles Politics Simulator

**Part 1: The 2026 Campaign Trail.** Phase 3 build (deepest campaign mechanics).

A turn-based political strategy game built around the actual 2026 Los Angeles municipal elections. You play either a candidate for Mayor of Los Angeles or one of the eight City Council seats up this cycle, against the real declared field.

## How to play

Open `index.html` in any modern browser. The game runs entirely client-side. Saves are kept in your browser via localStorage.

---

## Build summary

- **Phase 1**: weekly turn loop, real opponents, blocs, endorsers, calendar, primary→runoff, save/load.
- **Phase 2**: tabbed UI, staff hires, neighborhoods, debate minigame, press relationships, IEs, voter file (1x/2x/3x), polling cross-tabs, message discipline, FPPC filings, burn rate.
- **Phase 3**: seven-language outreach, real LA faith institution circuit, holiday-aware schedule, multi-day branching crisis trees, communications creative (ads + multi-piece mail), slate building & surrogates, granular precinct-level voter file, full institutional minigames (LA Fed COPE, LA Times Editorial Board, LA County Dem Party convention as multi-question interviews), Neighborhood Council circuit, BIDs, post-primary coalition realignment + donor refresh.
- **Phase 4** (this build): opponent campaigns with their own staff and weekly schedules · multi-stage opposition research dossier · opponent drop-out absorption · volunteer tier system (rookie / trained / captain) · captain relational organizing · voter-file vendor contracts (PDI, VAN, EveryAction) · texting platforms (Hustle, RumbleUp, Scale To Win) · field offices in real LA neighborhoods with monthly rent · yard signs / swag with brand aesthetics · 6 alt-format debates (LAist AirTalk, KCRW, NC forum, Streets For All, Univision Spanish, hot-mic) · press conferences with topic picker · 12 earned-media event types · spokesperson deployment in crises · live SVG charts: polling line, money curve, precinct map, staff org chart, endorsement tree, calendar heatmap.

The single file is ~5,150 lines now. No build step. No server. No external dependencies.

---

## Phase 3 features in detail

### Schedule grid + holidays
Every week renders as a 7-day × 3-slot grid (Mon-Sun, AM/Aft/Eve). Real LA-cycle holidays land in the grid:
Veterans Day, Thanksgiving week, Christmas/NYE (whole week blocked), MLK Day (South LA prime), Lunar New Year, Persian New Year (Nowruz), Cesar Chavez Day, Easter/Passover, Eid al-Fitr, Yom HaShoah, Cinco de Mayo, Memorial Day, Juneteenth, Independence Day, Rosh Hashanah, Yom Kippur (lay low), Día de los Muertos. Holidays reduce AP, block specific slots, or feature them.

### Multilingual outreach (7 languages)
Spanish, Korean, Mandarin, Tagalog, Persian, Armenian, Russian. Each unlocks via "Recruit bilingual volunteers". Once unlocked you can run in-language canvasses (door-knocks in that language) and ethnic-language radio buys (KSCA/KLVE for Spanish, Radio Korea, Sing Tao Chinese, Persian satellite TV, USC Armenian Hour, Russian-language outlets). Precincts that need a non-English language get a 25% bonus when you have it — and a 35% penalty when you don't, modeling the language-barrier reality.

### Faith institution circuit (19 real LA congregations)
West Angeles COGIC, Faithful Central, First AME (Black church circuit). Young Nak Celebration, Oriental Mission Church (KTown). Nessah Synagogue, Sinai Temple (Persian-Jewish + Conservative). Our Lady of the Angels, Our Lady of Guadalupe, Dolores Mission (Catholic Latino). Wat Thai of LA. Vermont Avenue Gurdwara. St. Garabed Armenian Apostolic. Islamic Center of Southern California. Wilshire Boulevard Temple, Young Israel of Century City. Thien Hau (Chinatown). Filipino Christian Church (Filipinotown). Holy Virgin Russian Orthodox. Each maps to a bloc mix; in-language fit gives bonus impact.

### Crisis trees (multi-day branches)
7 crisis archetypes — old tweet surfaces, endorser scandal, donor indicted, opponent attack ad, hot-mic gaffe, senior staff scandal, family health crisis. Each is a 1-3 day decision tree with branching consequences (apologize → next-day options, or defend → different next-day options). Outcomes hit affinity, scandal risk, discipline, cash, sometimes force staff changes or pause the campaign for weeks.

### Communications creative
- 8 ad templates: bio, positive, comparative, attack, Spanish-language, Korean-language, cause-of-the-week, testimonial. TV and digital channels with separate costs. Non-English ads require corresponding language unlock.
- 7 mail templates as a sequenced program: intro → contrast → endorsements → ID → GOTV (plus Spanish & Korean parallel pieces). Sequence-locked: endorsements mailer needs 3+ won endorsements; GOTV needs week 28+.
- Ads run for 4 weeks generating weekly bloc lift after the initial drop.

### Slate building (5 partner pools per race)
Real-feel 2026 ballot partners: Kenneth Mejia (Controller re-elect), open City Attorney race, LA County Sup. District 3 (Westside / Horvath territory), LAUSD Board District 4, plus Assembly seats per geographic area (Eastside / Westside / Valley / South LA). Joining a slate gives appeal to their lanes but exposes you to slate-mate scandals (~4% chance per partner per week of a small affinity dip).

### Surrogate bench (8 named surrogates)
Real-feel former mayors, MoCs, and supervisors (Garcetti-archetype, Wesson-archetype, Ridley-Thomas-archetype, governor-tier, sitting MoC, Barragán-archetype, Horvath-archetype, Solis-archetype). Each has a lane and conflicts. Booking gives a one-time bloc bump plus weekly residual.

### Precinct-level voter file
Drops below the bloc level. Each race has 5-8 named real LA precincts (Highland Park core, Chinatown Broadway, Pico-Robertson, Cheviot Hills, USC Zone, etc.) with turnout history, language need, and bloc mix. Precinct walks (requires Field Director) are the highest-efficiency field action. Language-mismatched precincts give worse returns.

### LA institutional minigames
Three interview-style minigames replace the simple endorser progress bar for LA Fed COPE, LA Times Editorial Board, and LA County Dem Party.
- **LA Fed COPE** (5 questions): Project Labor Agreements, card check, living wage ordinance, affordable housing labor, hospitality wage. Score 10+ to endorse.
- **LA Times Ed Board** (5 questions): theory of governing, density tradeoff, Inside Safe, budget cuts, past mistakes. Score 10+ to endorse.
- **LA Dem Party Convention** (4 questions): party loyalty, top issue, charter schools, sanctuary. Score 8+ to endorse.

### Neighborhood Councils (50+ real NCs)
115 NCs in LA real life; we sample 5-10 per race. Each has a lean (progressive / homeowner / renter / biz / labor / neutral). Visits give small citywide affinity bumps weighted by lane fit.

### Business Improvement Districts (10 real BIDs)
Downtown Center, Hollywood, Fashion District, Miracle Mile, Venice Beach, South Park, San Pedro, NoHo Arts, Echo Park, Wilshire Center/KTown. Outreach pulls small-business affinity — bigger if you've got the smallbiz issue lane.

### Post-primary realignment
When you advance to the runoff, the eliminated candidates' coalitions redistribute based on bloc affinity overlap. If you were strongest in their high-affinity blocs, you absorb most of their voters; if your runoff opponent was, they do.

### Donor refresh on runoff
Real CA campaign finance rule: primary and runoff are separate elections for contribution limits. ~45% of your primary donors give again in the runoff phase, with limits reset.

### Family-crisis pause
The "family health crisis" crisis tree can pause your campaign for 1-2 weeks (your AP drops to ~20%). Models a real candidate having to step away.

---

## Phase 4 features in detail

### Opponent campaigns
Top-tier opponents (tier 2+ by their seed power) get full simulated staffs — real-feel CM, Field Director, Comms Director, Finance Director, each with role-specific archetypes ("Bearstar Strategies veteran", "Hugo Soto-Martinez 2022 alum", "former LA Times reporter", etc.). Each week they execute moves (door-knocks in their stronghold, press pitches that erode your moderate blocs, max-donor dinners, occasional TV flights). Their last 12 weeks of moves are visible to you on the Opponents tab. Tier 3 opponents make strategic decisions: TV ad flights citywide (~15% chance per late-cycle week), issue pivots, etc.

### Multi-stage opposition research
Per opponent, three cumulative stages: Archives sweep (free, 1 slot), Court & legal records ($8K, 2 slots), FPPC/Ethics deep dive ($4K, 1 slot). Each rolls for 0-2 specific hits. Hits become usable lines you can deploy at press conferences. Strategy + general consultant + comms director increase hit rate.

### Opponent drop-outs
After week 22, opponents below 4% support may suspend their campaigns (~25% chance per week). Their bloc affinity vacates and 40% of it flows to you automatically. The "Court a dropped-out opponent" action absorbs another 10% of their stronghold blocs.

### Volunteer tiers
Rookie → Trained → Captain. Train action promotes rookies to trained, and ~25% of those to captain. Each captain surfaces 8 personal contacts. The "Activate captain networks" action converts contacts into committed-tier voter file entries — modeling friend-to-friend relational organizing.

### Voter-file vendors
PDI ($4,000/mo, 92% accuracy), VAN/NGP ($3,500/mo, 88%), EveryAction ($2,200/mo, 82%), or DIY (free, 55%).

### Texting platforms
Hustle ($0.06/msg, labor pedigree), RumbleUp ($0.05/msg, MMS), Scale To Win ($0.07/msg, best multilingual), or none.

### Field offices
Per race, 2-5 named neighborhood offices with monthly rent, capacity, coverage. Open offices give passive weekly affinity bumps in covered neighborhoods. Setup = 2 months rent.

### Swag / yard signs
4 tiers × 4 brand aesthetics (Clean/civic, Warm/family, Bold/movement, Retro/70s LA). Brand aesthetic shifts which blocs the visual identity appeals to.

### Alt-format debates
6 formats: LAist AirTalk (1-on-1 with Larry Mantle), KCRW Greater LA, Neighborhood Council forum, Streets For All transit forum, Univision Spanish (requires Spanish unlock), hot-mic moment (high-risk).

### Press conferences
10 topic choices. Hero-issue-aligned topics give a 1.4× boost.

### Earned-media events (12 archetypes)
Pre-dawn factory/port visit, LAFD ride-along, town hall after fire, Inside Safe walkthrough, walking tour with homeless services, school visit, senior center, Metro ride-along, encampment listening session, ICE-affected family, Olympic venue walk, tenants' rights rally.

### Crisis spokesperson deployment
When a crisis fires, deploy a spokesperson (your CM, Comms Director, a top surrogate, or yourself). Each has scenarios where they're effective. Damps backlash and reduces scandal risk.

### Visual layer (new "Charts & Map" tab)
Six live SVG visualizations, all inline, no external libs:
- **Polling chart** — you and top opp over time
- **Money curve** — cash + IE-for + IE-against over time
- **Precinct map** — every named precinct sized by turnout, colored by walked / open / language-barrier
- **Staff org chart** — boxes connected from candidate to each hire
- **Endorsement tree** — WON / IN PROGRESS / OPEN columns
- **Calendar heatmap** — 52 cells colored by activity intensity, current week highlighted

---

## All races

### Mayor of Los Angeles (citywide)
Karen Bass (D, incumbent), Nithya Raman (D, CD4), Spencer Pratt (R, reality TV), Adam Miller (D, tech), Rae Chen Huang (D, DSA Presbyterian minister) + 9 minor.

### City Council (8 of 15 seats up; CD7 unopposed)
- **CD1** Hernandez (i) vs Calanche, Claros, Grande, Robledo
- **CD3** Open. Gaspar, Girvan, Celona
- **CD5** Yaroslavsky (i) vs Mantel, Oyler
- **CD9** Open. Ugarte, Mazariegos, Nuño, Sánchez, Roldan, Hernandez
- **CD11** Park (i) vs Malik
- **CD13** Soto-Martinez (i) vs Carlisle, Kendall, Sarian
- **CD15** McOsker (i) vs Rivers (Green)

---

## Architecture

```
index.html
├── <style>            inline CSS, dark mode UI
├── <body>             screen containers
└── <script>
    ├── DATA            races · candidates · blocs · endorsers · neighborhoods
    │                    · staff pool · reporters · IEs · debate bank · theories
    │                    · LANGUAGES · FAITH_INSTITUTIONS · HOLIDAYS · PRECINCTS
    │                    · SLATE_PARTNERS · SURROGATES · AD_CREATIVE · MAIL_TEMPLATES
    │                    · COPE/ED_BOARD/DEM_PARTY interview banks
    │                    · BIDS · NEIGH_COUNCILS · CRISIS_TREES
    ├── STATE           mutable game state (Phase 1+2+3 fields)
    ├── ENGINE          turn resolver · vote calc · ceilings · staff · IEs
    │                    · press · voter file · debates · payroll · FPPC
    │                    · ad runs · slate · surrogates · crisis trees
    │                    · institutional minigames · runoff realignment
    ├── ACTIONS         40+ actions across fund / field / endorse categories
    ├── EVENTS          calendar-bound + randomized + crisis triggers
    ├── UI              13-tab main view + 6 modals (event, debate, crisis, COPE/ed-board/dem-party, prompts)
    └── PERSIST         localStorage save/load
```

### Tabs
Schedule · Field & Voter File · Languages & Faith · Endorsements · Institutions · Press · Creative · Slate & Surrogates · IEs / PACs · Money · Polls · Staff · Strategy

### Game loop (52 weeks)
Each week: calendar event → debate trigger → staff auto-run → IE decision/spend → press drift → public poll → voter file → payroll → ad run continuation → slate exposure → surrogate residual → crisis check → opponent AI → affinity decay → discipline drift → burnout/scandal → FPPC filing → random event → recompute support → advance week.

---

## Election rules modeled

- Filing deadline: March 6, 2026 · Voter reg deadline: May 18 · Primary: June 2, 2026 · General/runoff: November 3, 2026
- Council contribution limit: $500/donor · Citywide limit: $1,700/donor
- Public matching: 6:1 ratio; 100 (council) / 500 (mayor) qualifying donors
- 3-word ballot designation (LA Clerk rule)
- FPPC Form 460 schedule (1/31, 4/24, 6/30, 10/24)
- Primary/runoff are separate elections for contribution limits

---

## Files

- `index.html` — the playable game (~4,200 lines)
- `README.md` — this file
- `DESIGN_PHASE2.md` — Phase 2 architecture doc

## Sources

Mayor: [Wikipedia](https://en.wikipedia.org/wiki/2026_Los_Angeles_mayoral_election), [Ballotpedia](https://ballotpedia.org/Mayoral_election_in_Los_Angeles,_California_(2026)), [LAist mayor guide](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-mayor), [UCLA Luskin poll](https://luskin.ucla.edu/volatility-ahead-in-la-mayors-race-ucla-luskin-poll-finds-40-of-voters-undecided), [Pat Brown / LWV / FOX 11 mayoral debate](https://www.foxla.com/news/la-mayoral-debate-bass-pratt-raman-wildfires-homelessness).
Council races: LAist district guides ([CD1](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-1), [CD3](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-3), [CD5](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-5), [CD9](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-9), [CD11](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-11), [CD13](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-13), [CD15](https://laist.com/news/politics/voter-guides/2026-election-california-primary-la-city-councilmember-district-15)).
Election rules: [LA City Clerk](https://clerk.lacity.gov/elections/municipal-elections), [LA Ethics Commission](https://ethics.lacity.gov/publications/contributor-guide-2026-elections/), [LA Code §23.102.3 ballot designation](https://codelibrary.amlegal.com/codes/los_angeles/latest/laac/0-0-0-86800).
Neighborhoods: Wikipedia [CD1](https://en.wikipedia.org/wiki/Los_Angeles%27s_1st_City_Council_district), [CD13](https://en.wikipedia.org/wiki/Los_Angeles_City_Council_District_13).
Pollsters: [Tulchin Research](https://tulchinresearch.com/), [FM3 Research](https://fm3research.com/).
Consulting archetypes: [Bearstar Strategies](https://bearstarstrategies.com/team/), [North Star Alliances](https://www.northstaralliances.com/about-us).
Endorsements: [LA Fed](https://thelafed.org/resource/lalaborvoterguide/), [UTLA](https://utla.net/campaigns/2026-endorsements/), [LA Forward](https://www.laforward.org/endorsements).

---

## Part 2 — In Office (Governing Mode)

A second way to play, from the title screen via **"Start sworn in — Govern (2027)."** Instead of campaigning, you take office on **December 14, 2026** (the real second-Monday-of-December term start) as either the **Mayor** or a **City Councilmember**, and govern a four-year term in **biweekly turns** to re-election in November 2030.

Grounded in the real, near-final June 2026 results and the actual LA City Charter (see `GOVERNANCE_REFERENCE.md`):

- **Real 2027 council** — all 15 seats with the actual members (six odd-seat incumbents re-elected; CD3 & CD9 open-seat runoffs you resolve; even seats carried from 2024), each with an ideology vector that drives realistic coalition behavior.
- **Real thresholds** — ordinances pass at **8 of 15**, veto overrides at **10**, urgency/charter items at **12**. The progressive/DSA bloc is a minority you must build past.
- **The mayoral cliffhanger** — Bass vs Raman went to a November runoff; you choose the winner. Pick **Mayor Raman** and CD4 goes vacant under Charter §409.
- **Legislation pipeline** — introduce real 2026–27 bills (SB 79 upzoning, Inside Safe, LAPD hiring, RSO, councilmanic-prerogative reform, council expansion, LA28, wildfire rebuild, the budget), move them through committee, **whip votes with political capital**, then face the mayor's veto / council override.
- **Biweekly events** — realistic, often action-triggered: encampment fights, developer pay-to-play (with a Huizar-style federal-probe risk), labor strikes, LAPD controversies, state preemption, budget shortfalls, Olympics logistics, wildfire recovery.
- **The real budget cycle** — a spring budget decision every year (Apr 20 propose -> Jun 1 adopt).
- **Three win vectors** — pass an agenda, hold approval to win re-election, survive the crises. Your end-of-term **legacy score** blends all three.

---

## Governing Mode v3 — A real city engine

Governing is now a simulation with consequences, not a menu of one-off buttons.

- **Live city-state engine.** The city carries real metrics — homelessness (sheltered/unsheltered), affordable & total homes built, LAPD sworn, a crime index — that evolve every turn. Do nothing and things drift worse; act and they respond, gradually.
- **Lagged, contingent, fallible pipelines.** Passing SB 79, Inside Safe, LAPD hiring, ED1, etc. feeds multi-year pipelines that deliver over months, cost money, can be **cut by the Council/County/State/feds**, and carry **court/audit reversal risk** (the real ED1 lawsuits and Inside Safe audit show up as delayed events). Inside Safe houses people gradually with a ~40% return-to-street rate.
- **Outcomes dashboard.** Live trend lines for homelessness, crime, homes built, and LAPD staffing, each with a green/red trend arrow.
- **Real-dollar budget.** Actual revenue sources (property, business, UUT, sales, volatile hotel tax…) that move with the economy, department spending in millions, fixed/locked costs, a live balance/deficit meter, and a reserve fund. Funding a department raises its health (and its outcomes); underfunding starves it; a deficit drives the reserve below the 2.75% floor into a **fiscal emergency** that hits every service.
- **31 real bills and 29 real events** drawn from current LA: ED1 codification, Measure ULA defense/repeal, 41.18 sweeps, oil-drilling phase-out, the Olympic wage, sanctuary protections, the DWP reservoir liability, HUD freezes, the County pulling LAHSA funds, ICE raids on vendors, heat waves, the Palisades insurance crisis, and more.
- **Mayor traits & the CD4 vacancy.** Raman: +1 action point and a warmer progressive bloc. Bass: +2 political capital/turn and a warmer establishment. If you play Mayor Raman, fill the vacated CD4 seat under Charter §409 (caretaker, moderate, or a special election).

See `LA_RESEARCH_V3.md` for the sourced data and design behind the engine.

