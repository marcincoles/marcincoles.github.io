---
layout: post
title: Day 2 plan - Repo setup, unit tests, falcon
date: 2018-01-07
categories: programming python falcon testing
---
## Lessons so far
Yesterday was a fruitful learning day. 

### Repo setup
Going through the repo setup has been very illuminating, and it's opened up for
me some of the 'meta' programming elements of python that I haven't really
dealt with before - so far I've been very much focussed on learning the core language constructs and applying them to algorithms from a more funtional sense, but real deployed software has constraints and python is no different.

I've still got to get my head around the Pipfile/requirements.txt/setup.py subtelties - and this discussion on [Reddit has been useful](https://www.reddit.com/r/Python/comments/3uzl2a/setuppy_requirementstxt_or_a_combination/)

### Falcon
I think there will be a bit for me to figure out how to best structure web
services using Falcon (or indeed any framework), and at the moment I'm having a
little bit of 'buyers remorse' whether a more popular framework like Flask
would have been a better choice given the size of its community, but
considering I'm on day 2 now, it's probably a bit too early to second-guess
these things, and let's face it, it's not like Falcon is that obscure.

## Today's Plan
1. Finish off repo setup, and fork the work for future ease of use
2. Write some unit tests for the status-service
3. Update this page at the end of the day with progress - yesterday I added a
second post with the same date and it's shown out of order.
4. Re-config vim - it's now starting to get good for python, but some settings
like hard stop at 79 chars is interfering with writing markdown.

### Outcome of today
1. Well, got a service running, on gunicorn locally at least.
2. Started some unit tests so that's good, and the Falcon tutorial has some examples of http client mocks which I'll put into the pytest as well. I think I get the module referencing now and should be able to use that going forward rather than the context.py approach, but we'll see how that goes as I do more stuff.
3. The project structure I was working on (the generic one) I'm not so sure about and I've backed-out a bunch of stuff.
4. Probably not surprising, the architecture is a bit of a mess as I have tried to combine the project structure with the falcon tutorial, so there may be some refactoring going in soon.
5. I'm using vim, but I don't think I've quite got the zen of vim just yet - I haven't achieved that nirvana of productivity (I still don't know how the cut/paste or yank and mark stuff works yet, and that's just the basics.  It highlights well enough for python, but I'm thinking that there's a load of scripts and plugins that I'm going to have to install to make it as productive as VScode.
