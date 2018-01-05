---
layout: post
title: Web services with Falcon
date: 2018-01-06
categories: programming python wsgi falcon
---
# Let's start getting practical today.
Last night I finally got jekyll & github pages working - as should be clear given this is post.  It was both more convoluted and simpler - a modern paradox.  Themes aren't working yet, but that can be for another time.
## Today's agenda
As the first order of business, I'm going to get a Falcon WSGI microservice built from scratch. It will be a bit of a hello-world microservice, but the aim will be to give it a bit of longevity and start implementing those software engineering disciplines like testing, some speccing and design work.  I'll build out the spec and document it here as I go, but the high-order goals are to:
1. Make it real.  It will be a 'Status' service that will in the future be able to provide information about the status of other services operating.  Initially, it will only report on itself (obviously).
2. Apply RESTful API service design in alignment with best practices. I intend to use Swagger to help drive some consistency and ideally documentation automation for this process.
3. Start implementing a CI pipeline for the development.
4. Deploy an initial version to the cloud (probably AWS) based on CI execution.

### Service Features
Initial iteration will have the following features:
1. Get list of services
2. Get current status of selected service
Roadmap items for consideration include:
3. Get historical service status data for a date/time range

I've chosen Falcon for now as the WSGI server, mainly because it's lean and I liked it's tagline "Unburdening APIs for over 5.00 x 10-2 centuries."  I was also considering Morepath, but that's probably a bit too niche to skill up in.  Flask would be an obvious candidate to fall back to if Falcon proves to be a problem.

**So let's go**
