---
layout: post
title: "Find and xargs - a match made in heaven"
date: 2014-09-08 13:01:48 -0500
comments: true
categories: [software]
published: true
---
Searching a Unix/Linux directory structure recursively can be baffling and inefficient for newbies. Here's a Unix/Linux shell programming pattern I've used for a rather long time to solve that problem... 

`find ${PATH} -type f | xargs grep ${PATTERN} 2>/dev/null`

### Anatomy of a hack ###
The first part of this is the `find` command. The first argument to find is always the directory path you want to search. The `-type f` modifier limits the results to files and filters out directories - no point in grepping them, right? The find command is a rich and powerful thing with a complex interface. Read up on the man page to learn things you can do with it, but be sure to experiment to make sure they work - find's behavior varies considerably from platform to platform. 

The second part is `xargs grep`. First, xargs. This command is a wonder of shell programming. It just takes a series of lines and concatenates them into a single line, and appends them to whatever command comes next. So it turns all the files listed by find into arguments for grep, which will process them all as inputs. So in this case, a single grep command can process as many files as you like, an entire directory heirarchy. The ${PATTERN} argument to grep is whatever string it is you're searching for. Like find, grep is very powerful, complex, and somewhat implementation-dependent. If you use regular expressions in your search pattern, be sure to escape them properly. 

### Why not just use -exec? ###
One of the many features of the find command is the -exec option, which executes a command on each file found. The problem with -exec is twofold. First, it's complex and implementation-dependent and needs everything escaped properly. Second, it forks a process for every file the find command returns. If you're searching thousands of files, this is very inefficient. 

I first developed this hack to improve performance on greps of large (10k+ files) directory structures back in the 1990s, when computers were made from stone knives and bearskins. The `find -exec` pattern could take hours to search. The `find | xargs grep` pattern was two orders of magnitude faster, giving results for complex regular expressions in less than a minute. It's also much simpler and more reliable when shifting from platform to platform. At that job, I was supporting pretty much every Unix platform available in the late 1990s, which was rather a lot of them. Open source wasn't widely used, and "simple" programs like grep were often farmed out to junior programmers, with results as bad as you might expect (Oh, HP-UX 9, it'd be nice if I could grep lines longer than 255 characters...). 

Patterns like this make you appreciate the beauty and power of the Unix model. Try it! 
