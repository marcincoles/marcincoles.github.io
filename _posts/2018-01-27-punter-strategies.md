---
layout: post
title: Punter Strategies
date: 2018-01-27
categories: icfp ai algorithms
---
## Here's a starting list of the Punter AI strategies, in rough order of my perceived difficulty of implementation, and probably score-performance.

### 1. Totally Random
This punter just claims river segments at random. Does not check for existing claims, does not look for mines.  My expectation is that this one will run really fast, but be pretty much useless.  It will likely not score any points as it will be unlikely to claim a river segment with a mine on it, it will not likely make joining river segments, and it will try to claim already claimed rivers, resulting in a pass.

### 2. Smarter Random
This punter starts by trying to claim a mine river segment if one is available, and it will not claim already claimed rivers, but beyond that it chooses at random.  Almost certain to beat #1

### 3. Sequential random
Like #2, but when it chooses the next node, it does so by choosing (at random) one of the river segments linked to the previous one. Should be better performant than the other randoms.

### 4.Long Runner
This punter is trying to optimise for the longest possible path for maximum points.  It will find the furtherest-away node, find the shortest path to it, and claim as many segments as possible.

### 5. Mine linker
Claim as many mine river segments as possible, then create a route between them.

### 6.Choker
Along the current path find fan-in scenarios, where there are more links on the source side of the graph than the destination side

### 7.Blocker
Claims mines first, then goes into reactive mode to block another players moves.  eg if player 2 claimed segment (1,2), and node 1 had neighbours (2,9,10) and node 2 had neighbours (1,3,5,6), it would select on of the possible sements (eg (2,3) or (1,10), etc).  Not sure yet what heuristic to use, maybe just random to start with.
