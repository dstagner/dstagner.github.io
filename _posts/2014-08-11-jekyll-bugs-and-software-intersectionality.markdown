---
layout: post
title: "Jekyll bugs and software intersectionality"
date: 2014-08-11 13:09:06 -0500
comments: true
categories: [bugs, jekyll]
---
Bugs don't just happen inside software. They happen *between* software, in the intersections between components. And I wind up writing a [gist](https://gist.github.com/dstagner/8d75dd16d43c35360f5e) to describe a fix rather than a pull request to actually fix it. In the process, I start applying feminist theory to software engineering... 

<!-- more -->

This weekend (August 2014), I rebuilt this blog using [Octopress](http://octopress.org/) with the beautiful [MediumFox](https://github.com/sevenadrian/MediumFox) theme. Unfortunately, pagination didn't work, so the front page wasn't populating with posts as it should. But it was working on the MediumFox demo/example, so I did some digging, and eventually found the bug was in the names of configuration variables (the gist explains the detail). But the bug doesn't mean the theme is buggy, or that Octopress is buggy... it means they don't play nicely together. 

I suppose I could be oversimplifying, and one of them actually *is* buggy and could stand a patch. But I'm not digging down that far. The gist at least gives people in my situation something to google for. Maybe I'll poke at it more later. 

The word ["intersectionality"](http://en.wikipedia.org/wiki/Intersectionality) is complex and politically charged. It's actually from feminist theory, and talks about how different kinds of discrimination interact and reinforce each other. For example, the experience of being a black woman is the experience of being black, and of being a woman, but also the unique experience of being both, with its own unique problems. I really like the concept of intersectionality in social theory, and I think it can be adapted to software architecture as well. There are problems in software that happen when different kinds of systems are combined, problems that are unique to the combination. For example, [ORM](http://en.wikipedia.org/wiki/Object-relational_mapping) problems aren't because of object-oriented programming, or because of relational databases, but rather because these two somewhat incompatible mindsets are often used together in the same project. 

But how do I talk about software intersectionality without a dangerous tendency to politicizing the discussion and the inevitable Godwin's Law violations? Hmmm. 
