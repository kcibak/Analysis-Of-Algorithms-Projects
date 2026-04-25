# Drone-Based Pollution Cleanup Optimization

**Analysis of Algorithms Project**  
**Author:** Kira Cibak  

---

## Overview

This project explores algorithmic approaches to optimize a drone’s pollution cleanup mission under energy constraints.

Each “hotspot” has:
- A **priority score** (importance of cleaning)
- A **cleaning cost** (energy required to fully clean)
- A **travel cost** (energy required to reach and return)

The goal is to **maximize total priority cleaned** given a limited battery capacity.

---

## Problem Definition

Each hotspot is defined as:

```
(id, priority, cleaning_cost, travel_cost)
```

The drone must:
- Spend energy to travel to a hotspot
- Spend energy to clean it (fully or partially)
- Maximize total collected priority score

Partial cleaning is allowed and yields proportional reward.

---

## Project Structure

```
Drone_project-pt1.ipynb   # Brute force approach + analysis
Drone_project-pt2.ipynb   # Optimized (greedy) approach + comparison
```

---

## Algorithms Implemented

### 1. Brute Force Approach

#### Description
- Generates **all subsets** of hotspots
- Evaluates **all permutations** of each subset
- Simulates energy usage and score accumulation

#### Key Idea
Exhaustively explores every possible cleaning plan to guarantee the optimal solution.

#### Time Complexity
```
O(n · n!)
```

#### Space Complexity
```
O(n)
```

#### Pros
- Guaranteed optimal solution

#### Cons
- Computationally infeasible for large inputs
- Factorial growth makes it impractical beyond small datasets

---

### 2. Greedy Approach (Optimized)

#### Description
- Sorts hotspots by:
```
priority / cleaning_cost
```
- Selects hotspots in descending order of efficiency
- Cleans as much as possible within remaining battery

#### Time Complexity
```
O(n log n)
```

#### Space Complexity
```
O(n)
```

#### Pros
- Efficient and scalable
- Works well for large datasets

#### Cons
- Does **not guarantee optimal solution** in all cases

---

## Performance Analysis

### Brute Force
- Demonstrates **factorial growth**
- Becomes unusable as input size increases
- Verified using runtime experiments and theoretical analysis

### Greedy
- Shows **near-linearithmic growth (n log n)**
- Scales efficiently to large datasets
- Practical for real-world scenarios

---

## Key Concepts Demonstrated

- Combinatorial optimization  
- Trade-offs between **optimality vs efficiency**  
- Algorithm design paradigms:
  - Brute force  
  - Greedy algorithms  
- Time and space complexity analysis  
- Empirical performance testing  
- Loop invariants and correctness reasoning  

---

## Dataset

The project uses a dataset of up to **100 hotspots**, each defined by:
- Priority score  
- Cleaning effort  
- Travel cost  

---

## Results & Insights

- Brute force confirms the true optimal solution but is computationally expensive  
- Greedy approach provides a strong approximation with significantly better performance  
- Demonstrates why optimization problems often require **heuristics instead of exact solutions**

---

## How to Run

1. Install dependencies:
```bash
pip install numpy matplotlib
```

2. Open Jupyter Notebook:
```bash
jupyter notebook
```

3. Run the notebooks:
- `Drone_project-pt1.ipynb` → brute force + analysis  
- `Drone_project-pt2.ipynb` → greedy optimization  

---

## Future Improvements

- Dynamic programming approach  
- Branch and bound optimization  
- Approximation guarantees for greedy solution  
- Real-world constraints (multi-drone systems, time windows, etc.)  

---

## Summary

This project highlights a classic algorithmic tradeoff:

> Exact solutions are expensive — efficient solutions are approximate.

By comparing brute force and greedy strategies, this project demonstrates how algorithm selection directly impacts scalability, performance, and real-world applicability.
