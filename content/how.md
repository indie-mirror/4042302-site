---
title: "How?"
date: 2018-01-05T21:01:29+01:00
draft: true
---

1. Back up your current site to a subdomain (e.g., 2017.your.site)
2. Add the 404 to 302 rule (see below)
3. If you change the site again in the future, rinse and repeat.

## nginx

```nginx
location / {
error_page 404 =302 https://2017.4042302.org$request_uri;
try_files $uri $uri/ =404;
}
```

## Other

If you‘d like to help, [get involved](/get-involved) and contribute rules for other servers and platforms.
