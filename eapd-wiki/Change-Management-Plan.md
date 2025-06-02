# Configuration Management (CM) Plan

## 1.	Introduction
This Configuration Management (CM) Plan establishes the technical and administrative direction and surveillance for the management of configuration items (i.e., software, hardware, and documentation) associated with the electronic Advanced Planning Document (eAPD) system that are to be placed under configuration control.  This document defines the project’s structure and methods for:
* Identifying, defining, and baselining configuration items (CIs);
* Controlling modifications and releases of CIs;
* Reporting and recording status of CIs and any requested modifications;
* Ensuring completeness, consistency, and correctness of CIs; and
* Controlling storage, handling, and delivery of CIs.
As the project matures, appropriate sections of this plan will be updated.

## 2.	Assumptions / Constraints / Risks
### 2.1	Assumptions
The following assumptions apply to the CM plan:
* The Version Description Document (VDD) will be used to manage the COTS version baseline.
* AWS AIM will be used to maintain Virtual Private Cloud (VPC) system images.
* The eAPD baseline will be reviewed and updated annually, or more frequently as CIs are added or changed.
### 2.2	Constraints
The following constraints apply to eAPD configuration management:
* eAPD runs in the CM AWS environment. Accordingly, eAPD infrastructure configuration management will be managed by the CMS AWS contractor. (Currently GDIT.)
### 2.3	Risks
The following risks are relevant to eAPD Configuration Management:
* Because eAPD runs in the AWS VPC environment, if infrastructure changes are made to the AWS VPC environment without eAPD management team impact assessment involvement, there may be unexpected system impact to eAPD. 
 
## 3.	Configuration Management Approach
### 3.1	Methods & Tools
The approach for eAPD CM consists of identifying, controlling, statusing, and auditing all changes throughout the system life cycle. The major CM processes include the following:
* CM Planning: The planning, monitoring, and reporting of CM processes and their results, including the resolution of discovered issues;
* Configuration Identification:  The identification of the functional and physical characteristics of system configurations and their appropriate baseline assignments;
* Configuration and Baseline Control:  The evaluation, coordination, approval or disapproval, and implementation of changes to the agreed-upon baselines; and
* Configuration Auditing:  The verification of system configurations to ensure that NSD personnel supporting NCPS follow CM policies consistently and document configura-tions accurately.
The eAPD CM Manager shall facilitate and manage the implementation of these CM processes across all CI changes to ensure the integrity of the CIs and baselines.  The eAPD CM Manager shall work with eAPD stakeholders to plan and acquire required CM resources to implement these CM processes effectively. 
End users cannot install software on any eAPD system. Administrators can install any software on any eAPD system only as necessary. Administrators should only install software when creating new machine images. After a machine image is created, any machine using that image should not have any additional software installed except in the case of emergency security hotfixes.

Security Changes:  All changes to eAPD security functions require a review, testing, and verification. When changes to the system occur, record the installation of information system components in the appropriate system documentation resource(s) (as applicable). Systems’ testing is conducted and, provided everything passes, a snapshot of all code is taken (of the revision) and released to the Production environment.

### 3.2	Roles & Responsibilities

Table 1: Roles and Responsibilities
Role 	Name	Responsibility
eAPD Configuration Manager	TBD
* Facilitate and manage the implementation of these CM processes across all CI changes to ensure the integrity of the CIs and baselines
* Work with eAPD stakeholders to plan and acquire required CM resources to implement these CM processes effectivel
Release Manager	TBD (AWS Maintenance Contractor)
* Manages deployment of system updates to Production Environment
eAPD Change Control Board TBD
* Provides approved changes to be implemented in eAPD Baseline

### 3.3	Environment
eAPD has three tiers of environments: development, test/preproduction, and production. Promoting the system from dev to test/preproduction environments requires code to have passed significant gate reviews, per the Technical Review Board (TRB) guidelines. To promote code from test/preproduction to production, the syste components must undergo all required testing and gate reviews.  The Release Manager creates a ticket for promoting eAPD from the JIRA ticketing system and subsequently receives the approval of the eAPD Configuration Manager. In addition, the Release Manager will get additional sign-off in JIRA from one of the CMCS people in charge of eAPD as well as sign-off in JIRA from the independent verification and validation testers.

In order to keep each new deployment and code promotion small and self-contained, eAPD has a quick, streamlined release and configuration management process. During high priority deadlines, this might result in multiple deployments per week. 

In general, eAPD attempts to deploy once per week.
Anyone responsible new releases should be familiar with the configuration management policies and procedures.

## 4.	Configuration Management Administration
### 4.1	Configuration Identification
The eAPD Configuration Items (CIs) include:
* System Requirements Documentation
* System Design Documentation
* System Operations and Maintenance Documentation
* COTS products
* Custom Code

### 4.2	Naming Standard
The naming standards for eAPD components will be managed by the following:
* COTS products will retain vendor naming standards
* eAPD system release will be based on X.0 where X designates a new release and X.y, where y designates a ew sprints
* Hardware and network CIs will follow CMS AWS naming standards.

### 4.3	Baselines
The three configuration baselines maintained for eAPD are:
* Functional Baseline (FBL):  The eAPD FBL defines what functions the system must perform (i.e., the functional requirements), not how it will perform the functions.  The FBL includes the following types of CIs:
  * Functional Requirements (eAPD Requirements Document)
  * Security Requirements (eAPD Requirements Document, eAPD System Security Classification)
  * High Level Architecture with System Interfaces (Interface Control Document)

* Allocated Baseline (ABL): The eAPD ABL defines the architecture and design of the physical system by allocating system functions in the FBL to their corresponding design elements. The ABL consists of the list of CIs that comprise the physical system as well as their interrelationships and primary interfaces. The ABL defines the requirements allocated to each CI and, as such, defines the top-level design of the system. The ABL includes the following types of CIs:
  * System design artifacts (eAPD System Design Document)
  * Logical data model (eAPD Logical Data Model, eAPD Data Definitions)
  * Security Artifacts (eAPD System Security Plan)
  * System interface requirements (e.g., LDAP, Okta)

* Product Baseline (PBL):  The eAPD PBL consists of the developed system and all its related CIs.  The PBL includes the following types of CIs:
  * COTS products 
  * Data models such as Physical Data Models (PDMs) 
  * Security artifacts, such as System Security Plan, ISRA 
  * Test artifacts such as test plans, test cases/procedures, Section 508 Assessment Package, and test results 
### 4.4	Storage & Retention
The eAPD baseline configurations are stored in the configs directory in the version control system.
* eAPD baseline configurations are stored in the configuration directory in the version control system (currently identified as GitHub.)
* AMI configuration is stored in configs/packer.
* AWS infrastructure configuration is stored in configs/aws.
* Additional application-specific configuration is stored in the relevant application directory. 
This eAPD CM Plan provides the details necessary to implement and ensure compliance with the requirements of the CMS SDLC Framework guidelines. The AWS Maintenance Contractor maintains baselines for infrastructure systems, devices, and appliances.
### 4.5	Configuration Control
The eAPD CM Plan defines the approach, administrative procedures, roles and responsibilities for submitting, evaluating, coordinating, approving or disapproving business and technical changes to baselined Configuration Items (CI) for the eAPD system. Upon approval by the eAPD Change Control Board, changes will go through the CMS XLC process to be tested and deployed to production. The eAPD CM will oversee the monitoring of all approved changes from the time they have been approved and through the process to deployment to production. The CIs will be placed under configuration control upon approval to be transitioned to the Test/Preproduction environment.

Additionally, the eAPD VDDs serve to establish baseline configurations. Changes to the configuration of the information system are reviewed by the Change Review Board are approved by the Enterprise CCB.  Historical reviews and all historical configuration changes are maintained indefinitely, so eAPD will retain records.  Configuration controlled changes are audited annually.
### 4.6	Configuration Integrity
Changes to the information system are managed to ensure configuration integrity. When changes to the system occur, a record of the change to of eAPD CIs is maintained in the VDD and CCB form/Board minutes (as applicable).
eAPD ensures that all code and configuration changes receive a review by someone other than the developer to uncover a baseline of issues. In addition to that, any security-relevant changes will have an additional security review.
### 4.7	Configuration Audits
 
An annual configuration audit will be conducted. Both a functional configuration audit (FCA) and product configuration audit (PCA) will be performed. The FCA will be conducted annually (once every 365 days) to verify that the CIs of the baselined system continue to meet the  functionality and performance characteristics consistent with the eAPD system requirements. The PCA will be conducted annually (once every 365 days) to ensure that the CM system captures the product baseline that has been deployed to the production environment.
