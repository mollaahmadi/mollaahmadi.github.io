---
layout: post
title: I-Had-A-Problem-With-Github-Pages
description:  I had a problem with github pages.

tags: Blog Github.io mollaahmadi
comments: false
permalink: I-Had-A-Problem-With-Github-Pages
sitemap:
  lastmod: 2020-03-18
---

I had the correct repository name and I still get a 404 error a solution is to push to the repository.
I pushed an empty commit and refresh the page. It worked.

```bash
git commit --allow-empty -m "Trigger rebuild"
git push
```
 
