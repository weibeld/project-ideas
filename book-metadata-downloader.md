---
id: 4yqcitddxhslv90w9cjmvj5
title: Book Metadata Downloader
desc: ''
updated: 1680280866196
created: 1680190222240
---

A command-line tool that allows downloading metadata about a book in YAML format.

## Description

The tool should take as input the ISBN or title of a book and return at least the following set of metadata:

- title
- subtitle
- isbn
- publisher
- edition
- year
- pages
- authors
- cover (image file)

The data may be returned in YAML or JSON.

## Background

This is for obtaining the data for the [[2.records.books]] which will be eventually used for the [[1.project-ideas.book-gallery-website]].

Book meatadata APIs:

- Google Books API
    - https://developers.google.com/books/docs/overview
    - Free (only requires API key from GCP)
    - Can search for volumes (books) with search terms, returns multiple volumes
    - However, the returned volumes are not consistent, there are multiple records for the same book with slighly different titles (and different ISBNs). Also, when retrieving a specific volume, the information doesn't match with the information of the same volume in the list result of the keyword search.
    - Return object for volumes does not contain info about the edition, however, may contain subtitle
    - The API provides the following resource types: volumes and bookshelves (no resource types for authors and publishers)
- ISBNdb
    - https://isbndb.com/isbn-database
    - 15$/month (7 day free trial), limited to 1 request per second
    - API seems much cleaner than the Google Books API, not so many duplicate books
    - Does not provide a separate subtitle field (subtitles included in `title` field)
    - Seems to return only the newest edition of a book, no way to query previous editions
    - The query endpoint, which allows supplying a string to match to either the `title` or `authors` fields, returns completely non-matching results (or maybe it include the better-matching results too, but they are not sorted)
    - Also provides endpoint for authors and publishers, but they seem to be less consistent (many duplicate entries, no queries by identifier, only fuzzy matching)
- Open Library
    - https://openlibrary.org/developers/api
    - Low quality covers
    - Books can't be queried by title (only ISBN and other identifiers)
    - Does have a books and authors endpoint, but no publishers endpoint

Open questions:

- How to handle author and publisher data? In the end, these entities also have to be present as metadata and the book metadata must link to them.
    - When downloading the meatadata for a book, also download corresponding metadata for the publisher and authors, saved in a separate file with the publisher and author ID as the filename, and replace the author and publisher values in the book metadata with these IDs? 
    - Then, when downloading in bulk, these author and publisher files might just overwrite each other (if the same author or publisher is downloaded multiple times), however, all the references would still stay intact.

## Resources

<!-- Resources that might be useful for implementing the project -->
