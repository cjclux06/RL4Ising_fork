\# Sources: Gset and MaxCut-Bench

\---

1. Gset (Stanford G-set Max-Cut instances)

\- Link: https://web.stanford.edu/~yyye/yyye/Gset/ - Original generator paper: Helmberg and Rendl, "A spectral bundle method for semidefinite programming," SIAM J. Optim. 10(3), 2000 - Type: Benchmark dataset (Max-Cut, equivalent to zero-field Ising ground-state search)

What it is: 69 Max-Cut instances (G1 to G72, with three numbers absent) built with Rinaldi's `rudy` generator. They fall into three structural families: random graphs, skew graphs with heterogeneous degree, and 2D toroidal grids.

Why we should add it.

Application: Standard for benchmarking classical heuristics, Ising machines and learned Max- Cut methods Prestige/community use: Used across MCPG, ECO-DQN-style work and MaxCut-Bench; best- known values are still being improved in recent literature Interesting features: The torus family is a set of 2D ±J Edwards-Anderson spin glasses; the periodic boundary makes ground-state search NP-hard Variety: Adds sparse random, skew and toroidal structure at scales beyond our generated BA graphs

Caveats for the paper.

\- Weights use the Max-Cut sign convention (w = -J); conversion must be documented. - Zero external field only. - Best-known values are not all proven optima and change over time, so record source and date.

\---

2. MaxCut-Bench (Nath and Kuhnle)

\- Link: https://arxiv.org/abs/2406.11897 - Code: https://github.com/ankurnath/MaxCut-Bench - Type: Related work / benchmark suite for learned Max-Cut heuristics

What it is: An open-source benchmark for Max-Cut (weighted and unweighted) with a unified

interface to classical and learned heuristics. Its instance mix includes Gset, Sherrington-


Kirkpatrick spin glasses, dense phase-transition graphs, a physics library set, and standard random graph models (ER, BA, Holme-Kim, Watts-Strogatz).

Why we should cite it.

Directly comparable scope: Same problem family as our Max-Cut results, and it evaluates ECO- DQN, which our paper mentions but never defines Addresses a reviewer complaint: Reviewers said the paper lacks an overview of how results fit into the literature Baseline critique: Reports that simple classical heuristics (Reversible Greedy, Tabu Search) outperform many learned heuristics and recommends Tabu Search as a standard baseline Evaluation methodology: Separates objective value, generalization and scalability, and discusses instance and baseline bias across papers Solver time limits: Notes that Gurobi's best-known value depends strongly on the cutoff time

How it should shape our work.

- 1. Add Tabu Search and Reversible Greedy as baselines, so claims about RL "beating" solvers are measured against strong cheap heuristics too. 2. Report approximation ratio alongside percentage energy gap, so our numbers can be compared with Max-Cut papers. 3. Report solver time limits and separate proven optima from best incumbents.

Caveat: MaxCut-Bench focuses on graph Max-Cut with GNN and RL heuristics, so it does not cover lattice spin glasses in 3D and 4D or Hamiltonians with a field, which are where RL4Ising's

dataset is broader.
