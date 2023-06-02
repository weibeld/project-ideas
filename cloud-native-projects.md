---
id: 9r0yscw69vzqewwxk2td1xv
title: Cloud Native Projects
desc: ''
updated: 1679798959385
created: 1679787470860
---

Similar to [[1.project-ideas.cloud-native-logos]] but with descriptions of cloud-native projects/tools/platforms instead of logos.

This project has been started on https://github.com/weibeld/cloud-native-wtf.

> Additional information relevant for this project can be found in [[1.project-ideas.cloud-native-logos]]. This project idea note only contains the information that is different from [[1.project-ideas.cloud-native-logos]].

## Description

The goal of this project is to provide an overview of projects in the cloud-native computing space, allow to quickly find out what project is doing what, and discover new projects.

The focus should be on fast and easy navigation of the projects (searching, filtering, sorting) and on "explain-like-I'm-5" (ELI5) kind of description of what a project does.

### Features

- Each project is presented as an entry that mainly consists of text.
- An entry may also include the logo of this project, which may be referenced from [[1.project-ideas.cloud-native-logos]]
- Possible data about a project
    - Full name (e.g. Amazon Web Services)
    - Short name (e.g. AWS)
    - Description
    - Logo
    - Website
    - GitHub URL
    - GitHub stars (check if can be added with https://github.com/badges/shields or similar)
    - CNCF membership status
- Very good search: fast, incremental, fuzzy, covers full name, short name, and description, sensible ranking of search results

### Open questions

1. Should tags be used (see [[1.project-ideas.cloud-native-logos]])?
    - If not, how to express relatedness between projects (see [[1.project-ideas.cloud-native-logos]])?
    - Omit tags and solely rely on search to discover projects? Search should cover both full name and short name, as well as the description text. Then, in the description, it could be made sure that certain key words always appear in the description text of related projects (e.g. "Infrastructure as Code", "Hypervisor"). Projects that are very closely related (e.g. Terraform and Pulumi) could also directly link to each other in the description. Thus, if searching for one, the other will appear too (and if searching for a common keyword, e.g. "IaC", both will appear too).
2. How does this project provide value?
    - There's the [CNCF Landscape](https://landscape.cncf.io/) which already categorises many cloud-native projects and presents a nice overview of them
    - However, the CNCF Landscape is heavy and slow to navigate. Also, it only provides the a short excerpt of the project's own README as the description, not a consistent description from an ELI5 perspective.
    - If this project is to provide any value, then the search and ELI5 features must be really good
3. The above means that most importantly the search functionality must be extremely good. What search engine to use?

## Background

<!-- Related projects, state of the art, motivation, etc. -->

## Resources

- https://github.com/weibeld/cloud-native-wtf
- https://landscape.cncf.io/