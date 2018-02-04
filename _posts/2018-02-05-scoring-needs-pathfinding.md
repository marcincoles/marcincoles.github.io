---
layout: post
date: 2018-02-05
title: Actually, scoring REQUIRES pathfinding
categories: icfp pathfinding algorithms
---

## So there's the rub

With all my thinking about whether I need to do 343 billion operations to find all the shortest paths on mega-maps, it turns out that yes I probably will, at least once (at the beginning). The reason is, that in order to evaluate my score (and those of other punters) during the game, I need a shortest path calculation for all claimed segments.  

While maybe that doesn't mean I need the whole map done, deferring the calculations for each round may not be the best idea if I'm going to be up against it time wise.  Well, the plan is to do a Dijkstra SPF across the map anyway for benchmarking purposes, so I'll have it in my pocket if needed, the alternative would be to run A* (or whatever) across all other punters' claimed segments each round. So it will be  a classic tradeoff of update cost vs retrieval cost.

### Today's progress

Apart from reading some theory, no implementation progress today. It's a bit hard to code with a raging headache.  True, bit hard to absorb new knowledge as well, but harder to assess so it helps to at least feel a little bit productive in spite of challenges.  I don't expect to get much time during the week to make more progress on implementation, but I get my Graph Theory book out every bus trip :)  

### Diversions-in-waiting

That book (Introduction to Graph Theory) in particular, and this project as a whole, is really hampering my progress through the Old Man's War series of books, which (based on the first 2) is a top notch sci-fi series.  #2 'The Ghost Brigades' was even better than the first book.  At some point I know I'm going to crack and get the third book onto my kindle, and then that's going to be zero-progress for 3 days as I consume it. I know it's going to happen, just have to time it well. I've got a work trip later this week, so that might be the opportunity.
