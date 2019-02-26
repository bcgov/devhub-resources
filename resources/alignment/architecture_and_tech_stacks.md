---
title: Application Architecture and Technology Stacks
description: Architecture and Technology Guidance for modern application development in BC Gov. 
---

# Application Architecture and Technology Stacks

- Leverage platform-provided templates/components when possible
    - Already adapted for OpenShift
    - Supported by RedHat (updates, patches, etc.)
    - Integrate with Red Hat security tooling (e.g. OpenSCAP)
- Use "cloud-native"/12factor architectures/principles (https://12factor.net/)
- Leverage/survey community for assistance/opinions on technology choices/approaches 
- Leverage platform’s DevOps pipeline tooling
- Assume continual evolution/improvement of applications on platform
- Recognize shared aspect of platform - some level of uniformity required
- Design applications for resiliency/high availability
- Infrastructure and tooling should sit alongside code (e.g. DeploymentConfigS, BuildConfigS, JenkinsfileS)
- Compose applications from re-usable components and share on GitHub