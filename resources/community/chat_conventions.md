---
title: Chat Channel Conventions
description: Conventions and etiquette related to the BC Gov developer chat platform. 
---
## Chat Channel Conventions
Below are the chat channels we manage and the intended use/etiquette around each. Note that this is by no means a complete list.
If you feel there is a channel that is missing here, please let us know.

We are encouraging a **community/peer-to-peer support model** where community members are expected to participate by sharing their experience and advice, and responding to problems and questions as they are able.  

While the platform team will attempt to triage, and moderate discussions, the success and sustainability of the model depends to a large degree on participation from the broader community.

For more information about the the expectations involved with the community support model, please see (insert link to Onboarding Outcomes here)

Note: Our current chat space is on Rocket.Chat at https://chat.developer.gov.bc.ca/

## General Rocketchat Etiquette

If you're not sure about the purpose of a channel (aka if you're not sure if that channel is the right place to post your question), check the channel description.

If you are responding directly to someone else, use the reply feature (click the little voice bubble next to the post to which you are replying).

This helps to keep the context of your posts clear to everyone in the channel and will notify the person you're responding to.

If your question did not get answered within a reasonable time (4 hrs during business hours, 24 hrs if a question was submitted after hours), please **re-post it and use @all annotation to get people's attention**. Urgent and time sensitive questions should be posted int the #sso channel.

## Channels

### \#devops-sos
\#devops-sos is where you should post when you have one of the issues below:

 * a production problem with an OpenShift-hosted app that you can't solve without external assistance from the DevOps platform team or AdvSol.
 * an issue with an OpenShift hosted project support tool that has caused a work stoppage that cannot be worked around

Note that normal BC Gov support channels (77000, IMB help desks, etc.) should be used for shared infrastructure such as reverse proxies, SiteMinder, firewall rules, etc.

This channel will be monitored by the platform team and AdvSol during business hours.     

### \#devops-how-to

\#devops-how-to is for asking *non-urgent* questions about approaches to solving problems, evaluating technical options, getting feedback on different approaches, familiarity with platform features or tools, resources/examples, etc. 

### \#geows-how-to

\#[Geo Spatial Web Services How-to](https://chat.pathfinder.gov.bc.ca/channel/geows-how-to), this is the channel you can inquiry how to consume Province provided spatial webservices such as WMS, WFS, ArcGIS REST services with your web applications.

### \#devops-alerts

\#devops-alerts is where the operations team will provide notices and progress notifications of upcoming or ongoing maintenance activities or incidents.  

### \#labops-alerts

\#labops-alerts is a channel for the lab-ops team to post notifications to other lab residents and the community at large.
Notifications about community events can be found here.

### \#team-coco

Team CoCo is the Common Components team - they can be found here if you're hoping to find a component that you think might already exist, or if you have a component that you want to share with the community.
 
### Tool Channels

There are a number of channels dedicated to community support and discussions about the use and development of specific tools.
These channels include: (note that this is not a complete list)
* \#rocketchat-help - Ask questions about the use of RocketChat for getting help and connecting with the Community
* \#devops-ocp4-migration - Ask general questions about working in Openshift 4 
* \#sso  - this is a dedicated channel for product teams that rely on the [Keycloak Single-Sign-On](https://developer.gov.bc.ca/BC-Government-SSO-Service-Definition) service for user authentication 
* \#devops-artifactory - Ask questions about how to leverage the [Artifactory](https://developer.gov.bc.ca/Artifact-Repositories) service that provides OCP 4 apps with access to a secure repository to store images, npm packages and other artifacts.  
* \#devops-aporeto - Ask questions about developing Network Security Policies to control communications in your namespaces that are enforced by [OCP 4 Software Defined Network Solution](https://developer.gov.bc.ca/Developer-Guide-to-Zero-Trust-Security-Model-on-the-Platform) based on the product called Aporeto.
* \#devops-vault - Ask questions about using Vault Secret Management Service to managing app's credentials, API tokens and any other sensitive information. 
* \#patroni - Ask question about using Patroni to build High-Available database service using PostgreSQL
* \#realm-o-matic
* \#documize - Ask questions about the use of Documize (https://docs.pathfinder.gov.bc.ca), open-source content management system that is used for protected content that cannot be published in the open through DevHub (http://developer.gov.bc.ca)
* \#bcdk

 
### \#general

Anything that might be of interest to the community.

### \#job-postings

Learn about job opportunities in and around the BC Gov DevOps community.

### \#kudos

If someone (or a group of someones!) deserve your public thanks, this is the place to do it.

### \#random 

Jokes (SFW only pls), links, and ~~cat~~ pug pictures. 'Nuff said.

## Naming New Channels

Teams are always welcome to make new channels for their own use! When doing so,  consider the following conventions for creating and naming your channel:

1. Is this additional channel necessary? Discussions are a great way to provide a dedicated space for taking about specific topics, especially if the topic will only be relevant for a finite amount of time!
2. Is this channel team-specific? If you're interested in making a channel for the use of the wider community, please give our LabOps and/or Platform Services teams a shout about it. This is so we can properly support this community-wide service!
3. Is your new channel's name clear? Team-specific channels should include the team's name (or shortname). A new user should be able to tell at-a-glance what this channel is about, even if they're not a member of your team. Consider using a format like this one: `team-topic`

As always, our community is more than welcome to fork this doc and include some recommendations of their own. We'd be particularly interested in hearing about how your team has chosen to organize their channels, so new teams can learn what has worked in the past!

