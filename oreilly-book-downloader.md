---
id: lovxhgvx1tri3jakvc8nb69
title: O'Reilly Book Downloader
desc: ''
updated: 1679088028080
created: 1679087604030
---

A tool that allows to download e-books from O'Reilly Online Learning (access with subscription only) as nicely formatted PDF files.

## Problem

O'Reilly doesn't sell PDF verions of its ebooks anymore. Instead, ebooks are accessible only on the O'Reilly Online Learning platform and must be read in a web browser.

## Solution

Create a tool, probably in the form of a scraper (since O'Reilly probably doesn't have an API), that downloads the content of O'Reilly e-books and formats them in a way that comes as close as possible to how previously PDF e-books were formatted.

The conversion to PDF can be done with [Pandoc](https://pandoc.org/) and an appropriate template.

## Features

<!-- What features does the project have? -->

## Remarks

<!-- Further remarks about the project -->

## Resources

- https://github.com/weibeld/pandoc-templates: possible Pandoc template
- https://gist.github.com/weibeld/e406a27275863660c61d3cba3b0cf2d3: result of applying the Pandoc template