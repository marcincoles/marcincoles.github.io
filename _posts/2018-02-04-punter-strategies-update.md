---
layout: post
title: Punter Strategies Update
date: 2018-02-04
categories: icfp ai algorithms strategy
---

## Some more thoughts on [Punter Strategies](/icfp/ai/algorithms/strategy/2018/01/27/punter-strategies.html)

### New ideas
8. Local spokes

Instead of trying to expand across the whole map with one long claim, hedge your bets and fork out in multiple directions for smallish distances initially.  Once that plan is exhausted, build on one for a number of moves, then on another, etc.  Since scoring is #rivers^2 pushing in one direction is recommended, but this method provides an in-between strategy that should score some decent points, and in theory doesn't require a complete map view to execute.  Algorithm could be: from current furtherest point node n, select adjacent nodes n(a), for each n(a) calculate SP back to mine. select the n(a) with the longest path SP and claim the river to that node.  We want to avoid creating short-circuits back to the mine that we haven't claimed.

9. Spoiler

Probably a late-game strategy. Look at other punters paths and see if you can reduce their score by creating short-circuit paths back to the mine. This could have a dramatic effect on their score - for example if they have a 12-river path back to the mine, and you can shorten it by just 2, you've taken their score down from 144 to 100, going from 20 to 18 would yield a decrease of over 140!  That's a decent payback for your 2 claims.  It could be a decent sized search space, but if we already have all shortest-path data for the map, then all we need to do is count the claimed rivers between a specific site in the claimed section and the mine, then compare against SP data we have. If |claimed path| > |SP|, then we have an opportunity to spoil. Obviously would need to compare against benefit of improving our own claimed paths.

### Old ideas revisited

1. Totally Random

Initially, the thought was for a totally random river claiming algorithm.  This is totally useless, so at a minimum this one needs to start from a river segment adjoining a mine.  Otherwise it will never score a point.

2. Smarter Random
This one can stay as is.

3. Sequential random

Keep as is.

4.Long Runner

As mentioned in the [discussion on pathfinding](/math/graph/pathfinding/complexity/big-o/2018/02/03/pathfinding-woes.html), this strategy can be very computationally intensive (and memory intensive) on mega-maps like Edinburgh.  Will need to take this into account in the design.
5. Mine linker

This one should be less of a resource hog than Long Runner as it only needs to calc Shortest Path to a single point, not all points, so O(n^2) rather than O(n^3) - that's quite a difference on a big map (49 million vs 343 billion).

6. Choker

With the addition of the 'options' extension, this strategy may be unviable as it will not actually achieve anything. The only caveat being that there is an option restriction == #mines, so if this strategy is adopted it will require a long straight segment, although from a cost-benefit perspective it's hard to see this being better than claiming another river flowing into a mine.

7. Blocker

Will be totally useless with options; was of dubious value even without options.  It's a pretty defeatist strategy, really, although it could be a mid-game switch if internal scoring shows things aren't going well anyway. Probably superceded by #9 spoiler.
