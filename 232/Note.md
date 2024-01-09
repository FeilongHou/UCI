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
e.g.: no delay constraint = packet loss probability close to zero 
## Processing delay
defined by the hardware
## Propagation delay
Propagation delay = distance/propagation speed 
## queueing delay
it is random 
## Throughput
Throughput = bits per seconds \
3 server 3 clients the throughput is Min(Rs, R/3, Rc) 
## Efficientcy
data successfully delivered to the destination / overall resource used
# Layers
## layering
- layers provide functionalities/services to the upper layers
- some information exchange (e.g. failure report)
- NOT optional

# 10/19
## Process
X(t) a random process
## Poisson Process
{X(t), t >= 0} increment
assume t and s, where s < t, we have random variabel X(t) and X(s) \
increment is X(t) - X(s) is random variable function of t-s\
**Independent Increments** disjoint intervals (2 intervals that are not overlapped) \
X(t1) - X(s1) and X(t2) - X(s2) are independent \
continuous time {N(t): t >= 0} Rate is lambda \
They have the following **properties**:
1. N(0) = 0
2. Has stationary(they have the same distribution i.e. same size interval) and independent increment
3. Distribution of N(t) is Possion with mean lambda * t. P(N(t) = k) = (lambda * t)^k / k! * exp(-lambda * t)
4. Superposition
   - 2 Possion processes lambda1 and lambda2, sum together with rate lambda1 + lambda2
5. Thinning
   - P.P with rate lambda mark some events with probability P minus the ones that are not marked so we have new rate lambda * P

## Possion process is a counting process
P(N(t2 - t1) = k1) assuming 0 to t1 is the same as t1 to t2

# 10/24
## HTTP (application layer)
**Does not track state**
- Purpose: request and transfer a webpage from a server to a user
- Service characteristcs:
  - pages requested and sent at random times
  - connected only for duration of download
- Performance:
  - loss, not ok
  - delay, few seconds ok, but flexible
  - throughput, higher is better, but flexible
- Connection initiation
  - well-known ports (80)
  - client(browser) - server(webserver)
  - connection access control (limited resources, TCP)
  - server balancing
- Connection management
  - Non-persistent:
    - each file requires a separated connection
    - workaround: open parallel connection, one for each image
  - persistent:
    - close connection only after client is done with server (or timeout)
    - Serial objects transfer

## TCP connection (application layer)


# 10/26
## File sharing
- Purpose: file a file and transfer it from multiple other users
- Service characteristics:
  - search for file
  - identify which users have which pieces
  - transfer pieces and put it together
- Performance:
  - loss - not ok
  - Delay - very flexible, often hours
  - throughput - higher is better, but flexible
## File sharing: search
- Location?
  - e.g. tracker
- Client-server or peer-to-peer?
- Two functions:
  - search usually client-server
  - file transfer peer-to-peer

## BitTorrent:
- File split into "chunks"
- CLient side:
  - request missing chunks directly from other peers, via TCP
- Server side:
  - listen for and service requests for chunks you have, via TCP
- Program:
  - client algorithm determines which chunk to request first, e.g. rarest first
  - Server algorithm determines rate, e.g. number connections, max rate

## Streaming
- Purpose: 1 way transmission of audio or video
- Service characteristecs:
  - constant bit rate (unless compressed)
  - duration = mins to hours
- Performance:
  - loss- small amout ok
  - delay - seconds, firm once stream started
  - throughput - fixed
## Voice and dideo over IP
- Purpose: 2 way interactive transmission of voice and video
- Service characteristics:
  - constant bit rate (unless compressed)
  - duration = mins to hours
- Performance
  - loss- small amout ok
  - delay - a few tenths of a second
  - throughput - fixed

## QoS Requiremetns
- Packet loss
  - up to 20% is tolerated
  - packedt llosses
    - buffer overflow
    - link layer
    - delay
- UDP vs TCP
  - reliability (retransimission)
  - delay
  - buffer starvation
  - delay variations
- Jitter
  - burst of packet
  - Timestamp
    - generation time
  - **delayed playout**
    - delay is a random variable
    - variations due to network conditions
    - min delay with loss constraint
    - fixed playout
      - t + q
      - generation + delay+ max variations
      - large variations = large delay
    - adaptiove playout

# 10/31
## Packet loss recovery
- TCP
  - retransmission
  - delay
- Recovery
  - FEC
  - interleaving
  - No additional RTT

## FEC
- Redundancy
  - +1 ojet every N
  - N small
    - larger than generation rate
  - delay: wait for entire group
- Low rate stream
  - low quality/low-bitrate stream appended

## Interleaving
**rearrange before sent, after received reconstruct**
- Samples are resequenced
  - adjucent sanples assigned to different chunks
- Packet loss mitigated
  - avoids gaps
- increased latency
- same bandwidth

## Real Time Protocal (RTP)
- UDP
  - RTP-UDP-IP
- RTP
  - independent RTP stream per source
  - video/audio payload+header

## Support Multimedia

# 11/07
## queueing system
router can be count as a queueing system \
## Delay analysis
arrival -> (rejection) -> delay -> departures \
T time spent in the system \
N(t) -> # of things in the system at time t \
Pb probability of "blocking" \
A(t) -> arrival ip to time t \
D(t) -> departures up to time t \
B(t) -> blocked up to time t \
N(t) = A(t) - D(t) - B(t)

## Arrival rate (pkt/sec)
lambda = lim(t -> inf) A(t)/t
## Through put (pkt/sec) rate of pkt went through
lim(t -> inf) D(t)/t
## Pb
lim(t -> inf) B(t)/A(t)
## Expected # of pkts in system
E[N] = lim(t -> inf) 1/t integral from 0 to t (N(telda) dt) \
average area under the curve

## Arrival graph
looks like stairs going up\
lambda = lim(n -> inf) n/(tel1 + tel2 + ... + teln) or 1/(tel1 + tel2 + ... + teln)/n = 1/E[tel]
## Little's Formula
E[N] = lambda * E[T] \
N(t) = A(t) - D(t) \
1/t0 integral from 0 to t0 N(t') dt' = 1/t0 sum (j = 1 to A(t0)) Tj * 1 = A(t0)/t0 * (1/A(t0) sum J = 1 to A(t0) Tj) \

with blocking: \
E[N] = lambda * (1 - Pb) * E[T]

## queueing model
A(t) -> B(t) -> buffer -> server -> D(t) \
lambda = 1/E[t]    service time mu = 1/E[x] \
m : arrival distribution m->Exp G->general D->Deterministic \
mu : servie distribution \
c : # of server \
k : max # pkts in system

# 11/21
m/m/1/k \
buffer with k slots, one is being served \
interarrival -> tal~EXP[lambda] E[lambda] = 1/lambda \
Arrival -> A(t) is a possion process \
service x~EXP[mu] E[x] = 1/mu \
state: 1, 2, 3, .... , k \
dt \
P[1 arrival in dt] = lambda * dt + o(dt) \
P[0 arrival in dt] = 1 - lambda * dt + o(dt) \
P[>1 arrivals in dt] = o(dt) \
P[1 departure in dt] = mu * dt + o(dt) \
P[0 departure in dt] = 1 - mu * dt + o(dt) \
P[>1 departure in dt] = o(dt) \
P[0 arrival & 0 departure] = (1 - lambda * dt + o(dt))(1 - mu * dt + o(dt)) = 1 - (lambda + mu) * dt + o(dt) \
P[1 arrival & 0 departure] = (lambda * dt + o(dt))(1 - mu * dt + o(dt)) = 
lambda * dt + o(dt) \
P[0 arrival & 1 departure] = (1 - lambda * dt + o(dt))(mu * dt + o(dt)) = mu * dt + o(dt) \
P[1 arrival & 1 departure] = o(dt) 

P[stay at 0 state] = 1 - lambda * dt \
P[goes to 1 state] = lambda * dt \
P[stay at n state] = 1 - (lambda + mu) * dt \
P[go to n+1 state] = lambda * dt \
P[go to n-1 state] = mu * dt 

P(N(t) = n) = Pn 

m/m/1 with infinite buffer(state) \
Pn+1 * (mu * dt) = Pn * (lambda * dt) flow conservation \
Pn+1 = (lambda / mu) * Pn \
Pn = (lambda / mu) * Pn-1 \
Pn+1 = (lambda / mu)^(n+1) * P0 \
1 = P0 + P1 + P2 + ... \
1 = P0(1 + ro + ro^2 +  ro^3 + ...) where ro = lambda / mu \
1 = P0 (1/(1 - ro)) -> P0 = 1 - ro = 1 - lambda/mu \
Pn = (1 - ro) * ro^n \
E[N] = sum (n * Pn) = sum (n (1-ro) * ro^n) = ro/(1 - ro) \
E[Total time] = E[N] / lambda = (1/mu)/(1-ro) \
E[waiting time] = E[Total] - E[x(service time)] = (1/mu)*ro/(1-ro) 

m/m/1/k \
Pn+1 = ro^(n+1) * P0
1 = P0 * (1-ro^k+1) / (1-ro) \
P0 = (1-ro)/(1-ro^k+1) \
Pn = (1-ro) * ro^n / (1-ro^k+1) \
E[N] = sum (n * Pn) = ro/(1-ro) - ((k+1)ro^k+1)/(1-ro^k+1) \
E[T] = E[N]/(lambda * (1-Pk)) \

# 11/28
m/m/c/c \
first c: # of server \
second c: # of things queuing \
mu = 1/E[x] \
P[connection request in dt] = lambda * dt \
P[1 connection termination in dt | N(t) = n] = n * mu * dt \
P[nothing happens in dt | N(t) = n] = 1 - (lambda + n * mu) * dt \
At c-1 stage moving back to c-2 stage is (c-1) * mu * dt \
Pn+1 * (n + 1) * mu * dt = Pn * lambda * dt -> Pn+1 = lambda/((n+1)*mu) * Pn = (lambda/mu)^(n+1)/(n+1)! * P0 \
1 = P0 + P1 + ... + Pc = P0 sum n from 0 to c(ro^n/n!) ro = lambda/mu \
P0 = 1/sum n from 0 to c(ro^n/n!) \
P[N(t) = n] = ro^n/n! / sum k from 0 to c(ro^k/k!) \
Pb = Pc = ro^c/c! / sum k from 0 to c(ro^k/k!) \
E[T] = 1/mu \
