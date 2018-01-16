---
layout: post
title: Getting started with Flask
date: 2018-01-16
categories: programming python flask cyoa
---
## Choose your own Adventure Presentation
I'm going to follow along with this tutorial as I think it will be interesting - a [Choose Your Own Adventure Presentation](https://www.twilio.com/blog/2014/11/choose-your-own-adventure-presentations-with-reveal-js-python-and-websockets.html) - which allows  the audience to influence the direction that the presentation will take.  I think it's a good one because at the end there's an app of some interest, plus it will expose me to:

1. Flask (obviously)
2. WebSockets (with Flask-SocketIO)
3. Using redis, which seems like overkill here, but whatever
4. Using the twilio SMS api, athough I will probably use the Telstra SMS API later
5. Space for experimentation - eg using perhaps twitter for voting, plus swapping out other tools (such as click for FLask-Script, look to persist data into mongo or postgre via sqlachemy, and things like that.

Being about 3 years since the tutorial was written, I'm also going to upgrade (and then lock) to the latest versions of each of the libraries, so *requirements.txt* looks like this:
```
Flask==0.12.2
click==6.7
Flask-SocketIO==2.9.3
gunicorn==19.7.1
redis==2.10.6
twilio==6.10.0
```
We'll see if that causes any issues.

### First sign of trouble you choose for yourself
Well, that didn't take long. My second decision above (after the decision to move to latest releases) was to replace Flask-Script with click.  The reason I did that was that Flask-Script is no longer being maintatined and click was recommended.  So now I have to figure out how that works, because this tutorial is a bit of a Richard Feynmann tutorial - 'imagine I have 0 knowledge and infinite intelligence'.  So it doesn't actually explain much detail and expects you to fill in the gaps really fast. However I think this will help me learn - a bit like checkio helps you learn by throwing challenges at you. In this scenario, I basically have to figure out how to translate the Flask-Script code into click code, well I guess I like making a rod for my own back.

## First mc74.org content
If you look at the browser address bar, it should show this site is now [blog.mc74.org](blog.mc74.org) content. I haven't actually moved the site to wordpress like I was threatening, just got the domain repointed.  I'm trying out [DNSimple](dnsimple.com) as it's programmable via terraform, so it could be useful for various things.  Anyway at $5/month I can afford to see how it works for a little while.
