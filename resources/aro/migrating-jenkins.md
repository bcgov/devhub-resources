## Migrating Your BC Gov Jenkins to the Cloud

There is a __UBI8__ based Jenkins image now available to build in your namespaces. You can leverage this image on its own (including the deployment config associated with it), or you can reference it from any existing pipeline that was using the `bcgov/jenkins-basic:<tag>` image.

## Things to take into account before building and deploying

1. Jenkins v2.235.5 now looks for builds/jobs in `/var/jenkins-data` instead of `/var/lib/jenkins/..
   You will __need to modify__ any existing Jenkins DeploymentConfigs. Adjust your `volumeMounts` to match that path. 

```yaml
# From
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

# To

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

```

2. If you are using Persistant Storage `double check` the storage class you are wanting to use is availble in your cluster. If not look for an alternative storage class and adjust accordingly.

## Building the Jenkins image

Instead of Platform Services managing a globally available Jenkins Image in Openshift (such as `bcgov/jenkins-basic` in 3.11), there is a [base image manifest](https://github.com/BCDevOps/openshift-components/pull/54) that you can build in your namespaces and extend how you wish. The base-image is community maintained. 

1. Build your jenkins-basic image.
`curl https://github.com/bcdevops/
