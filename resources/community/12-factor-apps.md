---
resourceType: Documentation
personas:
  - Developer
  - Product Owner
tags:
  - Cloud
  - Cloud Native
description: 'A guide that compiles some best practices for developing cloud native applications.'
---

## 12 Factor Apps

Web application design and architecture has undergone drastic changes in the past decade. With the ubiquity of an '*app for every type of service*',
how apps are built has evolved to meet modern requirements. There is an excellent guideline on designing apps in such a way that meets these
demands and provides robustness for future support and developement. This guideline is called **The 12 Factor App**.

> A **12 Factor App**
>- Uses declarative formats for setup automation, to minimize time and cost for new developers joining the project;
>- Has a clean contract with the underlying operating system, offering maximum portability between execution environments;
>- Is suitable for deployment on modern cloud platforms, obviating the need for servers and systems administration;
>- Minimizes divergence between development and production, enabling continuous deployment for maximum agility;
>- scales without significant changes to tooling, architecture, or development practices.
> *https://12factor.net/*

We recommend reading through the guidelines layed out at https://12factor.net/. You may find some of the 'factors' are fairly
common sense while others will (hopefully) become an *aha!* moment
