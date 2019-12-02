---
resourceType: Documentation
tags:
- Learn Openshift
- Beginner's Guide
- Openshift For All
personas: 
- Designer
- Developer
- Product Owner
description: Learn about OpenShift at a glance.
---

# What Is OpenShift?

You've been hearing words like _'OpenShift'_, _'Cluster'_, _'Cloud'_ and _'Cloud Native'_ in and around different parts of Goverment
(with a strong concentration located at the __Exchange Lab__). What does this all mean? Are these just buzz words or are they a new way of
doing app development in Gov?

> This document was inspired by you, a user of the DevHub. We found that although OpenShift is leveraged as a platform for over 100+ production,
government applications. There is still a lot of mystery of what it actually is and how it works. This small document will attempt to de-mystify 
OpenShift and explain it in non-technical terms. (not all of us are Developers 😏)

## A Tale of Two Infrastructures

Taken from OpenShift's [learning portal](https://www.openshift.com/learn/what-is-openshift), OpenShift is a
__Hybrid Cloud Enterprise Kubernetes Platform__.

This is very different in comparison to traditional infrastructure that we find leveraged in most Government Applications. 

So to start understanding what OpenShift is, we will first define _what it is not_. It is not like traditional Government
IT infrastructure for standing up and hosting applications.


## So What is OpenShift?
Let's breakup the term __Hybrid Cloud Enterprise Kubernetes Platform__

### Hybrid Cloud

> Definition of __Cloud Computing__: the practice of using a network of remote servers hosted on the Internet to store, manage, and process data,
rather than a local server or a personal computer.
>> source dictionary.com

In a nutshell, the __Cloud__ is just someone else's computer. Our computers are all in the __Kamloops Data Center__.

> Definition of __Hybrid Cloud__: Hybrid cloud is a cloud computing environment that uses a mix of on-premises, private cloud and third-party, public cloud services with orchestration between the two platforms.

OpenShift, as a platform solution, is able to leverage Clouds from different environments. For __our cluster__, we are completely on premise within the __Kamloops Data Center__.

### Enterprise

OpenShift has several built in features that make it useful to run at an enterprise level. 

- It has very good security practices built in by default
- The user access model allows managment of applications and teams
- It is very focused on the __Developer Experience__. All the dependancies that are required for an application (storage, databases, network rules, security, patching) are essentially in one box that can easily accessed by the Developer with minimal barriers.

### Kubernetes

Kubernetes is a open source application that is the foundation of OpenShift. In reality, there are several different 'versions' of Kubernetes, OpenShift is one of these 'versions' that we decided to work with. 

As described by Kimoon Kim, senior architect at Pepperdata: “Kubernetes is software that manages many server computers and runs a large number of programs across those computers. On Kubernetes, all programs run in containers so that they can be isolated from each other, and be easy to develop and deploy.”

### Platform

The OpenShift Container *_platform_* provides several different layers of control and access to allow applications to be developed, built, and deployed securely. 

From the administrative perspective, it is highly configurable. Anything from user access, to custom roles, to resource allocation, storage allocation, and even the provisioning of new servers is modifiable and scalable. 

From a Developer's perspective, it provides the ability to self serve your way to application success. A development team can be allocated a project (a room in the OpenShift mansion) to work in without having other applications interfere, provision their own storage, and configure their application as needed to get it up and running. 

There are several other features that are a part of OpenShift which can be found [here](https://www.openshift.com/learn/what-is-openshift).

## Summary

OpenShift is a platform that allows development teams to work in a self-service manner to build and deploy applications. A side effect of developing applications in a Cloud platform is that they are typically designed to be __Cloud Native__. This means they are scalable, lightweight, fault-tolerant, transportable, and in other words designed to meet the demands of the modern IT ecosystem.
