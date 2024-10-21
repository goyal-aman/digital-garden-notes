---
title: "Welcome to My Blog"
description: "A brief introduction and recent posts."
layout: home # This tells Hugo to use the 'home' layout.
---

## Welcome to My Blog!
Hi, I'm [Your Name], and this is where I share my thoughts on various topics. Below, you'll find some of my recent posts.

## Recent Posts
{{ range first 5 ( where .Site.RegularPages "Type" "post" ) }}
- [{{ .Title }}]({{ .Permalink }})
  {{ .Summary }}
{{ end }}

