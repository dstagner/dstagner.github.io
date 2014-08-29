---
layout: post
title: "An AHA! moment - Why am I even asking this?"
date: 2014-08-29 11:16:19 -0500
comments: true
categories: 
---
I started [Congruence](http://congruence.io) to scratch my own itch. After 20 years in the software industry, I had plenty of itches. But what pushed me from mere irritated grumbling to an actionable idea, the seed that would grow into a business? There were a bunch of "AHA!" moments. This is the story of one of them.

I pushed a build out to a test environment, and it failed. Hmm, what's wrong? After some digging in the logs, I found what looked to me like an app/schema mismatch. So I called up my friend the DBA to ask if the schema had changed, since I had neither the access nor the knowledge to determine that on my own. He said no, nothing had changed. 

**What he didn't know was that the other DBA in the cubicle next to his had made a change.**

So my hunch was right, but I was told it was wrong. I then spent hours trying to find *other* explanations for what broke - incorrect explanations, of course. So this begs the question - why didn't I have accurate data? The simple answer is "human error", but I think it's more complex than that. I actually see *two* questions here. The first question is, why didn't the DBA know for sure whether something had changed? The second question is, *Why should I even have to ask the DBA? Why can't I just look it up myself?*

So, why *did* I have to ask the DBA? I see two major reasons for that. First, I didn't have access to the server. This is a common pattern in software organizations. Developers are often locked out of complex infrastructure like databases, for both data security and practical operations reasons. If you give developers access to production databases, they have access to sensitive customer data - data that can cross HIPAA and PCI boundaries, as well as other regulatory issues. Better to not let them in at all than deal with the legal exposure. And developers, given access, will tend to "fix" things they shouldn't touch, heedless of downstream implications. So yeah, developers get locked out of resources, and it's usually a Good Thing. 

Second, even if I had access, would I be able to make heads or tails of it? I'm no Oracle expert. I can find my way around SQL pretty well, but pinning down whether or not *anything* changed in a schema with hundreds of tables? How would I do that? This, by the way, explains why the DBA gave me an incorrect answer as well. He didn't have a good point of comparison, either. If he didn't know about a change, he had no good way of tracing it. 

The stock answer for this sort of thing, from the DevOps and traditional configuration management communities, is to just automate the crap out of everything. But frankly, that's a boil-the-ocean strategy in large corporations. It's not like I had the authority to order them to do that! And would I have access to their source code, or deployment logs? So a world where changes are done manually, by many different teams, is just plain reality for most software organizations. 

So what's my answer? With [Congruence](http://congruence.io), it means just automatically detecting that *something* changed in the database, and putting notification for that change in a common system, alongside changes in the app servers, unix filesystems, firewalls, enterprise service busses, and all the other gazillion moving parts that make up a large modern application. Make it a drill-down so I can see not only that there was a change in configuration, but *what* changed. Index altered? Table dropped? Let's find out! With capability like this, I don't need to ask a DBA - I can just look it up. And I don't have to have access to the database, or understand how to use the tools to drill into it. Knowing what changed where is enough to get me started on solving the problem, by bringing in the people who do have the right access and knowledge. 

And isn't that easier? Isn't that smarter? 
