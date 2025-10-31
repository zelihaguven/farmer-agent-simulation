#  Farmer Agent Project

This project simulates how **model-based reflex agents** make decisions using different strategies in a **partially observable farm environment**.  
The agents aim to achieve **maximum performance** by collecting **eggs (Y)** and **milk (S)** while avoiding dangers like **swamps (B)** and **bears (A)**.

Three different agents were developed as part of this project:

| Agent | Behavior Type | Summary |
|--------|----------------|----------|
| **Agent1** | Basic Model-Based Reflex Agent | Goal-oriented, moves strategically |
| **Agent2** | Advanced Model-Based Reflex Agent | Stores danger information and avoids risks |
| **Agent3** | Random Model-Based Reflex Agent | Keeps the model structure but acts randomly |

---

##  Goal (PEAS Definition)

| Component | Description |
|------------|-------------|
| **Performance (P)** | Collecting eggs: **+2**, collecting milk: **+5**, stepping into swamp: **-10**, encountering a bear: **-100** |
| **Environment (E)** | 10×10 grid world. Resources (S, Y) and hazards (A, B) are statically placed. |
| **Actuators (A)** | Actions: `FORWARD`, `LEFT`, `RIGHT`, `LOAD` |
| **Sensors (S)** | The agent can perceive the current cell and its four adjacent cells. |

---

##  Environment Properties

| Property | Value |
|-----------|--------|
| Observability | **Partial** – only the current and neighboring cells are perceived |
| Deterministic | **Yes** – same actions always produce the same outcomes |
| Dynamic | **Static** – the map does not change over time |
| Number of Agents | **Single agent** |
| Episodic | **Sequential** – past decisions affect future ones |

---

##  Agent Types and Behavioral Differences

###  **Agent1 – Basic Model-Based Reflex Agent**

- Perceives its environment and **stores past perceptions in memory**.  
- Moves toward known resource locations, otherwise explores randomly.  
- Does not consider danger information.

**Decision Mechanism:**
1. If the current cell contains a resource → **LOAD**  
2. If known resources exist in memory → **Turn and move toward them**  
3. If no information → **Random exploration (prefer moving forward)**  

---

###  **Agent2 – Risk-Aware Model-Based Reflex Agent**

- Includes all Agent1 features, plus:
  - **Stores dangerous cells (A, B)** in memory.
  - Avoids risky directions.
- Determines safer routes, achieving higher efficiency.

**Key Differences:**
- Uses memory to avoid hazards.  
- Primary goal: **Collect resources + minimize risk.**

---

###  **Agent3 – Random Movement Agent**

- Retains the model-based structure but **has no memory or decision logic**.  
- Chooses random actions and directions each step.  
- **Has low intelligence**, but serves as a “behavioral baseline” for comparison.

**Purpose:**  
To measure the performance of a completely random agent and compare it with reflex and memory-based ones.

---

##  Comparative Feature Table

| Feature | Agent1 | Agent2 | Agent3 |
|----------|---------|---------|---------|
| Model-Based | ✅ | ✅ | ✅ |
| Memory | 🟡 (Resources only) | 🟢 (Resources + Hazards) | ❌ |
| Decision Logic | Goal-oriented | Goal + risk analysis | Random |
| Learning Ability | ❌ | ❌ | ❌ |
| Intelligence Level | Medium | High | Low |
| Expected Performance | Medium | High | Low |
| Randomness | Low | Low | High |

---

##  Code Structure

| File / Class | Description |
|---------------|--------------|
| `XYEnvironment` | Manages the 10×10 grid world, including boundaries, resources, and hazards. |
| `Agent1` / `Agent2` / `Agent3` | Agents implementing different decision strategies. |
| `create_grid()` | Generates the grid, placing resources and hazards. |
| `run_episode()` | Runs the simulation and returns the agent’s total score. |
| `display_grid()` | Displays the environment visually in the console. |

---

##  Performance Evaluation

All agents are tested under the same environment to compare **average performance**, **resources collected**, and **hazards encountered**.

| Metric | Agent1 | Agent2 | Agent3 |
|--------|---------|---------|---------|
| Resources Collected | Medium | High | Low |
| Hazard Collisions | Medium | Low | High |
| Average Score | Medium | High | Low |

---

##  Conclusion

This project demonstrates how **model-based reflex agents** differ in performance depending on their **memory usage**, **decision logic**, and **randomness level**.  
In summary:

- **Agent2** performs best thanks to its balanced, risk-aware strategy.  
- **Agent1** achieves moderate success with limited memory.  
- **Agent3** performs poorly due to purely random actions and no reasoning.

---

📌 *This project was developed as part of an Artificial Intelligence course, illustrating the practical application of “Agents and Environments.”*
