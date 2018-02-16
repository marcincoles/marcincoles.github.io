---
layout: post
title: Maps and Pathfinders
date: 2018-02-16
categories: pathfinding algorithms
---

## Pathfinding realities

It's pretty clear that calculating the paths between **all** nodes within a map, for any reasonable sized map, is going to exceed my time budget in the contest.  The Floyd-Warshall algorithm has just too many calculations to make, and performance-wise I'm going to be in trouble.  I could get a decent boost using PyPy for the initial whole of map calcs, but according to the PyPy documentation, I'll then suffer the JIT compiler warmup for all following turns - they say up to a second on the [PyPy performance page](https://pypy.org/performance.html) - but they do also recommend actually measuring rather than guessing.  Yet another experiment to do! I haven't run with PyPy yet, so will be interesting.

The problem I discovered the other day regarding non-contiguous node numbering can be approached in two ways, that I'm assessing now.  Considering I've already got the FW algorithm coded, it would probably be best to get the map reader in the Graph class to normalise the node and edge ids as it goes along, and the pathfinders can then just use that.  Then all I'll need to do is have a translation for updates from the server and for making claims - and this can be encapsulated pretty easily.  I'll need to see if this makes debugging and visualisation a bit tricky, because the internal state and the external state won't be quite the same.  

My initial thought on the approach was to normalise/denormalise the represenation during pathfinding, so paths[x][y] would be mapped to paths[x'][y'] on every access, but considering we're already performance bound this is going to be much more overhead to deal with.

### Alternative Pathfinding

Since I don't need to know every path from every site, I can save a lot of time just focussing on mapping all the paths from mine sites only - this should take us down from O(v^3) to O(v^2) or thereabouts.  That could be a significanltly bigger saving than a upto 6x improvement moving to PyPy. So that will be either A* or a BFS/DFS search (thinking DFS in order to get at least some interesting - long path - results if time-bound) from the mine sites to all other sites.  I can see how to prune that further as required later.  Of course I should have known that FW was probably overkill, but it's been interesting to see how much a full search actually costs.
