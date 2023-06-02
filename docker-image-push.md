---
id: izg8jxf0b5g3dlw1pvk8x4j
title: Docker Image Push
desc: ''
updated: 1679088082359
created: 1679081528672
---

A tool that automatically builds and pushes a Docker image from GitHub to Docker Hub.

See also: [[1.project-ideas.docker-readme-sync]].

## Problem

Docker images must be explicitly built and pushed to Docker Hub in a multi-step process. This process must be repated

## Solution

Create a GitHub Actions workflow that automatically builds an image from the Dockerfile in the GitHub repository and pushes it to Docker Hub.

A run can be triggered when a specific Tag is pushed to the GitHub repository.

## Features

<!-- What features does the project have? -->

## Resources

<!-- Resources that might be useful for implementing the project -->