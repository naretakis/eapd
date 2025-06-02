# Medicaid Enterprise Systems (MES) Testing Guidance Framework 

Comprehensive and thorough testing of enterprise software throughout the IT investment life cycle leads to higher quality software products and higher user satisfaction. CMS expects the state to 
effectively test your applications and services to help you identify and resolve IT issues early. By detecting system problems early, the cost of redoing software and late in the development cycle, improving overall quality provides system and user satisfaction.

Within this document lists a set of test expectations and recommendations, defined as:
* Expectations explain actions and consequences that the state must demonstrate, and / or provide it as proof.
* Recommendations identify industry best practices that have proven to improve efficiency and product quality. The CMS encourages states to adopt and follow these recommendations, improve the quality of MES implementations and mitigate risk.

Expectations are three main project phases (test planning, test execution, and Operational monitoring).

* Testing planning begins with the capture process by incorporating the expectations of the test into the request to go further into the early stages of project planning to organize Request for Proposal (RFPs) and contracts, and those test procedures. The specifications of the test requirements in the contract are the role of states and providers in the testing process.
* Regardless of the software development methodology used (e.g., agile, waterfall), the type of system (e.g., custom development, COTS, SaaS), or the responsibilities of the state and vendor, the state is ultimately responsible for ensuring that robust testing has been performed and the delivered system is of high quality.
* Once a system goes into production, operational monitoring tracks the system “health” on an ongoing basis. 

# eAPD Testing Framework

## Unit Testing
Unit testing is important for testing out the functionality of individual components. Unit tests isolate a component and make sure the component is working individually before we implement it into eAPD. A good unit test has 100% code coverage, meaning that 100% of the code is touched during the tests.  For our unit tests we use a combination of:
* [Jest](https://jestjs.io/)
* [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
* Enzyme (Legacy code, we plan to migrate from Enzyme tests to React Testing Library)
* [Stryker](https://testing-library.com/docs/react-testing-library/intro/) (mutation testing, helps with covering edge cases)
* [Cypress](https://www.cypress.io/) (Future implementation, Cypress 10 announced component testing which is still in beta)

## Integration Testing
Integration testing is an essential part of our CI/CD pipeline. It’s essentially a “happy pass” of the features within eAPD. These tests make sure the intended functionality of each and every component of the application hasn't changed. This gives our developers confidence that the work they are merging does not have any unintended consequences elsewhere. For end-to-end integration testing we use Cypress.

## Visual Regression Testing
Visual regression testing is another form of automated testing. It covers aspects that cannot be checked during integration testing, the visuals. Every single change, no matter how small, is documented and easily reviewed by any team member. This is a powerful tool as it can catch any and all unintended visual changes as we continuously integrate to eAPD. The tool we use for this type of  testing is [Chromatic](https://www.chromatic.com/). Features of Chromatic include: 
* Pinpoint UI bugs instantly with visual checks down to the pixel. 
* Fully linked with our CI/CD pipeline. Meaning these tests are run whenever work is shipped.
* Capture rendered UI. Just like Cypress, Chromatic not only finds visual bugs, but shows you what changed and the code that changed it. 
* Consistency across browsers. Ability to test on Internet Explorer, Chrome, and Firefox simultaneously.  

## Accessibility Testing
eAPD is [508 compliant](https://www.section508.gov/) which aligns with [WCAG AA requirements](https://www.w3.org/TR/WCAG21/). Our QA engineers are responsible for testing all accessibility features such as tab navigation, intended screen reader functionality, UI adaptability to zoom/different screen sizes, and text scaling. We have future plans of implementing [The A11y Project](https://www.a11yproject.com/), a community driven philosophy that’s dedicated themselves to accessibility testing. This would most definitely help strengthen our accessibility tests. 

## CI/CD (continuous integration/continuous delivery)
All of the testing techniques listed above have been incorporated within our CI/CD pipeline. All these tests are run and must pass before any feature can be merged into eAPD. 

## Manual Testing
Along with manual acceptability testing, QA is also expected to manually test the intended functionality of each piece of work before it gets shipped. Once manual testing passes and all other automated tests pass, the final step in our QC process is the final sign off from our product/design team. This ensures that all eyes are on a piece of work before it fully gets merged in. 

## Measuring Testing Metrics
For measuring testing metrics, we use code coverage to get an idea about how much of our code is covered in tests. We use [CodeCov](https://about.codecov.io/) for the feature and are striving for a 90% code coverage across the whole application. 

## Security
We use a wide variety of software to help upkeep security within eAPD. The software we use is:
* [Snyk](https://snyk.io/): Keeps up to date with all of our developer dependencies and makes sure there are no vulnerabilities within them.
* AWS Security Hub - This looks at our AWS resources and scans them for violations against two different standards; [AWS Foundational Best Practices](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-fsbp.html) and [CIS AWS Foundations Benchmarks](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-standards-cis.html).
* [Okta](https://www.okta.com/): All users are managed through Okta. We use it to authenticate users before letting them in eAPD
* [AWS Cloudwatch](https://aws.amazon.com/cloudwatch/): Linked with our Slack channel. These alerts inform us about the current state of staging/production environments. 
* Weekly vulnerability scans: Just as it says, we run weekly vulnerability scans on production as a health check.