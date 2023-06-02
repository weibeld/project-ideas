---
id: 0oqeorwcqaiwxu1ytic695m
title: Facts Management Tool
desc: ''
updated: 1679088124105
created: 1679082295322
tags: todo
---

> TODO: evaulate whether this is is still necessary or whether it can be done in the Desk-Drawer-Shelf note system, for example, as simple notes in the Heap, or as a separate type in the Shelf compartment.

A tool that allows to quickly note down and retrieve learned facts.

## Problem

Often simple facts that are learened during research are forgotten because they are not written down, or the reference to the source that states the fact is forgotten.

Examples for such facts may be:

- Alpine uses [musl libc](https://musl.libc.org/)
- The `net` package causes a Go binary to be dynamically linked

## Solution

Make writing down and retrieving learned facts as simple and quick as possible.

```
Fact:
Alpine uses [musl libc](https://musl.libc.org/).

References:
[1] https://www.alpinelinux.org/posts/Alpine-Linux-has-switched-to-musl-libc.html

Additional information:
This makes it different from most other Linux distributions, which use GNU libc.
```

```
Fact:
The 'net' package causes a Go binary to be dynamically linked.

References:
[1] https://www.arp242.net/static-go.html

Additional information:
The reason is that the 'net' package uses [CGO](https://pkg.go.dev/cmd/cgo), which allows to call C code from Go.
```

## Features

- Each fact should be stored with rich meta data, such as the creation time
- Facts should be linked to each other
  - By Tags
  - Automatically by text/keyword analysis
  - TODO: by explcit links?
- Efficient full text search across facts
- Ability to edit and reorganise facts while maintaining the full modification history

## Resources

<!-- Resources that might be useful for implementing the project -->