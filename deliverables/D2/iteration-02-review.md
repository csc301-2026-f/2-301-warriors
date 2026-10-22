# 301 warriors - Group 2


## Iteration 02 - Review & Retrospect

 * When: October 21st, 2026, 10:40 P.M. - 11:00 P.M.
 * Where: Online (Google Meet)

## Process - Reflection

#### Q1. What worked well

1. **Forming subteams around related tasks.** We divided ourselves into three subteams based on closely connected responsibilities. This made it easier for teammates to coordinate changes, review each other’s code, and agree on data formats before combining their work. Working in smaller groups helped reduce misunderstandings and integration conflicts while allowing different parts of the project to progress simultaneously.

![Team task breakdown](subteams.png)

2. **Holding regular internal team meetings.** We decided to meet as a team, without the partner or TA, at least once a week to divide tasks, clarify uncertainties, and set timelines. Meetings before demos were particularly useful for reviewing progress and confirming what was ready to present. This helped everyone stay aligned and identify blockers before they became surprises during the demo.

3. **Integrating related components in stages.** We combined closely related pieces first, such as the backend client and discovery worker, before connecting them to the frontend. This gave us smaller integration steps to review and test, making it easier to identify where mismatches originated. It also allowed teammates to begin connecting their components while other parts were still being completed.

#### Q2. What did not work well

1. **Assigning broad tasks without clear individual ownership.** Initially, multiple teammates worked on the same broad task without clearly defined responsibilities. This created misalignment about who was implementing each part and how the pieces would fit together. Dividing the work into seven smaller subtasks improved this process by giving each member clear ownership and a manageable section of code to understand and maintain.

2. **Leaving some integration details unclear before implementation.** We did not fully agree on certain data formats and component interactions before starting development. When connecting our work, we needed additional clarification about how backend results would reach the frontend and how information would pass between components. This caused rework and extra coordination. Agreeing on shared interfaces and example inputs and outputs beforehand would have made integration smoother.


#### Q3(a). Planned changes

1. **Establishing a clearer branching, review, and integration workflow.** We plan to define which shared branches individual task branches should merge into, the order of merges, and the reviews and tests required before each merge. We will also set deadlines for completing individual work, integrating components, and testing the combined system. This should reduce merge conflicts and confusion about which branch contains the latest changes, while leaving enough time to address integration issues.

2. **Allowing members to rotate responsibilities between sprints.** Although we divided tasks among frontend, backend, and testing teams, the assignments did not offer equal technical scope or always match members’ interests. For the next sprint, we plan to let members express their preferences and switch areas where feasible, while accounting for dependencies and sharing knowledge during handoffs. For example, someone who took on frontend work for D2 could contribute to backend development in D3. This would distribute learning opportunities more fairly and help members gain experience across the system.

#### Q3(b). Integration & Next steps
Each member developed an assigned frontend, backend, or testing component on a separate branch, which we then merged into the dev branch. Team members tested individual components and their connections to verify that they worked together as one product.


## Product - Review

#### Q4. How was your product demo?
We prepared by testing our code to check that the components worked together and running the iOS simulator. We demonstrated the basic Ask Savi Cineplex workflow: entering a request, identifying the location and date, retrieving movie information, and displaying options with the movie title, theatre, date, and time.

Our partner accepted the backend functionality but requested UI improvements, which we will prioritize in the next sprint.

We learned to allow more time for integration testing before demos and pull requests, as we had overlooked conflicts and fixes. We also learned that preparing brief notes on completed features and blockers helps keep the demo clear, structured, and within the time limit.



