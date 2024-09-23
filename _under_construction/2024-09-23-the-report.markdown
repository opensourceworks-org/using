---
layout: post
title:  "The Report"
date:   2024-09-23 08:52:10 +0200
categories: code backend programming languages
---

## First
1. [Website Backends]({{ site.baseurl }}/code/backend/programming/languages/2024/06/22/website-backends.html)
2. [Pull the Plug]({{ site.baseurl }}/code/backend/programming/languages/2024/09/22/pulling-the-plug.html)

## TLDR;


| Language | Webserver | Templating Engine |
| -------- | --------- | ----------------- |
| __Go__ is a great language for pretty much anything, and even more and more so for data processing.  Compiles incredibly fast.  The only language that did not struggle with my older hardware. | __Chi__ is simple to use, plenty fast. Used Air for hot reloading.  Great experience. | __Templ__ is the templating engine I struggled with the most.  Cool how it compiles the templates in, but syntax is sometimes a bit verbose |
| __Python__ is by far the slowest at runtime and the only interpreted language used here. Deployment is annoying with having to set up a python environment first.  Used [Rye](https://rye.astral.sh/) instead of [Poetry](https://python-poetry.org/) which made that experience a lot faster though. | __Fastapi/Uvicorn__ is excellent, especially with Pydantic integration. Batteries included. | I have been using __jinja2__ templates for a while with django, ansible, flask and also fastapi.  It's pretty much my reference for the other templating engines. |
| __C#__ worked out better than I initially thought. `public static void Main(String[] args)` aside, it's a mature language with great documentation and community. DotNET8 allows for statically compiled single binary, including the [.NET runtime](https://learn.microsoft.com/en-us/dotnet/standard/clr). That CLR gets extracted to a temp location when executing the binary.  | Built-in.  Made me reconsider Go with Chi and should have gone with the standard lib http server too. No complaints. | Razor pages are nice, but it's an all or nothing kind of deal, no partials.  I mixed built-in routing and __RazorPages__. There's a [RazorSlices](https://github.com/DamianEdwards/RazorSlices), although for the few times I needed partials, I just replaced placeholder tags. |
| __Rust__ is a handful. Always. Every single line needs to pass the borrow checker.  Makes for better code, but you need to get passed the frustrations first.  Compilation is really slow. Just like with Python, you drag in a lot of dependencies. But when you run it, WOW! | __Axum__ is cool, has all you need. | __Askama__ templates are much like jinja2. Good stuff. |
| __Zig__ is a great language. Really love it. Also the way it interops with C. The language is very immature and the documentation, if there is any, is already superseded and obsolete. The community is very active and supportive. Struggled with a memory leak, but once I wrapped the General Purpose Allocator in the Arena allocator, I was able to pinpoint the culprit with the gpa's memory leak detection. | __Zap__ is a Zig wrapper around facil.io, a C library.  It's great, has everything I needed. Because of [this](https://github.com/zigzap/zap/pull/132#issue-2538805273), I should check out [httpz](https://github.com/karlseguin/http.zig) and [jetzig](https://www.jetzig.dev/) instead.| __Mustache__ comes with facil.io.  Not the best syntax, but supports includes, partials etc. Pretty straight forward.|


### GO

#### pros
#### cons
#### overall

### Python
#### pros
#### cons
#### overall

### C#
#### pros
#### cons
#### overall

### Rust
#### pros
#### cons
#### overall

### Zig
#### pros
#### cons
#### overall

## Conclusion


