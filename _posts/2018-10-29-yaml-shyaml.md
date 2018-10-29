---
layout: post
status: publish
published: true
title: YAML shyaml - Wrote a tool about it, here it goes
author: clint
categories:
    - Rust
tags:
    - rust
    - yaml
    - kubernetes
---
I'll keep this brief and on point: [I love
Rust](https://fewbar.com/2017/01/a-love-letter-to-rust/) and yet, I have
published so little [rust code](https://github.com/SpamapS/rustygear), and as
yet, none that actually saw real usage.

Well today that changes. With many thanks to my former employer,
[GoDaddy](https://www.godaddy.com/), for assigning copyright of a work product
to me, I am pleased to announce the publishing of
[shyaml](https://crates.io/crates/shyaml).

When I joined GoDaddy, among other duties, I was tasked with keeping their
"Legacy" Kubernetes installation alive and running. The team that had built it
were all gone, and I was fairly new to Kubernetes, so I had to tread lightly.

As a result, I found myself constantly wishing I could see what `kubectl` was
about to do. I was shocked that `kubectl` didn't have a diff mode. In
retrospect, I probably should have just learned Go, and added a --diff switch
to `kubectl`. But, I fell back on the tool I know, and I had just written
`shyaml` to get my rust chops up. It was just a general CLI manipulation tool
for YAML and JSON at the time. Adding the ability to intelligently diff
Kubernetes objects was pretty straight forward.

So I added a `kubediff` command, which tries to show you the real effect a
`kubectl apply` command will have before you run it. It's not perfect, but
it generally works.

And so, I give this tool to the world. I hope to make it even more general
purpose, as time permits. But until then, please enjoy the code, and feel free
to report issues and open PR's. Also, join us on the [Tools for Humans
Slack](https://toolsforhumans.slack.com) if you want to chat about it.
