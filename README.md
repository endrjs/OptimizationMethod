# OptimizationMethod


Contents
1 Important Notes About These Notes 1
2 Single-Source Shortest Paths 5
2.1 Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5
2.2 Useful Facts . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5
2.3 Negative Weights . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
2.3.1 Exchange Rate Example . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
2.3.2 Nega􀦧ve Cycles . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
2.4 Shortest-Path Trees . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
2.5 Relaxa􀦧on Technique . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
2.5.1 Ini􀦧alisa􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
2.5.2 Relaxation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
2.5.3 Relaxation Proper􀦧es . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
2.5.4 Checking for Cycles . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 9
2.6 Bellman-Ford Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 9
2.6.1 Correctness . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
2.6.2 Running Time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
2.6.3 Improving the Running Time . . . . . . . . . . . . . . . . . . . . . . . . 11
2.6.4 Optimisations: Early Termina􀦧on and Queue of Active Ver􀦧ces . . . . 11
2.7 Dijkstra’s Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
2.7.1 Running Time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
2.7.2 Correctness - Invariants . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
2.7.3 Correctness - Induction on Invariants . . . . . . . . . . . . . . . . . . . 14
2.8 Directed Acyclic Graphs (DAGs) . . . . . . . . . . . . . . . . . . . . . . . . . . . 15
2.8.1 Topological Order . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 15
2.9 Geographic Networks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 16
2.9.1 Re-Weighting Edges . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 16
3 All-Pairs Shortest Paths 17
3.1 Existing Algorithms . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 17
3.2 Floyd-Warshall Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 17
3.3 Johnson’s Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 17
3.3.1 Re-Weightng Edges . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 17
3.3.2 Calculating h-values . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
3.3.3 Full Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
3.3.4 Running Time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
3.3.5 Correctness . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
4 Network Flow Problems 20
4.1 Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
4.2 Types of Flow Problem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
4.3 Flow Formalisa􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
4.4 From Flows to Paths . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21
5 Max-Flow Problems 22
5.1 Residual Capacity . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 22
5.1.1 Adding Flow Using the Residual Network . . . . . . . . . . . . . . . . . 22
5.2 General Approach for Finding Maximum Flow . . . . . . . . . . . . . . . . . . . 23
2
OME: Optimisation Methods Gun Park
5.3 Side Note: Cuts . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 23
5.3.1 Theorem One: Max-Flow Min-Cut Theorem . . . . . . . . . . . . . . . 24
5.3.2 Theorem Two . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 24
5.4 Ford-Fulkerson Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 25
5.5 Edmonds-Karp Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 25
6 Flow Feasibility Problems 27
6.1 Reduc􀦧on to Maximum Flow Problem . . . . . . . . . . . . . . . . . . . . . . . 27
7 Min-Cost Flow Problems 29
7.1 Nota􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 29
7.2 Sending Flow Along Cheapest Paths . . . . . . . . . . . . . . . . . . . . . . . . 29
7.3 Residual Network . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 30
7.4 Successive Shortest Path Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . 31
7.4.1 Correctness and Run􀦧me . . . . . . . . . . . . . . . . . . . . . . . . . . 32
8 Mul􀦧-Commodity Flow Problems 33
8.1 Nota􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 33
8.2 Example . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 33
8.3 Flows of Commodites . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
8.4 Types of Multi-Commodity Flow Problems . . . . . . . . . . . . . . . . . . . . . 34
8.4.1 Feasibility . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
8.4.2 Min-Cost . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
8.4.3 Min-Conges􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
8.5 Computa􀦧onal Approaches . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35
9 Maximum Bipar􀦧te Matching 36
9.1 Compu􀦧ng a Maximum Matching . . . . . . . . . . . . . . . . . . . . . . . . . . 36
10 Linear Programming 37
10.1 General Form . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
10.1.1 Solution Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
10.2 Modelling Max-Flow Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
10.3 Modelling Min-Cost Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . . 38
10.4 Modelling Multi-Commodity Problems . . . . . . . . . . . . . . . . . . . . . . . 38
10.5 Modelling Min-Conges􀦧on Multi-Commodity Problems . . . . . . . . . . . . . 38
10.6 Adding Constraints . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 39
10.6.1 ‘Both edges out of b must have equal flow.’ . . . . . . . . . . . . . . . . 39
10.6.2 ‘The flow on edge (a; b) must not exceed the flow on edge (c; d).’ . . . 39
10.6.3 ‘There is a budget of 50 for all flow out of y.’ . . . . . . . . . . . . . . . 39
10.6.4 ‘Flow along (a; b) leaks by 5%.’ . . . . . . . . . . . . . . . . . . . . . . . 40
10.7 Adding Constraints with Binary/Integer Variables . . . . . . . . . . . . . . . . . 40
10.7.1 ‘Flow along (a; b) is either 0 or fully satura􀦧ng.’ . . . . . . . . . . . . . . 40
10.7.2 ‘Commodity 2 can only use one edge outgoing from i.’ . . . . . . . . . 40
10.7.3 ‘There is a fixed cost of 5 for using any edge.’ . . . . . . . . . . . . . . . 41
10.8 Mul􀦧ple Objec􀦧ves . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 41
10.8.1 Strict Priori􀦧es (Nested Solu􀦧ons) . . . . . . . . . . . . . . . . . . . . . 41
10.8.2 Equally Important Priorities . . . . . . . . . . . . . . . . . . . . . . . . . 41
10.8.3 Biased Priori􀦧es . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 41
10.8.4 Convert Objec􀦧ves into Constraints . . . . . . . . . . . . . . . . . . . . 42
3
OME: Op􀦧misa􀦧on Methods Gun Park
11 NP-Hard Problems 43
11.1 Combinatorial Optimisation Problems . . . . . . . . . . . . . . . . . . . . . . . 43
11.1.1 Example: Single-Source Single-Des􀦧na􀦧on Shortest Simple Path Problem
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 43
11.1.2 Example: Mul􀦧-Commodity Unspli􀄧able Minimum-Conges􀦧on Flow
Problem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 43
11.1.3 Example: Travelling Salesman Problem . . . . . . . . . . . . . . . . . . . 43
11.1.4 Example: Weighted Graph-Bisec􀦧on Problem . . . . . . . . . . . . . . 43
11.2 Problem Classes . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
11.2.1 P Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
11.2.2 NP Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
11.2.3 NP-Hard Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
11.2.4 NP-Complete Problems . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
11.3 Solu􀦧on Apporaches . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
12 Branch-and-Bound 46
12.1 Exhaus􀦧ve Search . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 46
12.2 Par􀦧al Configura􀦧ons and Branding Procedure . . . . . . . . . . . . . . . . . . 46
12.3 Bounding Procedure . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 46
12.4 General Descrip􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
13 Simulated Annealing 48
13.1 Neighbourhoods . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 48
13.1.1 Examples for Symmetric Travelling Salesman Problem . . . . . . . . . . 48
13.1.2 Example for Weighted Graph Bisec􀦧on Problem . . . . . . . . . . . . . 48
13.2 Local Search . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 48
13.2.1 Local Op􀦧ma . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49
13.3 Key Idea of Simulated Annealing . . . . . . . . . . . . . . . . . . . . . . . . . . 49
13.4 Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49
13.4.1 Odds of Taking a Worse Configura􀦧on . . . . . . . . . . . . . . . . . . . 50
13.4.2 Control and Length Parameters . . . . . . . . . . . . . . . . . . . . . . . 51
13.4.3 Stopping Criteria . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 51
13.4.4 Running Time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 51
14 Gene􀦧c Algorithms 52
14.1 Crossover Opera􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 52
14.1.1 1-, 2- and n-Point Crossovers . . . . . . . . . . . . . . . . . . . . . . . . 52
14.2 Muta􀦧ons . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 52
14.3 Fitness Func􀦧on . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 53
14.4 The Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 53
14.4.1 Stopping Criteria . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 54
