# Project B — Indian Railways Network
## Instructor Q&A Reference · YTS+ DSEB 2026

25 questions students will encounter or should be able to answer. Answers marked **[student]** vary by team.

---

### Part 1 — The Data and the Network

**1. What does an edge in this network represent?**
A physical track connection between two stations that are consecutive stops on at least one train — derived from train schedules, not from a track map.

**2. What does edge weight measure — and what does it miss?**
Number of trains running that connection. Misses: passenger volume, freight load, economic importance — one Rajdhani and one slow local both count as 1.

**3. What is the skip-edge problem?**
Express trains list non-consecutive stops as consecutive pairs — e.g. Delhi→Patna directly, creating a false 1,000 km "track edge" when no single physical track segment exists.

**4. How does the common neighbor test identify a skip edge?**
For long edge A→C: find stations B connected to both A and C. If distance(A,B) + distance(B,C) < 1.3 × distance(A,C), then B lies between them — the train skipped over B. Remove A→C.

**5. Why can't you just use a distance threshold to remove skip edges?**
Genuine track connections exist up to 894 km (remote desert/mountain areas). The shortest skip edge is 60 km. Distance alone cannot separate them.

**6. How many skip edges were removed, and what remains?**
63 skip edges removed from 8,675 raw pairs → 8,612 physical track connections.

**7. Why is haversine needed and why can't you subtract lat/lon?**
Latitude degrees are constant (~111 km) but longitude degrees shrink with latitude (111 km at equator, ~98 km at Delhi, zero at poles). Earth is a sphere — we need surface arc distance, not coordinate arithmetic.

---

### Part 2 — Who Matters

**8. What is degree centrality and which station ranks #1?**
Number of direct track neighbours. Moradabad (MB) is #1 — the only station that is also #1 on betweenness.

**9. What is betweenness centrality — in plain terms?**
For every possible journey between all station pairs, betweenness counts how many of those journeys must pass through this station. High betweenness = structural choke point.

**10. Why is betweenness pre-computed and not run live?**
Computing exact betweenness on 8,000+ nodes would take hours; the pre-computed approximation (k=300) takes 3–8 minutes.

**11. What is Kiul Junction's degree rank vs betweenness rank?**
Degree rank ~152, betweenness rank #13 — almost no train stops there directly, but it sits on the path of nearly every east-west journey across northern India.

**12. What is New Delhi's betweenness rank?**
#20. Students almost always predict top 3. The finding: political/economic salience and structural importance are different things.

**13. Which state dominates the top-20 betweenness stations?**
Bihar — the Bihar cluster (Kiul, Luckeesarai, Hathidah, Barhiya, Mankatha, Tilrath) occupies betweenness ranks #5–#13.

---

### Part 3 — Why Bihar

**14. What physical feature forces all east-west traffic through Bihar?**
The Ganges river — extremely wide, very few rail bridges. Every train crossing from south bank to north bank must use one of a handful of crossing points.

**15. What is the geodesic vs train distance ratio, and what does a ratio of 3 mean?**
Train distance ÷ straight-line distance. A ratio of 3 means the train travels 3× further than a crow would fly — a geographic barrier is forcing a massive detour.

**16. What are the two mechanisms that produce high detour ratios?**
River barrier (Bihar/Ganges): a physical crossing bottleneck creates high betweenness. Hub-spoke design (Gujarat/Ahmedabad): all lines radiate from one city, forcing detours through the hub — high ratios but not high betweenness because the hub can re-route.

**17. Why does the river barrier create high betweenness but hub-spoke does not?**
Remove a river crossing station and the network splits — no alternative path. Remove a hub-spoke centre and trains can reroute through other lines. Physical irreplaceability is what drives betweenness.

**18. When were the Bihar cluster stations built?**
1860s–1880s by the East Indian Railway under British colonial rule — specifically to connect Calcutta to the interior of the subcontinent.

**19. Why hasn't independent India built a second Ganges crossing corridor?**
The data cannot answer this — it is a question of politics, funding, and planning decisions over 75 years. Students must speculate; the network only identifies the gap.

---

### Part 4 — Removal and Wikipedia

**20. What does the removal simulation compute?**
Delete one station and all its edges. Count how many stations can no longer reach the rest of the network. Higher count = more structurally critical.

**21. Which station strands more stations when removed — Kiul or New Delhi?**
Kiul Junction strands more — it is a genuine chokepoint. New Delhi is well-connected enough that most traffic can reroute.

**22. What happens when you search Wikipedia for "Mankatha railway station"?**
You get the Wikipedia article for a Tamil film. Name collision — the agent returns wrong content with high confidence.

**23. What does the Mankatha failure teach about AI tools?**
Confidence score ≠ correctness. The model was confident and wrong. Students must verify AI outputs, not treat confidence as a proxy for accuracy.

---

### Part 5 — Limitations and Takeaway

**24. What three things does the network NOT see?**
Passenger volume (only train counts), platform capacity and congestion, political/economic importance of a city independent of its track position.

**25. What is the one-sentence answer to the project question?** **[student]**
Strong answers name a specific station, give its betweenness rank, explain the Ganges barrier, and note it was built in the 1860s — e.g.: "Kiul Junction (betweenness #13, degree #152) is India's structural missing link: every east-west journey crosses the Ganges here, on infrastructure the British built in 1862 that independent India never replaced."
