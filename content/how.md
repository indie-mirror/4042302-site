---
title: "How?"
date: 2018-01-05T21:01:29+01:00
draft: true
---

1. Backup your current site to a subdomain (e.g., `2017.your.site`).

2. Add a 404 to 302 rule (see below) to your latest version.

3. If you change the site again in the future, rinse and repeat.

## nginx

In your site configuration (e.g., for a site that uses [Let’s Encrypt](https://letsencrypt.org) running on Ubuntu, in `/etc/nginx/sites-available/https.conf`):

```nginx
server {

  # …

  location / {
    error_page 404 =302 https://2017.your.site$request_uri;
    try_files $uri $uri/ =404;
  }
}
```

## Others

If you’d like to help, get involved and contribute by sending pull requests detailing how to implement 404 → 302 on other servers and platforms.
