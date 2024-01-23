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

