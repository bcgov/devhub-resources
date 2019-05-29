---
resourceType: Documentation
author: patricksimonian
personas:
  - Developer
  - Product Owner
labels:
  - Stand Up Application
  - Build Apps
  - Modern Apps
  - 12 Factor
  - Cloud Native
description: 'Learn how to deliver an app-like experience to your users using these modern best practices for web app development'
---

## Progressive Web Apps

> A Progressive Web App (PWA) is a web app that uses modern web capabilities to deliver an app-like experience to users. 
> https://ionicframework.com/docs/v3/developer-resources/progressive-web-apps/

Progressive Web Apps are fast, work in poor network conditions, include good practices for **SEO** as well as **accessibility**.
It should be noted that Progressive Web Apps refer to the **Front End** of any **Web Application**.

### Fast

Progressive Web Apps utilize modern techniques to optimize, minify, bundle, and fetch assets. This makes the front end of the application
load much faster.

## Poor Network Conditions

PWAs utilize [service workers](https://developers.google.com/web/fundamentals/primers/service-workers/) to ensure that the application
has some offline and or poor network activity capability

### Best Practices

PWAs come out of the box with the correct markup (html) annotated with the correct properties so that they are accesible by different
devices (such as screen readers) and are indexed correctly by search engines. 

Best Practices also includes app's being **responsive** to different screen sizes


## All Volkswagons are Cars. Not All Cars Are Volkswagons

By this we mean that not all apps **should** or **can** be a PWA. It depends on your app requirements, target audience etc.

## How Do I Tell If My App Is A PWA?

The **Google Chrome** browser released a great tool as apart of their **Developer Tools** called **Lighthouse Audit**.

Here is a great guide on how to perform a Lighthouse Audit. https://developers.google.com/web/tools/lighthouse/

