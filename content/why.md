---
title: "Why?"
date: 2018-01-05T21:01:29+01:00
draft: false
---

[My first web site](https://1997.4042302.org) was hosted on [Geocities](https://en.wikipedia.org/wiki/Yahoo!_GeoCities).

Then [Tripod](https://web.archive.org/web/20040811232124/http://aral.tripod.com:80/).

Then it was a full Flash site that I coded from scratch.

Then it used [b2](https://web.archive.org/web/20020118200519/http://cafelog.com:80/).

Then it used [Wordpress](https://www.wordpress.org).

Now it’s [my own hand-rolled static site generator in Node.js](https://source.ind.ie/aral/blog).

Soon, it’ll be my own [Indienet](https://source.ind.ie/indienet) site.

The Geocities site lives on only thanks to the [Internet Achieve](http://archive.org) (thanks [Brewster](http://brewster.kahle.org)) as does the Tripod page. I’m glad they’re still there (so embarrassing, but we all had to start somewhere!) But the original URLs today are broken. I couldn’t do anything about that because, just like my Facebook or Twitter profile today, they were never mine. I was just renting them from those companies and, when they went away, they took that part of the Web with them. My own site (and [my Mastodon](https://mastodon.ar.al)), on the other hand, are mine and, among other things, I get to decide if they live or die.

Once I had my own domain, I was able to be more thoughtful.

I didn’t want to break the Web when I went from b2 to Wordpress. But that took some work. I had to write [a b2 to Wordpress migration script](https://ar.al/588/).

Then, when I went from Wordpress to my own hand-rolled static site generator, I had to again write code to process [my legacy content](https://ar.al/archive/) and make sure I maintained the URLs. That took some work also. It wasn’t trivial.

(And, when I changed my domain from [aralbalkan.com](https://aralbalkan.com) to [ar.al](https://ar.al), I had to keep a web server running at aralbalkan.com to forward the HTTPS calls to the new domain.)

Soon, my personal site will change completely as it becomes a federated personal site. So it’s going to go from a static web site to a Node.js application. I don’t want to break the Web but I also don’t want to burden the new system I’m building with a means to handle legacy static content. And yet, this is also an important use case that I cannot ignore.

So what’s a developer to do?

Here’s the simplest solution I could come up with:

1. Serve the current site from a subdomain (e.g., `2017.ar.al`)

2. Make my 404s into 302s that point to the previous version of the site.

3. If I change the site again in the future, rinse and repeat.

I call the technique <strong>404 to 302</strong>.

**Next:** [How does it work?](/how)
