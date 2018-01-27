---
layout: post
title: Punter Strategies
date: 2018-01-27
categories: icfp ai algorithms strategy
---
Here's a starting list of the Punter AI strategies, in rough order of my perceived difficulty of implementation, and possibly score-performance.  I intend to implement all these so that I can start having tournaments against myself, and it will be interesting to see how they all perform before any optimisations or strategy combinations.

I tend to think #4 Long Runner and #5 Mine Linker would have best overall score performance against intelligent opposition, unless the opposition takes approaches like #6 Choker and #7 Blocker.

Ultimately, the algorithm will need to probably be a combination of these.  I've got to read up more about Genetic Algorithms to understand how that could be used in combining the different strategies for an overall most successful outcome. I will probably need a greater population of algorithms so that it can experiment, mutate and all that more efficiently, so this list is a WIP.

### 1. Totally Random
This punter just claims river segments at random. Does not check for existing claims, does not look for mines.  My expectation is that this one will run really fast, but be pretty much useless.  It will likely not score any points as it will be unlikely to claim a river segment with a mine on it, it will not likely make joining river segments, and it will try to claim already claimed rivers, resulting in a pass.

### 2. Smarter Random
This punter starts by trying to claim a mine river segment if one is available, and it will not claim already claimed rivers, but beyond that it chooses at random.  Almost certain to beat #1

### 3. Sequential random
Like #2, but when it chooses the next node, it does so by choosing (at random) one of the river segments linked to the previous one. Should be more performant than the other randoms.

### 4.Long Runner
This punter is trying to optimise for the longest possible path for maximum points.  It will find the furtherest-away node from a mine, find the shortest path to it, and claim as many segments as possible.

### 5. Mine linker
Claim as many mine river segments as possible, then create routes between them.

### 6. Choker
Along the current path find fan-in scenarios, where there are more links on the source side of the graph than the destination side.  Probably has to be used with another strategy to generate the desired path.

### 7. Blocker
Claims mines first, then goes into reactive mode to block another players moves.  eg if player 2 claimed segment (1,2), and node 1 had neighbours (2,9,10) and node 2 had neighbours (1,3,5,6), it would select on of the possible sements (eg (2,3) or (1,10), etc).  Not sure yet what heuristic to use, maybe just random to start with.
