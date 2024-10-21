---
title: "Welcome to My Blog"
description: "A brief introduction and recent documents."
layout: home # This tells Hugo to use the 'home' layout.
---

## Welcome to My Blog!
Hi, I'm [Your Name], and this is where I share my thoughts on various topics. Below, you'll find some of my recent documents.

## Recent Documents
{{ range first 5 ( where .Site.RegularPages "Type" "docs" ) }}
- [{{ .Title }}]({{ .Permalink }})
  {{ .Summary }}
{{ end }}

