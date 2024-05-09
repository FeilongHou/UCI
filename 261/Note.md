# COMPSCI 261
call recurrence will be stored in call staack \
stacks uses singly linked list with a top pointer points at the top element \
declerative programming language will use array to simulate stacks. \
some real time system will require fast individual operation. \
binary counter, right most 0 changes to 1 and all the 1 behind it changes to 0 \
Naive averaging can be problematic 

Markov's inequality. P[X >= a] <= E[X]/a \
Chernoff bound: intuition X is unlikly to be far from E[X] 

Hash chaining due to different keys map to same address, then store values(key value paires) in a list in that same address. \
Why 2 keys map to same address   2 mod 8 = 2 & 10 mod 8 = 2 

poteintiol functions: 0 after expensive steps so phi(after) - phi(before) = negative 

## Expected size of the biggest chain
expected number of key in one cell is alpha \
Chernoff bound: the P() that any given cell has >= x * alpha is at mode (e^x/x^x)^alpha \
Expected size of largest cell is theta(logn/loglogn)

## Cuckoo Hashing
each key has 2 places that can be stored. 

## Week 5 Thursday
**Fibbonachi heap:**
When mark is true, cannnot remove more children. Make it a root. Once removed one child mark parent true.\
Last node on a removal path will have only one child removed. \
2 trees with equal degree should merge \
how to merge: compare priority of trees, larger priority become the child of smaller tree 

**interger priority queues:**
1. Bucket queue
   - arrange items into buckets by their priorities
   - scan buckets in order to find the first nonempty one
2. Flat Trees
   - map x_high to x_low
   - x_high are prefixes of numbers
   - x_low are actural numbers without prefixes

## week 6 Thursday
balanced binary search tree, we will need clost number of left nodes and right nodes. There are 2 methods of maintaining balance
1. rebuild 
    - rebuild subtrees when they go too far out of balance.
2. Rotate
    - take 2 nodes of the tree can rotate their orders and adjust their children.

**splay tress:**
can bring any node to root by sequences of rotation. 
- Search: using binary tree search and splay the lowest interior node 
- Split into 2 subtrees at some key: splay the key  break link to its left child
- concatenate two subtrees: splay leftmost key in right subtres and left subtree as its child
- add/remove: split and concatenate

for a node xi with subtree Ti (include xi and all its descendants) \
rank ri is floor(log(sum of all weights in Ti)) \
potential function = sum of ranks of all nodes \
amortized time to splay xi is O(log(W/wi))

