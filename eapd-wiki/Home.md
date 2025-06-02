Welcome to the Electronic Advanced Planning Document (eAPD) wiki! This is where we keep our product, design, and development documentation.

## Vision and Goals

As a core function of the MACPro suite, the eAPD system will serve as a singular, streamlined portal for state, federal, and associated partners to develop, review, track, analyze, and share APD, contract submissions, and data to improve accountability and outcomes associated with the State’s Medicaid business needs. The system will be developed and maintained through continuous integration/continuous delivery methods with a loosely coupled architecture connected by Application Programming Interfaces (APIs).

## Background

18F partnered with the Centers for Medicare & Medicaid Services (CMS) to develop an app that helps states submit APDs easily, and helps CMS analysts review APDs more efficiently. As part of this effort, we’re interviewing state users and CMS analysts, developing prototypes, and testing our assumptions in usability sessions. In 2020, 18F transitioned their efforts to a new team who has brought their expertise to keep the vision of the project alive and moving forward while building on the foundation of Human Centered Design that it a core part of the culture of the eAPD.

The HITECH program is funding through the ARRA and was designed as a stimulus program to support the advancement of the Health Information Technology (HIT) by incentivizing the adoption and meaningful use of Certified Electronic Health Record technologies (EHR) for Medicaid Eligible Providers. The program is an opt-in program, managed by the State’s Medicaid agency and governed by regulations found in 42 CFR 495, Part D.

Under this regulation, States are required to submit three categories of documents to qualify for enhanced Federal Financial Participation (FFP): The State Medicaid Health Information Technology Plan (SMHP), the Advanced Planning Document (APD) and procurements supporting the Promoting Interoperability Program, formerly known as the EHR Incentive program.

The Advanced Planning Document (APD) is the primary vehicle for States to request funding for the HITECH program and is used across many different agencies within the Federal government. While the SMHP paints a picture of where the state is and where they are going, the HITECH APD provides insight into who, what, when, where, how and how much the State needs to accomplish their goals described within their SMHP. The APD reiterates the State’s HIT goals and objectives, and provides insight into a 1-2 year plan on how the State will move their plan forward through a programmatic, regulatory and financial lens.

A decision from CMS generally occurs through the cyclical process of:  
1. Request
2. Review and Decision
3. Response

This process is primarily managed through email and electronic versions of the paper templates and while the HITECH program has provided very specific guidance on how to fill out the templates, the consistency of the State’s submission are not aligned with CMS’ guidance – this is oftentimes related to State’s using the documents beyond its intended purpose and is dependent on the experience of the author to develop a well formed submission. Likewise, as the APD has annual update requirements, the documents are often reused to include not only new additions, but the history of previous activities as well, often creating an unnecessarily long or complicated document.

## Success and KPIs

Project Mission
* Support a production application that assists and improves the way states creates, updates and submits APDs (and any associated contracts) to CMS.
* Build and continuously refine the application that assists and improves the way analysts review, comment on, and process APDs and associated contracts.
* Build and continuously refine the application which exposes operational details for work in progress and work completed to CMS.
* Build and continuously refine the eAPD to assure APDs (and any associated contracts) are in compliance with Federal regulations.
* Build and continuously refine the eAPD to report key operational and financial metrics.


Key Performance Indicators
* Adoption, Utilization and Retention
  * Number of states using the system to submit
  * Number of states which complete a second submission within the system.
  * Number of states that access the system
  * Page views
* Submissions
  * Aggregate submission data
  * Number of APD approvals
  * Number of contract approvals
  * Number of first and second cycle approvals
* Review Details
  * Process time
  * Federal review times
  * State response times
  * Number of first cycle comments
  * Number of second cycle comments

## Guidelines for the Wiki

This wiki is a place for...
* Information regarding how this project operates
* Documentation necessary to comply with CMS' [Target Life Cycle (TLC)](https://www.cms.gov/Research-Statistics-Data-and-Systems/CMS-Information-Technology/TLC) process (excluding security related documentation)
 
This wiki is not a place for...
* Any Personally Identifiable Information (PII)
* Any information about or from specific states
* Any security or privacy related documentation
