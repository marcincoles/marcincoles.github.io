---
layout: post
date: 2018-02-14
title: The Floyd-Warshall Algorithm
categories: pathfinding icfp algorithms
---
## The Floyd-Warshall Algorithm

Last night, for my birdhday, I implemented the [Floyd-Warshall algorithm](https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm), complete with path reconstruction.  It worked first time against a a small map, so that was nice (initial functional testing done).  I had to change the API a little bit, I was planning to implement this purely functional, but in the end went with a class and kept the two matricies as instance variables.  This made it easier to generate the path data first, and call upon reconstruction as required.  I will need to add an extra call, at the moment I have get_path(src,dest) --> list(sites), but for the challenge I also want to get a list of river segments, so I'll add two more member methods: get_path_sites(src,dest) and get_path_rivers(src, dest) which will return a list of river-segment tuples.  In fact, I will subclass this for ICFP-specific requirements, which will includ options and claims in the pathfinding.

### How does the algorithm work?

It's actually not a super-sophisticated algorithm, although it does have an optimisiation in the calculation of path distance, by taking the knowledge that if a path from node i to j goes through k, and we already know k->j we don't need to recalculate it.  Apparently this saves a lot of effort in highly-connected/dense graphs, although of less use in sparsely connected graphs where Dijkstra will do as well or better.  TBH, looking at the numbers, the ICFP maps are not that dense, but we'll need to benchmark to see if it's worth optimising.

All up, a nice step in progress. Now lets get timeit going.

### Except...

It turns out that the node ids, while they are guaranteed to be integers, are not guaranteed to be contiguous.  I found this on the 'tube' map, where of the 301 nodes, ids 164 and 165 are missing, and we have ids 301 and 302, which screw up the F-W algorithm.  So I guess I'm going to have to do some mapping of node numbers into a continuous patch, or hope that numpy arrays have some interesting capability there. One thought is making missing node id's unreachable, but I have a suspicion that's going to wreak some havoc on the algorthm, and it could potentially make it a very large sparse graph.  I guess some investigation is in order.

### Initial performance results

Running timeit on a graph *with* contiguous node ids (randomMedium - 97 nodes, 187 edges) takes just under 0.6 seconds to calculate all path lengths on my computer (i5 7220 i think).  A 5-node test map takes 0.0008s.  We can see the V^3 effect there, and I wanted to see how 'tube' would handle it - extrapolating from what I've got, running the FW algorithm on that map will get me close to my 10-second startup timeout, and doing it on a mega-map won't meet the time requirements.  So a rethink will be in order. Obviously doing constant mapping of nodeIds won't help that at all. Potentially a partial calc and save of state may help, but if I need to recalc all the paths every turn I'm going to get into trouble, so the all paths approach will probably need to be ditched or reworked.
