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
