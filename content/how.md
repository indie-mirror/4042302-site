---
title: "How?"
date: 2018-01-05T21:01:29+01:00
draft: false
---

This site is a contrived example to demonstrate the 404 → 302 technique in action.

There are three ‘versions’ of this site, being served from three different subdomains:

1. [**www.**](https://4042302.org)4042302.org

    This site. The latest version that you’re viewing right now. It’s a static site, being served with nginx.

2. [**www.**](https://2017.4042302.org)4042302.org

    A fictitious previous version of the site. It is also a static site being served by different nginx server. (But it could easily have been a dynamic site being served by Node.js, for example.)

3. [**1997.**](https://1997.4042302.org)4042302.org

    The oldest ‘version’ of the site is [my Geocities site from 1997](https://1997.4042302.org) that I downloaded from  [The Internet Archive](https://archive.org) using [Wayback Machine Downloader](https://github.com/hartator/wayback-machine-downloader). It is also being served by nginx.

If a page is not found on the latest site, we issue a 302 request to the 2017 site. If it’s not found there either, we issue a 302 request to the 1997 site. If it’s still not found there, we show a 404 error.

So: [**www**](https://4042302.org) → [**2017**](https://2017.4042302.org) →  [**1997**](https://1997.4042302.org) → Show 404 error

## In detail

Here’s a more verbose explanation of the flow:

  1. If a URL is found on this site, it is rendered.

  2. If a URL is not found on this site, instead of a raising a 404 (not found) error, we issue a 302 (temporary redirect) to the earlier version of the site (2017.4042302.org). We use a 302 and not a 301 (permanent redirect) because we want the latest site to have the chance to override the URL in the future.

  3. If the URL is found on the earlier version of the site, it is displayed by that site.

  4. If the URL is not found on the earlier version of the site, that site also has a 404 → 302 mapping that forwards the request to The Internet Archive’s snapshot of my Geocities site (1997.4042302.org).

  5. If the URL is found on my Geocities site, it is displayed.

  6. If the URL is not found, the Geocities site displays its 404 page.

This is a contrived example but it should be enough to demonstrate how you can use this technique on your own web sites.

So this is my solution and I’m documenting it here because I feel that if enough of us adopted it, we could make this the de facto way to foster an evergreen Web.

**Next:** [Get started!](/get-started)
