# COMPSCI 244
**IoT:** internet of things, set of connected devices \
collect data, send to data center for computing because embedded system has limtied processing power \
Demand of real time computer made cloud computing obsolete \
embedded system today requires computational power \
cyber-physical system can react or actuate base on data collected. 

**Efficiency**:
- code size
- run time
- weight 
- cost
- energy
  
real time constraints: A real time system must react to stimuli within the time interval dictated by the environment, CPS must meet real-time constraints. 

a sensor is a device that measures a physical quantity \
an actuator is a device that modifies a physical quantity 

design issue with sensors
1. calibration
2. nonlinearity
3. sampling
4. noise
5. failures

model is equations, target is the real thing, high fidelity is how werll the model matches the target. 

A model is deterministic if given initial state and the inputs, the model defines exactly one behavior. \
large system and be non-deterministic 

## Finite State Machine
At any time t, the system is in only one state until change mode, stay in one state until something happens. \
clock is used to sync different components with different frequencies .\
for more detail, there will be N states for N cars in a parking garage. \
powering up brings the system to state 0 \
threshold between 2 state needs buffer, i.e. cannot be the same value 
- switching state without an event is time-triggered model, no condition needed.
- switching state with an event is called event-triggered model .

history stage can be used to remember where the process leftoff. \
FSM is in all sub-states of a super-state. 

**Receptiveness**: For any input values, some transition is enabled. Our
structure together with the implicit default transition ensures that
our FSMs are receptive. \
**Deterministics**: In every state, for all input values, exactly one (possibly
implicit) transition is enabled. 

## Data FLow Model
node is a task or program with FIFO buffer in between nodes. Writers never wait. \
only 1 sender and one receiver per FIFO \
**concurrency!!!**

## Petri net
key elements
- conditions - met or not
- event - take place if condition is met
- flow relation - relates conditions and events

No mapping or connected edges between same group/class \
one token can only trigger one event even if a condition connected to 2 events \
simple nets not has more than 1 pre or post connections \
2 conditions connect to 1 event, then both conditions need to met before event fires \

## Embedded software
specialized software and OS to optimiza processor performance. General purpose OS is not suitable. 

## Multithreading
quad-core has one main memory and communicate with all the cores. shared memory architechture. \
threads run concurrently if their logical flows overlap in time. \
Single core is switching threads very frequently to achieve multi-threading. \
Multi-core has multiple cores that can run multu-thread simultaneously. \
each thread has its own private memeory to store things. \
shared memeory can be accessed by all threads .\
there is no ordering in multi-thread. 

## I/O management
input device independent \
CPU writes command to memory and the system bus will ship command from memory(I\O buffer) to device controller \
**I/O mapping:** I/O memory are shared by multiply devices and take up a section in physical memory \
**Isolated I/O:** separate address space for memory and I/O device \
**Programmed I/O(polling):** monitor I/O consitantly CPU is blocked \
**DMA-base(directed memory access):** Off-load CPU runtime to adaptor or DMA controller, I/O interact with memory \
**interrupt:** in the middle, CPU will be interrupted and save info to memory

## device driver:
black box, cannot be tested or seen. 

## virtualization on embedde 
**asymetric** multiprocessing means there are multiple OS runing. one-to-one mapping isn ot necessary. one OS can access one or multiple cores at a time without mapping.  \
**symetric** mean there is only one OS for all cores. \
VM to core has a layer called hypervisor to communicate between VM and core. 
overhead: system will be slower and memory useage is higher. 

**complete fair shcedule(CFS)**:
- task 1 40ms
- task 2 10ms
- task 3 80ms

divide 90ms to all three tasks so each one get 30ms computation time \
then
- task 1 10ms
- task 3 50ms

divide 90ms to 2 tasks so each one get 45ms \

## engergy comsumptions
P_total = P_dynamic + P_static \
the goal is to reduce power consumptions to preserve battery life and reduce heat on portable device. \
voltage frequency pair: high frequency high voltage, and vise versa. \
 off-load task from one core to 4 cores with lower frequency. The computation time is the same but saves enery and power due to non-linear relationship to volatge. \

 ## ILP (interger linear programming)
 x1, x2, x3, ... , xn \
 constrains: linear function of variables (2x1 - 3x2 + 0.5x3 <= 3.5) \
 objective: max 2x1 + 3x2 - x4 \
 knapsack example: constrains cixi <= C \
 max gixi  where gi is value 

HW: T1 -> T2 -> T3 Deadline D1, D2, D3 \
CPU: (v1, f1) (v2, f2) \
x1 indicates if T1 is running on (v1, f1) or (v2, f2) \
xij = 1 if Ti was at (v1, f1) else 0 \
excution time of T1 <= D1 \
sum of Cijx1j for all j <= D1 \
uniqueness contrains: sum of xij for all j = 1 \
C1jx1j + C2jx2j <= D2