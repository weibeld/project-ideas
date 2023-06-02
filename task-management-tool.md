---
id: 8sfa1a2q2jcu6v0oa057vql
title: Task Management Tool
desc: ''
updated: 1679088106588
created: 1679080065517
tags: todo
---

> TODO: evaluate whether this project idea is still relevant given the new Desk-Drawer-Shelf note-taking system.

A tool that's very similar to [Taskwarrior](https://taskwarrior.org) but with a few improvements and some additional features.

## Problem

Taskwarrior is a great tool, however, it has some downsides:

- It's not intended for managing free-form notes
    - EDIT: this might not be an issue anymore given the Desk-Drawer-Shelf note-taking system
- It's not easy to inspect the history of the existing tasks
- It's not convenient to create and review task descriptions that are longer than one line
- It has no notion of projects that tasks belong too
    - TODO: is this true?

On the other hand, Taskwarrior also puts some emphasis on features that are overkill for my use case, such as:

- The sophisticated sorting of tasks based on many parameters

## Solution

A command-line tool, e.g. implemented with Go.

## Features

### Base objects

Provide two types of objects: tasks and notes

- Tasks: like in Taskwarrior
- Notes: free-form notes (no due date, priority, etc.)

### Focus on work retrospection

- Display completed task along with pending tasks (don't make completed tasks disappear)
- Allow modification of completed tasks (e.g. retroactively add a completed task to a project)
- Maintain ID of task after it's completed (in Taskwarrior, the ID of a completed task is removed and available for new tasks, however, the UID remains and a completed task can be selected and edited through its UID)

### Focus on change history

- Keep track of the diffs of all changes to tasks and notes and allow to easily display them
  - Display changes to content in diff output
  - The `information` command of Taskwarrior also displays the entire change history of a task, but the output is not easy to grasp if long descriptions are used

### Focus on projects

- Make projects a first-class citizen (for tasks)
  - Similar semantics as namespaces in Kubrernetes: every task must be in a project. At any time, one project is selected. By default, only tasks of the current project are displayed.
- For notes, projects are optional
  - Notes can be assigned to a project. Notes that are not assigned to a project can be organised in hierarchical topics.

### Focus on multi-line descriptions

- Make first line of description the title and rest the body
- In concise views, display only the title, in detail views, display the body as well (similar to Git commit messages)
  - See [Taskwarrior #2090](https://github.com/GothenburgBitFactory/taskwarrior/issues/2090) and [Taskwarrior #1397](https://github.com/GothenburgBitFactory/taskwarrior/issues/1397) (`description.oneline`, `description.truncated`, `description.truncated_count`, `description.count` all don't have the desired effect)
- Create and edit descrptions in Vim, similar to the Vim plugin for editing Git commit messages

### Focus on usability

- Motto: don't try to be smart for the users, but make it as easy as possible for them to be smart themselves
- Don't use sophisticated algorithms to order and present tasks based on many parameters, but make it easy for the users to freely order and edit tasks themselves

### Git-centric design

- Use a local Git repository as the local storage backend
  - Leverage functionality of Git for history and change tracking, diffs, etc.
  - Replacing the custom storage format used by Taskwarrior
- Use a Git hosting service, such as GitHub, for backups, syncing, and sharing
  - Replacing a dedicated server application like [Taskserver](https://taskwarrior.org/docs/taskserver/why.html) (`taskd`) for Taskwarrior

### Miscellaneous

- Allow defining custom named dates, e.g. last working day of month
- Allow defining custom date semantics (custom weekends and off days, leave days, holidays, etc.)
  - Data can be imported as JSON and generally applicable data files can be shared (e.g. public holidays in a specific country)

## Resources

<!-- Resources that might be useful for implementing the project -->