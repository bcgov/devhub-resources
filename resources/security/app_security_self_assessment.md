---
title: Application Security Self-Assessment
description: A quick reference of application security-related factors that development teams should consider as they design, build and deploy applications.
---

# Application Security Self-Assessment

This document contains a set of items to think about, questions to ask, tools, and references for conducting a STRA in a BCGov DevOps environment. Based on various Information Security frameworks, the focus is on the system and the practices of the team supporting it and avoids the enterprise policy questions.

For further detail or questions/answsers please contact your Ministry security team.

## Preparation

Understand:

- Scope and timeline of the assessment
- Criticality of the system
  - consider Confidentiality, Integrity and Availablity requirements
  - consider whether the system is a [Critical System](https://www2.gov.bc.ca/assets/gov/british-columbians-our-governments/services-policies-for-government/information-management-technology/information-security/defensible-security/critical_systems_standard.pdf)

### Asset Management	

- Is there an inventory of:		
    - hosts, platform, and/or system stack?		
    - critical software components and versions?		
    - licenses?		
- Is there a process to keep the inventory up to date?	
- Have you [classified your data](https://intranet.gov.bc.ca/thehub/ocio/ocio-enterprise-services/information-security-branch/advisory-services/information-security-classification-guidelines)?

### System Design
		
- Is there a Data Flow Diagram or other document describing:		
    - all entities, (servers, services, APIs, end-users and admin)?		
    - all communications between entities (protocols, ports, direction)?		
- Is the design kept up to date?		

### System Implementation
		
- Do firewall rules support the system design?	
- Do network security policies (i.e. Aporeto) limit communications between components?
    - Use encrypted communications wherever possible (e.g. between app server component and database component)
- Are all exposures necessary (i.e. no unused services running)?		
- Does a port scan confirm the above (i.e. nmap)?		
- Is TLS configuration sufficient? (e.g. Grade A at https://www.ssllabs.com/ssltest/)?
    - Ensure Entrust certificate used for Prod environments
- Consider encrypting database elements that contain [Protected B/C data](https://www2.gov.bc.ca/gov/content/governments/services-for-government/information-management-technology/information-security/information-security-classification)
	
### Access Management
		
- Is there idir/BCeID integration or an exemption otherwise?
    - follow OAuth2 best practices
- Are _A accounts used for server admin?		
- Have any default user accounts been removed?		
- Is the process for granting/revoking access documented?
    - to include details for clients, ministry staff, devs, admins
- Is access control centralized (i.e. Active Directory)?		
- Is the purpose/location of system accounts documented?		
- Do system accounts have the least amount of privilege?		
- Are system passwords/keys well protected?
    - Ensure secrets are not exposed in GitHub repos or OCP environment variables
    - Utilize Vault* when available

### Vulnerability Management		

- Are there vulnerability notifications for all critical software components?
    - Dependabot alerts (SCA)
- Is there testing for each build:		
    - static code analysis (e.g. SonarQube, SonarCloud)?		
    - dynamic app testing (e.g. ZAP)?
    - review container vulnerability analysis (CVA) (e.g. Aqua/Artifactory Xray)* when available
    - user testing (e.g. fuzzing, invalid inputs)?		
    - APIs protected/not leaking data?		
 - Consider Interactive Application Security Testing (IAST)

### Change Management
		
- Are critical security patches prioritized?		
- Are changes scheduled?		
- Are changes tested? 		
- Are changes/outages communicated:		
    - from service providers (e.g. Hosting)?		
    - to stakeholders?	
 - Do no permit local auth in Prod instances

### Logging and Monitoring		

- Do logs record an appropriate level of detail for each of the following categoies of events?		
    - Web Access?		
    - Error?		
    - System?		
    - Admin access?		
- Are logs stored external to the system?
 - Retention of security logs (e.g. access logs) is minimum 13 months.
- Are logs protected from tampering/deletion?		
- Are there alerts to notify system admins/owners of:		
    - system outages?		
    - performance degradation?		
    - unauthorized access attempts/misuse (e.g. brute force)?		

### Backup and Retention		

- Are there backups for critical data?		
- Are there periodic/recent restore tests?		
- Is data at-rest protected (e.g. encrypted disks)?		
- Business Continuity		
    - Are Recovery Time Objectives defined (e.g. maximum downtime)?		
    - Is there a communication plan for unexpected outages?		
    - Is there a contact list for key staff and alternates?		
    - Are operating manuals/docs sufficient for others to understand?		
    - Have recovery plans been tested?		
