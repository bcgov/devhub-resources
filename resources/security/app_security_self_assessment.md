---
title: Application Security Self-Assessment
description: A quick reference of application security-related factors that development teams should consider as the design, build and deploy applications.
---

# Application Security Self-Assessment

This document contains a set of items to think about, questions to ask, tools, and references for conducting a STRA in a BCGov DevOps environment. Based on various Information Security frameworks, the focus is on the system and the practices of the team supporting it and avoids the enterprise policy questions.

## Preparation

Understand:

- Scope and timeline of the assessment
- Criticality of the system

### Asset Management	

- Is there an inventory of:		
    - hosts, platform, and/or system stack?		
    - critical software components and versions?		
    - licenses?		
- Is there a process to keep the inventory up to date?		

### System Design
		
- Is there a Data Flow Diagram or other document describing:		
    - all entities, (servers, services, APIs, end-users and admin)?		
    - all communications between entities (protocols, ports, direction)?		
- Is the design kept up to date?		

### System Implementation
		
- Do firewall rules support the system design?		
- Are all exposures necessary (i.e. no unused services running)?		
- Does a port scan confirm the above (i.e. nmap)?		
- Is TLS configuration sufficient? (e.g. Grade A at https://www.ssllabs.com/ssltest/)?
	
### Access Management
		
- Is there idir/BCeID integration or an exemption otherwise?		
- Are _A accounts used for server admin?		
- Have any default user accounts been removed?		
- Is the process for granting/revoking access documented?		
- Is access control centralized (i.e. Active Directory)?		
- Is the purpose/location of system accounts documented?		
- Do system accounts have the least amount of privilege?		
- Are system passwords/keys well protected?		

### Vulnerability Management		

- Are there vulnerability notifications for all critical software components?		
- Is there testing for each build:		
    - static code analysis (e.g. SonarQube)?		
    - dynamic app testing (e.g. ZAP)?		
    - user testing (e.g. fuzzing, invalid inputs)?		
    - APIs protected/not leaking data?		

### Change Management
		
- Are critical security patches prioritized?		
- Are changes scheduled?		
- Are changes tested? 		
- Are changes/outages communicated:		
    - from service providers (e.g. Hosting)?		
    - to stakeholders?		

### Logging and Monitoring		

- Do logs record an appropriate level of detail for each of the following categoies of events?		
    - Web Access?		
    - Error?		
    - System?		
    - Admin access?		
- Are logs stored external to the system?		
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


