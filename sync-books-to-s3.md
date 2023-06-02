---
id: 0xmdg1pykocqp2o7q18gcap
title: Sync Books to S3
desc: ''
updated: 1679758236926
created: 1679757374846
---

Store books on Amazon S3 instaed of Google Drive.

Store books on AWS S3 instead of Google Drive. Sync books to a local folder with [`aws s3 sync`](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/sync.html).

Later, a gallery website could be created that links to the books on S3. The list of books and the data that is displayed about each book could be taken from the 'Books' records in these notes on GitHub (e.g. GitHub Actions rebuild the website on each change under 'records/books'). The cover images could be taken from the PDF files on S3 or scraped from Amazon.

Note: in that case, maybe still use tags for describing the topics of the books in records/books.

## Description

Store all books in an S3 bucket and sync them to a local directory. This should be similar in behaviour as the current solution with Google Drive, just using S3 instead as the remote storage.

This can probably be implemented rather easily with [`aws s3 sync`](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/sync.html). For example by having a local process that watches the local synced folder and initiates a local-to-remote sync whenever a file in the local folder changes. The remote-to-local syncs could be done periodically in fixed intervals, or also explicitly initiated.

## Background

This could be a first step towards the [[1.project-ideas.book-gallery-website]] project.

Also, removing the books from Google Drive reduces the used storage space on Google Drive. Storage on S3 is extremely cheap with about $0.023/GB, thus storing the books on S3 would be almost free.

## Resources

- https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/sync.html
- https://aws.amazon.com/s3/pricing/