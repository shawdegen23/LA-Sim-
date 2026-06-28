# LA Sim — Phase 2 (Campaign deep-dive) design doc

Phase 1 shipped a playable campaign loop with weekly Action Points, bloc-level affinity, and endorser progress bars. Phase 2 keeps that frame but adds the texture that real LA campaigns operate inside: staff, scheduled days, neighborhoods, debate prep with topic-specific answers, press relationships, IEs, a voter-file/GOTV layer, polling cross-tabs, and message discipline.

## Goals

1. **More to do** — replace the flat 10-AP menu with a richer time budget and 30+ distinct actions.
2. **More to track** — staff, donors, voter file, IEs, press, FPPC filings, ballot designation, message discipline.
3. **More realism** — every new entity (staff, reporters, IEs, pollsters, consultants) is named or based on real LA campaign-industry players.
4. **Tradeoffs intensify** — finite slots + payroll burn + scandal risk forces hard choices.

## Mechanic changes

### From AP to Schedule

Phase 1: 10 AP per week, drag actions until empty.
Phase 2: each week is a 7-day × 3-slot grid (21 slots), of which the player personally fills ~12 (the rest are personal/family/sleep). Different actions consume different numbers of slots — a debate prep session is 1 slot, a major donor dinner is 1 evening slot, a tour with press is 2 morning slots. Saturday & Sunday slots are fully available and weight toward field events.

Staff produce parallel "staff actions" each week without consuming player slots — so a Field Director adds 2 free door-knock waves per week, a Comms Director plants 1 op-ed pitch, etc. Staff effectiveness is gated by the staffer's tier (1=junior, 2=senior, 3=star).

### Staff (new)

Hire from a roster of candidates with role × tier × salary. Real LA-region archetypes (and a few real firm names where appropriate as suggested affiliations).

Roles:
- **Campaign Manager** — global efficiency multiplier; required to field above-the-line operations
- **Field Director** — runs door-knocking, phone-banking, voter-file ops
- **Communications Director** — pitches reporters, drafts releases, prep notes for debates
- **Finance Director** — runs the call-time book, reports to FPPC, manages burn rate
- **Pollster** — internal tracking polls every 2-3 weeks; unlocks cross-tabs
- **Consultant (general / on retainer)** — Bearstar Strategies-tier strategist or boutique; high cost, big strategic boost
- **Digital Director** — runs paid digital, social, micro-influencer outreach
- **Volunteer Coordinator** — keeps volunteer count from decaying, plus runs phone banks

Hiring pulls from a small pool of named roster candidates (fictional, archetype-based) per role. Fire = severance hit. Mismanagement (overworked, underpaid) = staff quits and leaks.

Salary cadence is monthly (every 4 game weeks). Burn rate display shows "weeks of runway" at current cash + commitments.

### Geographic depth: Neighborhoods

Each race now has a **neighborhood layer** under blocs. A neighborhood maps onto bloc weights. Door-knock and event actions target a specific neighborhood, which converts to bloc affinity bumps via the neighborhood's bloc mix. Real neighborhoods used:

- **CD1**: Highland Park, Echo Park, Chinatown, MacArthur Park, Pico-Union, Koreatown, Cypress Park, Lincoln Heights, Mt. Washington, Glassell Park
- **CD3**: Woodland Hills, Tarzana, Reseda, Winnetka, Canoga Park
- **CD5**: Beverly Grove, Fairfax, Pico-Robertson, Westwood, Cheviot Hills, Bel Air-Beverly Crest, Mid City, Palms
- **CD9**: Historic South Central, Exposition Park, USC Zone, Florence, Vermont-Slauson, South Park, Convention/LA Live
- **CD11**: Pacific Palisades, Brentwood, Venice, Playa del Rey, Westchester, Mar Vista
- **CD13**: Hollywood, Silver Lake, Echo Park, Atwater Village, East Hollywood, Thai Town, Larchmont, Little Armenia, Historic Filipinotown, Atwater
- **CD15**: San Pedro, Wilmington, Watts, Harbor Gateway, Harbor City
- **Mayor**: All 15 council districts as "regions" with rough weight

Each neighborhood event has a chance to surface a hyperlocal issue (e.g., "Highland Park parking and restaurant scene", "Chinatown rent stabilization", "San Pedro port cleanup") that a player can take a stand on.

### Debates as a real minigame

Phase 1 had "debate prep" tokens that abstractly improved debate outcomes. Phase 2 makes each scheduled debate (4 mayoral, 2 council per cycle) a multi-question minigame:

- 5–8 topic questions per debate
- Each question lists 3–4 answer choices keyed to issue lanes
- Choosing an answer moves bloc affinity (positive in aligned blocs, negative in conflicting ones)
- Real LA topics: Inside Safe, ICE response, SB 79 / housing, LAPD staffing, Olympics 2028, Palisades Fire recovery, Measure ULA, sanctuary city, encampment sweeps
- Debate prep tokens unlock a "smart" preview that hints at bloc impact for each choice
- Performance score affects post-debate news cycles, polling lift, and IE activity

### Press / reporter relationships

A small roster of beat reporters per outlet with cultivable relationships:
- LA Times: David Zahniser-archetype / Dakota Smith-archetype (City Hall)
- LAist: Frank Stoltze-archetype, Larry Mantle (AirTalk host)
- KCRW: Anna Scott-archetype (housing/homelessness beat)
- Spectrum News 1: Inside the Issues archetype
- LA Public Press / LA Reported (independent)
- Capital & Main, CalMatters
- FOX 11, KTLA, NBC4, ABC7
- Local: theeastsiderla.com, Westside Current

Actions: schedule sit-down (1 morning slot), pitch a story, give an exclusive scoop, decline interview (relationship cost). Each reporter has an outlet, a beat (housing / police / fire / labor / general), and a "stance" toward your candidacy that drifts based on relationship + your message discipline.

A high-relationship reporter generates favorable earned-media news cycles. Low-relationship can plant unflattering items.

### Independent Expenditures (IEs / super-PACs)

A small set of real-feel IE entities that decide whether to spend FOR or AGAINST you:

- **LA Police Protective League IE** — pro-police, anti-progressive, big spender
- **Working Families IE / LA Fed PAC** — pro-labor candidate
- **BizFed PAC** — pro-small business, pro-Olympics
- **California Apartment Association IE** — anti-tenant-strict candidates
- **LA Tenants Power IE** — pro-tenant
- **Charter Public Schools IE** — splits in council races
- **Environment LA IE** — pro-climate
- **Fire Survivors PAC** — fire-recovery focused (CD11/Mayor)

Each IE has a "decision week" early in the campaign where it picks a side based on alignment. Once committed, it spends weekly (cash equivalent in TV, mail, digital). IEs cannot coordinate but their spend appears in your news feed and on opponent affinity. Players can lobby IEs (1 slot/week) to influence them but cannot accept anything coordinated.

### Voter file & GOTV universe

Replaces simple "GOTV score" with three identified-voter buckets:

- **1x supporter** (light identification — said yes once)
- **2x supporter** (committed — pledged to vote, on ballot-chase list)
- **3x supporter** (champion — committed + advocate, asked to recruit 3 friends)

Door-knocks/calls move voters from cold → 1x → 2x → 3x. After May 4 (week 30), you start "ballot chase" — 2x and 3x supporters need a return to count. VBM return rate for each bucket: cold ~25%, 1x ~45%, 2x ~75%, 3x ~92%. GOTV activities push 1x→2x and 2x→3x, raising effective turnout.

This converts to a turnout multiplier in election resolution, replacing the old `gotv` scalar.

### Polling cross-tabs

Without a pollster, you only see public polls (released via news cycles). With a pollster:
- Internal poll every 2-3 weeks
- Cross-tabs by bloc: see your support, opponent's, undecided %
- Cross-tabs by age, geography, ethnicity (where available)
- Identifies "soft" supporters and weakest blocs
- Costs $25K (council) / $90K (mayor) per poll

### Message discipline / Theory of the case

At character creation (or after pickup), the player picks:
- A **theory of the case** (one-sentence pitch — choose from 6 archetypes per race)
- A **hero issue** (one of your three issue lanes that gets reinforced)
- A **ballot designation** (3-word occupation, real LA Clerk rule)

A "discipline meter" tracks how on-message you stay in choices: speeches, debates, op-eds. High discipline → low-info voters lock in; low → confused, chasing every news cycle.

### Money realism

- **Burn rate** displayed weekly (cash, expected outflow, weeks of runway)
- **FPPC filing deadlines**: 1/31 (year-end), 4/24 (pre-primary), 6/30 (semi-annual), 10/24 (pre-general). Missed = ethics fine, news cycle.
- **Vendor expenses** auto-deducted (mail house, ad agency on retainer, polling)
- **Self-loan** option ($5–50K, must be repaid before end-of-cycle or scandalous)
- **Burn-rate scandal** trigger: spending more than $50K/week as a council candidate with no tangible signal makes the press and donors notice

## Data structures (additions)

```js
NEIGHBORHOODS = {
  highland_park: { name: "Highland Park", district: "cd1",
    blocMix: { lat_renter: 0.3, prog_renter: 0.4, lat_homeowner: 0.2, white_gentry: 0.1 },
    pop: 56000, flavor: "Gentrifying. Restaurants on York. NELA Forward turf." },
  ...
}

STAFF_ROLES = {
  campaign_manager: { name: "Campaign Manager", baseSalary: 8000, ... },
  ...
}

STAFF_POOL = [  // hireable named candidates
  { id: "gomez", name: "Maria Gomez", role: "campaign_manager", tier: 2, salary: 7500, bio: "..." },
  ...
]

REPORTERS = {
  zahn: { name: "[Zahniser-arch]", outlet: "LA Times", beat: "city hall", cultivable: true },
  ...
}

IES = {
  lappl_ie: { name: "LA Police Protective League IE", ... },
  ...
}

DEBATE_BANK = {
  mayor: [ { topic: "Inside Safe", prompt: "...", choices: [...] }, ... ],
  council_generic: [ ... ],
}

THEORIES = {
  mayor: [ "Steady hand", "Throw the bums out", "Rebuild after fire", ... ],
  council: [ ... ]
}
```

## UI changes

Tabbed main view replaces the three-column dashboard:
- **Schedule** — weekly grid, drag/click to fill slots
- **Field** — neighborhoods, voter file, GOTV
- **Endorsements** — same as Phase 1, deeper
- **Press** — reporter list & relationships
- **Money** — burn rate, FPPC, IE feed
- **Polls** — public + internal cross-tabs
- **Staff** — team management
- **Strategy** — theory of case, message discipline, ballot designation

Top bar always shows: Date, Cash, Weeks-of-runway, Modeled support, Name ID, Burnout, Discipline.

## Build plan

1. Extend `DATA` block with neighborhoods, staff pool, reporters, IEs, debate bank, theories
2. Replace AP with slot system in `STATE` and `endWeek`
3. Refactor `ACTIONS` to slot-cost actions; add 15+ new actions
4. New `engineDebate(g, debateId)` minigame
5. New `pressTick(g)` weekly relationship/news drift
6. New `iesTick(g)` weekly IE decision/spend
7. New `voterFileTick(g)` and replacement for GOTV scalar
8. UI: tabbed main view, schedule grid, voter file dashboard, debate modal, press relationship cards
9. Re-balance: final-week win rates: random play 5-10%, smart play 50-70% in winnable races, 20-35% in stronghold races

## What remains for future phases

- **Phase 3 (governing)**: post-election, you take office, vote, navigate crises, run for re-election
- Precinct-level (under-neighborhood) field
- Real-time multiplayer / leaderboard
- SVG district maps
- Sound, animation
