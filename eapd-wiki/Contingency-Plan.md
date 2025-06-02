# 1.	Introduction

Information systems are vital to {Organization’s} mission/business processes; therefore, it is critical that services provided by {system name} are able to operate effectively without excessive interruption. This Information System Contingency Plan (ISCP) establishes comprehensive procedures to recover
{system name} quickly and effectively following a service disruption.

## 1.1	Background

This {system name} ISCP- establishes procedures to recover {system name} following a disruption. The following recovery plan objectives have been established:
* Maximize the effectiveness of contingency operations through an established plan that consists of the following phases:
o	Activation and Notification phase to activate the plan and determine the extent of damage;
o	Recovery phase to restore {system name} operations; and
o	Reconstitution phase to ensure that {system name} is validated through testing and that normal operations are resumed.
•	Identify the activities, resources, and procedures to carry out {system name} processing requirements during prolonged interruptions to normal operations.
•	Assign responsibilities to designated {organization name} personnel and provide guidance for recovering {system name} during prolonged periods of interruption to normal operations.
•	Ensure coordination with other personnel responsible for {organization name} contingency planning strategies. Ensure coordination with external points of contact and vendors associated with {system name} and execution of this plan.

1.2	Scope

This ISCP has been developed for {system name}, which is classified as a moderate-impact system, in accordance with Federal Information Processing Standards (FIPS) 199 – Standards for Security Categorization of Federal Information and Information Systems. Procedures in this ISCP are for moderate-impact systems and designed to recover {system name} within {RTO hours}. This plan does not address replacement or purchase of new equipment, short-term disruptions lasting less than {RTO hours}, or loss of data at the onsite facility or at the user-desktop levels.

1.3	Assumptions

The following assumptions were used when developing this ISCP:
•	{System name} has been established as a moderate-impact system, in accordance with FIPS 199.
•	Alternate processing sites and offsite storage are required and have been established for this system.
•	Current backups of the system software and data are intact and available at the offsite storage facility in {City, State}.
•	Alternate facilities have been established at {City, State} and are available if needed for relocation of {system name}.
 


•	The {system name} is inoperable at the {organization name} and cannot be recovered within
{RTO hours}.
•	Key {system name} personnel have been identified and trained in their emergency response and recovery roles; they are available to activate the {system name} Contingency Plan.
•	Additional assumptions as appropriate.

The {system name} Contingency Plan does not apply to the following situations:
•	Overall recovery and continuity of mission/business operations.  The Business Continuity Plan (BCP) and Continuity of Operations Plan (COOP) address continuity of business operations.
•	Emergency evacuation of personnel. The Occupant Emergency Plan (OEP) addresses employee evacuation.
•	Any additional constraints and associated plans should be added to this list.

2.	Concept of Operations

The Concept of Operations section provides details about {system name}, an overview of the three phases of the ISCP (Activation and Notification, Recovery, and Reconstitution), and a description of roles and responsibilities of {Organization’s} personnel during a contingency activation.

2.1	System Description

NOTE: Information for this section should be available from the system’s System Security Plan (SSP) and can be copied from the SSP, or reference the applicable section in the SSP and attach the latest version of the SSP to this contingency plan.  Provide a general description of system architecture and functionality.

Indicate the operating environment, physical location, general location of users, and partnerships with external organizations/systems. Include information regarding any other technical considerations that are important for recovery purposes, such as backup procedures.


2.2	Overview of Three Phases

This ISCP has been developed to recover and reconstitute the {system name} using a three-phased approach. This approach ensures that system recovery and reconstitution efforts are performed in a methodical sequence to maximize the effectiveness of the recovery and reconstitution efforts and minimize system outage time due to errors and omissions.

The three system recovery phases are:

Activation and Notification Phase – Activation of the ISCP occurs after a disruption or outage that may reasonably extend beyond the RTO established for a system. The outage event may result in severe damage to the facility that houses the system, severe damage or loss of equipment, or other damage that typically results in long-term loss.

Once the ISCP is activated, system owners and users are notified of a possible long-term outage, and a thorough outage assessment is performed for the system. Information from the outage assessment is presented to system owners and may be used to modify recovery procedures specific to the cause of the outage.
 


Recovery Phase – The Recovery phase details the activities and procedures for recovery of the affected system. Activities and procedures are written at a level that an appropriately skilled technician can recover the system without intimate system knowledge. This phase includes notification and awareness escalation procedures for communication of recovery status to system owners and users.

Reconstitution – The Reconstitution phase defines the actions taken to test and validate system capability and functionality at the original or new permanent location. This phase consists of two major activities: validating successful reconstitution and deactivation of the plan.

During validation, the system is tested and validated as operational prior to returning operation to its normal state. Validation procedures may include functionality or regression testing, concurrent processing, and/or data validation. The system is declared recovered and operational by system owners upon successful completion of validation testing.

Deactivation includes activities to notify users of system operational status. This phase also addresses recovery effort documentation, activity log finalization, incorporation of lessons learned into plan updates, and readying resources for any future events.

2.3	Roles and Responsibilities

The ISCP establishes several roles for {system name} recovery and reconstitution support. Persons or teams assigned ISCP roles have been trained to respond to a contingency event affecting {system name}.

Describe each team and role responsible for executing or supporting system recovery and reconstitution. Include responsibilities for each team/role, leadership roles, and coordination with other recovery and reconstitution teams, as applicable. At a minimum, a role should be established for a system owner or business unit point of contact, a recovery coordinator, and a technical recovery point of contact.

Leadership roles should include an ISCP Director, who has overall management responsibility for the plan, and an ISCP Coordinator, who is responsible to oversee recovery and reconstitution progress, initiate any needed escalations or awareness communications, and establish coordination with other recovery and reconstitution teams as appropriate.

3.	Activation and Notification

The Activation and Notification Phase defines initial actions taken once a {system name} disruption has been detected or appears to be imminent. This phase includes activities to notify recovery personnel, conduct an outage assessment, and activate the ISCP. At the completion of the Activation and Notification Phase, {system name} ISCP staff will be prepared to perform recovery measures to restore system functions.


3.1	Activation Criteria and Procedure

The {system name} ISCP may be activated if one or more of the following criteria are met:
1.	The type of outage indicates {system name} will be down for more than {RTO hours};
2.	The facility housing {system name} is damaged and may not be available within {RTO hours}; and
3.	Other criteria, as appropriate.
 



The following persons or roles may activate the ISCP if one or more of these criteria are met:

Establish one or more roles that may activate the plan based on activation criteria. Authorized persons may include the system or business owner, or the operations point of contact (POC) for system support.

3.2	Notification

The first step upon activation of the {system name} ISCP is notification of appropriate business and system support personnel. Contact information for appropriate POCs is included in {Contact List Appendix name}.

For {system name}, the following method and procedure for notifications are used:

Describe established notification procedures. Notification procedures should include who makes the initial notifications, the sequence in which personnel are notified (e.g., system owner, technical POC, ISCP Coordinator, business unit or user unit POC, and recovery team POC), and the method of notification (e.g., email blast, call tree, automated notification system, etc.).

3.3	Outage Assessment

Following notification, a thorough outage assessment is necessary to determine the extent of the disruption, any damage, and expected recovery time. This outage assessment is conducted by {name of recovery team}. Assessment results are provided to the ISCP Coordinator to assist in the coordination of the recovery of {system name}.

Outline detailed procedures to include how to determine the cause of the outage; identification of potential for additional disruption or damage; assessment of affected physical area(s); and determination of the physical infrastructure status, IS equipment functionality, and inventory.  Procedures should include notation of items that will need to be replaced and estimated time to restore service to normal operations.

4.	Recovery

The Recovery Phase provides formal recovery operations that begin after the ISCP has been activated, outage assessments have been completed (if possible), personnel have been notified, and appropriate teams have been mobilized. Recovery Phase activities focus on implementing recovery strategies to restore system capabilities, repair damage, and resume operational capabilities at the original or an alternate location. At the completion of the Recovery Phase, {system name} will be functional and capable of performing the functions identified in Section 2.1 of this plan.

4.1	Sequence of Recovery Activities

The following activities occur during recovery of {system name}:

Modify the following list as appropriate for the selected system recovery strategy.
1.	Identify recovery location (if not at original location);
2.	Identify required resources to perform recovery procedures;
3.	Retrieve backup and system installation media;
 


4.	Recover hardware and operating system (if required); and
5.	Recover system from backup and system installation media.

4.2	Recovery Procedures

The following procedures are provided for recovery of {system name} at the original or established alternate location. Recovery procedures are outlined per team and should be executed in the sequence presented to maintain an efficient recovery effort.

Provide general procedures for the recovery of the system from backup media. Specific keystroke-level procedures may be provided in an appendix. If specific procedures are provided in an appendix, a reference to that appendix should be included in this section. Teams or persons responsible for each procedure should be identified.

4.3	Recovery Escalation Notices/Awareness

Provide appropriate procedures for escalation notices during recovery efforts. Notifications during recovery include problem escalation to leadership and status awareness to system owners and users. Teams or persons responsible for each escalation/awareness procedure should be identified.

5.	Reconstitution

Reconstitution is the process by which recovery activities are completed and normal system operations are resumed. If the original facility is unrecoverable, the activities in this phase can also be applied to preparing a new permanent location to support system processing requirements. A determination must be made on whether the system has undergone significant change and will require reassessment and reauthorization. The phase consists of two major activities: validating successful reconstitution and deactivation of the plan.

5.1	Validation Data Testing

Validation data testing is the process of testing and validating data to ensure that data files or databases have been recovered completely at the permanent location. The following procedures will be used to determine that the data is complete and current to the last available backup:

Provide procedures for testing and validation of data to ensure that data is correct and up to date. This section may be combined with the Functionality Testing section if procedures test both the functionality and data validity. Teams or persons responsible for each procedure should be identified. An example of a validation data test for a moderate-impact system would be to compare a database audit log to the recovered database to make sure all transactions were properly updated. Detailed data test procedures may be provided in Appendix E, System Validation Test Plan.

5.2	Validation Functionality Testing

Validation functionality testing is the process of verifying that recovered {system name} functionality has been tested, and the system is ready to return to normal operations.

Provide system functionality testing and/or validation procedures to ensure that the system is operating correctly. This section may be combined with the Data Testing section if procedures test both the functionality and data validity.  Teams or persons responsible for each procedure should be identified. An example of a functional test for a moderate-impact system may be logging into the system and running
 


a series of operations as a test or real user to ensure that all parts of the system are operating correctly. Detailed functionality test procedures may be provided in Appendix E, System Validation Test Plan.

5.3	Recovery Declaration

Upon successfully completing testing and validation, the {designated authority} will formally declare recovery efforts complete, and that {system name} is in normal operations. {System name} business and technical POCs will be notified of the declaration by the ISCP Coordinator.

5.4	Notifications (users)

Upon return to normal system operations, {system name} users will be notified by {role} using
predetermined notification procedures (e.g., email, broadcast message, phone calls, etc.).

5.5	Cleanup

Cleanup is the process of cleaning up or dismantling any temporary recovery locations, restocking supplies used, returning manuals or other documentation to their original locations, and readying the system for a possible future contingency event.

Provide any specific cleanup procedures for the system, including preferred locations for manuals and documents and returning backup or installation media to its original location.

5.6	Offsite Data Storage

It is important that all backup and installation media used during recovery be returned to the offsite data storage location. The following procedures should be followed to return backup and installation media to its offsite data storage location.

Provide procedures for returning retrieved backup or installation media to its offsite data storage location. This may include proper logging and packaging of backup and installation media, preparing for transportation, and validating that media is securely stored at the offsite location.

5.7	Data Backup

As soon as reasonable following recovery, the system should be fully backed up and a new copy of the current operational system stored for future recovery efforts. This full backup is then kept with other system backups.  The procedures for conducting a full system backup are:

Provide appropriate procedures for ensuring that a full system backup is conducted within a reasonable time frame, ideally at the next scheduled backup period. This backup should go offsite with the other media in Section 5.6.

5.8	Event Documentation

It is important that all recovery events be well-documented, including actions taken and problems encountered during the recovery and reconstitution effort, and lessons learned for inclusion and update to this ISCP. It is the responsibility of each ISCP team or person to document their actions during the recovery and reconstitution effort and to provide that documentation to the ISCP Coordinator.
 


Provide details about the types of information each ISCP team member is required to provide or collect for updating the ISCP with lessons learned. Types of documentation that should be generated and collected after a contingency activation include:
•	Activity logs (including recovery steps performed and by whom, the time the steps were initiated and completed, and any problems or concerns encountered while executing activities);
•	Functionality and data testing results;
•	Lessons learned documentation; and
•	After Action Report.

Event documentation procedures should detail responsibilities for development, collection, approval, and maintenance.

5.9	Deactivation

Once all activities have been completed and documentation has been updated, the {designated authority} will formally deactivate the ISCP recovery and reconstitution effort. Notification of this declaration will be provided to all business and technical POCs.