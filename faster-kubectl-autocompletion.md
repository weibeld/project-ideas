---
id: vnkjv6jet8s50usx6j8y8j4
title: Faster Kubectl Autocompletion
desc: ''
updated: 1679676989989
created: 1679084414849
---

Increase the autocompletion speed of kubectl by avoiding round-trips to the cluster.

## Problem

In many cases, the auto-completion of kubectl requires making a request to the Kubernetes cluster. For example, when auto-completing resource types or names. This may be very slow, thus hampering the Kubernetes usage experience.

## Solution

Find a way to mirror the information in the API server (which is required for auto-completion) locally and configure auto-completion to query this local data instead.

## Features

<!-- What features does the project have? -->

## Remarks

- How to keep the mirrored data in sync with the Kubernetes cluster?
- Maybe [[1.project-ideas.auto-completion-for-kubectl-explain]] is a first step towards this project

## Resources

- [mkokho/kubemrr](https://github.com/mkokho/kubemrr): exactly the same idea, but project is not maintained anymore
- [Telepresence](https://www.telepresence.io/): check what it does and what functionality it provides