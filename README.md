## Goal
Solve efficiently a generic $2^N-1$ ($N$ x $N$) puzzle using path-search algorithms. <br>
**Quality**: number of actions in the solution. <br>
**Cost**: total number of actions evaluated. <br>
**Efficiency**: Quality vs Cost

## Implemented approach

I have chosen to use the A* algorithm. In this implementation, I consider two possible admissable heuristic estimates: <br>
1. Manhattan distance (MD). It considers the manhattan distance of each tile (except for 0 encoding a free space) from its current position to its position in the goal state and sums these distances up. 
2. Enhanced Manhattan (EM). It is based on the previous idea, but adds a penalising factor for tiles which are in the correct row/column but in the wrong order. It's slightly more computationally expensive, but in general it allows to find the path to the goal sooner, with algorithm evaluating less states compared to A* with Manhattan distance.

## Results obtained

| NxN | Heuristic | Quality | Cost |
|-----|-----------|---------|------|
| 2x2 | MD | 2 | 3 |
| 2x2 | EM | 2 | 3 |
| 3x3 | MD | 24 | 1380 |
| 3x3 | EM | 24 | 567 |
| 4x4 | MD | 48 | 2315491 |
| 4x4 | EM | 48 | 801712 |

For 5x5 grid, neither MD- or EM-based A* provides solution in a reasonable time (after 2.5 hours of running the algorithm, the search was not concluded).

Using Enhanced Manhattan heuristic allows to decrease the number of states evaluated by 2.5 times compared to using the standard Manhattan distance.