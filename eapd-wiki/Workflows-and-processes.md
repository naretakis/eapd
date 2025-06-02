## Working in GitHub

### Creating and closing tasks (issues)
All tasks should be created according to the [issue template](https://github.com/18F/cms-hitech-apd/blob/master/.github/ISSUE_TEMPLATE.md), with a clear description and a checklist of what must be done before the task is complete. Once every item on the checklist is completed, the task is done and the issue can be closed.

### Creating design issues

#### Export view
When a decision is made to change an element in the UI, if the design will be affected more than a small content change, a mock-up for the export view should accompany any mock-ups of the builder view. 

#### Considerations for each design issue
All design changes should consider the builder view, the review view, the PDF export view, the executive summary (if applicable), multiple FFY (if applicable), multiple items entered (if applicable), and whether the changes will affect a summary, table, or any field in other parts of the application

### Handing tasks off to another teammate

#### For Design handing off to Development
For elements that need to move from design into code, this process identifies how we track and spawn issues to provide a smooth delivery for the design and development teams.


![image](https://user-images.githubusercontent.com/113388640/213814570-8c9a1bbc-ffea-4809-8176-017212f87b96.png)

1. Design Assignee moves issue to "In Progress"
2. Design Assignee ensures scope of work and acceptance criteria has been met
3. Design Assignee moves issue to "Ready for Review"
4. Design Lead, Product Owners and Tech Lead reviews capability to ensure accuracy and provide closing notes 
5. Once Approved, Tech Lead creates Development ticket and assigns to QA
6. Quality Assignee ensures user efficiency and creates Testing Criteria
7. Product Owners ensure Development ticket and Testing Criteria is correct; Once Approved, Product Owners close original design ticket


#### For interactive or back end changes
More comprehensive changes, especially anything affecting the API or data, should be handled a little more formally. It's generally most effective to discuss these changes in a meeting, to make sure any questions are addressed.

1. It's best to discuss changes face-to-face, versus in text
   * Design is responsible for making sure the conversation happens
2. Design and dev will create one or more new issues in GitHub as appropriate
3. Design will add any helpful artifacts (for example, wireframes) to the issue
4. Whoever creates the issue will CC the rest of the team
5. New issues will be added to the project backlog (not the current sprint)
   * Product will prioritize the issues in the next refinement or sprint planning session
   * Items that need to be added to the current sprint should be raised to the product team

#### For Development Work That Needs QA
QA Pipeline in GitHub - for development work that needs to be QA’d, we want to make sure that the QA Pipeline is used so that we can prioritize the work and ensure the work is assigned. To do this our process is:

1. When a _Pull Request_ is ready for QA, it gets moved into the **QA pipeline** by the dev working the PR. Then, the person doing the QA will self-assign and add themselves to the PR in the QA pipeline (focusing on top items in the pipeline as a priority).
2. Once the QA work is done, if it passes QA, the PR can be moved into the **Ready for Review** pipeline as per our normal process.
3. If the PR does not pass QA and additional development work is needed to address, the tester will add comments to the PR and move it back into the **In-progress pipeline**. This way PRs that need to be reworked are more visible on the board. The assigned dev can then fix whatever needs to be fixed, and then move the PR back into the **QA pipeline** (move to bottom of the QA pipeline unless a special circumstance warrants moving it back to the top).

##### Use of the QA Label
We use the QA Label for _Zenhub issues_ for any “QA work that is not actually _QA’ing a dev issue_”. This is for things like research and development of QA automation, or other QA-related tasks during a sprint. Use of this label allows us to see work on the board via the **This Sprint** or **In-Progress** pipelines. 

### Handling issues blocked by other issues
Issues don't exist in isolation, if you discover an issue that can't be resolved due to other issues:

1. Using ZenHub, update the issue dependencies within the issue. ZenHub's documentation about how to utilize dependencies: https://help.zenhub.com/support/solutions/articles/43000010349-create-github-issue-dependencies
2. Document in the comments how specific issues are blocking progress toward completing the issue. 
3. During stand-up, **blocked** issues may be reviewed with a plan/timeline for resolution.
4. Long standing **blocked** issues will also be reviewed as part of sprint planning. 

### Handling tasks that grow in scope
Sometimes a task is bigger than expected, or you discover additional complexity after you start.

1. Identify a bite-sized piece that you can tackle
   * If you can't do that because the work is unmanageably big, complicated, or ambiguous, call in product or design!
2. Create a new issue for the bite-sized piece that you can do, and link to it from the parent issue and tag it with related Epic.
3. Where appropriate, tag the issue with the current Milestone. If you are unsure whether or not it fits in the current Milestone, call in product!
4. Rinse and repeat

### Tracking and Adding a Future Enhancement
Sometimes you come up with a great idea, but it isn't viable in a current milestone, or requires a significant amount of work to address. 

1. Create a new issue for the future enhancement.
2. Describe the enhancement with as much detail as you can.
3. Add a label to mark it as **Future Enhancement**.
4. Triage of these issues will be done during backlog refinement and **Future Enhancements** will be added to active pipelines, when appropriate.

### Creating and closing pull requests
All pull requests should be created according to the [pull request template](https://github.com/18F/cms-hitech-apd/blob/master/.github/PULL_REQUEST_TEMPLATE.md), with a clear description of the changes introduced in the pull request. Any items in the merge checklist that are not applicable to the pull request should be struck out (not deleted). [This is a good example of a pull request.](https://github.com/18F/cms-hitech-apd/pull/282)

### Reviewing pull requests on accessibility tickets or testing accessibility of new features
The ideal process for testing the accessibility of features is to test with a diverse set of screen readers/systems/browser, as well as test the feature/page manually for any issues that may have been introduced with changes to the components.

This might look like a combination of common system, browser, and screen readers. A very common set up is using the JAWS screen reader on the Chrome browser on Windows.

We routinely test on:
1. VoiceOver (Apple) 
2. ChromeVox (Chrome extension)

We are working to add these Windows environments as well:
1. NVDA on Windows - Ty will look into testing for Windows
2. JAWS on Windows

When testing new features, a reviewer should also use the WAVE extension for uncovering errors. 

What to look for when reviewing features/issues for accessibility:
1) Are we communicating the same information to sighted and not sighted users. There shouldn’t be a difference in experience. 
2) Not every screen reader will interpret the application the same. Keyboard shortcuts could be working fine, but voice commands could be acting differently. Check different set ups.
3) Look at the feature in general - make sure it still looks and works as expected both for folks using and not using assistive devices. 

Who will review for accessibility issues? 
1) Product, dev lead, QA and design lead will review and sign off on accessibility specific issues. 
2) For regular/new features, product and front-end dev and/or QA will review for accessibility problems. 

## Epics in GitHub

An Epic is used to group issues by their subject or key theme. The description of the Epic will include a clear description of what user story is being addressed and how it will look like when it is done.

Epics are created through the use of ZenHub and appear in GitHub as issues with the label `Epic.`

Issues and Pull Requests may be added to the Epic to help track progress in meeting the goals defined in the Epic's user story.

### Epic Name 

> `<Descriptor>`

> **Example:** Minimalist State Dashboard

### Epic User Stories 

The description of the Epic should include a clear description of the user story being addressed following this format:

> As a `<user-type>`, I want `<description of need>` so that I can `<description of how that need is met>`.

> **Example:** As a _state user_, I want _to see my documents and the actions I can take_, so that _I can create, view, and edit them_.

## Design Decisions

### Documenting Design Decisions
For documenting design decisions, we will talk together in design sync, parking lot, or other meetings, and decisions, thoughts and history will be documented as annotations on the Figma file or on the Mural, whichever we’re using for various artifacts. 

In Figma, we will use a header component/frame to show the issue number, the approximate date of last work on the design, and any other relevant information that will help folks know what to look at in Figma to review or to create dev tickets. You can see an example of this on the admin flow pages in Figma. 

In Figma, we will move the most recent work on a page to the top left of the page, above all other versions, frames, or ideas. 

If there is a corresponding Mural or Figma link to a Figma or Mural, make sure there are links back and forth to keep continuity. 

We will share Figma or Mural links in our design tickets so that product and dev always have the latest updates on the designs. 

To share a link in Figma, right click, go to copy/paste, then to Copy Link. If Copy Link doesn’t exist, we’ll need to put a frame on whatever we want to share. Avoid using the “Share” option in the top right because Figma doesn’t always create a link that is expected through that option. 

### Troubleshooting Figma Links
* If you have more than one element selected at a time, the link will not be accurate and will take you to the main page on the Figma file. 
* Sometimes I’ve seen issues with clicking on a Figma link straight from an email (this usually takes me to some random spot on the right page), so I always go to github or zenhub to click on the link to get to the right spot. 
* If you have any trouble with a Figma link, please bring it to the team’s attention in Slack so we can continue to make sure we know how these links are intended to work and always have the latest designs at the ready. 


## Project management

![image](https://user-images.githubusercontent.com/113388640/213318841-e6295104-5f63-4b07-bf52-1603e4785263.png)

### Agile approach
Our team is committed to working in short intervals where we constantly update our vision, designs, and code based on what we learn from testing our product. In other words, we use an **agile development** approach. We specifically use a simplified approach derived from the [Scrum](https://www.scrumalliance.org/learn-about-scrum) framework (we recommend that inexperienced teams consider using the full scrum process, not the modified method that we use).

### Project cadence
The project timeline is broken is broken into **sprints** and **milestones**. Each sprint is two weeks, or 10 work days, long. This is short enough that we can pretty accurately predict what work we can get done, and long enough that we can see real progress in each sprint. Milestones are three sprints (six weeks) long. We can't accurately predict everything that we can complete in a given milestone, but we are able to set thematic goals for each milestone that help us stay focused on getting work done without shutting out the big picture.

### Planning
Product planning happens at three main levels of fidelity: MVP planning, milestone planning, and sprint planning. The vision was drafted before the project even started, and all work comes from that vision.

An MVP, or Minimum Viable Product, is the smallest amount of work that we need to do to make a product that is, well, viable. In our case, that means it needs to support a specific set of workflows that we've defined in our project framing.

Milestone planning happens every six weeks. We examine how much progress we've made since our last milestone, compare that to our MVP target, and set concrete goals that will help us achieve that MVP. Our initial development milestone focused on creating a tool that would allow a user to draft an HIT APD submission. 

Sprint planning happens every two weeks. We first hold a retrospective meeting where we reflect on what ways of working we should continue, and which ones we should adjust in order to work together more smoothly. We start planning by looking at how much work we completed in the last sprint and take note of any work that we don't think will get done before the new sprint starts. Then we set our concrete goals for the upcoming sprint and talk about what tasks everyone will need to complete in order to achieve those goals. We document tasks as they are identified and assign them to individuals who are responsible for completing them. Finally, we wrap up planning by looking at the work assigned to each person and everyone answers two questions:

1. Do I understand the work assigned to me?
2. Do I have the right amount of work assigned to me?

### Open source

We follow the [18F open source policy](https://18f.gsa.gov/open-source-policy/), meaning we develop our work in the open, we publish all of our source code publicly, and we prefer free, open source libraries, frameworks, and companion software for our work. As a work of the federal government, there is no copyright and all of our work is committed to the public domain within the United States. We adopt the [CC0 v1.0](https://creativecommons.org/publicdomain/zero/1.0/legalcode) license in the rest of the world.

### Setting Priorities After Go-Live
Once we go live with the HITECH APD release, we'll continue to prioritize issues in a similar way that we've done before. 

* Is something causing the details of an exported APD to be incorrect? If yes, priority is high to fix.
* Does something in the UI appear to be incorrect from a usability or accessibility perspective. (e.g. the name of the Activity List)? If yes, priority TBD based on severity of issue and past testing observations. 
* Is something preventing exporting an approvable APD out of the system for review? (e.g. a bug in the math) If yes, priority high to fix.
* Is the feature on the roadmap?
* Is the feature a necessary addition to the roadmap based on user research, leadership requests, or regulation changes?
* Is the time to make a change vs the severity of UI improvement worth bumping up in priority (e.g. everyone in testing doesn't understand the field label, and it will take a very short amount of time to update)? 

We will have the additional consideration of the dev team working on tech debt and completing refactor work before working on implementation of new MES features. 

For bugs, we'll continue to prioritize according to severity, need, and time outside of sprint planning or refinement if needed.

For feature requests from users, we will try to not make changes to the HITECH APD unless it's going to significantly improve MES as well. We will limit HITECH only feature requests for users at this time, unless it meets the general criteria for prioritization. 

We may prioritize some features related to the export view based on user feedback, but those should also significantly improve MES, and would not be just a HITECH improvement. 

### Day-to-day project management

The Team uses ZenHub (http://www.zenhub.com) to manage activities and visualize project progress, but activities and progress can also be tracked in [GitHub Projects](https://github.com/18F/cms-hitech-apd/projects/1). 

We meet every day for about 15 minutes, reviewing the current Epics, Milestones, and underlying issues to ensure coordination between product, design and development. 

Reports should focus on:

**Epic Issues:** What issues were completed with an emphasis on what items resulted that in additional work/hand off to another component of the team.

**What's Next:** What issues are in progress/next priority from the active GitHub Milestones/Epics

**Milestone Blockers:** Any blockers to getting the existing or next set of issues completed, identifying who what needs to take action to remove the blockers.

Individuals who are not able to attend the daily call should post their update in Slack using the format above.

## Tools we use

### Design
* [Figma](https://www.figma.com/files/recent) for wireframes, high fidelity mock-ups, and clickable prototypes (or front-end can code them if needed). 
* Google Forms for recruiting participants for research. 
* Google Docs for user research planning and notes. We make the original plan in google docs so the team can participate, then move the approved plan to Dovetail for posterity and sharing with other MACBIS teams. 
* [Dovetail](https://dovetailapp.com/) for storing research plans and artifacts (this is the current MACBIS repository), synthesis, automated transcriptions, notes, reports, tagging, etc. 
* [Mural](https://mural.co/) for product/design flows, tracking decisions around major changes to designs, and workshop facilitation (this is the CMS standard for whiteboards).
* Wiki for final research findings.

### Development
* [Visual Studio Code](https://code.visualstudio.com/) for writing code
* [GitHub](https://github.com) for code repository and version control

### Product management
* [GitHub ZenHub](https://github.com/marketplace/zenhub) for tracking work and progress
* [Mural](https://mural.co/) for roadmaps, milestone planning, workflows and team retros

### Team communication
* [Slack](https://slack.com/) for daily communication
* [Zoom](https://zoom.us/) for video calls
* Keybase chat if slack goes down