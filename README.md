# Pathfinding Performance Analyzer: Dijkstra vs BFS

A real-time pathfinding visualization tool built with **C++** and **Raylib** to analyze the efficiency gap between weighted and unweighted search strategies.

## Project Motivation

This project was developed as a personal challenge to bridge the gap between academic theory and practical engineering application. By visualizing complex concepts learned in my **Data Structures** and **Algorithm Analysis** courses, I aimed to deepen my understanding of:

* **Algorithmic Efficiency:** Observing how heuristic decisions impact search space in real-time.
* **Data Structure Implementation:** Using `priority_queue` (min-heaps) for Dijkstra and standard `queue` for BFS to manage node expansion.
* **Weighted Graph Logic:** Understanding how edge weights (terrain costs) transform a simple search into an optimization problem.

Developing this tool has significantly enhanced my ability to think algorithmically and manage performance-critical systems.

## Technical Features

* **Weighted Terrain (Mud):** Implements a cost-based grid where "Mud" tiles are 5x more expensive to cross than normal tiles.
* **Side-by-Side Metrics:** Real-time tracking of execution time (ms), node expansion (visited count), and mathematical path cost.
* **True Cost Metric:** A custom logic that recalculates BFS results using Dijkstra's weight system to expose the "hidden" inefficiency of unweighted searches.
* **Dual-Path Overlay:** Renders both algorithms simultaneously (Current: Yellow, Previous: Orange) for direct visual comparison. 

## Key Comparison

| Feature | Dijkstra (Weighted) | BFS (Unweighted) |
| :--- | :--- | :--- |
| **Logic** | Finds cheapest path | Finds fewest steps |
| **Terrain** | Avoids high-cost mud | Ignores mud costs |
| **Use Case** | Realistic navigation | Simple maze solving |

## Tech Stack & Build

* **Language:** C++11
* **Library:** Raylib
* **Platform:** Optimized for macOS

## Performance Analysis: The Mud Challange

To demonstrate the efficiency gap, I designed a "Mud Challenge" where a high-cost terrain blocks the direct path to the goal.

### 1. Test Scenario
Users can interactively place walls and high-cost mud tiles (Cost: 5) on the grid.

<img width="912" height="880" alt="TheMudChallenge" src="https://github.com/user-attachments/assets/245b7736-a717-48ab-983e-fbc8234a30c6" />


### 2. Comparison Results
Dijkstra's Algorithm (Orange) detours to find the cheapest path, whereas BFS (Yellow) blindly crosses the mud, resulting in a significantly higher "True Cost".

<img width="912" height="880" alt="TheMudChallengeResult" src="https://github.com/user-attachments/assets/fd572d2f-07c4-458d-9ad8-febe1f78869d" />


## Weighted Terrain Efficiency Test
This real-time demonstration captures the core purpose of the project: observing how different search strategies handle environmental costs.

![WeightedTerrainEfficiencyTest](https://github.com/user-attachments/assets/baa3c5e9-b91f-4bef-b547-4729bc141961)


Proof: The performance dashboard highlights the "True Cost" discrepancy. While BFS appears faster in terms of execution, it results in a much higher path cost (54 vs 40), proving that "shortest" isn't always "cheapest" in complex systems.

## 🚀 How to Run (macOS)

You can utilize the following build command to link the Raylib library and framework dependencies on macOS:

### 1. Install Raylib via Homebrew

```bash
brew install raylib
```

### 2. Compile and Run the Visualizer

*(Ensure you are in the PathfindingVisualizer directory)*

```bash
g++ -std=c++11 PathfindingVisualizer.cpp -o visualizer \
-I/opt/homebrew/include -L/opt/homebrew/lib -lraylib \
-framework CoreVideo -framework IOKit -framework Cocoa -framework GLUT -framework OpenGL \
&& ./visualizer
```

> **Note:** Ensure you are in the `PathfindingVisualizer` directory before executing the compilation command.
