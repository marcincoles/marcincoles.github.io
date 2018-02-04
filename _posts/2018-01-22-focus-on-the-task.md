---
layout: post
title: Focus on the task at hand
date: 2018-01-22
categories: programming python icfp tdd 
---
## Let's focus on the task at hand, shall we

Last couple of posts, I was getting a bit excited about doing some Flask development.  I got a bit carried away with the idea of doing APIs and microservices.  I drew up a microservice architecture, and how I was going to use that as the springboard for doing the ICFP contest task.  

#### But really....

What I want to achieve is to do is create a solution for the ICFP 2017 contest. Web development is not really part of that. The problem domain is in graph theory and optimisation, not microservice architecture.  So instead of getting distracted by the next shiny thing (well, maybe just one or two - see below) I'm returning my focus back to ICFP.  

Last 2 days I've got a map reader built, using a TDD approach, and now I'm working on the Graph code.  Again I'm using a TDD approach - I've designed an API on paper (not a webservice/HTTP API, a traditional software API) and started writing tests. So far my experience has been pretty good with the TDD approach, although I know that I'm still doing it pretty light on, and mostly focussing on making sure happy paths work, rather than unhappy paths don't work, but even now going onto my second test suite (test_graph) I'm implementing more of the unhappy flow test cases.

I've got some existing code for a generic undirected graph already (from one of the exercises in checkio) and I'll use that as a staring point, depending on how much work there will be to redo the interface to what I need.

#### Python properties

Today I learned about properties
```python
class C():
    __init__(self):
        self._x = 0
        
    @property
    def x(self):
        return self._x
        
    @x.setter
    def x(self, value):
        self._x = value
```

So these are like properties in C# and Java and allow for a bit of encapsulation of the internal structure vs the external API. There seems to be a body of thought that doing things the 'Java way' is un-Pythonic, but it makes sense to me especially to avoid getXXX() and setXXX() type methods.  I don't really want to expose the internals too much, but the bigger driver was that I wanted to be able to update internal data when certain properties change and short of using setXXX()-style getter/setter methods (which certainly aren't the Python way), properties seem like a good solution.

## Shiny new toys.

While I'm not interested right now about web dev, it's good to know that I can extend python into the presentation layer inside the browser. There's two tools that I will investigate:
* [Transcrypt](https://www.transcrypt.org)
* [Brython](http://www.brython.info)

I'm not yet at the stage where I need to make a decision on the above, but they both look promising.  
