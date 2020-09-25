## Migrating Rhel Images

Depending on your Openshift 4.x cluster you may not the necessary licences and or subscriptions to pull certain repositories that are needed for your
Rhel based builds. One thing you can do is try to migration your Rhel based images to __Universal Base Images__ or __UBI__ for short. 


## Getting Started

Source your flavor of UBI image from the [RedHat Container Catalog](https://catalog.redhat.com/software/container-stacks/detail/5ec53f50ef29fd35586d9a56)

### Changing packages in your Image Manifests from Rhel based to UBI based

Take a look at the `jenkins-basic` image that is used in the __3.11__ cluster. 

```Dockerfile
FROM registry.access.redhat.com/rhel7/rhel-atomic

...

RUN set -x && microdnf -h && \
    curl -so /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo && \
    rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key && \
    microdnf --enablerepo=rhel-7-server-rpms --enablerepo=rhel-server-rhscl-7-rpms --enablerepo=jenkins install which gpg java-1.8.0-openjdk-devel shadow-utils "jenkins-$JENKINS_VERSION" zip unzip bzip2 rsync elfutils rh-git29 --nodocs && \
    microdnf clean all && \
    echo "unset BASH_ENV PROMPT_COMMAND ENV" > /usr/local/bin/scl_enable && \
    echo "source scl_source enable rh-git29" >> /usr/local/bin/scl_enable && \
    chgrp -R 0 /usr/local/bin && \
    chmod -R g+rx /usr/local/bin && \
    microdnf clean all && \
    rpm -qa
```

There are a few key things here that __may not work__ if you attempt to build this image in a different Cluster. 

1. Firstly you may not have access to pull the `rhel7/rhel-atomic:latest` image from the RedHat Registry. This is easily addressed by creating a Redhat Container Catalog
Service Account and setting up a Pull Secret. 

2. Even if your images are working, you may not have the proper subscriptions to be able to pull repos stated in the `microdnf` commands. 
> in this case the `-enablerepo=rhel-7-server-rpms --enablerepo=rhel-server-rhscl-7-rpms` repos require subscriptions and do not work in ARO.

..
