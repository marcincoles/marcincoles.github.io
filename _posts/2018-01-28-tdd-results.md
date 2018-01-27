---
layout: post
date: 2018-01-28
title: TDD Results
categories: TDD programming python
---

Nice to get a little win here and there.  I've been working with the TDD approach of writing tests before writing code, and it's actually been quite useful.  I've even got to the point of having to refactor tests when the implementation was unworkable.  My approach is probably still not 'TDD canon' as I do put a few tests into each test case, but I don't know, it makes sense to assert validity of all steps up to and including the one you're interested in.  I still find it useful to design on paper first, then write the tests, then code.  Designing purely through the tests I'm not quite sure about yet.

```bash
$ pytest -x
========================================= test session starts ==========================================
platform linux -- Python 3.5.2, pytest-3.3.2, py-1.5.2, pluggy-0.6.0
rootdir: /home/marcin/dev/icfp2017/marcin, inifile:
collected 15 items                                                                                     

tests/test_graph.py ........                                                                     [ 53%]
tests/test_mapper.py .......                                                                     [100%]

====================================== 15 passed in 0.05 seconds =======================================
```

I'm assuming the [53%] is test coverage, so I'll need to look at that...
