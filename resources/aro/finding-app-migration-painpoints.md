
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
