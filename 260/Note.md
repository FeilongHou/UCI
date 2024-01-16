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
G-S algo process is non deterministic but result is deterministic \
