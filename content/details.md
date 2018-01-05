---
title: "Details"
date: 2018-01-05T21:01:29+01:00
draft: true
---

## Why?

My first web site was on Geocities.

Then Tripod.

Then it was a full Flash site that I coded from scratch.

Then it was b2.

Then it was Wordpress.

Now it’s my own hand-rolled static site generator in Node.js.

Soon, it’ll be my own Indienet site.

The Geocities site lives in on only in the Internet Achieve (thank you Brewster) as does the Tripod page. I’m glad they do (and yet, so embarrassing!) But the original links today are broken. I couldn’t do anything about that because, just like my Facebook or Twitter profile today, they were never mine. I was just renting them from those companies and, when they went away, they took that part of the Web with them.

Once I had my own domain (first aralbalkan.com and now ar.al), I was able to be more thoughtful.

I didn’t want to break the Web when I went from b2 to Wordpress. But that took some work. I had to write a b2 to Wordpress migrator.

Then, when I went from Wordpress to my own hand-rolled static site generator, I had to again write code to process my legacy content and make sure I maintained the URLs. That took some work. It wasn’t trivial.

(And, when I went from aralbalkan.com to ar.al, I had to keep a web server running at aralbalkan.com to forward the HTTPS calls to the new domain.)

Soon, my site will change completely as it becomes a personal federated site. So it’s going to go from a static web site to a Node.js application. I don’t want to break the Web but I also don’t want to burden this new system with a means to handle legacy static content. So what do I do?

## How?

So this is the solution I came up with:

1. Back up the current site to a subdomain (e.g., 2017.ar.al)
2. Make my 404s into 302s to the previous version of the site
3. If I change the site again in the future, rinse and repeat.

So this is my solution and I’m documenting it here because I feel that we could make this the de facto way to foster an evergreen Web.
