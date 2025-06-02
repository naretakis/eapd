## Shifting Testing to the Left
- To shift testing to the left means to breaks the traditional way of testing, in which testing is normally done at the end. When testing is moved to the left it starts the process of testing earlier to streamline the development cycle as a whole. 
### Why shift testing to the left? What is the goal?
- When testing is done at the very end it can become a bottleneck in the process, ultimately delaying product delivery. Shifting testing to the left is an aim to reduce that bottleneck and help catch potential problems earlier before they can become bigger down the road.
- How do we do that? Test engineers will meet with product/design to get the full scope of each feature. It is the tester's responsibility to ask questions about intent, possible risks, possible alternatives, intended functionality, etc...
- This whole process is to help smooth out the transitions from product -> design and from design -> product.
- Want to read about more? Check out these articles!
  - [Shift Left Testing: What, Why & How To Shift Left](https://www.bmc.com/blogs/what-is-shift-left-shift-left-testing-explained/#:~:text=Shift%20Left%20is%20a%20practice,in%20the%20software%20development%20process)
  - [What Does it Mean to Shift Left?](https://smartbear.com/learn/automated-testing/shifting-left-in-testing/)
## Testing Tools we use:
- Unit testing: Jest, Stryker (mutation testing), React Testing Library and Enzyme (we are trying to move away from Enzyme and migrate to React Testing Library)
  - Unit testing allows us to test individual components and make sure they work by themselves before we put them all together.

- End-to-end automation testing: Cypress
  - End to end testing is a way we can automate a specific workflow. This process comes after unit testing and basically tests multiple components together and overall the functionality of the app. These e2e tests help keep the functionality consistent as we integrate in our CI/CD pipeline.  

- Visual: Chromatic (not yet implemented, but planned)
  - Chromatic is visual regression testing tool. This should help keep the look of the app consistent, as that is something e2e tests cannot track

## Roles and Responsibilities for Testing
- Develop scripts to run automated tests
- Develop test plans and follow guidelines set by test plan.

## What is the expectations for QA in ticket authoring process
- QA is expected to work on testing new pages/features provided by the Development team
- keep in communication with the developers on new discoveries before closing the ticket

## How do we measure testing? Codecov? Outputs? Metrics?
- One way we measure testing is through code coverage. Which is a percentage of what lines of code are being touched by our tests. Ideally every project would like to have 100% code coverage. While that may seem reasonable, as projects expand it is almost impossible to keep track of every single line of code. A more realistic target would be 90%, which is what we are aiming for.


