---
layout: post
title:  "Website Backends"
date:   2024-06-22 22:52:10 +0200
categories: code backend programming languages
---
## So many new programming languages
There are so many new and improved general purpose programming languages lately.  [LLVM](https://llvm.org/) probably has something to do with that.  Anyway, C and C++ are the defacto standard languages for embedded and performance critical applications, including games, web development, etc. But what about Rust, Go, Zig?  I might check out Gleam, Odin, Roc, ... later too. They all look so incredibly promising.

## The start
To learn a new programming language, they say you should build a go-to project. Something you're familiar with. But also, something which fits in the language's capabilities.  I've been wanting to build a portfolio site for a very long time, just never had a reason or the will to get at it.
Playing around with [htmx](https://htmx.org/) at my current professional project, [a backend](https://flexworks.eu) seemed like a good fit.  

## The environment
Anything frontend is htmx.  Static content is fetched by the backend from a static location on an openresty server, which I already wanted to use as reverse proxy (ssl offloading, cache, etc). Static components like js, css and images are served directly from a /static endpoint on the reverse proxy.

The frontend is all htmx and bootstrap.  This is not a performance benchmark (per se), so the focus is on using whatever is popular and convenient.  The projects will run on rasperry pi 4B, a pi zero 2w and even a pi zero 1.1 w (32bit). All dockerized.  Development is on a macbook air M1 13", an HP 840 G3 i5-u6300u elitebook and an HP Proliant ML110 G6 Xeon X3440.  Apart from the mac, the rest is pretty old and resourcilly challenged. Perfect for these programming languages.  I can already guess that compile times will hurt, but looking forward to runtime performance.

[![sequence diagram](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)

## The contestants



| Language | Web Server | Templating Engine |
| -------- | ---------- | ----------------- |
| [Go](https://go.dev/) | [Chi](https://go-chi.io/#/) | [Templ](https://templ.guide/) |
| [Python](https://www.python.org/) | [FastAPI](https://fastapi.tiangolo.com/)/[Uvicorn](https://www.uvicorn.org/) | [Jinja2](https://jinja.palletsprojects.com/) |
| [C#](https://learn.microsoft.com/dotnet/csharp/) | [.NETCore8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | [Razor Pages](https://learn.microsoft.com/aspnet/core/razor-pages/) |
| [Rust](https://www.rust-lang.org/) | [Axum](https://github.com/tokio-rs/axum) | [Askama](https://github.com/djc/askama) |
| [Zig](https://ziglang.org/) | [Zap](https://github.com/Snektron/zigzap) | [Mustache](https://mustache.github.io/) |

