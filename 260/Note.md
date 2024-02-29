# COMPSCI 260
## 1/9
First Problem \
**Stable Matching** \
n employers and n employees and all employees apply for all employers \
- A matching is a subset S of M x W such that each man in M and each woman in W appear in at most one pair in S 
- A perfect matching is a matching S s.t. each m in M and each w in W appear in exactly one 
- An instability in a matching S is a pair (m, w) not in S, but each of m, w prefers the other to their partner in S (prefer each other both ways)

## week 1 discussion
AX DY BZ CW \
stable matching can have many different conbinations \
going left to right and right to left will not necessarily produce the same result \
Doing A-Z is best case for A worst case for Z \
Doint from Z to A, is best for Z, worst for A \
G-S algo process is non deterministic but result is deterministic 

## 1/16
A simple graph is where all the vertices are visited exactly once \
**Breadth-First Search**
1. start at vertex s in layer 0
2. for j > 0, layer j consists of all nodes that
   - are not in lower numbered layers
   - are joined by an adge to a node in layer j-1
3. explore all neighbors of all nodes in layer j before moving onto layer j+1
4. produce a tree naturally.
5. on queue FIFO

**DFS**
stack LIFO

## Week 2 discussion
stable matching/ gale-shapely \
asymptotic analysis/complexity \
DFS/BFS \
Topological(sort) (DAG or event order)\
graph \
DFS is good at finding cycles \ 
BFS is good at shortest path \
O (<=) \
o (<) \
big omega (>=) \
small omega (>) \

## 1/23
**Greedy Algorithms**
- An approach to solving optimization problems
- No crisp defination but build up from small steps each step make decision base on local information
- To implement heuristics is easy
- To obtain a global optimum is often impossible

If greedy does provide an optimal solution that implies the algorithm is simple but proof of optimality is nontriial 

Greedy might not be optimal at many situations

## 1/30
DFS traversal of an undirected graph partitions the edges into tree edges and back edges
- Tree deges connect a node X to a node Y

DFS traversal of a directed graph partitions the edges into tree edges, forward edges, back edges, and cross edges

## week 4 Discussion
Interval Scheduling \
greedy: picking the one end the earliest \


[6-8] [2-10] [5-18] [4-6] [1-2] [3-5] [8-10] [12-18] [0-12] [16-20] \
CPU 1: [0-12] \
CPU 2: [1-2] [2-10] [12-18]\
CPU 3: [3-5] [5-18] \
CPU 4: [4-6] [6-8] [8-10] [16-20]\
greedy: picking the one start the earliest \

**task scheduleing with deadline** \
greedy: starting the earliest deadline

**Dijkstra's Algorithm** \
Finds the minimum distance between one point to all other points. \
small negative weights solvable! \
large negative weights that create a negative cycle, question is meaningless. \
Dijkstra loop: O(n + m) \
at each step: we need to sort the smallest path O(nlogn) \
total time complexity O((n+m)logn) \

**How to find MST** \
Jarnik/Prim
- only add min edges
- dont add any that causes a cycle

Kruskal
- look at globallly min cost edge
- dont add that causes a cycle

Borunka
- 

## week 5 discussion
a: O(n^1.33) \
b: O(n^2) \
c: o(n^1/2) \
d:  \
**simplify to n^(log_b(a))** \
if n in front of log is the same add one more log^1(n) \

## 2/13
exercise 4: if a sequence is a subsequence of another sequence. \
exercise 9: a NO b YES proof by contradiction

## week 6 discussion
if largest coin is twice as big as the second largest, it is safe to do greedy algorithm \

## week 7 discussion
**Exam!!!!!** \
Greedy:
- Minimize lateness(easy) 
- Dijkstra's (maybe modification) *****
- MST *****
  - prim/jarnik
  - kruskal
  - bouauuka
- Huffman (typically easy)
- Bellman ford
- min cost arboreence (easy maybe)
- divide & conquer ****
  - master theorem
  - FFT (not likely)
- DP ****
  - at some instance of middle of solving what sub instance can be used
- Fast exponentiation(always adding)



