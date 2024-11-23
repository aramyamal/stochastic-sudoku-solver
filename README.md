# Stochastic Sudoku Solver

## Background
This sudoku solver utilizes various heuristic optimization algorithms to solve 
sudoku puzzles represented as two-dimensional arrays. The following are brief 
explanation of each algorithm and the source paper I drew inspiration from:

### Genetic Algorithm (GA)
This algorithm simulates the process of natural selection to find better and
better solutions over multiple generation. An initial population is randomly
created according to sudoku criterias. For each generation, individuals with
best solution are combined and mutated to create the next generation, until a
correct sulotion is found.

My implementation is inspired by the paper:
- [Genetic Algorithms and Sudoku](https://micsymposium.org/mics_2009_proceedings/mics2009_submission_66.pdf) by John M. Weiss (2009) [[1]](#1).

### Simulated Annealing (SA)
This algorithm is inspired by the pysical process of annealing in heated
materials gradually cooling down. It seeks a solution by iteratively adjusting
proposed sudoku boards. Firstly, a temperature $T$ is initialized that 
decreases for each iteration. 
Then, a proposed sudoku board is randomly modified, with better
solutions being instantly accepted, but worse solutions being probabalistically
accepted according to the [Boltzmann distribution](https://en.wikipedia.org/wiki/Boltzmann_distribution)
$e^{\Delta E / T}$, where $\Delta E$ is a measure of how much worse the
proposed solution is. Over time, as $T$ decreases, the algorithm converges on a 
valid Sudoku board, or restarts if it is stuck at a local minima.

My implementation is inspired by the paper: 
- [Metaheuristics can Solve Sudoku Puzzles](https://rhydlewis.eu/papers/META_CAN_SOLVE_SUDOKU.pdf) by Rhyd Lewis (2007) [[2]](#2).

### Ant Swarm Optimization (TO BE IMPLEMENTED)
Ongoing implementation based on ideas from:

- [Solving Sudoku with Ant Colony Optimisation](https://arxiv.org/pdf/1805.03545) by Huw Lloyd and Martyn Amos (2020) [[3]](#3).

### Backtracking Algorithm
This is not a heuristics algorithm, but a brute force one. Can be used to verify
results and for comparisons.

## Usage
Simply run ```python3 .``` in the repo directory. You will be prompted with either entering your own sudoku board manually, or choosing from a selection of
four boards of varying dififficulties. Then you are asked for which algorithm to use for solving the sudoku.

<details>
  <summary>Example usage (click me):</summary>
  
```
user@localhost:~/repos/stochastic-sudoku-solver$ python3 .
Sudoku Solver
-------------
Write your own puzzle? (y/n)
Enter choice: n
-------------
What difficulty of puzzle?
1. Easy
2. Medium
3. Hard
4. Evil
Enter choise: 4
-------------
Puzzle is:

3 . . | 1 . . | 2 6 .
1 9 . | . . 8 | . . 3
. . 5 | 6 . 3 | 1 . .
------+-------+------
. 3 . | . 9 . | . 2 5
5 1 . | 2 . . | . 3 .
9 6 2 | . . . | . . 1
------+-------+------
. . 1 | 9 6 . | 3 . .
8 . 3 | . 1 . | . . 6
. 2 . | . . 5 | . . 4
-------------
Choose algorithm:
1. Genetic Algorithm
2. Simulated Annealing
3. Backtracking Algorithm (brute force)
4. Exit
Enter choice: 1
Solving...
-----------------------------

Solution found after 76 generations and 0.47 seconds.

3 4 7 | 1 5 9 | 2 6 8
1 9 6 | 7 2 8 | 5 4 3
2 8 5 | 6 4 3 | 1 9 7
------+-------+------
7 3 4 | 8 9 1 | 6 2 5
5 1 8 | 2 7 6 | 4 3 9
9 6 2 | 5 3 4 | 8 7 1
------+-------+------
4 5 1 | 9 6 7 | 3 8 2
8 7 3 | 4 1 2 | 9 5 6
6 2 9 | 3 8 5 | 7 1 4

```
  
</details>

## References
<a id="1">[1]</a> J. Weiss, “Genetic Algorithms and Sudoku,” 2009. Available: https://micsymposium.org/mics_2009_proceedings/mics2009_submission_66.pdf

<a id="2">[2]</a> R. Lewis, “Metaheuristics can solve sudoku puzzles,” Journal of Heuristics, vol. 13, no. 4, pp. 387–401, May 2007, doi: https://doi.org/10.1007/s10732-007-9012-8.

<a id="3">[3]</a> H. Lloyd and M. Amos, “Solving Sudoku with Ant Colony Optimization,” IEEE Transactions on Games, vol. 12, no. 3, pp. 1–1, 2019, doi: https://doi.org/10.1109/tg.2019.2942773.
