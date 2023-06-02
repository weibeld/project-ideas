---
id: xple2fsvrbvwdqt9glozc45
title: Cloud-Native Logos
desc: ''
updated: 1679798542303
created: 1679782714532
---

A gallery-type website that displays a collection of cloud-native project logos.

Attempts to start this projects have already been made in https://github.com/weibeld/cloud-native-logos.

This project may be based on the work for [[1.project-ideas.book-gallery-website]].

## Description

The goal of this project is to have a place to collect high-quality and official logos of projects and tools that are relevant to the cloud-native computing world.

### Architecture

The logos and their metadata should be maintained on GitHub (open-source so that people can contribute to the website with GitHub pull requests, etc.). 

The website should be rebuilt whenever the data in the GitHub repository changes.

The logos may be provided in different formats (e.g. SVG and PNG), however, the source-of-truth format (in which the logos are introduced into the system) should be SVG. There may be an automated process (e.g. GitHub Action) that converts all the provided SVG logos into PNG versions (possibly in different sizes).

### Features

The focus of the provided user interactions should be on searching, filtering, and sorting. These operations should be as fast and easy as possible.

It should be possible to download each logo (possibly in different formats, such as SVG and PNG). This refers to every single version of a logo (horizontal, vertical, monochrome, coloured, etc.).

If available, the source of a logo (e.g. from the official project website) should be specified. If a logo has been created manually, the source could be a link to the repository where the design files (e.g. Sketch files) are maintained. See [Open questions](#open-questions) below.

Each logo might link to its proper project website, but also to the corresponding entry in [[1.project-ideas.cloud-native-projects]].

Non-features include the editing of metadata and adding or removing of logos through the website. All these operations should be done exclusively through the GitHub repository.

### Open questions

1. Which technology to use?
    - Same question as in [[1.project-ideas.book-gallery-website]]
2. Should topical tags be used for the logos?
    - Having tags might be useful for discovering new projects, however, it's always subjective and ambiguous which tags are appropriate
    - How to determine the relatedness between projects? Is there a different way? E.g. Google, etc?
    - In general, the focus of this project is not to discover new projects (that's the goal of [[1.project-ideas.cloud-native-projects]]). Rather, the main goal is to obtain a logo for a specific project. Thus, a user would typically search directly for the project name. Tags or a categorisation or relatedness data might thus not be so important in this project (however, it is the crucial part of [[1.project-ideas.cloud-native-projects]]).
3. Logos are almost always provided in different versions (horizontal, vertical, icon only, etc.). How to define a common naming/storage scheme for these versions?
4. How to handle logos that have been manually created?
    - Include design file (e.g. Sketch file) in main repository? Then, how to handle manually created logos of contributors that only provide the resulting SVG files?
    - Keep design files of manually created logos in separate repositories, and then use the links to these repositories as the source of the logos?
    - In both ways, probably still not all logos could be attributed with a source since there might be contributors who don't want to maintain a repository with the design files and just provide the SVG files. In these cases, the source could be indicated as "Added/created by contributors" or something like this.

## Background

This project may come with other projects in the following package:

- [[1.project-ideas.cloud-native-logos]]
- [[1.project-ideas.cloud-native-projects]]
- [[1.project-ideas.cloud-native-books]]

All of thes projects might use a similar design language, user experience, and technology base. Ideally, they should use a common code base to avoid code duplication.

Possible domain names for the projects could be:

- logomonster.cloud
- projectmonster.cloud
- bookmonster.cloud

The basic functionality of all these projects is the same: display information stored in a GitHub repository as a gallery-type website.

## Resources

- https://github.com/weibeld/cloud-native-logos

Similar websites:

- https://svgporn.com/