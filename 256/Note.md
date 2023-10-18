# COMPSCI 256
# 10/2
## Paper review (40%)
- due 2 pm day of class
- Three parts
  - A short summary 5-10 lines
  - 2-5 points on strenth
## Course Project (60%)
1. Group of 1-3
2. Multiple Stages
   - Title and plan (Oct 16th 5%)
   - Checkpoint 1   (Nov 5 15%) 1-2 pages of report and 5 min recorded presentation
   - Checkpoint 2   (Nov 5 10%) 3-4 pages
   - In-class presentation (Nov29- Dec6 15%)
   - Final report (10%)

## Topics:
1. Deep Learning Frameworks
2. Deep Learning Compiler
3. Deep Learning Hardware

## Distributed Training:
- DNN training is iterative with parameter aggregation after each iteration
- Large amounts (GBs) data exchanged after each iteration
- Two popular modes of aggression
  - Parameter Server
  - Decentralized Aggregation
- Hyperparameter Tuning
- Neural Architectural Search

# 10/4
## Deep Learning WOrkload
- Types of workload
    1. DNN training
    2. inference
- Workload characteristics
  1. Compute intensive 
  2. Memory intensive

## Origin of TPU
- High level architecture
  - Matrix multiply unit
  - 25X MACs compared to GPU
  - 700MHz clock rate
  - 92 T operations/s
  - 4 MiB on-chip accumulator memory
  - 3.5X 

## Systolic Execution
- Problem: During matrix multiplication multiple

## reasons for TPUv1 success
- 2D multiplier instead of 1D

## TPUv2 
- v1 tailored for inference
- v2 targets training workloads

## Training is difficult 
- more compute
- more memory
- more programmable
- bigger numberics
- parallelization is harder