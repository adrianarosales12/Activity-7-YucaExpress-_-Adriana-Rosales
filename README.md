# Activity 7: YucaExpress — The Fastest Route Challenge
## Sessions 14
## Due date (mm/dd/yyyy): 09/27/2026
## Delivery Format: [] Video URL | [X] Markdown file | [] Jupyter Notebook file

---

# Activity Description

## The Story

You dispatch deliveries for **YucaExpress**, a last-mile courier service in Mérida. A courier
needs to get from the **Depot** to the **Client Office** using the *cheapest total distance* —
every extra kilometer costs the company time and fuel.

You know the straight-line ("as the crow flies") distance from any junction to the client's
office — that's easy to read off a map. But real roads don't always go in a straight line.
This activity is about **Heuristic Search**: using that straight-line estimate to guide your
search, without letting it fool you.

This activity is a single interactive app — no coding required. Everyone in the class uses the
**same fixed delivery map** (there is no randomness anywhere in the app), so your results should
match your classmates' exactly.

**App link:** https://uam-aiclass-a7.streamlit.app/

The app has three tabs:

1. **🗺️ The Map** — the problem definition, the full road network with real distances, and a
   table of straight-line distances (the heuristic, h) from every junction to the goal.
2. **🎯 Greedy Best-First** — click through a search that always drives toward whichever
   junction *looks* closest to the goal, ignoring how far it has already driven.
3. **⭐ A\* Search** — click through a search that balances real distance driven (g) *and* the
   straight-line estimate (h), using f(n) = g(n) + h(n).

---
### Your Tasks

1. **Read the Map tab.** Note the initial state, the goal state, and the heuristic formula
   f(n) = g(n) + h(n). Look at the straight-line-distance table.
   <img width="623" height="617" alt="image" src="https://github.com/user-attachments/assets/dc6a7619-16e6-45cc-a55b-5dbd5ba287ee" />
- Initial: Depot
- Goal: Client Office
- Formula: f(n) = g(n) + h(n)

---
2. **Step through the Greedy Best-First tab, one click at a time, until you arrive.** Take a
   screenshot of the final result.
<img width="622" height="566" alt="image" src="https://github.com/user-attachments/assets/f5bfb131-035a-4c3b-9eb5-91265977e947" />
- Route found: Depot → Hub Norte → Parque Cruce → Retorno del Lago → Client Office
- Total distance: 19.34 km

---   
3. **Step through the A\* tab, one click at a time, until you arrive.** Take a screenshot of
   the final result, including the comparison message.
<img width="613" height="608" alt="image" src="https://github.com/user-attachments/assets/b54369de-f739-4133-a23a-f4d36d8d2a73" />
- Route found: Depot → Hub Sur → Anillo Periférico → Circuito Sur → Client Office
- Total distance: 11.23 km
- Comparison message: “A* found a route 8.11 km shorter by weighing real driven distance (g) instead of straight-line closeness (h).”


---
4. **Find the one road in this map that costs noticeably more than a straight line between its
   two junctions would suggest.** Take a screenshot of it (visible as an edge label on the map,
   or in either trace table).
<img width="520" height="407" alt="image" src="https://github.com/user-attachments/assets/30e271d9-baf7-4e85-82e5-5055069c8e46" />

- Road identified: Retorno del Lago → Client Office
- Observation: Actual cost ≈ 9.49 km, while straight-line heuristic is only 3.16 km. This misleads Greedy into choosing a longer path.

---
6. **A7_ReflectionQuestions.md**

**1. What is the **initial state** and the **goal state** in this activity?**
- The initial state in this activity is the Depot, which represents the starting point of the courier. The goal state is the Client Office, the destination where the delivery must arrive. The search problem is framed around finding the cheapest path from Depot to Client Office using the heuristic formula f(n)=g(n)+h(n), where g(n) is the real distance already traveled and h(n) is the straight‑line estimate to the goal. 


**2. What route did **Greedy Best-First** take (list every junction, in order), and what was its total distance driven**?**
- The Greedy Best-First Search algorithm followed this route:
   - Depot → Hub Norte → Parque Cruce → Retorno del Lago → Client Office.
   - Its total distance driven was 19.34 km.
- This happened because Greedy always chooses the junction with the smallest heuristic h(n), without considering how far it has already traveled. Retorno del Lago looked very close to the goal (small h), but the actual road from there to the Client Office was much longer than expected, which inflated the total cost.



**3. What route did **A\*** take (list every junction, in order), and what was its **total distance driven**?**
- The A\* algorithm found a different and cheaper route:
   - Depot → Hub Sur → Anillo Periférico → Circuito Sur → Client Office.
   - Its total distance driven was 11.23 km.
- Unlike Greedy, A\* evaluates both the real cost g(n) and the heuristic h(n). This balance allowed it to avoid the misleading shortcut through Retorno del Lago and instead choose a path that minimized the overall cost.



**4. One road in this map costs noticeably more than the straight-line distance between its two junctions would suggest. Name that road (its two endpoints) and report both its real cost
and the straight-line distance between those same two junctions.**
- The road between Retorno del Lago → Client Office is the one that costs noticeably more than its straight‑line distance suggests.
   - Real cost: 9.49 km
   - Straight‑line distance (h): 3.16 km
- This discrepancy shows why relying only on h(n) can be dangerous: the heuristic made Retorno del Lago look attractive, but the actual road was much longer, tricking Greedy into a poor choice.



**5. Which algorithm found the cheaper overall route, and by how many kilometers?**
- The algorithm that found the cheaper route was A\*. It saved 8.11 km compared to Greedy Best-First. This difference is significant in logistics terms, as it represents less fuel consumption, less travel time, and lower overall delivery cost.

**6. In your own words, explain **why** Greedy Best-First got misled into a more expensive route while A\* did not. Use the terms **g(n)** and **h(n)** somewhere in your answer.**
- Greedy Best-First was misled because it only considers the heuristic h(n), the straight‑line estimate to the goal. It ignored g(n), the real distance already traveled. As a result, it was drawn toward Retorno del Lago, which looked close to the Client Office but required a long detour. A\, on the other hand, combines g(n) and h(n) into f(n)=g(n)+h(n), ensuring that both the actual cost and the estimate are considered. This balance prevented A\ from being fooled and guaranteed the optimal route. 

**7. Name one **real business or logistics scenario** where blindly chasing whatever "looks closest to the goal" — without accounting for the real cost already spent — could backfire,
similar to Greedy's mistake here.**
- A real logistics scenario where blindly chasing “what looks closest” could backfire is urban delivery routing. For example, a courier might choose a shortcut through a narrow downtown street because it looks geographically closer to the destination. However, if that street is congested with traffic, has speed bumps, or is under construction, the actual travel time and fuel cost will be much higher. Companies like FedEx or UPS must avoid this Greedy‑style mistake by using algorithms that weigh both estimated distance and real travel costs, just like A\* does. 

**8. Suppose the heuristic in this app sometimes *overestimated* the true remaining distance instead of always underestimating it. Would A\* still be guaranteed to find the cheapest route? Why or why not?**

- If the heuristic sometimes overestimated the true remaining distance, A\* would lose its guarantee of finding the cheapest route. A\* requires an admissible heuristic — one that never overestimates — to ensure optimality. Overestimation could cause A\* to wrongly discard the true optimal path because it would appear more expensive than it really is. In practice, this means that A\* might settle for a suboptimal route if the heuristic is not carefully designed. 

# References:
- [Streamlit documentation](https://docs.streamlit.io/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
