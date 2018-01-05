---
title: "Why"
date: 2018-01-05T21:01:29+01:00
draft: true
---

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

Here’s the solution I came up with:

1. Back up the current site to a subdomain (e.g., 2017.ar.al)
2. Make my 404s into 302s that point to the previous version of the site
3. If I change the site again in the future, rinse and repeat.

I call it <strong>404 to 302</strong>.

## Example

This site is a contrived example of the 404 to 302 technique.

There are three ‘versions’ of this site:

  * <strong>A:</strong> <a href='https://4042302.org'>4042302.org</a> is the latest version that you’re reading now. It’s a static site, being served with nginx.

  * <strong>B:</strong> <a href='https://2017.4042302.org'><strong>2017.</strong>4042302.org</a> is a fictitious previous version of the site. It is also a static site being served by different nginx server. (But it could easily have been a dynamic site being served by Node.js, for example.)

  * <strong>C:</strong> The oldest version is <a href='https://web.archive.org/web/20030319083157/http://www.geocities.com:80/broadway/1085/'>my Geocities site from 1997</a>, and it is served by <a href='http://archive.org'>the Internet Archive</a>.

On A and B, I have added the following <strong>404 → 302</strong> mappings:

  * A (404) → B
  * B (404) → C

On C, if there’s a 404, the Internet Archive will show it’s 404 page and thus end the chain.

## In detail

Here’s a more verbose explanation of the flow:

  1. If a URL is found on this site, it is rendered.
  2. If a URL is not found on this site, instead of a raising a 404 (not found) error, it issues a 302 (temporary redirect) to the earlier version of the site (2017.4042302.org)
  3. If the URL is found on the earlier version of the site, it is displayed
  4. If the URL is not found on the earlier version of the site, that site also has a 404 → 302 mapping that maps the request to the Internet Archive’s snapshot of my Geocities site.
  5. If the URL is found on the Internet Archive, it is displayed.
  6. If the URL is not found on the Internet Archive, the Internet Archive displays its 404 page.

This is a contrived example but it should be enough to demonstrate how you can use this technique on your own web sites.

So this is my solution and I’m documenting it here because I feel that if we all adopted it, we could make this the de facto way to foster an evergreen Web.

Next: read about how to implement it for nginx servers and how you can get involved to contribute code for implementing on other servers (and even in serverless architectures).