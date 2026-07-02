<p align="center">
    <img src="assets/Maquette-du-REM-au-DIX30-Miniature.jpg" alt="Cute but ironic maquette"><br>
    <em>Image courtesy of the REM and illustrator/muralist Vincent Toutou</em>
</p>

# Eight Weeks Without the REM: An Analysis of Open Data

When the REM suspended service between Brossard and Gare Centrale from July 5 to August 17 2025, the RTL (Réseau de transport de l'agglomération de Longueuil) put a shuttle bus network in place for the sake of service continuity.

Given the transit disruption, where did the people that relied on the REM go, and what did they do instead? Was the shuttle bus a part of the solution?

This notebook uses open GTFS data from the RTL to assess the shuttle system on based on coverage, frequency, and travel time.

---

## Research Questions

### Primary question: *operational scope*

- Did the RTL shuttle system provide a meaningful replacement for REM service during the summer 2025 closure?
  -  as measured by:
     -   scheduled frequency
     -   travel time
     -   stop coverage.
- Where specifically did the REM riders go?
  - Did they take the shuttle services?
  - Did they try to bypass the closure with buses to the Yellow Line?
  - Did they switch to driving/carpooling?

### Secondary question: *strategic scope*

- Did the RTL anticipate demand for the replacement network? What can we glean about their operational strategy?
  - Specifically, did they increase frequency on the bus routes during the closure window relative to baseline?
  - Which buses at which nodes were changed?

---

## Data sources

| Dataset | Source | Purpose |
|---|---|---|
| RTL GTFS 20250623 | RTL open data | BASELINE: normal scheduled service before closure |
| RTL GTFS 20250707 | RTL open data | DURING CLOSURE: shuttle routes and frequency changes |
| RTL GTFS 20250825 | RTL open data | POST-CLOSURE: normal service restored |

---

## Notebook Structure

### 1. Data setup

Load GTFS feeds. Define the closure window (July 5 - August 17, 2025) and the comparison period (same dates in 2024).

### 2. Establishing a baseline understanding

Extract normal REM service from the pre-closure GTFS feed. Profile the route: stops, scheduled headways and end-to-end travel time (Brossard to Gare Centrale).

> A note on "headways", for those unfamiliar: a headway is the measurement of time interval between consecutive vehicles (such as a bus or train) traveling along the same route. This notebook refers to them a lot.

### 3. The analysis part

Extract replacement services from the mid-closure GTFS feed and profile two alternatives riders had:

**Shuttle service:** stop coverage, headways, and scheduled travel time vs. the REM baseline.

**Longueuil metro bus routes:** RTL routes serving Longueuil–Université-de-Sherbrooke (Yellow Line). Did RTL increase scheduled frequency during the closure relative to baseline? A frequency increase is visible in the GTFS feeds and would indicate the agency anticipated demand for the traditional bus/metro path as a bypass to the shuttle.

### 4. What the data can and can't tell us

See [the analysis notebook](./analysis.ipynb##4-what-the-data-can-and-can't-tell-us) for a full set of conclusions and insights around limitations.

---

## Environment

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run jupyter notebook
```
## AI usage disclosure

Anthropic's Claude Sonnet 4.6 was used for:
- general planning
- code review
- generating boilerplate code (cell output formatting, etc.).

All code was either written by the author or carefully reviewed and validated by the author prior to use.
The author is solely responsible for all data sourcing, statistical reasoning, methodological decisions, and interpretation.
