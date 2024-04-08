Key values of Agile development:
- **Individuals and interactions** over processes and tools
- **Working software** over comprehensive documentation
- **Customer collaboration** over contract negotiation
- **Responding to change** over following a plan

These values are then further articulated into 12 principles:
- Our highest priority is to satisfy the customer through **early and continuous delivery of valuable software.**
- **Welcome changing requirements**, even late in development. Agile processes harness change for the customer's competitive advantage.
- **Deliver working software frequently**, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
- **Business people and developers must work together** daily throughout the project.
- **Build projects around motivated individuals**. Give them the environment and support they need, and trust them to get the job done.
- The most efficient and effective method of conveying information to and within a development team is **face-to-face conversation.**
- **Working software** is the **primary measure** of progress.
- **Agile processes promote sustainable development**. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
- **Continuous attention** to technical excellence and good design enhances agility.
- **Simplicity**--the art of maximising the amount of work not done--is essential.
- The best architectures, requirements, and designs emerge from **self-organising teams.**
- At regular intervals, **the team reflects on how to become more effective**, then tunes and adjusts its behaviour accordingly.

## Agile methodologies in a nutshell
- **Requirements** there are things that your clients want
- **Documentation** you need to document these things
- **Prioritisation** you need to prioritise critical tasks
- **Estimation** you need to know how long it will take to complete

**Start with the most important tasks in your first release** implement less important aftr
Have mechanisms in place to handle changing environments

## Different Agile Approaches
- Scrum
	- most popular
	- proven record of success and most companies use this
- Kanban
	- Work is represented by cards, cards move from left to right in stages
	- Common stages are Backlog, ready, coding, testing, approval and done
	- WIP limits limits how much work is done at once
- Extreme Programming
- Lean software development
- Feature-driven development

# Scrum

![500](Pasted%20image%2020240322190430.png)

![600](Pasted%20image%2020240322191012.png)

## Artefacts
Artefacts are documents, diagrams and models that ensure that the software you're creating addresses the clients needs, and can be installed and maintained while being delivered within schedule and allowing the team to learn and improve.

In the Scrum development structure, there are practices called **events** that are meant to structure daily and weekly work into manageable chunks, and insure the work is constantly informed and improved through continuous revision and client's feedback

### User stories
![200](Pasted%20image%2020240322191404.png)
User stories are used to express goals and describe features. They are informal descriptions of desired features and its goal in a software system. These are written in collaboration with the client and from the perspective of the user. They are also **encoded** in such a way that a team of developers can **estimate the amount of work** needed to implement. It also serves as a measurement of if the feature has been adequately implemented.

#### How to make a good user story
- Story must have a brief description of functionality
- Stories must be written from the perspective of the user
- Stories must be testable
- There should be enough information to generate a tough time estimate (in units)
- Applications usually have more than one **type** of user (e.g. administrative vs student)
- Brainstorm potential roles with client 
- Don't bother with extreme edge cases initially, they'll come later

#### Estimating time
There are lots of estimation methods:
- Consensus discussion
- Most popular estimate
- Highest estimate
- Poker estimation

### Release Plan
A **release plan** is a document that provides a strategic guide, delineating the timeline and scope of tasks necessary to launch a product. It serves as a **roadmap**, steering the entire project team through the development and release journey. Key pieces of information detailed in the release plan are:

| Term            | Description                                                                            |
|-----------------|----------------------------------------------------------------------------------------|
| Scope           | Describes what features, enhancements, or bug fixes will be included in the release.   |
| Timeline        | Specifies the release date or timeframe.                                               |
| Resources       | Identifies the team members, tools, and infrastructure needed for successful delivery. |
| Dependencies    | Addresses any external factors or prerequisites.                                       |
| Risk Assessment | Evaluates potential risks and mitigation strategies.                                   |
However, it is important to note that in the **Agile methodology**, this plan is subject to change and is allowed to evolve over time. This means that when requirements change, it is good practice to update the relevant documents and maintain a paper trail of what was decided and when.

### Product Backlog
In its simplest form, the product backlog is an ordered list of tasks that the team agrees need to be completed to deliver value to the customer.

The list of prioritised user stories to implement in a given sprint is the most common example, the product backlog can however include other tasks to complete, for example usability tests, documentation, and more. A shared product backlog serves several purposes: 

- provides transparency by making work and progress visible to the entire team
- helps answer the question: “What should we work on next?”
- maps advances towards the product goal as work that was 'burned down'

## Events
A key emphasis of scrum is the emphasis on regular events, or ceremonies that help the team to stay focussed on the goal, and to ensure that the work is constantly informed by the client's feedback. 

### Sprint 
A sprint is a fixed stretch of time, usually less than a month, in which the team works towards a given objective (the sprint goal). Sprints focus on **delivering value**, rather than adding features. In this time user stories are moved from the product backlog to the sprint backlog. Activities carried out during a sprint include:

| Name                  | Time            | Description                                                                                                                |
|-----------------------|-----------------|----------------------------------------------------------------------------------------------------------------------------|
| Sprint Planning       | Start of Sprint | The work to be performed in the sprint is spelled out and detailed in the sprint plan.                                     |
| Sprint Implementation | During Sprint   | The sprint will focus on the next most important product goal, implementing a number of user stories related to that goal. |
| Sprint Review         | End of Sprint   | A review of the work done during the sprint.                                                                               |
| Sprint Retrospective  | End of Sprint   | A reflection on the sprint process and identification of improvements for the next sprint.                                 |

### Sprint Planning
A sprint starts with a sprint planning session in which the team and product owner agree on what value can be added to the product in the next sprint cycle. A sprint is focused on **delivering value** rather **than adding features.**

A sprint goal is decided as **part of the planning**. The developers commit to reach the sprint the goal, but they have flexibility regarding what features need to be implemented to deliver the goal. The sprint plan itself is an agreement between team members on what value will be added next, and what steps will be needed to deliver it.

#### Summary
- **Identify the goal:** meet with the product owner and scrum master to identify the sprint goal
- **Capacity Planning:** the team estimates the amount of work units they can complete before the sprint
- **Task Selection:** relevant items are moved from the project backlog to the sprint backlog
- **Discussion:** the team may discuss any assumptions or risks which may impede progress

### Sprint Implementation
- **Development work:** tasks are implemented from the sprint backlog
- **Limited Timeframe:** a sprint usually runs for 2-4 weeks
- **Daily Scrum:** the team conducts daily scrum sessions
- **Quality Assurance:** the team conducts testing and code reviews throughout the sprint

### Sprint Review
- Inspect the product increment. Have stakeholders try the updated product and receive feedback
- Discuss the product backlog: discuss the product backlog and make any updates needed before the next sprint

### Sprint Retrospective
In **scrum**, a sprint retrospective is a meeting in which the team reflects on the past sprint and discusses how to improve process, teamwork, team culture or anything else that is of concern for the team. This is a widely adopted practice in **scrum**, and corresponds to analogous practices in workplace management and team building.

**Formats:**
Here we discuss the 4 L's:
- What you liked about the process
- What you lacked
- What you longed for

Start, stop, continue
- What should the team start doing
- What should the team stop doing
- What should the team continue doing

Spring retrospectives include aspects such as:

| Term               | Description                                    |
|--------------------|------------------------------------------------|
| Individuals        | How team members collaborated and contributed. |
| Interactions       | How communication and teamwork played out.     |
| Processes          | The effectiveness of the Scrum process.        |
| Tools              | The tools and technologies used.               |
| Definition of Done | Whether the work met the agreed-upon criteria. |

### Prioritising (MoSCoW)
Prioritisation is part of sprint planning and in CAB302 we adopt the **MoSCoW** framework. It consists of deciding (normally in consultation with the product owner) what features in the system add the most value and therefore need to be implemented earlier. The framework helps to identify four priority categories:

| Priority Level | Classification                               | Description                                                                                                                                                   |
|----------------|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Must-have      | Non-negotiable essentials for the project    | These are the features and functionalities that add defining value to the project: the 'search' to one's Google, or the 'share' to one's Facebook.            |
| Should-have    | Valuable features that enhance functionality | These may add value to the product, but are not necessarily implemented from the very first iteration.                                                        |
| Could-have     | Desirable but not critical                   | These features are 'nice to have' but their absence does not make the system less useful or functional. Can be implemented after everything else is in place. |
| Won’t-have     | Excluded from the current scope              | -                                                                                                                                                             |

### Daily Scrum
A daily meeting in which the development team reviews progress from the last day, adjust the plan as necessary, check if anything is blocking progress for any of the developers, and produces a plan for the next day of work. It is intended to be short (15 minutes) and focused on development. **This meeting has an emphasis on brevity**

## Roles
### Product (or project) owner
The product owner is in charge of the **project** backlog, represents the customer and stakeholders in all decisions involving requirements, user stories and prioritisation. The product owner ensures that the team works on features that deliver the most value to the customer and make decisions about what gets developed. This means that they **represent the voice of the customer** in the team

| Responsibility             | Description                                                                                                                 | Example                                                                                              |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| Product Backlog Management | They curate the product backlog, ensuring that the features delivering the better value are developed first.                | Prioritizing a feature that improves user experience based on customer feedback.                     |
| Product Vision             | The Product Owner sets the overarching vision for the product, aligning it with business goals and customer needs.          | Setting a vision for the product to be the most user-friendly project management tool in the market. |
| Stakeholder Communication  | They bridge the gap between the Scrum team and external stakeholders, translating their requirements into actionable items. | Converting a client's request into a user story that the development team can work on.               |
| Decision Making            | Product Owners make critical decisions about what features to build, balancing trade-offs and maximizing value.             | Deciding to delay a feature in favor of fixing a critical bug that's affecting users.                |
| Market Awareness           | They stay informed about market trends, customer expectations, and competitive landscapes.                                  | Keeping track of a competitor's new feature and proposing a similar feature for your product.        |

### Developers
The development team consists of individuals who do the actual work to deliver product increment

Contrary to the name its not just limited to software developers and can also include designers, writers, testers and other specialists. The team collaborates to create a potentially shippable product increment during each sprint. This table describes the key responsibilities of the development team:

| Responsibility         | Description                                                                                                               | Example                                                                                                       |
|------------------------|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| Cross-Functional Work  | Development team members bring diverse skills (e.g., coding, design, testing) to the table, ensuring a holistic approach. | A developer with design skills contributes to both the backend and frontend of a feature.                     |
| Self-Organization      | They organize their work, commit to sprint goals, and collaborate closely to deliver high-quality increments.             | The team autonomously decides how to divide tasks among themselves to achieve the sprint goal.                |
| Continuous Improvement | The team commits to a reflective practice, identifies areas for enhancement, and adapts their practices.                  | After each sprint, the team holds a retrospective to discuss what went well and what can be improved.         |
| Collaboration          | They actively engage with the Product Owner and Scrum Master, seeking clarity and alignment.                              | The team regularly communicates with the Product Owner to understand the requirements and priorities.         |
| Ownership              | Team members take ownership of their commitments and strive for excellence.                                               | A team member proactively identifies a bug, fixes it, and adds tests to prevent similar issues in the future. |
### Scrum master
The scrum master **facilitates** the scrum process ensuring that the team adheres to agreed upon practices, works to remove obstacles or impediments and fosters a collaborative and positive environment

They also facilitate ceremonies like sprint planning, daily stand-ups and retrospectives. It is important to note that the scrum master is a **facilitator** and not a boss.

| Responsibility       | Description                                                                                                                       | Example                                                                                                             |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Daily Scrum Meetings | The Scrum Master facilitates daily stand-up meetings, where team members share progress, discuss impediments, and plan their day. | Scrum Master asks each team member about their progress on assigned tasks and any blockers they might be facing.    |
| Sprint Planning      | They lead sprint planning sessions, helping the team define sprint goals and select backlog items.                                | Scrum Master organizes a meeting where the team discusses and agrees on the scope of work for the next sprint.      |
| Retrospectives       | After each sprint, the Scrum Master 'chairs' the retrospectives to review what went well and identify areas for improvement.      | Scrum Master facilitates a meeting where the team reflects on the last sprint and identifies areas for improvement. |
| Obstacle Removal     | They actively manage obstacles faced by the team, collaborating with stakeholders outside the team to resolve issues.             | Scrum Master coordinates with the IT department to resolve a technical issue that's blocking the team.              |
| Team Support         | The Scrum Master ensures team members have the resources they need and fosters a positive work environment.                       | Scrum Master arranges for additional training for a team member who needs to learn a new technology.                |
| Scrum Advocacy       | Beyond the team, they advocate for Scrum practices within the organization.                                                       | Scrum Master presents the benefits of Scrum at a company-wide meeting to encourage other teams to adopt it.         |

## Pair Programming
A collaborative practice in software development where two programmers work together at one workstation. The process involves two roles: the **driver** and the **navigator**. 

The driver writes the code to address the problem at hand. The navigator reviews each line of code as it’s typed in, keeping an eye on the bigger picture to ensure the code fits into the overall structure of the program and adheres to coding standards.

This method encourages teamwork, improves code quality by catching errors early, and facilitates knowledge sharing, especially from more experienced to newly added team members (and when a more experienced programmer works in pair with a novice one, it is common for the novice to be the driver). It’s a practice that originated in Extreme Programming (XP) and is also used in other Agile methodologies.

## Burndown charts
- Burndown charts show how many story points worth of tasks still need to be completed for the release. 
- **Velocity** is the expected number of story points the team can complete in one sprint
- Use the point count for the release and expected velocity to estimate the required number of sprints


## Project Management Tools
![700](Pasted%20image%2020240322202934.png)
- Trello - probably use
- Jira
- Teams