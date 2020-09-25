## Migrating Rhel Images

Depending on your Openshift 4.x cluster you may not have the necessary licences and or subscriptions to pull certain repositories that are needed for your
Rhel based builds. One thing you can do is try to migrate your Rhel based images to __Universal Base Images__ or __UBI__ for short. 


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

### Translating Packages from Rhel (or other distributions) to UBI

As stated from Redhat, UBI images come in 3 flavours: [Standard, Minimal, and Init](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/building_running_and_managing_containers/index#what_are_red_hat_base_images).

TL;DR

If you are using __UBI Standard__, you will be using `yum` to manage packages.
If you are using __UBI Minimal__, you will be using `mirodnf` to manage packages. 


### Available Repositories to UBI Images

Checkout this great article on available repositories for Rhel and UBI images https://access.redhat.com/articles/4238681.

You can also (in a UBI Standard Image) reference available repos by running `yum list all`. 

### Translating Images

Armed with what we know is available to our UBI base images we can now translate the `jenkins-basic` rhel-based image to UBI Standard or Minimal. For this example UBI Standard is used. 


1. The repos `rhel-7-server-rpms` and `rhel-server-rhscl-7-rpms` are not available to UBI8 images. Instead use `ubi-8-appstream` as discovered by reading through that article or listing it in yum.

2. Run the image and see what fails!

3. You will find that it will complain that the package `rh-git29` does not exist. Of course! this is a Rhel git package.

4. As described in the article above, you can sift through the actual repo to see what packages are available. https://cdn-ubi.redhat.com/content/public/ubi/dist/ubi8/8/x86_64/appstream/os. Find the git package available to UBI8 images. In this case it is `git-2.18.4-2.el8_2.x86_64` 

> This is a higher version of git. Usually a good thing, be mindful if you are version locked to certain packages.

5. Lastly, we update the Dockerfile to reference the UBI 8 Standard image and update our package declarations from `microdnf` to `yum` including the correct repositories and packages

```Dockerfile
FROM registry.redhat.io/ubi8/ubi:8.2

...

RUN set -x && yum -h && \
    curl -so /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo && \
    rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key && \
    yum -y --disableplugin=subscription-manager --enablerepo=ubi-8-appstream --enablerepo=jenkins install which gpg java-1.8.0-openjdk-devel shadow-utils "jenkins-$JENKINS_VERSION" zip unzip bzip2 rsync elfutils git-2.18.4-2.el8_2.x86_64 --nodocs && \
    yum clean all && \
    echo "unset BASH_ENV PROMPT_COMMAND ENV" > /usr/local/bin/scl_enable && \
    echo "source scl_source enable rh-git29" >> /usr/local/bin/scl_enable && \
    chgrp -R 0 /usr/local/bin && \
    chmod -R g+rx /usr/local/bin && \
    yum clean all && \
    rpm -qa
 ```





