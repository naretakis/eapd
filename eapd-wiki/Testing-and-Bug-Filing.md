## Testing
### Accessibility
This product must conform to the [WCAG 2.0 AA guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/).

### Manual testing
We use automated testing tools to make sure that our software works as well as possible, but automated testing doesn't catch everything. That's why we also do regular manual testing.

1. Reference the checklist of [[testing scenarios]] based on our use cases
   * Run through checklist once a sprint
2. Play with features as they're released
3. As bugs are found, file them according to our bug filing process

### Filing bugs
When you find a bug, you should file it so that we can address it!

1. Double check the bug to make sure you can reproduce it
2. File a new issue about the bug
3. Describe the bug in the body of the issue
   * Write steps for how to reproduce the bug
   * Add a screenshot or [GIF](https://giphy.com/apps/giphycapture) if you can!
4. Add a label to mark it as a bug
5. Add a label to mark the severity of the bug
   * Severity 1: the experience cannot be completed
   * Severity 2: a workaround exists but the experience has serious flaws
   * Severity 3: the experience is unpolished
6. If Sev 1, alert the team in the CMS eAPD Slack channel for prioritization (triage - see below). 
7. If Sev 2 or Sev 3, bugs will get prioritized in zenhub during refinement. 

### Bug triage
Product leads bug triage.

1. Mark the priority of fixing the bug (priority cannot be higher than the priority of the experience the bug applies to)
2. Take appropriate action
   * If the bug should be fixed, pull it into the backlog so that it gets assigned to someone to fix
   * If the bug should not be fixed, add a comment explaining why and then close it
