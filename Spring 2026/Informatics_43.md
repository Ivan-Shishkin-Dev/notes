# Lecture 1: What is Software Engineering?

**What Is Software Engineering?** → Software is everywhere

**Software**

- Code
- Documentation, user manuals
- Designs, specifications
- Test cases
- Plans and schedules

**Engineering**

- Creatively applying science and math
- To designing and building things
- Involves trade-offs, risk analysis, skill, and knowledge

**Video ("Computer Science Field Guide: Software Engineering")**

- Software development has teams to write huge software
- Software engineering is so much more than just programming
- 1/3 of software projects fail

**Definitions of Software Engineering by Experts**

- A broad field that touches upon all aspects of developing and supporting a software system
- "A discipline that deals with the building of software systems which are so large that they are built by a team or teams of engineers." [Ghezzi, Jazayeri, Mandrioli]
	- Scalability
	- Need layers of management
- Multi-person construction of multi-version software
	- Not static in time → constantly updating
	- Multiple versions of different software
- A discipline whose aim is the production of fault-free software, delivered on time and within budget, that satisfies the user's needs. Furthermore, the software must be easy to modify when the user's needs change.
	- Shows how many things to worry about when building software
- Informatics 43 definition
	- The process of constructing software
	- Phases of development (focusing on those other than programming)
	- Principles and qualities of enduring value
- Also of (lesser) interest in this course
	- Managing and scheduling software development teams
	- Making money → business models
	- Software's impact on users, organizations, and society
	- AI

**Waterfall Model** → Requirements → Design → Implementation → Verification → Maintenance

**Principles and Qualities of Enduring Value**

- Correct
- Reliable
- Adaptable
- Modular
- Usable
- Efficient → [[ICS_46#Lecture 1: Algorithms & Analysis|algorithm efficiency and Big-O in ICS 46]]
- Robust

**Summary**

- **Software is Everywhere**
	- It touches nearly every domain: cars, medicine, politics, military, space exploration, disaster response, gaming, law enforcement, and more.
- **Software is...**
	- On one hand, it's exciting, fun, versatile, and helpful (though it can also be harmful). On the other, it's large, built by teams, long-lived, multi-versioned, and complex.
- **Informatics 43: Definition of Software Engineering**
	- Software engineering is the process of constructing software, with a focus on the phases of development beyond just programming, guided by principles and qualities of enduring value.

# Lecture 2: What is Software Engineering? (cont.)

**Shawna, CEO → Business Perspective**

- Thinking about staff hours
- People being employed
- Cost, profits, and revenue
- Federal agencies and approval
- What matters most → quality

**Andy, SWE → Engineering Perspective**

- Ethical issues
- Implementation of software
- Uptime of software
- Fixing issues
- Usability issues like the one with the x-ray coming down prematurely
- Design (video games)

**Clara, Mother → User Perspective**

- Cars
	- Interface the user experiences
	- Safety of usability (being distracted while driving)
- Medical
	- How can tech help me?
- Video Games
	- Is it engaging?
	- External quality is what the user cares about

**What Part of Software Do We See?** (outside of the above)

- Electrical Engineer
- Society
- Designers
- SWE PMs
- Professor of SWE
- Students of SWE

- Many domains of software engineering → everyone looks at it differently; some things come up often across domains (e.g., profits)

**Three Essential Ingredients of Software Engineering**

1. People
	1. Everyone mentioned above
2. Process
	1. Software process models
		1. Scrum
		2. Agile
		3. Waterfall
3. Tools
	1. IDE
	2. Programming language
	3. APIs
	4. LLMs

**Software Principles**

- Core concepts that inform everything around SE

*Davis 1994*

1. Quality is number 1
2. Give products to customers early
3. Understand the problem first
4. Choose an appropriate process
5. Good management is more important than good tech
6. People are the key to success

*Royce 1998*

1. Follow architecture-first process
2. Use component-based development (buy vs. build) to reduce the coding effort
3. Show the customer preliminary versions of the software frequently
4. Have incremental releases

*Wasserman 1996*

- Modularity → [[ICS_51#Layered / Structured View|modularity in hardware layers (ICS 51)]]
- Abstraction → [[ICS_51#The M/L Hierarchy (Levels of Abstraction)|abstraction hierarchy in ICS 51]]
- User Interface (UI) Prototyping
- Reuse
- Metrics
	- Understanding the performance of our work

**INF 43 Recurring, Fundamental Principles**

- Rigor and formality → describe concepts using shared terminology
- Separation of concerns →
	- Modularity
	- Divide and conquer
	- Abstraction
		- Making it simpler to understand
- Anticipation of change
- Generality
- Incrementality

**No Silver Bullet (The Essence and Accidents of Software Engineering)**

- What are the actual issues with SE?
- Why "Silver Bullet" → Werewolf killed with a silver bullet
	- Werewolves are all of the problems
		- Delayed milestones
		- Bugs
	- There is no perfect bullet to solve them all

**Essential Problems of SE**

- Complexity
	- "...a construct of interlocking concepts: data structures and classes, algorithms, function calls."
	- "No two parts are alike."
	- That's the fundamental nature of SE → we can mitigate with abstraction → [[ICS_51#Why Use Abstraction?|how hardware uses abstraction to manage complexity]]
	- Consequences:
		- Difficult to communicate problems and solve them
- Conformity
	- Software must conform to human institutions and systems
	- Example: TurboTax changing because the laws are changing
- Changeability
	- All software gets changed
	- Why? → Due to conformity, software is supposed to change inherently
- Invisibility
	- The reality of software is not inherently embedded in space
		- Even though we can see code, the encapsulation is a human-built thing
	- Consequences:
		- Difficulty in understanding and communicating

**"False" Silver Bullets** (did not fix these issues)

- High-level languages → [[ICS_51#Bridging the Mismatch Between Humans and Computers|how high-level languages get translated down in ICS 51]]
- Time-sharing
- Unified programming environments
- Object-oriented programming
- Artificial intelligence
- Expert systems
- Automatic/graphical programming
- Program verification
- Environments/tools
- Workstations

**Potential Silver Bullets** (not really "silver bullets," but thought to greatly help)

- Buy vs. build
- Requirements refinement and rapid prototyping
- Incremental design
- Great designers

# Lecture 3: How Do We Know What to Build? (Requirements)

**Failure Readings → What's the Real Problem?**

From the articles:
- Complexity
- Conformity
- Progress is hard to measure
- Legacy systems (older systems moving to new systems)
- Hubble psychology → keep dumping money

**Shopa Failure**

- Never solidified the vision of the product
- No one inside the company really knew what they were building

**Jurgen Laartz**

- Said that half of projects deliver on budget and on time
- On average, cost overruns about 34% and projects are late
- Some are doing fine, some are doing super horribly

**2015 Chaos Report**

- 29% of projects considered successful
- 52% challenged (not on budget, not on time goals)
	- Still results in a software product
- 19% failed
- Billions wasted per year on canceled, unused, or unusable projects

**Why Requirements?**

- Let's say we want to build a to-do list app → toooo many options
- If you write requirements, it allows you to write tests and be concrete with your goals

**Top Failures**

- Not understanding the target audience → requirements issue
- Incomplete requirements or specification → requirements issue
- Constantly changing requirements or specification → requirements issue
- Lack of discipline in development process → lack of rigor/formality
- Lack of methodical usage of metrics → lack of rigor/formality
- Lack of resources

![Screenshot 2026-04-07 at 11.26.58 AM.png|334](attachment:469fdb21-fe65-40c8-9e54-e9938a77e1fc:Screenshot_2026-04-07_at_11.26.58_AM.png)

**Definition of Requirements**

- What the software should do (without saying how it should do it)
- Requirements address what the customer needs, not wants

**CHAOS Reports (More): Requirements Defects Are Expensive**

- They represent more than 70% of rework cost
- Rework consumes about 30-50% of total project budget
- Lack of user input/user involvement listed as most frequent problem

**Requirements Engineering**

*Requirements Phase — Terminology*

- **Requirements Analysis** → activity of discovering/observing/gathering customer's needs
- **Requirements Specification** → activity of describing/documenting customer's needs
	- Can also refer to the requirements document itself

**Requirements Analysis**

- Interview customer
	- think of edge cases 
- Observe customer (CNBC article)
	- Have to actually be the customer to create a good product
- Create use cases/scenarios/user stories
- Prototype solutions
- Identify important objects/roles/functions/goals
- Perform research
- Construct models

**Data-Driven Requirements Analysis**

- Usage data is analyzed and business metrics are recorded to discover the value of new (potential) features
	- Techniques
		- Data analytics
		- A/B testing
		- Prototyping
		- Market research
	- This information is used to create/prioritize/analyze/evaluate requirements

**Summary**

- Software failures can be disastrous
- Proper requirements engineering (analysis and specification) is essential
- Requirements analysis is learning what the system should do (without worrying yet about how it should do it)

# Lecture 4: Requirements Specification

**Requirements Specification**

- Serves as the fundamental reference point between customer and software producer
- Defines:
	- The what, not the how
	- Environmental requirements on the software
	- Constraints on the software
	- Software qualities

**Why Spend So Much Time on Requirements Specification?**

- It doesn't cost as much to do it now, but if you get it wrong it will definitely hurt you later (money-wise)
- Changes are cheaper now than later

**Who Uses It?**

- Everyone, to be honest

**Document Structure**

- **Introduction**
	- What is the document about
	- Who it was created for
	- Who created it
	- Outline
- **Executive summary**
	- Short, succinct, concise, to-the-point description of product
		- No more than one page
	- Identifies main goals, key features, key risks/obstacles
	- Called "executive summary" because a busy executive should be able to gloss over it
- **Application context**
	- Describes the situation in which software will be used (home, office, ...)
	- Identifies all things the system affects → objects, processes, other software, ...
- **Environmental requirements**
	- Platforms
		- Hardware → operating systems, type of machines, memory size
		- Software → web app, mobile app, open source (Linux, Apache, PHP/MySQL), enterprise (.NET), ...
	- Programming languages
	- Standards
	- Naturally, some "how" might creep in here
- **Functional requirements** (main section, so longest)
	- Identifies all concepts, functions, features, and information the system provides to its users
	- Provides an abstraction for each, characterizing properties and functions relevant to the user
		- What is the system supposed to do?
		- What information does the system need?
		- What is supposed to happen when something goes wrong?
- **Software "ilities"** (qualities)
	- Correctness, reliability, efficiency, ...
	- Helps developers assess tradeoffs in the system's implementation
- **Other requirements**
	- Catch-all for everything that didn't fit elsewhere → cost, documentation, etc.
- **Time schedule**
	- By when should all of this be done?
	- What are some important milestones to be reached?
- **Potential risks**
	- Future uncertain events with a probability of occurrence and a potential for loss
	- Any project faces risk, so it's important to identify them up front
- **Assumptions**
	- Often combined with risk → if our assumptions fall through, that's a risk
	- Factors believed to be true during the life cycle of the project
	- If changed, they may affect project outcomes negatively
- **Future changes**
	- Any project changes over time
	- Structure the requirements document so it easily absorbs changes
- **Glossary** → definition of terms used throughout
- **Reference documents** → pointers to other useful documents
- Some documents include a UI prototype section

**Observations About the Specification Document**

- Document is structured to address the fundamental principles:
	- Rigor
	- Separation of concerns → modularity, abstraction
	- Anticipation of change
	- Generality
	- Incrementality
- Not every project requires every section of the document

**Specification Methods**

- Natural language → SRS, user stories
- Diagrams → data flow, finite state machines
- Formal language → Z, TLA+
- Models → domain model (objects), usage model, goal model

**Verification**

- Is the requirements specification complete?
- Is each requirement understandable?
- Is each requirement unambiguous?
- Are any requirements in conflict?
- Can each requirement be verified?
- Are all terms and concepts defined?
- Is the requirements specification unbiased?

**Acceptance Test Plan**

- Often accompanies a requirements specification
- Specifies how it will be determined that each requirement is met
- Binds a customer to accept the delivered system if it passes all the tests
- May include:
	- Specific test cases
	- Number of test cases that will pass

**Ziv's Law** (professor here at UCI)

- Software development is unpredictable and the document artifacts such as requirements will never be fully understood
- Uncertainty is inherent and inevitable in software engineering processes and products

---

## Quiz 2 Study Guide

**Software Failure Causes & Requirements Issues**

- Top failure causes are almost all requirements-related:
	- Not understanding the target audience
	- Incomplete requirements or specification
	- Constantly changing requirements
- Lack of rigor/formality → no discipline in development process, no methodical use of metrics
- 2015 CHAOS Report → only 29% of projects successful, 52% challenged, 19% failed
- Requirements defects represent >70% of rework cost; rework consumes 30-50% of total project budget

**"Which category employs the most programmers in the US?"**

- In-house staff writing systems for internal use
- The word "customer" is arbitrary and can change depending on context

**Failure Readings — Main Ideas**

- [Minnesota DMV fiasco](https://spectrum.ieee.org/riskfactor/computing/it/minnesotas-licensing-and-registration-system-costly-chronic-fiasco) → licensing/registration system became a chronic fiasco, needed an extra $43 million to fix; failure of risk management and project oversight
- [TSB Bank failure](https://spectrum.ieee.org/riskfactor/computing/software/new-software-system-snags-tsbs-online-and-mobile-banking-customers-in-uk) → failed IT migration left tens of thousands unable to access online/mobile banking for weeks; CEO had to publicly apologize; shows critical need for proper testing and migration planning
- [Shopa failure](http://www.businessinsider.com/shopa-british-startup-winding-down-2015-8?r=UK&IR=T) → never solidified the vision of the product; no one inside the company really knew what they were building → classic requirements failure
- [Overoptimism in IT](http://spectrum.ieee.org/riskfactor/computing/it/overoptimism-plagues-it-project-plans) → large IT projects consistently suffer from delusional time/cost estimates; on average 34% cost overruns; systemic problem across healthcare, airlines, government
- [Five Enduring Government IT Failures](https://spectrum.ieee.org/five-enduring-government-it-failures) → poor planning, inadequate oversight, scope creep → massive cost overruns and abandoned systems; failures sit at the intersection of business, political, technological, and societal risks
- [CNBC — Doctors & Technologists](https://www.cnbc.com/2018/12/27/doctors-are-asking-technologists-from-google-to-shadow-them-before-they-build-medical-apps-.html) → doctors asked Google technologists to shadow them before building medical apps; you have to actually observe and understand the user's world to build the right product → ties directly to requirements analysis techniques (observation, interviews)

**Requirements — Key Concepts**

- **Definition of requirements** → what the software should do (without saying how); addresses what the customer needs, not wants
- **Requirements phase** → two activities:
	- Requirements Analysis → discovering/observing/gathering customer's needs
	- Requirements Specification → describing/documenting customer's needs
- **Techniques for requirements analysis** → interview customer, observe customer, create use cases/scenarios/user stories, prototype solutions, identify objects/roles/functions/goals, perform research, construct models, data-driven analysis
- **Sections of the requirements document** → Introduction, Executive Summary, Application Context, Environmental Requirements, Functional Requirements, Software Qualities ("ilities"), Other Requirements, Time Schedule, Potential Risks, Assumptions, Future Changes, Glossary, Reference Documents
- **Ziv's Law** → uncertainty is inherent and inevitable in SE processes and products; we won't actually fully know requirements until we build it


## Discussion 1: Project Kickoff

**Project Theme → Live Geolocation IRL Common-Interest Friend Finder**
- Think Apple's Find My Friends, except:
	- Not based on existing contacts
	- Instead based on a shared hobby, interest, or activity
- Example: want to meet other e-bike riders → subscribe to that activity and see those people's live location on the map
- Whenever you're in an area, turn it on → shows range to all people around you with similar interests

**What Are the Specifications?**
- Up to you!
- Be creative
- Each team will make different choices
- Some overlap, some difference between groups

**Optional Feature Ideas**
- Range/diameter setting → get notified when someone with common interest enters your range (notification system)
- Should the app focus on a single interest or support multiple?
- Should interests be predefined?
	- Decided by app creators (closed set)
	- Decided by users (open ended, anything)
	- Based on hashtags or other tagging
- When someone is in range, can you chat with them?
	- If multiple people in range → auto-create a groupchat?
- Filtering criteria → user-chosen or predefined?
	- e.g., age ranges
- Once joined to a group → voice chat support?
- Common interests strict or diverse?
	- Common mode → must share same interest (e.g., crocheting)
	- Diversity example → one user plays guitar, looking for a bassist
- Impromptu groups vs. planned meetups
- Sticky groups vs. dynamic (based on changing location/range/interests)
	- If you met up with a group, can you save it? Or do they drop when they leave range?
- Discovering interests of others in the area
	- Public interests (local)
	- Private interests (have to share ID)
- Ability to block a user → what happens when blocked?
- Anonymity → fully anonymous, user-chosen handle, or tied to real name?
- Location always shared, or user-controlled?
- Should location be precise?

- **Pick 5 features from the list (with rationale) + at least 2 of your own (with rationale)** → 7 total minimum, more encouraged

**Project Assignments**
- Requirements → assigned next week, due two weeks later
	- Other deadlines TBD
- Ethics report
- Architecture and internal design
- UI/UX design
- Test plan
- Final implementation / prototype demo
	- Every group must attend and present
	- Roughly half the groups will present half of these deliverables

**Logistics**
- Everyone should contribute
- All work committed to a private GitHub repo → add TA and professor as collaborators
- Documents written in Markdown
- Discussion section attendance is **mandatory** → used to meet with teams and present progress
- One absence from discussion per quarter allowed

# Lecture 5: How Do We Know What To Build?

**What Is a Use Case?**
- A textual description of a set of actions defining interactions between an actor and the system to achieve a goal
- Includes:
	- Basic functionality/goal
	- Any preconditions
	- Flow of events
	- Any postconditions
	- Any error conditions and/or alternative flows
- Use cases go hand-in-hand with requirements

**Flows**
- Flow → a sequence of steps describing an interaction between a "user" and a "system"
- A use case describes a set of flows that together accomplish a specific user "goal"

**Types of Flows**
- **Basic flow** → "happy day" scenario
- **Alternative flow** → the goal is achieved, but in an alternative way
- **Exception flow** → the goal is not achieved
- A use case should capture all possible flows → successful and unsuccessful

**Why Use Cases?**
- Other requirements engineering methods:
	- May not map well to design/code
	- May not translate well to acceptance tests
	- Can be difficult for non-experts to understand
- Use cases:
	- Map well to design and implementation constructs
	- Make it easy to verify/validate a design and implementation against user goals
	- Framed in terms of user goals and flows of events, user requests and system responses

**Why Not Use Cases?**
- Use cases are not good for specifying:
	- User interfaces
	- Data formats
	- Business rules
	- Non-functional requirements
- Produce use cases in conjunction with other requirements engineering methods

**Actors**
- Represent external entities that interact with the system
	- Human
	- Hardware
	- Another software system
- A use case is initiated by an actor (primary actor) to invoke a certain functionality in the system
- A use case is a dialogue between actors and the system
- Symbolically represented as a stick figure in use case diagrams

**Identifying Actors**
- Actors are discovered:
	- By reading system documents
	- By talking with customers and domain experts
- Useful questions for identifying actors:
	- Who uses the system?
	- Who installs the system?
	- Who starts up the system?
	- Who shuts down the system?
	- What other devices and external systems work directly with the system?
- Additional questions:
	- Who gets information from this system?
	- Who provides information to the system?
	- Does anything happen automatically at a preset time?
	- Who is interested in a certain requirement?
	- Where in the organization is the system used?
	- Who will benefit from the use of the system?
	- Who will support and maintain the system?
	- Does the system use an external resource?
	- Does one person play several different roles?
	- Do several people play the same role?
	- Does the system interact with a legacy system?

**Practice: Brainstorm Actors for a ToDo List App**
- The user (you, the person)
- Cloud storage (possibly)

**Identifying Use Cases → Useful Questions**
- What functions will the actor want from the system?
- What are the tasks of each actor?
- Does the system store information? What actors will create, read, update, or delete (CRUD) that information?
- What use cases will support and maintain the system?
- Can all functional requirements be performed by the use cases?

**Scope of a Use Case**
- WHAT, not HOW
- Use audience-friendly terminology
- Include:
	- How the use case starts and ends
	- The interactions (in sequence) between use case and actors
	- What data is needed by/exchanged during the use case
	- Basic flow
	- Alternative/exception flows (if applicable)

**Example Use Case: Buy a Product**
1. Customer browses catalog and selects items to buy
2. Customer goes to check out
3. Customer fills in shipping information
4. System presents full pricing information, including shipping
5. Customer fills in credit card information
6. System authorizes purchase
7. System confirms sale immediately
8. System sends confirmation email to customer
- **Alternative Flow (3a):** Customer is a regular (repeat) customer
	- System displays current shipping, pricing, and billing information
	- Customer may accept or override defaults → returns to step 6

**Example Use Case: Add Item Deadline**
1. User selects list item to which they want to add a deadline
2. System presents detailed view of list item (name, completed/not completed, description)
3. User selects the deadline field
4. System presents user with a way to enter a date and time
5. User enters date and time for deadline
6. System shows item with new deadline
- **Alternative Flow (5a):** User wants to add deadline to calendar
	- After adding deadline, user selects an option to post to calendar
	- System posts deadline to calendar, displays a confirmation to user
	- Returns to step 6
- **Exception Flow (5a):** Date/time is invalid
	- System notifies user that date/time is invalid, deadline not added to item

**Example Use Case: Toggle Completed State**
1. User selects list item they wish to toggle
2. System presents detailed view of list item (name, completed/not completed, description)
3. User toggles completed state
4. System shows item with new completed state
- **Alternative Flow (1a):** User swipes left on list item
	- System displays the option to toggle completed state
	- User confirms selection
	- Returns to step 4

**How to Build a Use Case**
- Name the use case
- Describe basic flow
- Add variations, if applicable:
	- Alternative flows
	- Exception flows

**Use Case Template**
- Name/title
- Description
- Revision history
- Actors
- System scope
- Goal
- Level
- Assumptions
- Relationships
- Includes
- Extends
- Extension points
- Precondition
- Trigger event
- Basic Flow 1 — Title
	- Description (steps), etc.
- Postconditions
- Alternative Flow 1 — Title
	- Description (steps)
- Alternative Flow 2 — Title
	- Description (steps)
- Alternative Flow 3 — Title
	- Description (steps)
- Exception Flow 1 — Title
	- Description (steps)
- Activity diagram
- User interface
- Special requirements
- Performance requirements
- Reports
- Data requirements
- Outstanding issues

**Use Case Diagrams**
- A graphical view of actors, use cases, and their interactions
![[Informatics_43-1776191734787.webp|500x258]]

**Air Travel Use Case Diagram**
![[Informatics_43-1776191752688.webp|500x363]]

**Incident Management Use Case Diagram**
![[Informatics_43-1776191769906.webp|500x373]]

**Library Software Use Case Diagram**
![[Informatics_43-1776191786305.webp|500x345]]

**Bringing It All Together**
- There is generally one use case model per system, consisting of:
	- Use case diagrams (one or more)
	- Textual descriptions of use cases

**Variety of Readers**
- Marketing personnel, human factors engineers, specialty engineers
- System engineers
- Reviewers
- Software devs
- System/software testers
- Project managers
- Technical writers
- ...
- Use cases are used as a unifying thread throughout development
- Use cases are used as a communication/understanding tool among diverse stakeholders

**Reminder: Fundamental Principles** (these apply to all aspects of software engineering!)
- Rigor and formality
- Separation of concerns
	- Modularity
	- Abstraction
- Anticipation of change
- Generality
- Incrementality

**Summary**
- **Use case** → textual description defining interactions between an actor and the system to achieve the primary actor's goal
	- Includes different flows (basic, alternative, exception)
- **Use case model** → diagrams + use case descriptions
- Use cases serve as a unifying thread throughout development
- Use cases serve as a communication/understanding tool among diverse stakeholders

**Reading: ACM Software Engineering Code of Ethics**
[ACM Software Engineering Code of Ethics](https://cacm.acm.org/magazines/1999/10/7800-software-engineering-code-of-ethics-is-approved/fulltext)

- ACM/IEEE **Software Engineering Code of Ethics and Professional Practices** (version 5.2), adopted in 1999 by both organizations
- Lays out **8 core principles** that software engineers should follow, ordered by priority:
	1. **Public** → serve the public interest, ensure safety, protect privacy, don't harm the environment. Duty to speak up if something's wrong (whistle-blowing clauses)
	2. **Client & Employer** → act in their best interests, but never at the expense of the public. Keep confidential info private, flag failing projects early, avoid conflicts of interest
	3. **Product** → maintain high professional standards. Honest cost/schedule estimates, thorough testing, proper documentation, treat maintenance with the same seriousness as new development
	4. **Judgment** → stay objective and independent. No bribery, no deceptive financial practices, no signing off on work you don't understand
	5. **Management** → promote ethical practices, give realistic estimates, offer fair pay, never punish someone for raising ethical concerns
	6. **Profession** → protect the reputation of software engineering. Report violations of the Code
	7. **Colleagues** → be fair, give credit, help each other grow professionally, don't sabotage anyone's career
	8. **Self** → commit to lifelong learning, don't let personal biases affect decisions (clause 8.07 is intentionally open-ended for future social concerns), hold yourself to the Code's standards
- **Key takeaway** → **public welfare is the ultimate tiebreaker** in every decision
- The Code isn't a rigid algorithm but a framework for ethical judgment
- Developed by a multinational task force — unique in being adopted by two major international computing societies

---

# Lecture 6: How Should I Conduct Myself While Building Software?

**Last Lecture Recap**
- **Use case** → textual description defining interactions between an actor and the system to achieve the primary actor's goal
	- Includes different flows (basic, alternative, exception)
- **Use case model** → diagrams (actors, use cases, relationships, system boundary) + use case descriptions
- Use cases serve as a unifying thread throughout development
- Use cases serve as a communication/understanding tool among diverse stakeholders

**Do Cool Things That Matter / Don't Do Bad Things**
- Think and learn about the social responsibility of software engineering
	- Examples of software with ethical implications:
		- Social media
		- Car software
		- Video games
		- Dating sites
		- Employment sites
		- Gambling sites

**Why Ethics Matters**
- Software impacts society
- Failures cause harm
- Engineers have responsibility

**ACM/IEEE Software Engineering Code of Ethics**
- **Background** → developed by ACM & IEEE, multinational task force, approved professional standard
- **Purpose** → guide ethical decisions, define responsibilities, educate professionals

**The 8 Principles (in priority order)**
1. **Public** → act in the public interest
	- Disclose dangers to users/public
	- Approve software only if safe
	- Consider privacy and fairness
	- Report significant risks
2. **Client & Employer** → act in their best interest
	- Maintain confidentiality
	- Be honest about limitations
	- Avoid conflicts of interest
	- Do not use employer resources improperly
3. **Product** → strive for high quality and reliability
	- Use appropriate testing and validation
	- Document properly
	- Ensure maintainability
	- Fix known defects before release
4. **Judgment** → maintain integrity and independence
	- Avoid deceptive practices
	- Disclose conflicts of interest
	- Base decisions on evidence
	- Reject bribery or undue influence
5. **Management** → promote ethical development practices
	- Ensure realistic schedules
	- Provide proper resources
	- Support quality assurance
	- Encourage reporting of concerns
6. **Profession** → advance integrity of the profession
	- Follow standards and best practices
	- Contribute to public understanding
	- Avoid discrediting the field
	- Support ethical policies
7. **Colleagues** → be fair and supportive
	- Credit others' work
	- Review work constructively
	- Avoid discrimination
	- Help colleagues develop skills
8. **Self** → engage in lifelong learning
	- Improve technical competence
	- Know limits of expertise
	- Seek feedback and improvement
	- Act with personal integrity

**Summary**
- **Ethics in SE** → software engineers have a responsibility to the public, clients, colleagues, and themselves
- **The Code** → 8 principles ordered by priority, with **public welfare as the ultimate tiebreaker**
- **Not a rigid rulebook** → a framework for ethical judgment and professional conduct
- Know the principles and be able to apply them to real-world ethical scenarios

---

## Quiz 3 Review

**Use Cases (Lectures 4-5)**
- **Use case** → textual description defining interactions between an actor and the system to achieve the primary actor's goal
- **Actors** → primary actor (initiates the use case to achieve a goal) vs. supporting actors (help the system fulfill the use case)
	- Actors can be people, organizations, or other systems
- **Three types of flows:**
	- **Basic flow** → the "happy path," everything goes right
	- **Alternative flow** → valid deviations from the basic flow (different but still successful)
	- **Exception flow** → something goes wrong, system handles the error
- **Use case descriptions** → structured text documenting a use case (name, actors, preconditions, flows, postconditions)
- **Use case diagrams** → visual representation of the use case model
	- Components: actors (stick figures), use cases (ovals), system boundary (rectangle), relationships (lines/arrows)
	- Relationships: association, include (`<<include>>`), extend (`<<extend>>`), generalization
- **Purposes/uses of use cases:**
	- Communication tool among diverse stakeholders
	- Unifying thread throughout development (requirements → design → testing)
	- Help discover and document requirements
	- Basis for test case development

**Ethics (Lecture 6 + Reading)**
- Know the **8 principles** of the ACM/IEEE Software Engineering Code of Ethics (Public, Client & Employer, Product, Judgment, Management, Profession, Colleagues, Self)
- Understand that **public welfare takes priority** over all other concerns
- Be able to **assess basic ethical issues** → given a scenario, identify which principle(s) apply and whether a behavior is ethical or not
- The Code is a **framework for judgment**, not a checklist

# Lecture 7: How Do We Structure the Software?

**From Requirements to Structure**
- After getting enough requirements, what's next?
- Option One:
![[Informatics_43-1776794633338.webp|500x323]]
- Another possibility:
![[Informatics_43-1776794666060.webp|500x324]]

**Software Architecture**
- Requirements → Architecture & Design → Code

**Analogy to Building Architecture**
- The architect has a distinctive role and character in a project
	- broad training
	- extensive experience
	- deep understanding of the domain
	- leads the team
	- good communicator
	- decision maker
	- deals with a higher level of abstraction than those performing construction
	- often serves as the interface to key business stakeholders/customers

**Limitations of the Analogy**
- The nature of software is different from that of building architecture
	- software serves a much broader range of purposes
	- we know much more about buildings than software
	- software is much more malleable than physical materials
	- software is a machine
	- software is invisible

**Why Architecture in Software Engineering?**
- intellectual control
- conceptual integrity
- effective project communication
- reusability
- maintainability (management of a set of variant systems)

**Defining Software Architecture**
- Software architecture → the set of principal design decisions about the system
![[Informatics_43-1776795089648.webp|500x239]]
- Software architecture → the blueprint for a software system's construction and evolution
![[Informatics_43-1776795116658.webp|500x233]]

Other definitions:
- The set of structures needed to reason about the system, which comprise software elements, relations among them, and properties of both
- How your whole system (in the widest possible sense) will be decomposed into processes or services; how data are stored, communicated, and processed; and how all parts fit together to deliver the required functionality, reliability, capacity, scalability, maintainability, and portability
- The highest-level breakdown of a system into its parts; the decisions that are hard to change
- The clear definition of multiple high-level components that, when working together, form your system and solve your problem

**Architecture in Action: Email**
- Functional specification:
	- send and receive messages
	- get your own messages and not others (addressing scheme)
	- store messages
	- electronic
	- block spam
![[Informatics_43-1776795292809.webp|500x329]]

**Architecture in Action: WWW**
![[Informatics_43-1776795315557.webp|500x277]]![[Informatics_43-1776795323760.webp|500x280]]
![[Informatics_43-1776795330828.webp|500x328]]

WWW in a (big) nutshell:
- The web is a collection of resources, each with a unique name (URL)
- A URL can be used to determine the identity of a machine on the internet (origin server), from which the resource may be obtained
- Clients (user agents / web browsers) make requests of servers for their resources
- Clients manipulate representations of resources
- All communication between user agents and origin servers must be performed by a simple, generic protocol (HTTP)
- All communication between user agents and origin servers must be fully self-contained

Observations about WWW's architecture:
- There is no single piece of code that implements the architecture
- Stylistic constraints of the web's architectural style are not apparent in the code
- One of the world's most successful applications is only understood adequately from an architectural vantage point
- All of the diagrams and text on the previous several slides = WWW's architecture (also known as the REST reference architecture)

**Architecture in Action: Facebook**
- Functional requirements:
	- friends list
	- status updates
	- news feed
	- comments / likes / reactions
	- messaging
	- photos
	- location services
	- 3rd party apps
- Non-functional requirements:
	- efficiency / performance
	- scalability
	- availability
	- security
	- privacy
	- reliability
	- portability

**Client–Server Architecture**
- Most common distributed system architecture
- Clients make requests of servers
- Centralized
	- data
	- security
	- access
![[Informatics_43-1776795618026.webp|500x335]]
![[Informatics_43-1776795638698.webp|500x418]]

**Real-World Architecture Diagrams**

Netflix architecture diagram:
![[Informatics_43-1776795718974.webp|500x296]]

Reddit architecture diagram:
![[Informatics_43-1776795731259.webp|500x251]]

**Software Architecture Elements**
- A software architecture consists of:
	- components
	- connectors
- Components and connectors are arranged into **configurations**

**Architectural Erosion**
- **Prescriptive architecture** → as-designed / as-intended architecture
- **Descriptive architecture** → as-implemented / as-realized architecture

Linux → prescriptive architecture
![[Informatics_43-1776795825843.webp|500x306]]
Linux → descriptive architecture
![[Informatics_43-1776795844276.webp|500x269]]

iRods → prescriptive architecture
![[Informatics_43-1776795861008.webp|500x313]]
iRods → descriptive architecture
![[Informatics_43-1776795875989.webp|500x406]]

Erosion in practice:
- When a system evolves, ideally its prescriptive architecture is modified first
- In practice, the system — and thus its descriptive architecture — is often directly modified

Why does architectural erosion happen?
- developer sloppiness
- short deadlines
- lack of (documented) prescriptive architecture
- code optimization
- inadequate techniques or tool support

**Summary**
- Software architecture is a very powerful tool in software engineering
	- intellectual control, conceptual integrity, communication, reusability, maintainability
- A software system's architecture is:
	- the set of principal design decisions about the system
	- the blueprint for its construction and evolution
- A software architecture consists of **components** and **connectors**, arranged into **configurations**
- **Architectural erosion** happens when a system evolves and its prescriptive architecture is not updated

# Lecture 8: How Do We Structure the Software? (Part 2)

**Software Architectural Style**
- Just like there are different architectural styles for real-world buildings, there are different software architectural styles
- **SAS** → a named collection of architectural design decisions that
	- are applicable in a given development context
	- constrain architectural design decisions
	- result in beneficial qualities in each resulting system
- A named, commonly used set of components/connectors/configurations
	- each component/connector has its own job

**Model-View-Controller (Example 2: ATM)**
- Goals
	- withdrawals, deposits, transfers, balance checks
	- separation of concerns
		- want to experiment with different UIs
		- isolate business rules (due to frequent anticipated changes)
![[Informatics_43-1776967571375.webp|500x257]]
![[Informatics_43-1776967580699.webp|500x544]]
- The view and controller portion of the top is the user interface
- Key benefits of MVC
	- modularity
	- anticipation of change

**Client-Server (Example 3: Video Game)**
- Goals
	- multiplayer, online
	- control access to data and players
![[Informatics_43-1776967651132.webp|500x236]]
- Key benefits of client-server
	- sharing data and services over a wide range of clients
	- centralized control over access, functionality, data

**Cloud Computing has Changed Client-Server**
- Most modern client-server applications run on servers in the cloud
	- software developers no longer have to manage physical servers
	- instead, they are managed by a third party
	- many cloud providers also provide application services
- Started by AWS (Amazon Web Services)
- Benefits
	- scalability
	- more computing power
	- cost-effective
- Drawbacks
	- security/privacy
	- may not be cost-effective

**Layered (Example: Restaurant)**
- Goals
	- prepare and serve food to customers
	- enforce specific protocols of interaction
		- abstract away irrelevant details
		- minimize the effects of changes
	- separate concerns: keep each part focused on a specific task
- person eating ↔ server ↔ chef ↔ farm

Layered Example (Android)
![[Informatics_43-1776967882303.webp|500x360]]
- Key benefits of layers
	- modularity
	- abstraction
	- anticipation of change
	- reuse

**Peer-to-Peer**
- Goals (Skype)
	- online (multi-person) video chat and voice calls
	- share same functionality between multiple people without slowing down video/audio streaming
![[Informatics_43-1776967981830.webp|500x299]]
- Key benefits
	- efficient
	- robust

**Pipe and Filter (Compiler)**
- takes in code → compiler → spits out binary
- Goals
	- translate a high-level programming language into a low-level one that a computer can execute
	- separate different steps of translation so I can add/edit/remove/replace steps easily
![[Informatics_43-1776968053896.webp|500x282]]
![[Informatics_43-1776968064110.webp|500x281]]
- Key benefits
	- modularity
	- reuse
	- anticipation of change

**Publish and Subscribe (Stock Market Ticker)**
- Goals
	- filter through enormous amounts of info (stock prices) and only broadcast info that a subscriber is interested in
![[Informatics_43-1776968118846.webp|500x255]]
- Key benefits
	- efficiency
	- scalability

**Mixing Styles is Often Necessary**
![[Informatics_43-1776968133829.webp|500x269]]

**Evolution**
- All successful software evolves
- Essential part of software development
- Must be accommodated/planned for as much as possible
- Architecture is a key tool in accommodating evolution

**Trend: From Monolithic Towards Microservices**
- **Monolithic** → one big unified codebase
	- simple to develop and deploy
	- works for small teams / simple apps
	- everything ships together → one bug or change can affect the whole system
- **Microservices** → app split into small, independent services
	- each service can be scaled, deployed, and updated independently
	- different services can use different tech stacks
	- better fit for large, complex systems
	- tradeoff → more operational complexity (networking, monitoring, coordination)
![[Informatics_43-1776968239296.webp|500x441]]

**Reminder: Recurring Fundamental Principles**
- Rigor and formality
- Separation of concerns
	- modularity
	- divide and conquer
	- abstraction
- Anticipation of change
- Generality
- Incrementality

How do these relate to software architecture?
- **Rigor and formality** → architecture forces us to make principal design decisions explicit instead of leaving them implicit in the code
- **Separation of concerns** → components and connectors split the system so each piece has one job (MVC, layered, pipe-and-filter all do this)
- **Anticipation of change** → choosing a style up front is a bet about *what kinds of change* the system will need to absorb (new UIs → MVC, new translation steps → pipe-and-filter)
- **Generality** → styles themselves are general patterns, reusable across many systems and domains
- **Incrementality** → architecture lets us build and evolve the system piece by piece (add a new layer, swap a filter, add a new subscriber) without rewriting everything

**Summary**
- An architectural style is
	- a named collection of architectural design decisions that result in beneficial qualities in each resulting system
- Styles → model-view-controller, client-server, layered, peer-to-peer, pipe and filter, pub-sub
	- there are more styles
- All successful software evolves
	- we must plan for this
	- architecture helps us do so

**Quiz 4 Topics**
- Understand what software architecture is
	- the set of principal design decisions about the system
	- blueprint for construction and evolution
- Elements of software architecture
	- **components** → units of computation/data with a specific job
	- **connectors** → mechanisms that mediate interaction between components
	- **configurations** → arrangements of components and connectors into a working system
- Architectural erosion (prescriptive vs descriptive architecture)
	- **prescriptive** → the architecture as designed/intended
	- **descriptive** → the architecture as it actually exists in the implemented system
	- **erosion** → when the system evolves and the prescriptive architecture is not updated to match → the two drift apart
- Know and understand the 6 architectural styles
	- **MVC** → separates data (model), presentation (view), and input handling (controller) → modularity, anticipation of change
	- **Client-Server** → centralized server provides data/services to many clients → sharing, centralized control
	- **Layered** → strict hierarchy of layers, each only talks to adjacent layers → modularity, abstraction, reuse
	- **Peer-to-Peer** → equal nodes share functionality directly → efficient, robust
	- **Pipe and Filter** → data flows through a sequence of filters connected by pipes → modularity, reuse, swappable steps
	- **Publish-Subscribe** → publishers broadcast events, subscribers only receive what they care about → efficiency, scalability
- Know that mixing styles is normal in real systems
- Understand why all successful software evolves and how architecture helps plan for it

# Lecture 9: How Do We Structure the Software in Detail? (Part 1)

**Last Lecture Recap**
- An architectural style → a named collection of architectural design decisions that result in beneficial qualities in each resulting system
- Styles: MVC, client-server, layered, peer-to-peer, pipe and filter, publish-subscribe (there are more)
- All successful software evolves → we must plan and account for this → architecture helps us do so

**Design Phase of Software Engineering**
- requirements → architecture & design → code

![[Informatics_43-1777399541918.webp|500x266]]

- requirements (what) → design (how) → implementation → verification → maintenance

**Software Design Goals/Activities**
- Making system-wide decisions
	- architecture, languages, libraries, platforms, communication protocols
- Making lower-level decisions in an iterative manner
	- studying the problem
	- identifying solutions
	- creating abstractions
	- evaluating

**Some Approaches to Software Design**
- Software architecture
- Functional decomposition
- Relational database design
- Object-oriented design and UML
- User interface design
- Sketching → lecture 10

**Functional Decomposition**
- Design process led by breaking down the functionality

![[Informatics_43-1777399726890.webp|500x290]]

**Relational Database Design**
- Design process led by breaking down the data

![[Informatics_43-1777399755951.webp|500x283]]

**Object-Oriented Design and UML**
- Design process led by breaking down the entities identified in the domain and the functionality that accompanies each entity
- An "object" contains both data and methods
- A "class" is a blueprint for making objects

![[Informatics_43-1777399830539.webp|500x257]]

**User Interface Design**
- Design process led by envisioning the user interface and iterating

![[Informatics_43-1777399853989.webp|500x337]]

**Designs**
- Think of architecture designs and blueprints
- Models also get created

![[Informatics_43-1777399889891.webp|500x270]]

- ^ is a UML diagram

**Purpose of Designs**
- Designs to think
- Designs to talk
- Designs to prescribe
- Designs are developed iteratively

**Abstraction**
- Abstractions are formed by removing irrelevant information and retaining/highlighting relevant information
- Every design notation supports a certain kind of abstraction
- Software engineering is all about constructing and elaborating abstractions/models

**Summary**
- Design phase of software engineering → the **how** to the **what** of requirements
	- Architecture, functional decomposition, relational database design, OO design/UML, UI design, sketching
- Designs are used iteratively to think, talk, and prescribe
- Software engineering is all about constructing and elaborating abstractions/models

# Lecture 10: How Do We Structure the Software in Detail? (Part 2)

**Last Lecture Recap**
- Design phase of software engineering → the "how" to the "what" of requirements
	- Architecture, functional decomposition, relational database design, OO design/UML, UI design, sketching
- Designs are used iteratively to think, talk, and prescribe
- Software engineering is all about constructing and elaborating abstractions/models

**Software Design Recap**
- All creative decisions, includes high-level and low-level
- Different notations and models allow designers to focus on a perspective, while freed from thinking of others
- Design is used to:
	- Think
	- Talk
	- Prescribe

**Design Notations**
- "By relieving the brain of all unnecessary work, a good notation sets it free to concentrate on more advanced problems, and in effect increases the mental power of the race." — A.N. Whitehead (1911)

**Software Development Languages**
- Different languages are used at different stages
- Requirements → Design → Coding/Testing
- English → Diagrams/UML → Java, Python
- The diagrams/UML are design notations

**UML (Unified Modeling Language)**
- Industry standard for software design/modeling
- Different types of UML diagrams are used to represent different aspects of a system (structure, behavior, interactions)
	- Class diagrams
	- Activity diagrams
	- Sequence diagrams
	- Use case diagrams

**UML Class Diagrams**
- Used in decomposing a system into modules known as classes
- Typically used to:
	- Model domain concepts
	- Create a detailed, object-oriented design of the code
![[Informatics_43-1777572488984.webp|500x251]]

Visibility notation:
- `+` → public visibility
- `-` → private visibility
![[Informatics_43-1777572516123.webp|500x260]]

**Translation to Code**
![[Informatics_43-1777572534036.webp|500x378]]

**Relationships Between Classes**
- Inheritance
- Association
	- Multiplicity
- Whole-part (aggregation and composition)

**Relationships: Inheritance**
![[Informatics_43-1777572580106.webp|500x878]]

**Association Relationships**
![[Informatics_43-1777572596475.webp|500x315]]

**Multiplicity Examples**
![[Informatics_43-1777572608491.webp|500x330]]

**Relationships: Aggregation**
- One object contains (or is composed of) a set of other objects
- Aggregation relationships are transitive and asymmetric
![[Informatics_43-1777572641802.webp|500x684]]

**Relationships: Composition**
- A variant of aggregation which adds the property of existence dependency
![[Informatics_43-1777572669852.webp|500x761]]

**Example: UML Class Diagrams**
![[Informatics_43-1777572684538.webp|500x280]]
![[Informatics_43-1777572696970.webp|500x292]]
![[Informatics_43-1777572704655.webp|500x282]]

**Other UML Diagrams** (besides class diagrams)
- Activity diagrams
- Sequence diagrams
- Use case diagrams

**Example: UML Activity Diagram**
![[Informatics_43-1777572742117.webp|500x389]]

**Example: UML Sequence Diagram**
![[Informatics_43-1777572759171.webp|500x359]]

**Example: UML Use Case Diagram**
![[Informatics_43-1777572770026.webp|500x358]]

**Other Diagrams → User Interface Mockups**
![[Informatics_43-1777572784885.webp|500x344]]
![[Informatics_43-1777572801874.webp|500x451]]

**Other Diagrams → Pseudocode**
![[Informatics_43-1777572822650.webp|500x289]]

**Other Diagrams → Entity Relationship Diagram**
![[Informatics_43-1777572843782.webp|500x324]]

**Other Diagrams → Architecture Diagrams**
![[Informatics_43-1777572855403.webp|500x297]]

**Other Diagrams → Storyboard**
![[Informatics_43-1777572871054.webp|500x383]]

**Other Diagrams → Sketches**
![[Informatics_43-1777572886021.webp|500x441]]

**What is Software Engineering?**
- Software engineering is the process of building a set of related models that represent the system-to-be

**Design Principles**
- High cohesion / low coupling
- Information hiding

**High Cohesion / Low Coupling**
- **High cohesion** → grouping related functionality
- **Low coupling** → ungrouping unrelated functionality / reducing interdependency
- Effects:
	- Changes don't propagate
	- Reuse is facilitated
![[Informatics_43-1777572985582.webp|500x271]]

**Information Hiding**
- Hide design decisions that are most likely to change, thereby protecting other parts of the program from change if the design decision is changed
- "Showing only those details to the outside world which are necessary for the outside world and hiding all other details from the outside world"

**Summary**
- Every design notation supports an abstraction
- A design diagram is a statement in a language that has a syntax
	- UML diagrams, UI mockups, pseudocode, ER diagrams, architecture diagrams, storyboards, sketches
- Software engineering is the process of building a set of related models that represent the system-to-be

---

## Quiz 5 Study Guide

**Six Approaches to Software Design**
- **Software architecture** → high-level structure of the system (components, connectors, configurations)
- **Functional decomposition** → break the system down by functionality, top-down
- **Relational database design** → break the system down by data and the relationships between data entities
- **Object-oriented design (UML)** → break the system down by domain entities; each object bundles data and methods, classes are blueprints for objects
- **User interface design** → drive the design from the user-facing experience and iterate on UI mockups
- **Sketching** → informal, low-fidelity drawings used to think and communicate early in design

**Purpose of Design**
- **Think** → designs help you reason about the problem and explore solutions
- **Talk/communicate** → designs are a shared language for stakeholders, devs, and testers
- **Prescribe** → designs specify what should be built and how

**Abstraction**
- Formed by removing irrelevant information and retaining/highlighting relevant information
- Every design notation supports a certain kind of abstraction
- Software engineering is all about constructing and elaborating abstractions/models

**UML Class Diagrams**
- Used to decompose a system into classes, model domain concepts, and produce a detailed OO design
- Visibility: `+` public, `-` private
- **Relationships:**
	- **Inheritance** → "is-a" relationship between subclass and superclass
	- **Association** → general relationship/link between classes
		- **Multiplicity** → annotates how many instances participate (e.g., `1`, `0..1`, `1..*`, `*`)
	- **Aggregation** → whole-part, transitive and asymmetric; parts can exist independently of the whole
	- **Composition** → stronger aggregation with existence dependency; parts cannot exist without the whole

**Design Principles**
- **High cohesion** → group related functionality together inside a module
- **Low coupling** → reduce interdependency between modules
	- Effects → changes don't propagate, reuse is facilitated
- **Information hiding** → hide design decisions most likely to change; expose only what the outside world needs
	- Protects other parts of the program from change when the hidden decision changes

<!-- last cleaned: end of Lecture 10 (UML Class Diagrams & Design Principles) -->
