# Eight Weeks Without the REM

When the REM suspended service between Brossard and Gare Centrale from July 5 to August 17 2025, the RTL (Réseau de transport de l'agglomération de Longueuil) put a shuttle bus network in place for the sake of service continuity.

The question: during that downtime, where did the people that relied on the REM go? What did they do instead?

This notebook uses open GTFS data from the RTL and Bixi trip data to assess the shuttle system on the dimensions that matter to riders and agencies alike — coverage, frequency, and travel time — and then looks for a behavioural signal in Bixi ridership near REM stations during the closure.

---

## Research Questions

### Primary Question
*operational scope*
- Did the RTL shuttle system provide a meaningful replacement for REM service during the summer 2025 closure?
  -  as measured by:
     -   scheduled frequency,
     -   travel time,
     -   and stop coverage.
- Where specifically did the REM riders go?
  - Did they take transit (i.e. use the replacement network),
  - or did they switch to driving/carpooling/Bixi?

### Secondary Question
*strategic scope*
- Did the RTL anticipate demand for the replacement network? Specifically, did they increase frequency on the Longueuil metro bus routes during the closure window relative to baseline (a scheduling decision visible in the GTFS feeds, and a meaningful proxy for expected demand)?

### Tertiary Question:
*behavioural scope*
- Is there a detectable change in Bixi ridership near island-side REM stations during the closure window, consistent with riders seeking alternatives?



---

## Data Sources

| Dataset | Source | Purpose | Scope |
|---|---|---|---|
| RTL GTFS 20250623 | RTL open data | BASELINE: normal scheduled service before closure | operational, strategic |
| RTL GTFS 20250707 | RTL open data | DURING CLOSURE: shuttle routes and frequency changes | operational, strategic |
| RTL GTFS 20250825 | RTL open data | POST-CLOSURE: normal service restored | operational |
| Bixi trip data 2025 | Bixi open data | Behavioural proxy during closure window | behavioural |
| Bixi trip data 2024 | Bixi open data | Year-over-year control | behavioural |

---

## Notebook Structure

### 1. Setup
Load GTFS feeds and Bixi trip data. Define the closure window (July 5 - August 17, 2025) and the comparison period (same dates in 2024).

### 2. The REM Baseline

Extract normal REM service from the pre-closure GTFS feed. Profile the route: stops, scheduled headways, and end-to-end travel time (Brossard to Gare Centrale).

### 3. The Replacement Options

Extract replacement services from the mid-closure GTFS feed and profile two alternatives riders had:

**Shuttle service:** stop coverage, headways, and scheduled travel time vs. the REM baseline.

**Longueuil metro bus routes:** RTL routes serving Longueuil–Université-de-Sherbrooke (Yellow Line). Did RTL increase scheduled frequency during the closure relative to baseline? A frequency increase is visible in the GTFS feeds and would indicate the agency anticipated demand for the traditional bus/metro path as a bypass to the shuttle.

### 4. Gap Analysis

Three-way comparison: REM baseline vs. shuttle vs. Longueuil metro bus option:
- Did the shuttles serve all REM stations?
- How did headways compare across all three options?
- How much longer was each alternative journey?
- Theoretical capacity: buses vs. automated trains

### 5. The Bixi Signal

Compare Bixi trips starting or ending within 500m of Gare Centrale (island-side REM terminus) during peak commute hours (7–9am, 5–7pm):
- Closure window 2025 vs. same period 2024
- Simple before/after framing

### 6. What the Data Can and Can't Tell Us
- GTFS captures scheduled service, not actual real-time operations or ridership
- The strategic scope question is answered in terms of RTL's intentions, not outcomes
- Bixi is a noisy proxy: summer weather and tourism muddy year-over-year comparisons

What better data would look like:
- Fare gate counts
- RTL passenger loads
- Anonymised trip plan data

---

## Key Limitations

- GTFS reflects scheduled service, not actual operations. On-the-ground reliability during the closure (traffic variance, bus bunching) is not captured.
- The secondary question is answerable from GTFS, but a frequency increase only confirms RTL planned for demand, not that riders actually used those routes.
- Bixi ridership near Gare Centrale is heavily influenced by factors unrelated to the REM (tourism, weather, downtown events). Any signal found should be treated as directional, not conclusive.
- No ridership denominator: without REM or shuttle passenger counts, modal shift rates cannot be calculated, only directional signals.

---

## Environment

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run jupyter notebook
```
