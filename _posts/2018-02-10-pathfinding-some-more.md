---
layout: post
date: 2018-02-10
title: More on pathfinding
categories: pathfinding icfp algorithms
---

Some clarification is required.  I'd [previously written](/math/graph/pathfinding/complexity/big-o/2018/02/03/pathfinding-woes.html) that I'd be using Dijkstra's algorithm to find all the shortest paths, but that's not correct. To get all the shortest paths between all the nodes, it seems the [Floyd-Warshall](https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm) algorithm is what I mean - I keep getting all the names mixed up - silly :)  Anyway, I'll start with a fairly naive implementation, but it looks like a good task for numpy with its optimised matrix operations.

I was watching some geek TV on youtube while I was travelling on business, and I came across [this talk by Scott Meyers](https://www.youtube.com/watch?v=RT46MpK39rQ) about what's important to focus on when developong software, from DConf, and he's certainly made me think that optimising for speed and efficiency when you need it is obviously important, especially in simulation.  Don't be lazy! I know I need to learn numpy at some point, so it's probably a good time now.
