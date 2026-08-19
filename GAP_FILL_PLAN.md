# AWT Coverage Gap-Fill Plan — Pilots N Paws Missed Missions

> **Source:** Slack thread — https://angelswingstransport.slack.com/archives/C07105PQ1U7/p1787111929243619
> **Date:** 2026-08-19

This plan turns the Pilots N Paws "Top Missed Missions Analysis (AWT Fit)" into concrete additions to the recruiting map's target group (the `airports` array in `index.html`) plus a coordination playbook. It responds to two directives from #coordinating-animal-and-veteran-flights: (a) make sure these gaps are part of our target group, and (b) make sure we have a plan to fill those gaps. Every airport reference below has been checked against the current `airports` array in `index.html`.

## 1. The gaps — five missed missions

| # | Route | Distance / legs | Date & outcome | Why it was missed |
|---|-------|-----------------|----------------|-------------------|
| 1 | Reno NV → Seattle — 2 cats | ~497 nm, 2 legs | Jul 10; cancelled Jul 21 — went by ground | Pilots offered both halves 11 days apart but nobody joined them. AWT owns this corridor. |
| 2 | Hailey ID → Roseburg OR — pit bull mix | ~396 nm, 1 leg | May 23, ready May 26; never flown / expired | A Paine Field pilot offered in 40 minutes; the thread then went silent. Cleanest miss in the set. |
| 3 | SF → Boise — two large dogs | ~454 nm, 3 legs | Jul 27; withdrawn Aug 5 | Nine days spent building a Lovelock NV handoff, killed by 100°F heat, a TFR, smoke, and missed notifications. |
| 4 | Menifee CA → Seattle — Dobie/pit mix | ~867 nm | Jun 24; zero replies in 30 days | Too long for AWT to fly whole, but nobody owned the northern third. |
| 5 | Porterville CA → Vancouver WA ("Levi") | ~598 nm, 2 aircraft, 2 days | Jan 7; flown Jan 13 — **succeeded** | Only succeeded because one Medford pilot chased it for six days. The 195 nm closing leg into Pearson (VUO) is AWT's exact corridor. |

## 2. The headline insight

- In **4 of 5** cases willing pilots were already on the thread — the failure was **coordination, not a lack of pilots**.
- Ground transport won twice on **certainty, not speed**.
- AWT's edge is **owning the 400–600 nm relay leg**, not competing for sub-250 nm hops that get covered in minutes.
- Conclusion: the fix is partly **geographic** (add the missing relay anchors to the target group) and partly **operational** (a playbook so AWT commits fast and owns its leg).

## 3. Gap → target-group mapping

Current target-group state per mission (verified against `index.html`):

- **Mission 1 (Reno → Seattle):** Seattle end covered — Paine Field (PAE, top), Boeing Field (BFI, high), Renton (RNT, home base). Redding (RDD) is on the map as the northern-California anchor / southern boundary of the service area. **Reno itself is missing**, despite the analysis stating AWT owns this corridor.
- **Mission 2 (Hailey → Roseburg):** Roseburg (RBG, medium) is covered. **Hailey / Sun Valley (an eastern-Idaho feeder) is missing.** Boise (BOI, top) is the nearest anchor on the map.
- **Mission 3 (SF → Boise):** Boise (BOI, top) is covered. **The CA origin and the NV relay waypoints (Lovelock / Winnemucca) are missing** — this is the same Nevada corridor gap as Mission 1.
- **Mission 4 (Menifee → Seattle):** The northern relay leg (roughly Redding → Seattle) is fully inside the current target group. The gap here is **operational — nobody claimed the northern third — not a missing airport.**
- **Mission 5 (Porterville → Vancouver):** Pearson (VUO, high) and Medford (MFR, high) are already covered — this mission **validates the current target group** and reinforces keeping MFR and VUO at high priority.

## 4. Gaps to close

### A. Geographic additions to the target group (`airports` array)

The `airports` array today runs from Bellingham (BLI) south to Redding (RDD) on the I-5 corridor and east to Boise (BOI) / Missoula (MSO) on the I-90 corridor. Available priority tiers are `top`, `high`, `medium`, and `home` (from `priorityConfig`); corridor values in use are `i5` and `i90`.

- **Add Reno, NV** (Reno-Stead RTS / Reno-Tahoe RNO) — the southern anchor of the US-395 / I-5 relay corridor the analysis says AWT already owns. Assign a **`top`** (or `high`) priority tier. A new corridor grouping may be warranted since it sits south/east of the current I-5 line.
- **Add Nevada relay waypoints** — Lovelock (LOL) and/or Winnemucca (WMC) — the CA/OR ↔ ID handoff points that both Mission 1 and Mission 3 needed.
- **Add an eastern-Idaho feeder** — Hailey / Sun Valley (SUN) — or explicitly designate Boise (BOI) as its collection point for missions originating in central/eastern Idaho.
- **Elevate / confirm priority** on the existing relay anchors the missions leaned on: Redding (RDD, currently medium), Medford (MFR, currently high), and Vancouver/Pearson (VUO, currently high).

### B. Model the relay itself (map / data enhancement)

The map currently draws only two visual corridor polylines (I-5 and I-90) and does **not** model relay handoff points or the 400–600 nm sweet spot. As a **future enhancement (not required now)**, tag airports as relay-handoff nodes and/or visualize the 400–600 nm relay range so recruiters can see where AWT should claim a leg rather than reading the map as a flat list of anchors.

## 5. The plan — actionable steps

1. **Map / data edits.** Add the airports from §4A to the `airports` array in `index.html` with `corridor`, `priority`, and `notes` fields, and update the header stat counts accordingly. *Owner: map maintainer.*
2. **Recruiting.** Run targeted outreach for pilots based at / near the newly added gap airports (Reno, the NV waypoints, eastern Idaho), and deepen the MFR / RBG / VUO closing-leg bench that Missions 2 and 5 depended on. *Owner: recruiting lead.*
3. **Coordination playbook ("own our leg").** When a cross-posted PnP mission touches an AWT corridor, AWT commits to a **specific leg fast** — define a target time-to-commit (e.g. within 24–48 h) rather than waiting for the whole relay to assemble. Designate a coordinator to claim the northern / closing leg on long-haul cross-state posts (the Mission 4 failure mode). *Owner: dispatch / coordination lead.*
4. **Redundancy on notifications / weather.** The SF → Boise miss died partly on missed notifications and summer heat / TFR / smoke. Build a lightweight watch so a mission in an AWT corridor isn't lost to a silent thread. *Owner: coordination lead.*
5. **Metrics.** Track missed missions in AWT corridors and time-to-commit over time to see whether the gaps are closing. *Owner: recruiting lead.*

## 6. Next steps

- Circulate this plan in the #coordinating-animal-and-veteran-flights Slack channel.
- Get sign-off on the specific airports to add (Reno RTS/RNO, Lovelock LOL, Winnemucca WMC, Sun Valley SUN).
- Implement the `index.html` edits in a follow-up PR.
