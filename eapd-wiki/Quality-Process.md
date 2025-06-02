## Updated Quality Process as of 12/2022:
### Ticket Life Cycle
1) As design tickets come to a close, Tif (Tech Lead) and Darren (QA Tester) will be tagged for a final review of the ticket's contents.
2) Once the ticket has been approved by both the Tech Lead and QA, the ticket handoff to dev is complete.
3) The Tech Lead will be responsible for writing tickets and splitting up work into separate tickets if necessary.
4) Once the dev tickets have been created, The testers responsibility is to review said dev ticket and establish an appropriate acceptance criteria for the work that was outlined.
5) When the acceptance criteria is done, we then ask for a final review of the dev ticket from Design, Product, and the Tech Lead. 
6) Once each discipline is content with the ticket created it is considered complete and ready to be worked on by devs. 

### PR Reviews and QA Process
1) Once devs have finished working on a ticket, it is then moved into Code Review.
2) In Code Review, a dev other that the one who worked on the ticket reviews the code.
3) Once another dev has signed off on the PR, it's then moved over to QA.
4) In QA's review, they are responsible for verifying functionality, accessibility, automated tests passing, and to ensure no other side effects have happened. 
5) Once QA has approved the PR it is sent to Product and Design for a final review. If no design changes were made, Design doesn't need to review the PR. ( what are times when product doesn't need to review the PR?)
---
We are shifting testing to the left! If you would like to know more about what that process entails, please refer to our Testing Philosophies and Strategies page. Here is how we are adapting our quality process to a shift left mentality:

* The Quality team will take time to review Design tickets before they get handed off to dev
* The Quality team participates in early Design conversations. Conversations such as “What are we building?”, “Why are we building?” ,”Who are we building for?”
  * Design sync is a good example of these conversations. Could quality get a heads up on tickets planned on being discussed so we can have a preview?
* Towards the end of a design ticket, test cases will be documented before it gets handed off to dev. These test cases will be reviewed by Design and Product and ultimately Dev.
* Test cases created should help separate the ticket into individual pieces of work.
* Once the test cases have been approved, the process proceeds as normal with a ticket handoff to dev.  
* What type of tickets are these run on? Mainly used for feature tickets, but also possible for exploratory tickets too. 
* **Beta**: Testers will try writing dev tickets for upcoming work.