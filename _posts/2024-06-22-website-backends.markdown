---
layout: post
title:  "Website Backends, The Start"
date:   2024-06-22 22:52:10 +0200
categories: code backend programming languages
---
## So many new programming languages
There are so many new and improved general purpose programming languages lately.  [LLVM](https://llvm.org/) probably has something to do with that.  Anyway, C and C++ are the defacto standard languages for embedded and performance critical applications, including games, web development, etc. But what about Rust, Go, Zig?  I might check out Gleam, Odin, Roc, ... later too. They all look so incredibly promising.

## Why
To learn a new programming language, they say you should build a go-to project. Something you're familiar with. But also, something which fits in the language's capabilities.  I've been wanting to build a portfolio site for a very long time, just never had a reason or the will to get at it.
Playing around with [htmx](https://htmx.org/) at my current professional project, [a backend](https://flexworks.eu) seemed like a good fit.  

## Setup
Anything frontend is htmx.  I started a similar exercise for the frontend using Angular, React and Next.JS. My backend endpoints return either html for htmx (based on an htmx header) or json.  The common content is fetched by the backend from an internal-only static location on an openresty server, which I already wanted to use as reverse proxy (ssl offloading, cache, etc). Static components like js, css and images are served directly from a /static endpoint on the reverse proxy.  

### requests
So for example, the backend renders a container div for the content box. All content tabs need to be fetched from the internal-only common shared endpoint on the openresty reverse proxy, using an htmx on-load trigger.  The html received may have htmx on-load triggers as well.  Html is common, the templates are not.

```html
    <table class="table table-striped table-hover">
        <tbody>
            <tr>
                <th>os</th>
                <td hx-get="/sysinfo/os"
                    hx-trigger="load"
                    hx-indicator="#stats-os-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-os-spinner" class="htmx-indicator"></div>
            </td>
            </tr>
            <tr>
                <th>architecture</th>
                <td hx-get="/sysinfo/arch"
                    hx-trigger="load"
                    hx-indicator="#stats-arc-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-arc-spinner" class="htmx-indicator">
                </td>
            </tr>
            <tr>
                <th>cpu model</th>
                <td hx-get="/sysinfo/cpu_model"
                    hx-trigger="load"
                    hx-indicator="#stats-model-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-model-spinner" class="htmx-indicator"></div>
                </td>
            </tr>

            <tr>
                <th>cpu count</th>
                <td hx-get="/sysinfo/cpu_count"
                    hx-trigger="load"
                    hx-indicator="#stats-count-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-count-spinner" class="htmx-indicator"></div>
            </td>
            </tr>
            <tr>
                <th>total memory</th>
                <td hx-get="/sysinfo/total_memory"
                    hx-trigger="load"
                    hx-indicator="#stats-total-memory-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-total-memory-spinner" class="htmx-indicator"></div>
                </td>
            </tr>
            <tr>
                <th>memory used by this</th>
                <td hx-get="/sysinfo/memory_used"
                    hx-trigger="load"
                    hx-indicator="#stats-memory-used-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="stats-memory-used-spinner" class="htmx-indicator"></div>
                </td>
            </tr>
            <tr>
                <th id="programming-language" >programming_language</th>
                <td hx-get="/implementation/programming_language"
                    hx-trigger="load"
                    hx-indicator="#programming-language-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="programming-language-spinner" class="htmx-indicator"></div>
                </td>
            </tr>
            <tr>
                <th id="web-server" >*web-server*</th>
                <td hx-get="/implementation/web_server"
                    hx-trigger="load"
                    hx-indicator="#web-server-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="web-server-spinner" class="htmx-indicator"></div>
            	</td>
            </tr>
            <tr>
                <th id="templating-engine" >*templating-engine*</th>
                <td hx-get="/implementation/templating_engine"
                    hx-trigger="load"
                    hx-indicator="#templating-engine-spinner"
                >
                    <div class="spinner-border text-warning" role="status" id="templating-engine-spinner" class="htmx-indicator"></div>
                </td>
            </tr>

        </tbody>
    </table>
```

response: html vs json
```bash
$ curl http://localhost:3001/sysinfo/os -s -H "Hx-Request: true"
Darwin%
$ curl http://localhost:3001/sysinfo/os -s | jq
{
  "os": "Darwin"
}
$
```

### complete flow
[![sequence diagram](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)](https://flexworks.eu/static/img/flexworks.eu.sequence.diagram.amber.svg)

### hardware

This is not a performance benchmark (per se), so the focus is on using whatever is popular and convenient.  The projects will run on rasperry pi 4B, a pi zero 2w and even a pi zero 1.1 w (32bit). All dockerized.  Development is on a macbook air M1 13", an HP 840 G3 i5-u6300u elitebook and an HP Proliant ML110 G6 Xeon X3440.  Apart from the mac, the rest is pretty old and resource constrained. Perfect for these programming languages.  I can already guess that compile times will hurt, but I am looking forward to runtime performance.


## The contestants


| Language | Web Server | Templating Engine |
| -------- | ---------- | ----------------- |
| [Go](https://go.dev/) | [Chi](https://go-chi.io/#/) | [Templ](https://templ.guide/) |
| [Python](https://www.python.org/) | [FastAPI](https://fastapi.tiangolo.com/)/[Uvicorn](https://www.uvicorn.org/) | [Jinja2](https://jinja.palletsprojects.com/) |
| [C#](https://learn.microsoft.com/dotnet/csharp/) | [.NETCore8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | [Razor Pages](https://learn.microsoft.com/aspnet/core/razor-pages/) |
| [Rust](https://www.rust-lang.org/) | [Axum](https://github.com/tokio-rs/axum) | [Askama](https://github.com/djc/askama) |
| [Zig](https://ziglang.org/) | [Zap](https://github.com/zigzap/zap) | [Mustache](https://mustache.github.io/) |

