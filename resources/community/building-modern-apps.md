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
  - Chrome
  - Front End
  - Progressive Web App
  - PWA
  - Web Development
 description: A guide that compiles some best practices for developing applications in the modern world. This guide speaks on 12 Factor Apps as well as Progressive Web Apps.
---

## Building Modern Web Applications

Web application design and architecture has undergone drastic changes in the past decade. With the ubiquity of an '*app for every type of service*',
how apps are built has evolved to meet modern requirements. There is an excellent guideline on designing apps in such a way that meets these
demands and provides robustness for future support and developement. This guideline is called **The 12 Factor App**.

## 12 Factor Applications

> A **12 Factor App**
>- Uses declarative formats for setup automation, to minimize time and cost for new developers joining the project;
>- Has a clean contract with the underlying operating system, offering maximum portability between execution environments;
>- Is suitable for deployment on modern cloud platforms, obviating the need for servers and systems administration;
>- Minimizes divergence between development and production, enabling continuous deployment for maximum agility;
>- scales without significant changes to tooling, architecture, or development practices.
> *https://12factor.net/*

We recommend reading through the guidelines layed out at https://12factor.net/. You may find some of the 'factors' are fairly
common sense while others will (hopefully) become an *aha!* moment

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

