---
tags:
- context
- oc config
- multiple login
- oc login
- multi-cluster
description: Learn how to more easily interact with two or more OpenShift Clusters using contexts
---

## Working in Multiple Clusters

When performing a migration from one cluster to another it is important that you can rapidly change between clusters without having to 
manually login. This can be done by leveraging `contexts`. Contexts allow you to change between clusters (when logged in) on the fly using the command `oc config use-context <context name>`

1. Login to the clusters you wish to work with (ie something like Azure Redhat OpenShift and Pathfinder 3.11)

2. Open up your oc config file in your code editor of choice (located at `~/.kube/config`)

You will find a set of contexts (namespaces you have logged into). From here locate a couple of contexts, one for each cluster you wish to login to.
```yaml
- context:
    cluster: api-platform-services-aro-devops-gov-bc-ca:6443
    namespace: default
    user: patricksimonian@github/api-platform-services-aro-devops-gov-bc-ca:6443
  name: default/api-platform-services-aro-devops-gov-bc-ca:6443/patricksimonian@github
- context:
    cluster: console-pathfinder-gov-bc-ca:8443
    namespace: default
    user: patricksimonian/console-pathfinder-gov-bc-ca:8443
  name: default/console-pathfinder-gov-bc-ca:8443/patricksimonian
```

3. The `name` property is actually a __nickname__. Modify the name to a more useable one for context switching.

```yaml
- context:
    cluster: api-platform-services-aro-devops-gov-bc-ca:6443
    namespace: default
    user: patricksimonian@github/api-platform-services-aro-devops-gov-bc-ca:6443
  name: aro-default
- context:
    cluster: console-pathfinder-gov-bc-ca:8443
    namespace: default
    user: patricksimonian/console-pathfinder-gov-bc-ca:8443
  name: 3.11-default
```

4. You can now switch contexts by using a command like `oc config use-context aro-default`
> pro tip, store the command `oc config use-context` in your profile settings (`.bashrc` `.zshrc` etc) as an `alias` to speed up your workflow


## When Clusters are of different versions

For the most part, `oc 3.11` and `oc 4.x` binaries do behave similarily for many actions. There are some actions that may cause you trouble if you attempt to use a binary that doesn't match your cluster version. 

Something that may help you organize your binaries is to store them into a directory and reference them as aliases in your profile config (`.zshrc`, `.bash_profile` etc)

For example you could organize your oc binaries like:

```sh
.
├── oc3
│   └── oc
└── oc4
    └── oc
```

and reference them in a `profile`:

```sh
# .zshrc
alias oc3="~/Tools/oc3/oc"
alias oc4="~/Tools/oc4/oc"
```
> you can set your default oc on the `PATH` to the one you use most. 