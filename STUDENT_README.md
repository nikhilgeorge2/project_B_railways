# Project B — Indian Railways Network
## Student Guide · YTS+ DSEB 2026 · Plaksha University

---

## The question you are answering

> *Which Indian railway station, if it shut down, would cause the most disruption across the entire country — and is the answer a station most people have never heard of?*

Your final presentation gives a data-backed answer to this question. The answer will probably surprise you.

---

## Before you open any notebook

Each student writes down independently — no discussion:
1. The 5 Indian railway stations you think are most critical to the network.
2. Your prediction: if you had to shut down ONE station to cause maximum disruption, which would you pick?

**Paper. Sealed. You will open these at the end of Notebook 2.**

---

## What you are working with

```
project_B_railways/
  nb1_build_the_network.ipynb       ← Session 1
  nb2_who_matters.ipynb             ← Session 2
  nb3_why_bihar.ipynb               ← Session 3
  data/
    stations_metrics.csv            ← all 8,697 stations with GPS, degree, betweenness rank
    track_edges_enriched.csv        ← all 8,612 physical track connections with distance and names
    train_stats.csv                 ← 4,888 trains with stop counts and distances
    betweenness_track.csv           ← pre-computed betweenness for physical track network
    betweenness_scores.csv          ← pre-computed betweenness for stop network
    stations_clean.csv              ← station codes, names, states, GPS
    track_edges.csv                 ← raw physical track connections
    geodesic_vs_train.csv           ← pre-computed straight-line vs train distance pairs
```

The data comes from real Indian Railways train schedules — 417,080 individual station stops from 4,888 trains. The two `_enriched` and `_metrics` files are simplified versions prepared for Notebooks 1; the raw files are used in Notebooks 2 and 3.

---

## What each notebook asks you to do

### Notebook 1 — Build the Network (Session 1)

You will understand what the raw schedule data looks like, explore express trains vs slow trains, understand how to build a physical track network from timetables (the skip edge problem), and then answer five real questions about Indian Railways using only pandas.

**Tools used:** pandas, matplotlib only. No complex libraries.

**At the end of Notebook 1 you will have:**
- A scatter plot of train distance vs average km between stops
- A map of all 8,612 physical track connections
- Answers to: longest gaps, dead end stations, total network length, densest/thinnest state coverage, busiest corridors
- A written answer: who does Indian Railways actually serve?

---

### Notebook 2 — Who Matters? (Session 2)

You will compute three different measures of station importance, compare them, and discover that they disagree dramatically — and that the disagreement is the finding.

**Tools used:** pandas, networkx, matplotlib.

Three measures:
| Measure | Question | What it counts |
|---|---|---|
| Degree | Who is most connected? | Number of direct track neighbours |
| Weighted degree | Who handles the most traffic? | Total trains through direct connections |
| Betweenness | Who controls the flow? | Fraction of shortest paths passing through |

**At the end of Notebook 2 you will have:**
- Ranked lists of all three measures
- A scatter plot showing where degree rank and betweenness rank disagree
- A removal simulation: stranded stations when you remove each of 6 key stations
- A written answer to the big question — and your sealed prediction opened

---

### Notebook 3 — Why Bihar? (Session 3)

You will measure how far trains must travel compared to the straight-line distance between stations. When the ratio is very high, there is a physical barrier forcing a detour. You will map these barriers across India, identify two different reasons ratios can be high, and research the founding years of the top-betweenness stations on Wikipedia.

**Tools used:** pandas, networkx, matplotlib, haversine formula (provided).

**At the end of Notebook 3 you will have:**
- Dijkstra's algorithm run from Patna — the Ganges crossing question
- A map of high-ratio pairs across India
- A written explanation of two mechanisms (river barrier vs hub-spoke)
- A Wikipedia research table of founding years
- A paragraph answering the big question with both data and history

---

## The presentation (Session 4)

10–12 minutes. 13 slides. Your team presents to the program. Required structure:

| Slides | Content |
|---|---|
| 1 | The question you set out to answer |
| 2–3 | The network: what it is, how it was built from timetables |
| 4–5 | Degree: who is most connected — familiar names, spread across India |
| 6–7 | Betweenness: who controls the flow — very different list, clustered in Bihar |
| 8–9 | Why Bihar: geodesic vs train distance, the Ganges river barrier |
| 10 | The removal test: which station's closure strands the most stations |
| 11 | The colonial finding: when were these stations built, and why |
| 12 | What the network cannot see |
| 13 | Your answer — one station, one sentence, data-backed |

Every claim in the presentation must be backed by a number or chart from your notebooks.

---

## What the network can and cannot see

The network measures physical track connections and train traffic from schedules. It can see:
- Which stations are directly connected by physical rail
- How many trains run on each connection
- Which stations every shortest path in the network must pass through
- How far trains must detour around geographic barriers

The network cannot see:
- Passenger or freight volumes (only train counts, not how many people are on each train)
- Platform capacity or operational congestion
- Economic importance of a city independent of its network position
- Political decisions about which cities get new connections

When the data gives an unexpected answer — a station you've never heard of ranking above New Delhi — ask: is the algorithm wrong, or is the data showing you something the headlines don't?

---

## How to run the notebooks

```bash
conda activate clean_env
jupyter notebook
```

Or open each `.ipynb` directly in VS Code or JupyterLab. Data loads from `data/` (relative path). No internet required except for the Wikipedia task in Notebook 3.
