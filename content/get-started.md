---
title: "Get Started!"
date: 2018-01-05T21:01:29+01:00
draft: false
---

1. Serve your current site from a subdomain (e.g., `2017.your.site`).

2. Add the 404 to 302 rule for your server (see below) to the latest version of your site to forward links that are not found on the latest version to the previous version.

3. If you change the site again in the future, rinse and repeat.

## nginx

In your site configuration:

```nginx
server {
  # …
  location / {
    error_page 404 =302 https://2017.your.site$request_uri;
    try_files $uri $uri/ =404;
  }
}
```

For example, if your site uses [Let’s Encrypt](https://letsencrypt.org) on Ubuntu, you should find your site configuration file in `/etc/nginx/sites-available/https.conf`.

## WordPress
 [Fabrica Evergreen Web](https://github.com/yeswework/fabrica-evergreen-web) is a tiny plugin which allows you to use 404 → 302 on WordPress sites. After installation and activation, you specify the fallback path in a settings screen.

## Contribute

[Edit this page on GitHub](https://github.com/indie-mirror/4042302-site/blob/master/content/get-started.md) to contribute 404 → 302 configurations for your favourite servers and platforms and send us a pull request.
