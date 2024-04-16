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
Why 2 keys map to same address   2 mod 8 = 2 & 10 mod 8 = 2 \

poteintiol functions: 0 after expensive steps so phi(after) - phi(before) = negative \

## Expected size of the biggest chain
expected number of key in one cell is alpha \
Chernoff bound: the P() that any given cell has >= x * alpha is at mode (e^x/x^x)^alpha \
Expected size of largest cell is theta(logn/loglogn)

# Cuckoo Hashing
each key has 2 places that can be stored. 