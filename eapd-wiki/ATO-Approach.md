# ATO Approach
As a core function of the MACPro suite, the eAPD system will serve as a singular, streamlined portal for state, federal, and associated partners to develop, review, track, analyze, and share APD, contract submissions, and data to improve accountability and outcomes associated with the State’s Medicaid business needs. 

Since eAPD functions as part of MACPro, we will be leveraging the MACPro Authority to Operate (ATO), by adding our documentation to theirs. However, because we do have some differences, we are still producing artifacts as a part of the [CMS eXpedited Life Cycle](https://www.cms.gov/research-statistics-data-and-systems/cms-information-technology/xlc/index.html). 

In order for us to go live with the eAPD pilot we must achieve the following criteria:
- [x] Pilot scope identified, allowing a 508 exception for the duration of the pilot
- [ ] Security controls identified and mapped to MACPro's SSP
- [ ] Information Security & Privacy Group (ISPG) acceptance of eAPD as an addendum to MACPro's SSP
- [x] 508 accessibility requirements exempted during pilot - concurrently working with the 508 testing team for go-live
- [ ] CMCS Director and Group Director sign-off on eAPD pilot

***

As a core function of the MACPro suite, we are looking to conduct a pilot of the eAPD. The pilot will be limited in scale (approximately 4 state users) and limited in term (duration of the CMCS APD review process). Concurrently with the pilot, the development team will pursue 508 testing/approval in preparation for scaling the application to additional users for production release, including the completion of the VPAT and the CMS 508 testing plan.

To address the 508/accessibility requirements associated with the eAPD, we are conforming to WCAG 2.0 standards, and our accessibility approach is document the requirements, guidelines, validation, and exemptions based on the [WCAG 2.0 Standard CodedSniffer](http://squizlabs.github.io/HTML_CodeSniffer/Standards/WCAG2/). Additionally, as part of our technical architecture, [[we have several tools to test for accessibility violations during development.|Development accessibility, testing, and linting#accessibility]]

## _WCAG 2.0 Guidelines Table not yet completed:_

[table snapshot to be inserted here]

***

To address and identify the security controls associated with eAPD, we are reviewing all security controls and mapping them from MACPro to eAPD. Doing so will provide us a specific breakdown of the 348 MACPro security controls, and eAPD's consistency or difference in approach. The table below will be used do present the mapping of security controls results:

## _Security Control Table not yet completed:_

| Security Control                    | Code | # MACPro Codes | # eAPD Codes Appear to be consistent w/MACPro | #eAPD Controls to be further evaluated | #eAPD Controls differ from MACPro | % Consistent | %TBD |
|-------------------------------------|------|----------------|-----------------------------------------------|----------------------------------------|-----------------------------------|--------------|------|
| Access Control                      | AC   | 38             | 20                                            | 17                                     | 0                                 | 53%          | 45%  |
| Authority & Purpose                 | AP   | 1              | 1                                             | 0                                      | 0                                 | 100%         | 0%   |
| Governance & Privacy                | AR   | 5              | 4                                             | 0                                      | 1                                 | 80%          | 0%   |
| Security Awareness & Training       | AT   | 5              | 0                                             | 4                                      | 0                                 | 0%           | 80%  |
| Audit & Accountability              | AU   | 26             | 22                                            | 0                                      | 0                                 | 85%          | 0%   |
| Security Assessment & Authorization | CA   | 13             | 5                                             | 0                                      | 0                                 | 38%          | 0%   |
| Configuration Management            | CM   | 27             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Contingency Plan                    | CP   | 25             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Data Quality and Integrity          | DI   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Data Minimization and Retention     | DM   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Identification & Authentication     | IA   | 24             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Individual Participation            | IP   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Incident Response                   | IR   | 17             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| System Maintenance                  | MA   | 11             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Media Protection                    | MP   | 12             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Physical & Environmental Protection | PE   | 21             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Security Planning                   | PL   | 6              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Information Security Program Plan   | PM   | 16             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Personal Security                   | PS   | 8              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Risk Assessment                     | RA   | 8              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| System & Services Acquisition       | SA   | 20             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| System & Communications Protection  | SC   | 30             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Security Control                    | SE   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| System and Information Integrity    | SI   | 28             | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Transparency Control                | TR   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
| Use Limitation Control              | UL   | 1              | 0                                             | 0                                      | 0                                 | 0%           | 0%   |
|                                     |      |                |                                               |                                        |                                   |              |      |
| Total                               |      | 347            | 52                                            | 21                                     | 1                                 | 15%          | 6%   |