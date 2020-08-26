## Check #1: Exploring the images you leverage and its availability

Double check your build and deployment infrastructure for the images you are leveraging. 
There is a __high likelihood__ that some of the images you are referencing will not exist inside your new namespace, the default `openshift` namespace etc. 

> This is also a good opportunity to discover out-of-date images and upgrade them wherever possible


### S2I builds 

There is a high chance some of your s2i builder images do not exist within the namespace. You will need to rebuild these inside of your `tools` namespace and update references to the s2i builder within your `BuildConfig`(s).

### RedHat Images

There is a high chance some of the RedHat Images you were referencing do not already exist within your namespace or the default `openshift` one. You can easily pull these using a Redhat Service Account. 

1. Visit [RedHat](https://access.redhat.com/terms-based-registry/) and create an account or login.
2. Create a __Registry Service Account__.
3. Take note of your __username__ and __password__ (the password is a JWT)
4. create a `docker-registry` secret in your namespace

```sh
oc create secret docker-registry rh-registry --docker-server=registry.redhat.io \
--docker-username='<NAME>'
--docker-password='<PASSWORD>'
--docker-email=''
```

5. When running your `BuildConfig` make sure to set the `build-secret`
```sh
oc set build-secret --pull <buildconfig> rh-registry
```
> make sure to capture any changes from your build config and store it back as code!!!


