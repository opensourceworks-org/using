---
layout: post
title:  "Website Backends"
date:   2024-09-22 20:52:10 +0200
categories: code backend programming languages
---
## So many new languages
There's much ado about programming languages lately.  [LLVM](https://llvm.org/) has probably something to do with that.  Anyway, C and C++ are the defacto standard languages for embedded and performance critical applications. But what about Rust, Go, Zig?  I might check out Gleam, Odin, Roc, ... later too. They all look so incredibly promising.

## The start
To learn a new programming language, they say you should build a go-to project. Something you're familiar with. But also, something which fits in the language's capabilities.  I've been wanting to build a portfolio site for a very long time, just never had a reason or the will to get at it.

Playing around with htmx at my current professional project, a backend seemed like a good fit.  Anything frontend is htmx.  Static content is fetched by the backend from a static location on an openresty server, which I already wanted to use as reverse proxy (ssl offloading, cache, etc). Static components like js, css and images are served directly from a /static endpoint on the reverse proxy.

[![sequence diagram](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)

## The contestants

As stated earlier, the frontend is all htmx and bootstrap.  This is not a performance benchmark (per se), so the focus is on using what's popular and convenient.



| language | web server | templating engine |
| -------- | ---------- | ----------------- |
| Go | Chi | Templ |
| Python | Fastapi | jinja2 |
| C# | dotnet8 | Razor |
| Rust | Axum | Askama |
| Zig | Zap | Mustache |


## Findings

### GO

### Python

### C#

### Rust

### Zig

## Conclusion

