# Incident Response Plan - DRAFT
## Defining an Incident
There are two main types of incidents; Security, and Availability. While the responses for these two types of incidents will have overlapping and similar components, they do need to be addressed separately as there are stricter rigors and greater involvement around Security incidents.

### Availability Incident
An availability incident is an event which causes our app or service to be inaccessible or unusable to our users due to an issue with the app or service itself.  
Examples:  
Not an Incident: A user can not log in because of a forgotten password. The service/app itself is still functioning and usable.  
Incident: A user can not log in because the backend has become unresponsive. The service/app is not functioning properly resulting in it being unavailable to the user.  
Incident: The performance of service/app is extraordinarily slow. The service/app has become so slow that our users can not/will not use the app because of the service degradation. 
* [[ Service Level AOI ]]

### Security Incident
A security incident is an incident in which we have identified a data breach, unauthorized incursion, critical security vulnerability, or other security related threat/vulnerability/thing.  
  
Data Safeguarding and Data Breach Reporting  
The State’s MES projects and operations are subject to federal regulations at 42 CFR Part 431, subpart F, “Safeguarding Information on Applicants and Beneficiaries,” and the Administrative Simplification provisions under the Health Insurance Portability and Accountability Act (HIPAA) requirements as specified in 45 CFR [Part 160](http://www.access.gpo.gov/nara/cfr/waisidx_07/45cfr160_07.html) and [Part 164](http://www.access.gpo.gov/nara/cfr/waisidx_07/45cfr164_07.html). Further, the State is bound by the requirements in section [1902(a)(7) of the Social Security Act](https://legcounsel.house.gov/Comps/Social%20Security%20Act-TITLE%20XIX(Grants%20to%20States%20for%20Medical%20Assistance%20Programs).pdf), which require states to provide safeguards that restrict the use or disclosure of information concerning applicants and beneficiaries to purposes directly connected with the administration of the Medicaid program.

In the event of data breach, the State must immediately report the incident to the CMS IT Service Desk by **email at cms_it_service_desk@cms.hhs.gov**, or call the 24/7 CMS Service Desk phone number: **1-800-562-1963**.

Examples:  
Incident: Secrets are pushed to our GitHub Repository.  
Incident: Sensitive information is available to unauthorized persons, this can be either publicly, or if PII/PHI is available to a person who is authorized to view another state’s PII/PHI, but not the exposed information. **Please help me word this better**  
Incident: A vulnerability is discovered in some piece of our application/stack that allows unauthorized users entrance or to view data.  
  
## Responding to an Incident
* [[ On-Call Policy ]]  
**This will need a decision on an alerting mechanism** 
* [[ Service Level AOI ]]
When a potential incident is reported either via a user or through an alarm/alerting mechanism the on-call person will need to assess the situation. If the on-call confirms an incident they will need to determine what kind of incident and if the incident needs to be addressed immediately or if it can wait for business hours. When the incident is being worked on-call will need to contact an incident commander. The incident commander will then coordinate the response. The Incident Commander are responsible for communicating that there is an incident to stakeholders and contacting anyone necessary to resolve the incident while the responding tech works towards resolution. The incident command will continue to update stakeholders periodically **Needs to be defined** with updates from the responding tech. The Incident Command will also document **Needs to be defined** the start of the incident, the people working on the incident, the resolution of the incident, etc… If it is determined to be a security incident the Security Desk will need to be notified and additional documentation and communication will be required.

## Contact Tree
**This will need to be built out with the names and email addresses of parties that need to be contacted incase of an incident. The incident command will need to be able to use this contact list.**

## Roles During an Incident
### On-call
The role of on-call is to receive and assess the alert and make a determination. On-call can then become the incident commander or the responding tech.

### Incident Commander
The role of the incident commander is to take the communication and coordination responsibilities away from the responding tech. This includes communicating with stakeholders, contacting other people to help resolve the incident, if necessary, and periodically checking in with the responding tech.

### Responding Tech
The role of the responding tech is to resolve the incident. This could be the on-call individual or it could be someone else. The responding tech needs to have the skill set to resolve the incident. Multiple responding techs may be necessary.
