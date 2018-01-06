# 404 → 302

A simple gesture for an evergreen Web.

```nginx
# nginx
location / {
error_page 404 =302 https://2017.4042302.org$request_uri;
try_files $uri $uri/ =404;
}
```

**What if links never died?** What if we never broke the Web? What if it didn’t involve any extra work?

It’s possible. And _easy_.

Just make your 404s into 302s.

**Interested?** Great! Learn more:

  * [Visit the 4042302 web site.](https://4042302.org)
  * Read: [Why?](https://4042302.org/why)
  * Read: [How?](https://4042302.org/how)

[Get involved](https://4042302.org/how#contribute) and help out.

---

**Canonical Git Remote:** https://source.ind.ie/indienet/4042302/site
