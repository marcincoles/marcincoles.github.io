---
layout: post
title: IT troubles and fun times
date: 2018-01-14
categories: programming terraform aws linux
---
### IT Troubles and Fun Times

#### The Trouble

The last week's been a bit traumatic in the IT sense.  Having run Ubuntu 16.04 in a VM on my Windows machine for a couple of weeks, I decided it was time to give it it's own partition.  So I resixed the Windows partition (even though chkdsk warned me about issues) and lo and behold Windows won't boot. Luckily I've got Linux going now on bare metal which is nice, and I was able to mount the NTFS partition read only and get all my data off.  Oh yeah, backups, important!

Because I couldn't initially access the Windows partition, I couldn't get at the settings I'd done on the VM-installed linux, so had to configure it all from scratch again, but I'm getting there. I've got i3wm set up pretty well, just have a slight issue with getting the laptop to suspend on lid down, and it goes a bit funny when I add/remove the monitor. And Spotify doesn't work which is annoying.

![DesktopImage](/assets/i3wm-shot.png)

All in all it's forced me to get more into Linux which I think has been a good thing.

#### The fun times

I've taken a little bit of a diversion since I couldn't really code until I got everything set up again, and I've made a few changes and tried out some new things.

1. I've been playing around with [Terraform](www.terraform.io) and AWS have so far been able to get it to deploy a server and ELB into AWS.  I'm going through [The Terraform Book](www.terraformbook.com) which seems to be a good introductory, hands-on guide.  I'm keen to drive a proper CI/CD pipeline as part of what I'm doing, and Terraform looks like a great tool for that.
2. Related to this, I've decided to move my repos to [GitLab](www.gitlab.com).  The related reason is that I wanted some private repos for the terraform scripts (and GitLab's free account has that), and also they've got some other things that are worth trying including an issues board, which I'm using as my task list.  Plus it's worth trying something new, and so far it seems to be ok.
3. I've decided to change direction and go with Flask for the web framework. I don't think there's anything inherently wrong with Falcon but Flask seems to have a lot more mindshare out there and a lot of libraries and plugins that just aren't there for Falcon (SocketIO is one).
4. And I've got myself a new domain - mc74.org - which I'll use for hosting whatever projects I make, and a little summery logo.

<img src="/assets/MC74orgLOGOB3.png" alt="Drawing" style="width: 200px; height: 200px"/>

Over time I'm going to take down this site and probably just host a wordpress on AWS or Digital Ocean. I'm not really loving the github pages experience that much.
