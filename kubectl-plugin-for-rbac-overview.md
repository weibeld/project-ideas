---
id: o2qe5qhy3ypkwguxcsob70n
title: RBAC Overview Plugin for Kubectl
desc: ''
updated: 1679682171499
created: 1679677593005
---

A kubectl plugin allowing easy lookup of Roles/ClusterRoles assigned to a given subject (user, group, ServiceAccount), as well as subjects that have a given role.

## Idea

User interface:

```bash
kubectl rbac <user>
```

The above would list all the Roles and ClusterRoles that are assigned to the specified user.

```bash
kubectl rbac <role>
```

The above would list all the users, groups, and ServiceAccounts that have the specified Role assigned.

### Remarks

- Maybe implement as standalone command rather than kubectl plugin?
    - The main issue with kubectl plugins is that auto-completion doesn't seem to be supported yet
        - https://github.com/kubernetes/kubernetes/issues/74178
    - However, some experimental auto-completion support for plugins seems to have been released (check how this works)
        - https://github.com/kubernetes/kubernetes/pull/105867
    - Also see https://dev.to/tarodbofh/customizing-k8s-plugins-autocomplete-on-bash-and-zsh-4hph

## Background

- An existing similar tool is [rbac-lookup](https://github.com/FairwindsOps/rbac-lookup). This idea is basically the same as rbac-lookukp, just with a possibly simpler user interface

## Resources

<!-- Resources that might be useful for implementing the project -->