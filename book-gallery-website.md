---
id: 23so812q8ysg61ucwdjx1xj
title: Book Gallery Website
desc: ''
updated: 1680190057934
created: 1679758071975
---

Create a gallery-type website displaying all the books from my collection.

## Description

### Architecture

All data for the website could be taken directly from [[2.records.books]] on GitHub (to have a single source-of-truth for the data about the book collection).

The website could then be rebuilt whenever the data in [[2.records.books]] changes on GitHub (e.g. through GitHub Actions).

### Features

The focus of the website should be on searching, filtering, and sorting the displayed books. The main goal is that these operations be extremely fast and easy.

The website should also allow downloading the PDF files of individual books (from the storage on S3, see [[1.project-ideas.sync-books-to-s3]]), as well as of all books at once. The latter may possibly include downloading and installing the syncing daemon (see [[1.project-ideas.sync-books-to-s3]]) for setting up a local synced folder on a new machine.

It should also be possible to overwrite the PDF files of individual books by re-uploading them through the website (e.g. after downloading them and making edits).

Non-features are editing the metadata of the books, adding new books, and removing books. These operations should be exclusively done through [[2.records.books]], which is the single source-of-truth for the book collection.

Thus, the website can be seen as ready-only (with the exception of overwriting the PDF files of the books).

### Open questions

1. What technology to use?
    - Static website?
    - Client-side JavaScript framework (Angular, React, Vue)?
2. What's the canonical or most efficient way to build such a website?
    - Study similar websites (see [Resources](#resources) below)
3. How to implement access control?
    - Access to the website could be public, but downloading and uploading PDF files should be restricted to an authenticated user.
4. Would it be possible to express the relatedness between books in other ways than tags?
    - E.g. by scraping the "related books" for a given book on Amazon?
    - In that case, tags wouldn't be necessary at all. The default mode of searching would be a title search. Then, any related books that are not already returned by the title search could be returned additionally.
5. Does it make sense to keep the book data in these notes? Or just keep it in a separate repository (similar to how [[1.project-ideas.cloud-native-logos]], etc.) are planned?
    - Observe if any links from notes to the book record notes will emerge. If not, then probably the books don't need to be maintained in these notes.
6. How to gather the book metadata? Obtaining it manually is very tedious with nearly 200 books.
    - 

## Background

This project builds on [[1.project-ideas.sync-books-to-s3]]. While using S3 instead of Google Drive as the remote storage may not be necessary for implementing this gallery website, it certainly makes things easier.

The insights gained from this projects can then also be used for other projects that use a gallery-like website, such as:

- [[1.project-ideas.cloud-native-logos]]
- [[1.project-ideas.cloud-native-projects]]
- [[1.project-ideas.cloud-native-books]]

## Resources

Similar websites:

- https://svgporn.com/
- https://collabnix.github.io/kubetools/

Book APIs for gathering metadata:

- Google Books API
    - https://developers.google.com/books/docs/overview
- ISBNdb
    - https://isbndb.com/isbn-database
    - 15$/month (7 day free trial)
- Open Library
    - https://openlibrary.org/developers/api
    - Low quality covers
