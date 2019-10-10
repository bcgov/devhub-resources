
# Setup Docker in localhost 


## Instruction of How to Deploy Devhub on local Minishift:

Which means you will not Have a nodejs version 10 and s2i-caddy image from Redhat in 'openshift' namespace.

### You will need:

-   Minishift
-   Docker
-   Access permission to console.pathfinder.gov.bc/openshift namespace.

---

### Step 1: Download and config Minishift 

Ensure that you download and install  [VirtualBox](https://www.virtualbox.org/wiki/Downloads)  before using the embedded drivers. Install before install minishift.

Official instruction can be found  [here](https://docs.okd.io/latest/minishift/getting-started/installing.html).

Use the following command to install and config the latest version of the driver with Homebrew on your computer:

```
brew install docker-machine-driver-xhyve
sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve

```

Install minishift through Homebrew:

```
brew cask install minishift

```

The --vm-driver VirtualBox flag will need to be given on the command line each time the minishift start command is run. For example:

```
$ minishift start --vm-driver virtualbox

```

---

### Step 2: Install Docker

Docker will be required to pull image from Bcgov openshift and push to your local minishift

You can download from  [here](https://docs.docker.com/docker-for-mac/install/). Make sure that you have the Docker client binary installed on your machine.

---

### Step 3: Pull  image from the production cluster to be used locally.

To configure your console to reuse the Minishift Docker daemon, follow these steps:

-   Start Minishift with the  `minishift start`  command.
-   Run the `minishift docker-env`  command to display the command you need to type into your shell to configure your Docker client. The command output will differ depending on OS and shell type.
```code
$ minishift docker-env
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.101:2376"
export DOCKER_CERT_PATH="/Users/john/.minishift/certs"
export DOCKER_API_VERSION="1.24"
# Run this command to configure your shell:
# eval $(minishift docker-env)
```

-   Run this command to configure your shell:  `eval $(minishift docker-env)`
-   Test the connection by running the following command:

```
$ docker ps
```

***Only If successful***, the shell will print a list of running containers.

#### Now we are ready to pull image
_In this example, the  ***NodeJS:10***  image is being pulled from the production cluster's openshift namespace_

-   login to  `console.pathfinder.gov.bc.ca`
```
docker login docker-registry.pathfinder.gov.bc.ca -u $(oc whoami) -p $(oc whoami -t)
docker pull docker-registry.pathfinder.gov.bc.ca/openshift/nodejs:10
```
Use the command `docker images` in your terminal to list the images you currently have on your computer.


---

### Step 4: Push the image to minishift openshift namespace

-   log in to your minishift with system: admin role by  `oc login -u system:admin`  or login through UI and copy login token
    
-   Run following command to figure out minishift openshift namespace registry address
    
```
minishift openshift registry
```
 in this example case: 172.30.1.1:5000
 
-   You will need your admin user have real 'admin' privilage on minishift by running:

```
oc login -u system:admin
oc adm policy add-cluster-role-to-user cluster-admin admin --as=system:admin
oc login admin
```

-   docker login to minishift openshift namespace as admin by

```
docker login -u admin -p $(oc whoami -t) $(minishift openshift registry)
```
-   figure out the **image Id** that you build by running  `docker images | grep nodejs`
-   Use openshift namespace registry and namespace's name and image name to tag your image and pushing it to minisift openshift namespace


```code
docker tag <image ID> 172.30.1.1:5000/openshift/nodejs
docker push 172.30.1.1:5000/openshift/nodejs:latest
```
Check if you have nodejs image in your minishift openshift namespace, pull any other app-required images can be done similarly.
You can check  [next insturction](https://github.com/bcgov/devhub-app-web/blob/master/docs/disasterRecoverInstructions.md)  if you are interested in deploying devhub on your minishift instance!
