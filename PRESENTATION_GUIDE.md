# Presentation Guide — Indian Railways Network
## YTS+ DSEB 2026 · Plaksha University

---

## A suggested spine

This is a starting point, not a template. You found your own interesting things — decide where they live.

| # | Slide |
|---|---|
| 1 | Cover — team, project, date |
| 2 | The question: which station, if it shut down, causes maximum disruption? |
| 3 | The raw data — 417,080 stops, 4,888 trains, 8,697 stations |
| 4 | How we built the network — consecutive stops become edges |
| 5 | The skip edge problem — and how we fixed it |
| 6 | The simplest measure: who is most connected? |
| 7 | The answer — familiar names, spread across India |
| 8 | A different measure: who controls the flow? |
| 9 | The answer — names you have never heard of, all in Bihar |
| 10 | Why do the two measures disagree so completely? |
| 11 | Why Bihar? Geodesic vs train distance |
| 12 | The Ganges — the physical reason |
| 13 | The removal test: shut down one station |
| 14 | The colonial finding: when were these stations built? |
| 15 | What the network cannot see |
| 16 | Our answer — one station, one sentence |

Found something the notebooks didn't ask for? Put it in. Something here doesn't apply? Cut it.

---

## Explaining how the network was built

This project is unusual: the network is not given to you. You built it from raw timetable data. That construction has a problem and a solution — and both are worth explaining clearly, because they affect what your results mean.

**The raw data is schedules, not tracks.**
A train schedule lists which stations a train stops at, in order. To build a track network, you connect each pair of consecutive stops. But express trains skip stations — a train running Delhi to Prayagraj without stopping at Kanpur creates a false direct edge between Delhi and Prayagraj. That edge does not represent physical track.

**How we detected skip edges.**
Distance alone cannot find them — some genuine track connections are long (remote desert and mountain regions). The actual test uses three steps:

1. Flag every edge longer than 60 km as suspicious
2. For each suspicious edge A→C, find stations already connected to both A and C by other trains
3. If any such station B lies geographically between A and C — meaning `distance(A,B) + distance(B,C) < 1.3 × distance(A,C)` — then the train bypassed B. Mark A→C as a skip edge and remove it.

The 1.3 factor allows for natural track curvature — physical rails are never a perfect straight line.

**Say what this means for your results.**
Your network represents physical rail infrastructure — the iron in the ground — not train routing choices. Every finding that follows is a finding about the structure of the track, not about how any particular train runs.

This is slide 5. One diagram: raw network on the left (including false long-distance edges), filtered network on the right (physical track only). State the result: 8,612 real connections.

---

## Presenting to someone who has never seen a network

Your audience travels on Indian Railways. They do not know what betweenness centrality is.

**Introduce each concept at the moment you need it — not before.**
When you introduce degree, explain it in one sentence — "how many stations are directly connected to this one" — then immediately show the ranking. Same for betweenness. The concept earns its place by doing something surprising right away.

**Show it first, name it second.**
Show the betweenness ranking before defining betweenness. Let the audience see Bihar dominate a list of names they have never heard of. Then explain what the measure captured. The name lands as recognition, not vocabulary.

**Say what question the concept answers before explaining the concept.**
Before betweenness: *"Degree tells us who is most connected. But we wanted to know something different — who does every journey have to pass through? That is what betweenness measures."*

---

## Telling the story

**Slide 2 states the question before showing any data.**
This is unusual — most presentations show data first. Do it anyway. The audience needs to know what they are trying to answer before they can follow the evidence.

**The disagreement between degree and betweenness is your finding — not your problem.**
When degree says Moradabad and betweenness says Tilrath, that is not a contradiction to explain away. That is the result. Each finding should make the next one feel necessary: *"Degree gives us the most connected stations. But connection is not the same as control — which led us to betweenness, and a completely different list."*

**The Bihar slide is the payoff.**
Everything before it builds to one question: why do stations no one has heard of control the entire network? The Ganges answer is the moment the data connects to the physical world. Don't rush past it.

**The last slide is your answer.**
One station. One sentence. The number from the removal test. If the answer is genuinely uncertain — several Bihar stations cluster together and removing any one has similar effects — say that honestly.

---

## Before you finalise any slide

**Showing how something works is not the same as saying what it means.**
"Tilrath has betweenness rank #5" is a result. "Remove it and the east half of India loses its connection to the west" is an interpretation. Both must appear on the same slide.

**Degree and betweenness need to say why they are not the same question.**
When you introduce betweenness, open explicitly with what degree cannot answer. If the two measures look like the same thing to the audience, the disagreement between them won't land.

**Read just your slide titles. Does the story make sense?**
Before presenting, read the titles alone, in order. They should tell the investigation from question to answer.

**Your slide title should say exactly what the slide claims — not bolder, not softer.**
"Bihar controls Indian Railways" is bolder than what the data shows. "Betweenness rank: four Bihar stations in the top 10" is accurate.

**Explain every term the first time it appears — in one sentence, inline.**
Not a separate slide. One parenthetical on first use: *"betweenness centrality (the fraction of all shortest journeys that pass through a station)."*

---

## Chart rules

1. Label every axis — name and unit
2. No index numbers on axes — replace 0, 1, 2, 3 with actual station names or values
3. Title states the finding, not the variables
4. One chart, one claim
5. Don't put it in if you can't explain every element — you will be asked
6. Label the interesting point directly — if Tilrath is your finding, annotate it on the chart
7. If you use ranks, say which direction is better — write *(1 = most critical)*
8. Remove decoration that carries no information
9. Consistent colours — if Bihar stations are highlighted in one chart, highlight them the same way in every chart
10. Every number visible on the chart comes out of your mouth

---

## Images

- Charts you generated: always fine
- Maps from your notebook output: always fine
- Google Maps screenshots: do not use — restricted licence
- OpenStreetMap: fine, include attribution — *© OpenStreetMap contributors*
- Wikipedia images: fine, include the URL below the image

---

## Citation

> DataMeet. (n.d.). *Indian Railways train schedule data* [Dataset]. GitHub.
> https://github.com/datameet/railways

Put this on the slide where you introduce the data.
