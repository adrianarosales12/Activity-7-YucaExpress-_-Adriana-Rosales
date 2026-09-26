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
6. **Fill out `A7_ReflectionQuestions.md`**, using the exact data from your run, and submit it
   along with your labeled screenshots.



# References:
- [Streamlit documentation](https://docs.streamlit.io/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
