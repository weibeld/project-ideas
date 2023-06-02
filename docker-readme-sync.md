---
id: oht6gjxtm9puhrwe8rqkmu9
title: Docker README Sync
desc: ''
updated: 1679088095349
created: 1679080898046
---

A tool that automatically syncs the README of a Docker image repository on GitHub to the corresponding repository on Docker Hub.

See also: [[1.project-ideas.docker-image-push]].

## Problem

Currently, the README of a Docker Hub repository must be entered manually, that means, whenever the README is changed in the GitHub repo, it must be manually updated in the Docker Hub repo.

> TODO: it's possible that previously the README could be automatically synced with the free version of Docker Hub. It's also possible that with a paid version of Docker Hub, the syncing can be automated.

## Solution

Create a GitHub Actions workflow that automatically syncs the README whenever it is updated.

## Features

<!-- What features does the project have? -->

## Resources

- https://github.com/peter-evans/dockerhub-description
- https://github.com/marketplace/actions/docker-hub-readme-description-sync
- https://github.com/ms-jpq/sync-dockerhub-readme