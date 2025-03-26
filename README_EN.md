# 🚇 Metro Network Simulation

This project is a metro network simulation developed in Python. It allows journeys across metro stations and lines and enables finding the **fastest** or **least-transfer** routes between two stations.

---

## ⚙️ Technologies and Libraries Used

- **Python 3**: Main programming language.
- **`collections`**
  - `deque`: Double-ended queue for Breadth-First Search (BFS).
  - `defaultdict`: For easily grouping stations by lines.
- **`heapq`**: Used to create a priority queue (min-heap) for the A* algorithm.
- **`typing`**: For type hints (`Dict`, `List`, `Optional`, etc.)

---

## 🧠 Algorithm Logic

### 🔄 BFS (Breadth-First Search) – Least Transfer Route
- A queue-based search algorithm.
- When a station is visited, its connected neighbors are added to the queue.
- The same station is not revisited on the same line.
- A transfer is counted when the neighboring station is on a different line.
- **Advantage**: Finds the path with the fewest steps (in this case, least transfers).

### 🚀 A* (Works like Dijkstra) – Fastest Route
- Uses a priority queue with `heapq`.
- At each step, the station with the lowest total time is processed.
- A station is not reprocessed if already visited in a shorter time.
- Since there is no geographical heuristic, it works like classic Dijkstra.
- **Advantage**: Finds the most efficient route based on travel time.

### Why These Algorithms?
- BFS: When the number of steps (e.g., fewest transfers) matters.
- A*: When actual travel durations are important.

---

## ▶️ Sample Usage and Test Results

When the program runs, the following scenarios are tested:

1. **AŞTİ → OSB**
2. **Batıkent → Keçiören**
3. **Keçiören → AŞTİ**

For each scenario:
- The route with the least number of transfers
- The fastest route based on total time is printed

### Sample Output:

```text
1. From AŞTİ to OSB:
Least-transfer route: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
Fastest route (19 minutes): AŞTİ -> Kızılay -> Kızılay -> Ulus -> Demetevler -> OSB
```

---

## 🚀 Project Improvement Ideas

- Visualization with a GUI
- Taking live input for start and destination stations from the user
- Map integration (e.g., using geographic coordinates with heuristic A*)
