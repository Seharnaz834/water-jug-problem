# Water Jug Problem — State Space Search (BFS & DFS)

**Internship Hands-On Project — Pynexia Technology**
**Submitted by: Sehar Naz**

A classic Artificial Intelligence search problem, solved with a complete and tested Python implementation.

## Problem Statement

- Represent the water jug problem using two containers with fixed capacities.
- Model each state as the amount of water in both jugs.
- Implement state space search (BFS/DFS) to reach the target quantity.
- Display the exact sequence of state transitions that leads to the solution.

## Project Setup

| Item | Value |
|---|---|
| Jug X capacity | 4 litres |
| Jug Y capacity | 3 litres |
| Target quantity | 2 litres (in either jug) |
| Initial state | (0, 0) — both jugs empty |
| Goal test | x = 2 or y = 2 |
| Language | Python 3 (standard library only) |

**State representation:** `State = (x, y)` where `x` = litres in Jug X and `y` = litres in Jug Y.

**Six production rules:** Fill Jug X · Fill Jug Y · Empty Jug X · Empty Jug Y · Pour X → Y · Pour Y → X.
A pour stops when the source is empty or the destination is full: `pour = min(source, capacity − destination)`.

**Solvability (Bézout's identity):** a target is reachable only if it is a multiple of `gcd(capacities)`.
Here `gcd(4, 3) = 1`, so 2 litres is guaranteed measurable.

## Results (verified by running the code)

**BFS — optimal solution, 4 steps:**

```
(0, 0) → (0, 3) → (3, 0) → (3, 3) → (4, 2)   # 2 L measured in Jug Y
```

**DFS — valid solution, 6 steps:**

```
(0, 0) → (4, 0) → (1, 3) → (1, 0) → (0, 1) → (4, 1) → (2, 3)   # 2 L measured in Jug X
```

| Criterion | BFS | DFS |
|---|---|---|
| Frontier | Queue (FIFO) | Stack (LIFO) |
| Path length | 4 steps — optimal | 6 steps |
| States expanded | 10 | 8 |
| Optimal? | Yes, guaranteed | No |

## How to Run

```bash
python Water_Jug_Problem.py
```

No installation needed — only Python 3 and its standard library (`collections`, `math`).
The program prints the explored states and the exact step-by-step transition sequence for both searches. A built-in validate() function then asserts that each returned path starts at (0, 0), that every transition is a legal move, and that the final state is a goal - and prints "Validation: PASSED" under each solution.
Expected final results: BFS ends at `(4, 2)` and DFS ends at `(2, 3)`.

## Files in This Repository

- `Water_Jug_Problem.py` — complete source code (BFS + DFS)
- `program_output.txt` — actual verified output of the program
- `Sehar_Naz_Water_Jug_Problem_Pynexia_Technology.pdf` — full 13-page project report

## Reference

Water Pouring Puzzle — Wikipedia (resource provided with the assignment):
https://en.wikipedia.org/wiki/Water_pouring_puzzle
