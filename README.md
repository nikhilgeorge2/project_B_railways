# Project B — Indian Railways Network
## YTS+ DSEB 2026 · Plaksha University

---

## What this project is

You will analyse the actual Indian Railways timetable as a network, then present what you found as an investigation report.

The network measures physical track connections weighted by train frequency — not passengers, not freight, not economic importance. A packed express and an empty goods train look identical in this data. Everything you find must be interpreted through that constraint.

---

## Getting started

```bash
git clone https://github.com/nikhilgeorge2/project_B_railways.git
cd project_B_railways
jupyter notebook
```

Work through the notebooks in order:

| Notebook | What you do |
|---|---|
| `nb1_build_the_network.ipynb` | Understand the raw schedule data, build the physical track network |
| `nb2_who_matters.ipynb` | Compute degree and betweenness, compare them, run the removal simulation |
| `nb3_why_bihar.ipynb` | Measure geodesic vs train distance, map the barriers, research founding years |

---

## The data

417,080 individual station stops · 4,888 trains · 8,697 stations

The raw source is the Indian Railways timetable. Track connections represent physical rail links; edge weights are the number of trains sharing each connection.

---

## The presentation

**15–20 slides. You choose the structure.**

Before you open any slide software: go back through your notebooks and find the moment where you thought *that's weird* or *I didn't expect that*. That is your presentation.

Every good investigation report has five parts:

1. **The question** — what did you set out to understand?
2. **The instrument** — what does your data measure, and what does it not?
3. **What you found** — three to five findings, each with a number
4. **Where the data surprised you** — the most important part
5. **Your answer** — one station, one sentence, data-backed

---

## Chart rules

Every chart you put in the presentation must follow these:

1. Label every axis — name and unit
2. No index numbers on axes — 0, 1, 2, 3 from your dataframe carry no information; replace them with actual station names or values
3. Title states the finding, not the variables — not *"Degree rank vs betweenness rank"* but *"Two measures, two completely different answers"*
4. One chart, one claim
5. Don't put it in if you can't explain every element — you will be asked
6. Label the interesting point directly — if Tilrath is your finding, annotate it on the chart
7. If you use ranks, say which direction is better — write *(1 = most critical)* on the chart
8. Remove decoration that carries no information — no 3D bars, no background gradients
9. Consistent colours — if Bihar stations are highlighted in one chart, highlight them the same way in every chart
10. Every number on the chart comes out of your mouth — if you skip over it while presenting, it shouldn't be there

---

## Image policy

- Charts you generated: always fine
- Google Maps screenshots: **do not use** — restricted licence
- OpenStreetMap: fine, include attribution — *© OpenStreetMap contributors*
- Wikipedia images: fine, include the URL below the image
- Your charts are your visuals — every slide that makes a claim should show the chart that backs it

---

## Data citation

> DataMeet. (n.d.). *Indian Railways train schedule data* [Dataset]. GitHub.
> https://github.com/datameet/railways

Cite this on the slide where you introduce the network.
