---
description: Here are something to consider when building apps for Government on Openshift
title: Best Practices for Building Apps on Openshift
resourceType: Documentation
tags:
- Openshift
- Learning Openshift
- Developer Guide
personas: 
- Developer
---

## Best Practices For Building Apps on Openshift

This isn't a definitive guide on 'how to create an app' but rather a set of guidelines, principals, and troubleshooting tips that will help you and your team find its way to success. 

## Developing Cloud Native Apps

As you know, all Web Apps are deployed on Openshift which is a _kubernetes platform_. In order for you app to operate well in this platform, there are a few principles that should be followed. These principles will help your app respond to modern demands on IT infrastructure; __scalability__, __fault tolerance__, and __quick recovery__ can more easily be achieved.

A fundamental guide for developing apps to be __Cloud Native__ is the [12 Factor App](./12-factor-apps.md).

## Leverage the Design System

The [BC Gov Design System](https://github.com/bcgov/design-system) is an ongoing project that aims to unify
BC Gov UI web components. This is the place to go to find out more about implementing common web components such as __headers__, __footers__, __buttons__ etc. You can find the design system live on the [Devhub](https://developer.gov.bc.ca/design-system)

## Use BC Sans As Your Web Font

BC Sans is an opensource font that __should be used for all web front ends__. It can be leveraged as a __npm package__ as well as a static set of files. More info can be found on it [here](https://github.com/bcgov/bc-sans)

## Developing Performant Front End Applications

It is no surprise that more than __50% of all web traffic__ is now through __mobile devices__.
> https://www.statista.com/statistics/241462/global-mobile-phone-website-traffic-share/

Besides ensuring that your app looks and feels well on _small viewports_ it is important for them to performant, and in some cases behave like a native mobile app. 

There has been a term coined for web apps that meet these expectations: __Progressive Web Apps__. 

Here is a primer on [PWA's](./progressive-web-apps.md). 

### Key Takeaway

Regardless if your web app needs to operate well on mobile phones or not. One way you can greatly __improve site performance__ is by enabling __text compression__. 

If you are using __Caddy Web Server__ you can immediately gain to benefit from text compression by enabling
[_on the fly gzip_](https://caddyserver.com/docs/gzip). 


## Use Rocket.Chat and the Devhub

Rocket.Chat's [devops-how-to channel](https://chat.pathfinder.gov.bc.ca/channel/devops-how-to) is an amazing resource to get help, provide help, and learn about what teams are using in their day to day work. If you have had a problem, chances are someone else has had it too. 

The Devhub aims to be a central repository for all things digital in gov. Guides just like this one are being
produced to help teams succeed with their projects.  


## `@bcgov` npm organization

BC Government has a npm organization where open source npm packages are authored and distributed. One of the key packages that has been developed for npm is `bc-sans` (as described above).

Packages that are apart of `@bcgov` can be found [here](https://www.npmjs.com/search?q=%40bcgov).
