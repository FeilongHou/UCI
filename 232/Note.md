# COMPSCI 232 
# 9/28
Office: DBH3212 leverato@uci.edu

## Networks:
- Architecture
- Applications
- Protocals
- LANSs

# 10/3 Begin of Architecture
## Telephone network and circuit switching
1. 1 application
2. Long unicast connections/sessions
3. Almost constant traffic generation during the connection
4. Sparse call arrival

Trunk lines carry more than 1 call simultaneously (thousands- millions high capacity)

Signal degrades with distance
- Analog sensitive to noise
- Digital: regeneration, revocery

# 10/5
## Analog vs Digital
sample a analog signal can turn to ditigal \
get a y value at every dx, then each y value become bits \

multiple dimensions for signal
  - space
  - time
  - frequency

## Exponential distribution
X random variable - continueous \
X is exponential with (lambda) if it has the following probability density function \
f(x|lambda) = {lambda*exp(-lambda*x), x > 0 \
               0 , x <= 0} \
lambda > 0 ("rate") arrival
1. E[x] = 1/lambda = integral from 0 to inf (x * lambda * exp(-lambda * x))
2. P(x > t) = exp(-lambda * t) probability of recieve a new packet 

it has properties: 
1. memoryless property
   - x ~ EXP[lambda]
   - P(x > t) = exp(-lambda * t) probability receive packet after t
   - P(y > t | x > s) = exp(-lambda * t) probability receive packet after t give x > s
2. Minimum
   - x1, x2, ..., xn independent variable
   - xi ~EXP[lambdai]
   - min(xi) = ?
   - P(min(xi) > t) = exp(-(lambda1 + lambda2 + ...) * t) sum of all lambda
   - P(min(xi) = xj) = lambdaj /(sum of all lambda)

n variabes x1 to xn are independent random variable xi ~ EXP[lambdai] \
P(min(xi) > t) = exp(-(lambdai) * t)  lambdai is a rate \
P(min(x1...xn) = xi) = lambdai/(lambda1 + ... + lambdan)

## Example:
two server in series, service time at server 1 is exponential with rate mu1 service time, service time at server 2 is EXP[mu2] \
packet C goes into server 1 and packets A&B goes into server 2 
- Pa -> probability A is still in service when C move into server 2
- Pb -> probability B is still in service when C move into server 2
- E[T] = ? T is the time for C to finish process

**if just C exist E[T] = E[T1] + E[T2] = 1/mu1 + 1/mu2 where E[T1] = 1/mu1**

P(c -> server 2 before A -> out) = P(t1 < t2) = P(min(t1,t2) = t1) = mu1/(mu1+mu2)

# 10/10
we have 2 servers, with process rate mu1 and mu2 (mu1 packet/s) with AB packet in server 2 and C in server 1
- we have xA and xC
- Pa = P(xC < xA) = P(min(xA, xC)= xC) = mu1/(mu1 + mu2)
- P(a out) = mu2/(mu1 + mu2)

now difficult part: C -> 2 B is still in 2 \
only bad situation is after A out B is also out but C did not finish \
base on memoryless P(B out) = mu2/(mu1 + m2) \
Pb = mu1/(mu1 + m2) + mu2/(mu1 + mu2) * mu1/(mu1 + mu2) or (1 - (mu2/(mu1 + mu2))^2) \
T -> C -> OUT \
E[T] = ? \
NO B&A = 1/mu1 + 1/mu2 \
with B&A = 1/mu1 + 1/mu2 + ... \
if all ABC packet are in just one server \
E[T] = E[TA] + E[TB] + E[TC] = 3/mu1 \
if C move to 2, it will be the case above \
T = T1 + R1   E[T] = E[T1] + E[R1] \
E[T1] = 1/(mu1 + mu2) \
E[R1] = P(C -> 2) * E[R1 | C -> 2] + P(A -> OUT) * E[R1 | A ->OUT] \
P(C -> 2) = mu1/(mu1 + mu2) \
P(A -> OUT) = mu2/(mu1 + mu2) \
E[R1 | C ->2] = 3/mu2 \
E[R1 | A -> OUT] = E[T2] + E[R2] \
E[T2] = 1/(mu1 + mu2) \ 
E[R2] = P(C -> 2) * E[R2 | C -> 2] + P(B -> OUT) * E[R2 | B ->OUT] \
E[R2 | B -> OUT] = 1/mu1 + 1/mu2

# 10/12
Telephone network often connec 10000 lines \
Propagation delay = distance / propagation time \
## internet design
- Multiply applications (file transfer, email)
- Bursty traffic generation
- Short (frequent) connections
- Packet switching Resource sharing
- Best effort (design variable)

## Packet Switching (internet)
- idea: decompose message into packets
  - Transmit the packets one by one
- Packet switches/routers replace telephone routers
  - Instead of setting up "circuits" for each call, route packets one by one
  - Packet are buffered, first in first out.
- Efficient for bursty traffic

## Terminology
- synchronous
  -  all packets experience same delay from source to destination
- asynchronous
  - packets experience different delays from source to destination, depending on queuing in routers
- connection-oriented
  - packets arrive in sequence sent
- connectionless
  - packets dont necessarily arrive in sequence sent; need packet ordering
- reliable
  - no packets are dropped
- unrealiable
  - some packets dropped by routers; may need packets retransmission

# 10/17
BSC (base station controller) control channel resource and hondoff \
MSC (mobile switching center) routes calls using the visitor location register (local users) and the home location register (last known location) \
upstream and downstream are in different slots(halfduplex) \
## Packet switching performance metrics
- Packet delay
- Packet loss
- Throughput
- (Efficiency)

Performance metrics are interdependent \
e.g.: no delay constraint = packet loss probability close to zero \
## Processing delay
defined by the hardware
## Propagation delay
Propagation delay = distance/propagation speed \
## queueing delay
it is random 
## Throughput
Throughput = bits per seconds \ 
3 server 3 clients the throughput is Min(Rs, R/3, Rc) \
## Efficientcy
data successfully delivered to the destination / overall resource used
# Layers
## layering
- layers provide functionalities/services to the upper layers
- some information exchange (e.g. failure report)
- NOT optional
