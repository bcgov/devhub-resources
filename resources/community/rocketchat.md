---
resourceType: Documentation
description: Learn more about Rocket.Chat, a instant chat app, and how you can use it in your day to day work
tags:
- rocket chat
- rocketchat
- im
---

# Leveraging Rocket.Chat

Rocket.Chat a community building and team messaging tool. The [BCGOV rocket.chat](https://chat.developer.gov.bc.ca) is used by people in the BC Public Service who are building digital products and learning how to work a as a community to build the best practices of digital government in BC.

## It's Community

Most chat channels are public and allow you to discover/learn about new tech, upcoming events, solutions to common problems and even more. 
To learn more about the common channels, check out our [Chat Channel Conventions](https://developer.gov.bc.ca/topic/featured/Chat-Channel-Conventions) or go explore the options on RocketChat!

* Don’t know what to do? Say it out loud to our community and chances are that someone who does know will offer help.
* Holding onto a great idea, or have a brilliant answer? Contribute it and watch the community come together to evolve it.  

## It's A Place To Ask Questions

A good question is more likely to get an answer - and it’s likely to get a better answer more quickly, too! To help you learn how to ask a good question, here are some templates to follow that might help!

### I'm Having An Operational Problem

Having trouble getting your deployment-config to work? Struggling to pull an image from the internal registry? Seeing a funny error message when you try to mount a PVC? Having trouble pulling from Artifactory? Is the Backup Container not working the way you expected? When you're having problems relating to your deployment on Openshift itself or with one of our operational platform tools, you'll want to make sure you include all the following information:

1. **What cluster and namespace are having the problem?** Make sure you provide the `a1b2c3-env` formatted namespace name here. If you want to provide an app name too, that's great, but the community can provide much more effective help if we know where exactly to find the problem.
1. **What tool are you using?** If you're working with a specific platform tool, make sure you let us know which one. 
1. **What behaviour did you expect?** What was it you were trying to do? Were you building? Deploying? Mounting a PVC? Backing up a database? Let us know what it was you were trying to do and what outcome you expected.
1. **What actually happened?** So now that we know what was *supposed* to happen, tell us all about what *did* happen. Did the build fail? Did the pod enter CrashLoopBackoff instead of starting up properly? Tell us where it all went wrong.
1. **Include any error messages.** When something fails, chances are that there's an error message around somewhere that can tell you a little about why it failed. Make sure you include those when asking for help. Tip: put error messages into code blocks to make them easier to read in RC!
1. **What have you tried so far?** What did you find when you Googled the error message? What steps have you taken to try to figure out how to fix the problem? We don't want to give you advice, only to realize that we're telling you to do something that you've already tried. The results of your initial troubleshooting efforts can be really useful to the community when trying to determine the cause of your issue, so make sure you include them, with as much detail as you can manage. If you've been following instructions on a StackOverflow thread, link it! If you've been poring over some documentation looking for the problem, link it! The more information we have, the better!

These types of questions are usually best suited for #devops-howto or for any of the channels relating to the specific platform tool in question. Try one of those (or both)! You might also want to try #common-components, if you're using one of the tools developed through that team!

Special note: Keycloak *is* definitely a platform tool, but maintenance and support of that particular tool is being shifted to a dedicated team - make 100% sure that your keycloak issues are posted to #sso in particular, to make sure that team has a chance to see it!

## I'm Having An End-User Problem

Not sure how to figure out Documize privileges? Issues logging in to Rocketchat? Having trouble finding the right document on DevHub? When you're having problems with a tool you use as an end-user, make sure you include the following details:

1. **What tool are you trying to use?** Make sure you let the community know which tool seems to be causing the problem.
1. **What machine are you using when you have the problem?** Are you using a Windows machine, a Mac, an iPhone, an Android, or something else altogether? What version of the application are you using? If the problem tool is a web app, what browser are you using to access it? More detail is better - telling us that you're using Chrome is good, but telling us that you're using Chrome Version 89.0.4389.90 is even better. Have you tried to use the tool on a different machine or browser? If so, what happened?
1. **What steps brought you to the problem?** Once again, more detail is better - telling us "I was trying to log into RC and got an error" is okay, but "I was trying to log into RC with my Github account, and I got to the page where it asks me to pick IDIR or Github, but when I clicked on IDIR, the next page was an error message" is much, much better.
1. **Include any error messages.** If an error message comes up, copy-paste or screenshot the error and provide it as part of your question - they can often provide a lot of insight into the specific reason for the problem. Tip: put error messages into code blocks to make them easier to read in RC!
1. **What have you already tried to do to fix the problem?** What did you find when you Googled the error message? What steps have you taken to try to figure out how to fix the problem? We don't want to give you advice, only to realize that we're telling you to do something that you've already tried. The results of your initial troubleshooting efforts can be really useful to the community when trying to determine the cause of your issue, so make sure you include them, with as much detail as you can manage. 

These questions are probably best asked in the RocketChat channel specifically dedicated to the tool in question, but #devops-howto can also be a great starting point if you can't find a more appropriate channel!

### I'm Having A Development Problem

If you're having problems figuring out why your Javascript is producing a particular error, that's probably not an issue the Platform team can help too much with - we're mostly operational people. The teams working and developing on the platform are the expert programmers around here! But you absolutely *should* still ask such questions on RocketChat - someone else in the community might know exactly what the solution is! Here are some tips for how to ask good development questions:

1. **Tell us about your stack.** What languages are you using? What libraries? What versions of each?
1. **What are you trying to do?** Give us a quick rundown of what the code is *supposed* to do. Include the relevant snippets of your code and explain (with plenty of detail) what each section of code is meant to do. Ideally, you should provide enough code that someone else could copy-paste it and, with minimal effort, reproduce your problem.
1. **What is actually happening?** So now that we know what's *supposed* to happen, tell us what is actually happening. If there are any error messages involved, make sure you include those. If it's a logical error, provide plenty of examples of what output you'd expect vs what is actually being produced. 
1. **What have you tried?** What have you done to try to fix the problem so far? What troubleshooting steps have you taken and what were their results? Have you Googled the issue? If so, what did you find? Include links to any relevant sites you've been using to help troubleshoot your problem (ex: related StackOverflow answers, documentation pages, etc). 

These questions are probably best posed in #devops-howto - however, we do have a number of growing RC channels dedicated to development with specific languages/stacks, like #angular-development and #python, so be sure to check those out as well!

### I'm Having A Different Problem

Is your problem not effectively covered by one of the examples above? Here are some general tips for asking a good question:

1. **What are you trying to do?** Provide full details about exactly what you're hoping to achieve. What end result are you looking for?
2. **How are you trying to do it?** Provide full details about what you've already done to solve your problem and what tools you're using. If you're having problems logging into RocketChat, are you using IDIR or Github? Website or App? On Windows or Mac? Include all the details you can think of!
3. **What kind of help do you want?** What is it that you're hoping the community can provide for you?
4. **Why are you trying to do it?** Why is this important in the first place? Maybe there's another simpler way that can serve your purpose—it’s important for the community to know that, too!

And make sure you're asking on the right channel! Check out [Chat Channel Conventions](https://developer.gov.bc.ca/topic/featured/Chat-Channel-Conventions) to find out more!

## How to join?

All Government Employees (with an IDIR account) as well as GitHub users who are apart of the [bcgov GitHub Organization](https://github.com/bcgov) have instant access.

If you do not have access, please refer to the instructions here for details: https://developer.gov.bc.ca/Community-and-Events/Steps-to-join-Pathfinder-Rocket.Chat


> Case Study: The Devhub UX Survey
The Devhub (https://developer.gov.bc.ca) Team created a survey to learn more about how users are interacting with the app.
This was passed communicated through Rocket.Chat in the `#general` channel. Several community members responded to our survey which
has helped not get insight into usage of the Devhub, but has provided useful data to influence future work.
