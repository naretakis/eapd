## Admin Check Overview

The Admin Check works by running the joi validations on the backend and returning a pre-arranged array of objects to the frontend. The Admin check is run on every newly created APD as well as subsequent APD updates so it always represents the current state of invalid items. In addition to joi schema-based validations we also do some manual validations. Ideally we would like to remove the manual validations.

### adminCheck.js

Within `api/util/adminCheck.js` refer to each functions inline documentations but at a high level here are the main ones to note:
* `adminCheckApd` - This is the "main" function that is called to validate an apd. With the introduction of MMIS type apds we have split out into checking validations based on the type. 
* `adminCheck<TYPE>Apd` - This handles getting any of the required data to do the validations and combining any manual validations and the joi/schema-based validations into a single array before sending the validation results to be re-arranged into an array of objects the frontend can digest for display.
* `getManual<TYPE>Validations` - For HITECH we needed to do a validation that joi schema validation didn't support.
* `buildErrorList` - This function takes an array of error validations and creates a new array from it for the front end to display

### Gotchas
* In the case of `apdOverview` it's required to know data outside of the object it's validating against- the `fundingSource`. For this case we manually look it up and pass it in, but ideally this would be refactored to not have this requirement.
* There are some validations we have to do manually. Would be nice to find a way to do it with the schemas instead.
* The order of the resulting array is not sorted. Initially the order of the data being validated followed the order of the app/navigation structure. This has since grown and now some items appear out of order.

### Additional Notes
* Joi is used for both frontend and backend validation
* Using yarn workspaces we share the schemas for easy management. See `@eapd/common`
* Subforms have their own in-line validation so they're not included in the admin check


### Example array of errors sent to the frontend

```
adminCheck: adminCheck: {
      errors: [
        {
          section: 'Activity 1 State Staff and Expenses',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/state-costs',
          fieldDescription: 'Provide a description of the selected non-personal category.'
        },
        {
          section: 'Activity 1 State Staff and Expenses',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/state-costs',
          fieldDescription: 'Provide a description of the selected non-personal category.'
        },
        {
          section: 'Activity 1 State Staff and Expenses',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/state-costs',
          fieldDescription: 'Provide a description of the selected non-personal category.'
        },
        {
          section: 'Activity 1 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/contractor-costs',
          fieldDescription: 'Provide a start date.'
        },
        {
          section: 'Activity 1 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/contractor-costs',
          fieldDescription: 'Provide an end date.'
        },
        {
          section: 'Activity 1 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/contractor-costs',
          fieldDescription: 'Provide a start date.'
        },
        {
          section: 'Activity 1 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/0/contractor-costs',
          fieldDescription: 'Provide an end date.'
        },
        {
          section: 'Activity 2 State Staff and Expenses',
          link: '/apd/6440250a2a8b080090a4d65b/activity/1/state-costs',
          fieldDescription: 'Provide a description of the selected non-personal category.'
        },
        {
          section: 'Activity 2 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/1/contractor-costs',
          fieldDescription: 'Provide a start date.'
        },
        {
          section: 'Activity 2 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/1/contractor-costs',
          fieldDescription: 'Provide an end date.'
        },
        {
          section: 'Activity 2 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/1/contractor-costs',
          fieldDescription: 'Provide a start date.'
        },
        {
          section: 'Activity 2 Private Contractor Costs',
          link: '/apd/6440250a2a8b080090a4d65b/activity/1/contractor-costs',
          fieldDescription: 'Provide an end date.'
        },
        {
          section: 'Security Planning',
          link: '/apd/6440250a2a8b080090a4d65b/security-planning',
          fieldDescription: 'Provide Security and Interface Plan'
        },
        {
          section: 'Security Planning',
          link: '/apd/6440250a2a8b080090a4d65b/security-planning',
          fieldDescription: 'Provide Business Continuity and Disaster Recovery'
        },
        {
          section: 'Assurances and Compliance',
          link: '/apd/6440250a2a8b080090a4d65b/assurances-and-compliance',
          fieldDescription: 'Select yes or no'
        }
      ]
```


## HITECH Front-end APD Structure 
This is the original structure of the app/navigation that the validation list would match. Since introducing MMIS there has been some drift and this is no longer up to date.
```
APD
.
├── APD Overview
│   ├── APD Name <String>
│   ├── Federal Fiscal Years <String>
│   ├── Introduction (programOverview) <String>
│   ├── HIT Overview (narrativeHIT) <String>
│   ├── HIE Overview (narrativeHIE) <String>
│   └── MMIS Overview (narrativeMMIS) <String>
├── Key State Personnel
│   ├── Medicaid Director
│   │   ├── Name <String>
│   │   ├── Email <String>
│   │   └── Phone <String>
│   ├── Medicaid Office
│   │   ├── Address1 <String>
│   │   ├── Address2 <String>
│   │   ├── City <String>
│   │   ├── State <String>
│   │   └── Zip <String>
│   ├── Primary Point of Contact (Subform) <Array>
│   └── Additional Key Personnel (Subform/Optional) <Array>
├── Results of Previous Activities
│   ├── Previous Activities Summary <String>
│   └── Actual Expenditures
│       ├── HIT + HIE Federal share 90% FFP (Table) <Number>
│       ├── MMIS Federal share 90% FFP (Table) <Number>
│       ├── MMIS Federal share 75% FFP (Table) <Number>
│       └── MMIS Federal share 50% FFP (Table) <Number>
├── Activities <Array>
│   ├── Activity 1 - Program Administration (HIT)
│   │   ├── Activity Overview
│   │   │   ├── Provide a short overview of the activity (Summary) <String>
│   │   │   ├── Start Date <Date>
│   │   │   ├── End Date <Date>
│   │   │   ├── Include as much detail as is necessary to explain the activity (Description) <String>
│   │   │   ├── Statement of alternative considerations and supporting justification <String>
│   │   │   └── Standards and Conditions <String>
│   │   ├── Outcomes and Milestones
│   │   │   ├── Outcomes (Subform) <Array>
│   │   │   └── Milestones (Subform) <Array>
│   │   ├── State Staff and Expenses
│   │   │   ├── State Staff (Subform) <Array>
│   │   │   └── Other Expenses (Subform) <Array>
│   │   ├── Private Contractor Costs
│   │   │   └── Private Contractors (Subform) <Array>
│   │   ├── Cost Allocation and Other Funding
│   │   │   ├── Description of Cost Allocation Methodology <String>
│   │   │   ├── Other Funding Description (Per year) <String>
│   │   │   └── Other Funding Amount (Per year) <Number>
│   │   └── Budget and FFP
│   │       ├── Federal-State Split (Per year) <Map>
│   │       └── Estimated Quarterly Expenditure (Per year) <Map>
│   └── Activity 2-* (User added)
│       ├── Activity Overview
│       │   ├── Activity name <String>
│       │   ├── Program type <String>
│       │   ├── Provide a short overview of the activity (Summary) <String>
│       │   ├── Start Date <Date>
│       │   ├── End Date <Date>
│       │   ├── Include as much detail as is necessary to explain the activity (Description) <String>
│       │   ├── Statement of alternative considerations and supporting justification <String>
│       │   └── Standards and Conditions <String>
│       ├── Outcomes and Milestones
│       │   ├── Outcomes (Subform) <Array>
│       │   └── Milestones (Subform) <Array>
│       ├── State Staff and Expenses
│       │   ├── State Staff (Subform) <Array>
│       │   └── Other Expenses (Subform) <Array>
│       ├── Private Contractor Costs
│       │   └── Private Contractors (Subform) <Array>
│       ├── Cost Allocation and Other Funding
│       │   ├── Description of Cost Allocation Methodology <String>
│       │   ├── Other Funding Description (Per year) <String>
│       │   └── Other Funding Amount (Per year) <Number>
│       └── Budget and FFP
│           ├── Federal-State Split (Per year) <Map>
│           └── Estimated Quarterly Expenditure (Per year) <Map>
├── Activity Schedule Summary (No inputs in this section)
├── Proposed Budget
│   ├── Summary Budget by Activity (No inputs)
│   ├── Summary Budget Table (No inputs)
│   ├── Quarterly Federal Share (No inputs)
│   └── Estimated Quarterly Incentive Payments <Map>
└── Assurances and Compliance
    ├── Procurement Standards
    │   ├── Are you complying with 42 CFR Part 495.348? <Boolean>
    │   ├── Are you complying with SMM Section 11267? <Boolean>
    │   ├── Are you complying with 45 CFR 95.613? <Boolean>
    │   └── Are you complying with 45 CFR 75.326? <Boolean>
    ├── Access to Records, Reporting and Agency Attestations
    │   ├── Are you complying with 42 CFR Part 495.350? <Boolean>
    │   ├── Are you complying with 42 CFR Part 495.352? <Boolean>
    │   ├── Are you complying with 42 CFR Part 495.346? <Boolean>
    │   ├── Are you complying with 42 CFR 433.112(b)? <Boolean>
    │   ├── Are you complying with 45 CFR Part 95.615? <Boolean>
    │   └── Are you complying with SMM Section 11267? <Boolean>
    ├── Software & Ownership Rights, Federal Licenses, Information Safeguarding, HIPAA Compliance, and Progress Reports
    │   ├── Are you complying with 42 CFR 495.360? <Boolean>
    │   ├── Are you complying with 45 CFR 95.617? <Boolean>
    │   ├── Are you complying with 42 CFR Part 431.300? <Boolean>
    │   └── Are you complying with 42 CFR Part 433.112? <Boolean>
    └── Security and Interface Requirements to Be Employed for All State HIT Systems
        └── Are you complying with 45 CFR 164 Security and Privacy? <Boolean>
```