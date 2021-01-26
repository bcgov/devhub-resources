---
description: Step 1 in your cloud migration should be migrating your pipeline. Find out how :) 
tags:
- azure
- azure redhat openshift
- cloud migration
- public cloud
- ci/cd
- cicd
---
## Migrating Your BC Gov Jenkins to the Cloud

There is a __UBI8__ based Jenkins image now available to build in your namespaces. You can leverage this image on its own (including the deployment config associated with it), or you can reference it from any existing pipeline that was using the `bcgov/jenkins-basic:<tag>` image. For users of the __RHEL__ based Jenkins this will be the easiest point of transition from the Pathfinder `3.11` cluster and your next cluster. 

This all being said, Jenkins is becoming an older and older CI/CD tool. While it works, there are better, more kubernetes-supported tools out there. Look forward to tools like Argo being supported in the future. 

> What does this mean for me? Not a lot right now! If your pipelines are working well then keep them that way. There will be a point where Jenkins will be deprecated in favor of a more modern CI/CD tool. This does not mean your Jenkins will stop working. It just means Platform Services and the Community will not be providing regular support to the Jenkins Image.

## Things to take into account before building and deploying

1. Jenkins v2.235.5 now looks for builds/jobs in `/var/jenkins-data` instead of `/var/lib/jenkins/..`
   You will __need to modify__ any existing Jenkins DeploymentConfigs. Adjust your `volumeMounts` to match that path. 

```yaml
# From
volumeMounts:
  - mountPath: /var/lib/jenkins/jobs
    name: jenkins-jobs
    readOnly: false
  - mountPath: /var/run/pod
    name: pod-metadata
  - mountPath: /run/secrets/jenkins-slave-user
    name: jenkins-slave-user
    readOnly: true
  - mountPath: /run/secrets/github
    name: github
    readOnly: true

# To

volumeMounts:
  - mountPath: /var/jenkins-data
    name: jenkins-jobs
    readOnly: false
  - mountPath: /var/run/pod
    name: pod-metadata
  - mountPath: /run/secrets/jenkins-slave-user
    name: jenkins-slave-user
    readOnly: true
  - mountPath: /run/secrets/github
    name: github
    readOnly: true

```

2. If you are using Persistant Storage `double check` the storage class you are wanting to use is availble in your cluster. If not look for an alternative storage class and adjust accordingly.

## Differences between the BC Gov Jenkins and Redhat Jenkins

- In most situations the RedHat Jenkins image that __should__ be provided in the cluster will work for your pipeline. 

- If, in your pipeline, you are using tools such as `jq`, or other `tinytools` (curl, grep). These may not be available in the Redhat Jenkins image.

- The Redhat Jenkins is a single pod deploy

- The BC Gov Jenkins image contains the Jenkins `swarm` plugin which allows you to setup a Jenkins primary-secondary relationship.

- If you were using the `bcdk` or `nrdk` you will need to use the `BC Gov Jenkins` image

- If you are using `JenkinsPipeline` strategy you should use the Redhat Jenkins provided in the cluster. 
> Keep in mind JenkinsPipeline is being deprecated!

## Building the Jenkins image

Instead of Platform Services managing a globally available Jenkins Image in Openshift (such as `bcgov/jenkins-basic` in 3.11), there is a [base image manifest](https://github.com/BCDevOps/openshift-components/pull/54) that you can build in your namespaces and extend how you wish. The base-image is community maintained. 

1. Build your jenkins-basic image .
`curl https://raw.githubusercontent.com/BCDevOps/openshift-components/master/cicd/jenkins-basic/openshift/build.yaml | oc process -f - -p NAME=jenkins-2 -p VERSION=54 | oc apply -n <toolsnamespace> -f -`

> why version 54? This translates to the 54 Pull request to the repository. You can change this to whatever version you choose.


## Running the Image

Depending on how you leverage the above base image, either you will just deploy it or use it as a base for another build config. The latter is how the `bcdk/nrdk` jenkins image is built. 

1. Running Base Image as is:
  Your jenkins pipeline should contain some infrastructure code declaring how your Jenkins Deploys. This is most likely in the form of a `DeploymentConfig` modify that infrastructure code to reference your name jenkins base image (`image: <registry>/<toolsnamespace>/jenkins-2:${VERSION}`) and deploy as usual.
  > Make sure to check your [volume mounts are correct](#things-to-take-into-account-before-building-and-deploying)

2. Using base image with bcdk:
  - take a look at your jenkins infracode and modify the build config to point to your new base image that you have just build
  - modify the volume mounts in your jenkins deploymentconfigs [as described above](#things-to-take-into-account-before-building-and-deploying)
  - run your `npm run build/deploy` scripts as you would normally to maintain your jenkins instance
  
