# Usability Study Summary

**Group 5:** Amin Sharifi · Kala Fejzo · Moreki Khobotlo
**Full transcript, per-participant notes, and debrief questions:** see the original usability test
write-up (script, tasks, and all 9 participant logs) kept separately by the team.

## Participants

9 participants tested the dashboard. Each was asked to pick one persona to role-play for the
session — prospective homebuyer, homeowner, real estate investor, real estate professional, or
policymaker/community planner — and to make decisions as that role would. Participants weren't
assigned identifying labels beyond a number; observed behavior below is grouped by the role their
comments/choices implied rather than a logged persona field.

| # | Apparent role / framing | Completed all tasks unassisted? |
|---|---|---|
| 1 | General homebuyer/investor | Yes |
| 2 | Homebuyer weighing safety vs. appreciation | Yes |
| 3 | Homebuyer / market-savvy user (compared to Zillow/Redfin) | Yes |
| 4 | Real estate professional (evaluating for clients) | Yes |
| 5 | Homebuyer prioritizing family safety | Yes |
| 6 | Analytically-minded user probing methodology | Yes |
| 7 | Homebuyer comparing nearby ZIPs | Yes |
| 8 | Investor wanting deeper financial due diligence | Yes |
| 9 | Detail-oriented user, expected direct polygon interaction | Yes |

## Tasks

**1. Wildfire Risk Assessment**
- Identify the neighborhood with the highest wildfire risk.
- Compare wildfire risk between Pasadena and Santa Monica.

**2. Housing Market Impact & Recovery Analysis**
- Identify the neighborhood with the highest home appreciation.
- Compare home appreciation between Pasadena and Santa Monica.
- Identify the neighborhood that recovered fastest after a wildfire event.
- Describe how housing values changed before and after a wildfire event.

**3. Investment Decision Support**
- Acting as a long-term investor, recommend one ZIP code/neighborhood using all available layers
  and justify the choice over the alternatives.

## Main findings

**Strengths** — consistently observed across participants:
- Tasks completed with minimal to no assistance.
- Dashboard perceived as visually polished and professional ("something Zillow or Redfin could
  build").
- Choropleth + wildfire risk layer were easy to read and interpret correctly.
- Investment Category layer was useful for quickly narrowing down neighborhoods.
- Participants liked having wildfire, housing, and investment data unified in one place instead of
  cross-referencing multiple sites.

**Recurring issues:**
- The Investment Opportunity Score's calculation wasn't understood, even by participants who used
  it to make a decision (Participants 1, 6).
- The layer controls were initially overlooked by some participants (Participant 1).
- Multiple participants expected the ZIP polygons themselves to be clickable, not just the numbered
  pins (Participant 9).
- A search bar for ZIP/neighborhood was requested for faster navigation (Participant 3).
- Requests for more decision-support data in the popups: insurance costs (Participant 2), sales/
  inventory data (Participant 4), school ratings/emergency info (Participant 5), historical fire
  events (Participant 7), rental yield and longer appreciation history (Participant 8).
- Less experienced users wanted investment terminology explained in simpler language (Participant 1).

## Prioritized findings (MoSCoW) and current status

| Priority | Finding | Proposed improvement | Status |
|---|---|---|---|
| Must Have | Investment Opportunity Score calculation wasn't understood | Add an info icon explaining the methodology | **Done** — ⓘ toggle added next to the score in the masthead (see [`design_process/DESIGN_CHANGELOG.md`](design_process/DESIGN_CHANGELOG.md), row 3) |
| Must Have | Layer controls were overlooked by some users | Increase size/contrast/visibility of the layer control | **Done** — enlarged, bordered, and labeled "MAP LAYERS — TOGGLE TO EXPLORE" (changelog row 4) |
| Should Have | Users expected ZIP polygons to be directly clickable | Allow interaction with ZIP polygons, not just numbered markers | **Done** — click/tap popups added to ZIP polygons (changelog row 6) |
| Should Have | Users wanted a faster way to locate neighborhoods | Add a ZIP/neighborhood search bar | **Done** — search box added, top right (changelog row 5) |
| Could Have | Users wanted more neighborhood/financial context | Insurance costs, historical appreciation trends, rental yield, market inventory, recent sales in the popups | **Not done this pass** — these require sourcing and cleaning new datasets (FAIR Plan insurance data, MLS/inventory feeds, rental comps) that are out of scope for this iteration; flagged as the clearest next step |
| Could Have | Less experienced users wanted terminology explained | Tooltips/glossary for investment terms | **Partially done** — the Investment Score itself is now explained in place; a full glossary for other terms (e.g. "appreciation," "percentile rank") is not yet built |
| Won't Have (this version) | Predict future home values or insurance premiums | Consider for a future version | Out of scope, unchanged |

Four of the six actionable findings (both "Must Have" items and both "Should Have" items) are now
addressed in the current build. The remaining "Could Have" items are primarily blocked on new data
sourcing rather than interface changes, so they're the natural next step rather than something to
force into this pass.
