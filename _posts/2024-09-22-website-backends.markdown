---
layout: post
title:  "Website Backends"
date:   2024-09-22 20:52:10 +0200
categories: code backend programming languages
---
## So many new general purpose programming languages
There's much ado about programming languages lately.  [LLVM](https://llvm.org/) has probably something to do with that.  Anyway, C and C++ are the defacto standard languages for embedded and performance critical applications. But what about Rust, Go, Zig?  I might check out Gleam, Odin, Roc, ... later too. They all look so incredibly promising.

## The start
To learn a new programming language, they say you should build a go-to project. Something you're familiar with. But also, something which fits in the language's capabilities.  I've been wanting to build a portfolio site for a very long time, just never had a reason or the will to get at it.
Playing around with htmx at my current professional project, a backend seemed like a good fit.  

## The environment
Anything frontend is htmx.  Static content is fetched by the backend from a static location on an openresty server, which I already wanted to use as reverse proxy (ssl offloading, cache, etc). Static components like js, css and images are served directly from a /static endpoint on the reverse proxy.

The frontend is all htmx and bootstrap.  This is not a performance benchmark (per se), so the focus is on using whatever is popular and convenient.  The projects will run on rasperry pi 4B, a pi zero 2w and even a pi zero 1.1 w (32bit). All dockerized.  Development is on a macbook air M1 13", an HP 840 G3 i5-u6300u elitebook and an HP Proliant ML110 G6 Xeon X3440.  

[![sequence diagram](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)

## The contestants

| language | web server | templating engine |
| -------- | ---------- | ----------------- |
| Go | Chi | Templ |
| Python | Fastapi | jinja2 |
| C# | dotnet8 | Razor |
| Rust | Axum | Askama |
| Zig | Zap | Mustache |


## Findings

If I had to choose one for everything I'd ever do it would be any of these.

- language syntax, compiling, reload 
- webserver
- templates
- runtime

| language | Webserver | Templating Engine |
| -------- | --------- | ----------------- |
| __Go__ is a great language for pretty much anything, and even more and more so for data processing.  Compiles incredibly fast.  The only language that did not struggle with my older hardware. | __Chi__ is simple to use, plenty fast. Used Air for hot reloading.  Great experience. | __Templ__ is the templating engine I struggled with the most.  Cool how it compiles the templates in, but syntax is sometimes a bit verbose |
| __Python__ is by far the slowest at runtime and the only interpreted language used here. Deployment is annoying with having to set up a python environment first.  Used Rye instead of poetry which made that experience a lot faster though. | __Fastapi/Uvicorn__ is excellent, especially with Pydantic integration. Batteries included. | I have been using __jinja2__ templates for a while with django, ansible, flask and also fastapi.  It's pretty much my reference for the other templating engines. |
| __C#__ worked out better than I initially thought. `public static void Main(String[] args)` aside, it's a mature language with great documentation and community. DotNET8 allows for statically compiled "single binary.  | Built-in.  Maybe should have used Go's standard lib http server too. No complaints. | Razor pages are nice, but it's an all or nothing kind of deal, no partials.  I mixed built-in routing and __RazorPages__. There's a [RazorSlices](https://github.com/DamianEdwards/RazorSlices), although for the few times I needed partials, I just replaced placeholder tags. |
| __Rust__ is a handful. Always. Every single line needs to pass the borrow checker.  Makes for better code, but you need to get passed the frustrations first.  Compilation is really slow. Just like with Python, you drag in a lot of dependencies. But when you run it, WOW! | __Axum__ is cool, has all you need. | __Askama__ templates are much like jinja2. Good stuff. |
| __Zig__ is a great language. Really love it. Also the way it interops with C. The language is very immature and the documentation, if there is any, is already superseded and obsolete. The community is very active and supportive. Struggled with a memory leak, but once I wrapped the General Purpose Allocator in the Arena allocator, I was able to pinpoint the culprit with the gpa's memory leak detection. | __Zap__ is a Zig wrapper around facil.io, a C library.  It's great, has everything I needed. I should check out [httpz](https://github.com/karlseguin/http.zig) and [jetzig](https://www.jetzig.dev/)| __Mustache__ comes with facil.io.  Not the best syntax, but supports includes, partials etc. Pretty straight forward.|


### GO

### Python

### C#

### Rust

### Zig

## Conclusion

