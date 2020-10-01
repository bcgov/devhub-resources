---
description: Common pain points when migrating apps to the cloud.
tags:
- aro
- azure redhat openshift
- cloud migration
- public cloud
---

## Setting up your namespace

The pattern for building and deploying apps in the cloud should remain similar to what you originally had it set to. For BC Gov OCP projects this means that your team has a `dev`, `test`, `tools`, and `prod` namespace. 

A common pattern for administering these namespaces is:

__Dev__: Has `system:image-puller` access to the __Tools__ namespace. This is where development workloads are deployed.

__Test__: Also has `system:image-puller` access and typically will retag the __Tools__ imagestream into __Test__.

__Prod__: Similar to Test

__Tools__: This is reserved for applications that help serve your main business application. Things like a Jenkins pipeline, SonarQube, Matomo etc.

[Updating Image Pull Access](https://docs.openshift.com/container-platform/4.4/openshift_images/managing_images/using-image-pull-secrets.html#images-allow-pods-to-reference-images-across-projects_using-image-pull-secrets)
```sh
# grant image pull access between your development namespaces and tools
oc oc policy add-role-to-user system:image-puller system:serviceaccount:<namespacename>-dev:default --namespace=<namespace-name>-tools

oc oc policy add-role-to-user system:image-puller system:serviceaccount:<namespace-name>-test:default  --namespace=<namespace-name>-tools

oc oc policy add-role-to-user system:image-puller system:serviceaccount:<namespace-name>-prod:default  --namespace=<namespace-name>-tools
```

## DeploymentConfig Issues

1. __Implicit docker image registry is not the internal docker registry service.__  When pointing to namespaced images, Openshift will attempt to pull it directly from `docker.io` instead of the internal registry. You will need to specify the internal registry when referenced images outside of your namespace.

2. __ImagePullPolicy is IfNotPresent by default__. The `ImagePullPolicy` is set to `Always` in __3.11__. This is not the case in ARO. This means that when you push new images and redeploy a DeploymentConfig. It will not use the latest version of that imagestreamtag. You can switch the ImagePullPolicy to `Always` to rectify this

## Pod Debugging Issues

1. It appears in ARO specifically Pods logs can sometimes be truncated. This means that if you are attempting to debug a long stream of logs, the __head__ logs are not available. A __workaround__ for this is to make sure to view the logs as soon as the pod is available. 