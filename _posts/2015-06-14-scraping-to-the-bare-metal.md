---
layout: post
title: Scraping to the bare metal
comments: true
---

My sadly neglected blog needs restarting. However, I first need to figure out how it all works again, and fix stuff.

<!-- more -->

The blog was moved from Wordpress to Jekyll long ago, because I'm that kind of nerd. But Jekyll needs work, and my web design skills are suboptimal. So I messed with jekyll-bootstrap, but didn't like that too much. Then I moved to Octopress, which is supposed to make everything easier, but just makes it more complicated.

Coming back, I decided to just strip it down to the bare metal and build it back up from scratch. So I scorched the Earth, started a raw jekyll blog, copied over my old posts, and started fixing things...

So, uh, how was this deployed anyway? I seem to remember I had the file on Amazon S3, distributed by Cloudfront. Oh yeah, there was this publish.sh script that put the files on S3. Cloudfront is complaining? Hmm, maybe it's not the right S3 location. Is it that other one? No, that's not it. Oh yeah, the script was written for Octopress, and this is plain Jekyll. Ah, okay. Now it's deploying. But Cloudfront is still complaining. Oh, there isn't a Cloudfront config anymore. What does DNS say? Oh, DNS is pointed directly at S3. This is stupid anyway. I should change that shell script to a rake task... 

I want Disqus comments back. How did that work in the old setup? Oh, this is complicated, lots of indirection. Well, I'll set up an include. That's not working, hmmm. Let's just include directly from the post layout. Ok, that works for now. Kinda ugly, though. Maybe I'll add some indirection later... 

Oh, pagination? How does that work again? Let's actually read some documentation. Ok, paste that example. Hmm, doesn't work. Oh, this isn't site.posts, it's pagination.posts. Fixed. Next? 

Oh yeah, that huge backlog of content! You have a lot of ideas to write, Dave. 

I should probably get Google Analytics working too...