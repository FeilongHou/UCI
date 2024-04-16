# COMPSCI 274C
- Principle
   1. simplify
   2. generalize
   3. take the limit - go to the end of area of exploration
   4. always invert - on the other side perspective

activation functions:
1. identity f(x) = x
2. linear threshold f(x) = { 1, 0 base on condition}
3. sigmoid: continues of linear threshold
4. polynomial
5. max(wixi)
6. ReLU max(0,x)
7. leaky ReLU

|          | model   | error function | activation function | -de/ds | 
| -------- | ------- | ------- | ------- | ------- |
| Regression       | gaussian   | LMS | identity | t-o|
| 2-classification | binomial    | RE KL CE | logistic | t-o |
| multi-classification | Multinomial | RE KL CE | softmax | t-o |

P(M|D) = P(D|M)P(M)/P(D)  D is data, M is model \
binomial model P(t|o) = o^t * (t-o)^(1-t) 

Information theory:
1. event with probability p, the amount of information is -log(p)
2. entropy of H(p) = - sum(p logp)
3. relative entropy

S is activation (input) \
O is output \
f is activation function \

why not crazy activation functions? \
data / information in stored in activation function, not learned. \
coming up with an activation function is difficult \
not possible to come up with activation function in higher deminsion 

try to do xor with 2 x 2 x 1 \
boolean function is always possible with 1 hidden layer \
