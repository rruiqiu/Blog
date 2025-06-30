## SDLC - The Software Development Lifecycle

### What is Software Engineering

| **Topic**                              | **Description / Key Points**                                 |
| -------------------------------------- | ------------------------------------------------------------ |
| **Definition**                         | Software engineering is the application of scientific and engineering principles to the design and development of software. |
| **Origins & Evolution**                | - Emerged in the 1960s<br>- Addressed inefficiencies in early software development<br>- Triggered by the “Software Crisis” (mid-1960s to mid-1980s) |
| **The Software Crisis**                | - Software projects were over-budget, late, and unreliable<br>- Lack of formal process<br>- Prompted need for disciplined engineering approaches |
| **Crisis Solution**                    | - Standardized methodologies (e.g. SDLC)<br>- Use of CASE tools (e.g., debugging, project management, validation) |
| **CASE Tool Categories**               | - Business analysis<br>- Development tools<br>- Validation & verification<br>- Configuration management<br>- Metrics<br>- Project management |
| **Software Engineer Responsibilities** | - Design, build, maintain systems<br>- Write and test code<br>- Consult with stakeholders, vendors, security experts |
| **Engineer vs. Developer**             | - Engineers take a **system-wide** view, focused on architecture and scalability<br>- Developers focus on **specific features/functionality** |
| **Modern Practice**                    | Guided by the **Software Development Life Cycle (SDLC)** to ensure quality and structure in software development |



### Phases in the SDLC

#### Intro

The **Software Development Life Cycle (SDLC)** is a systematic process used to develop high-quality software efficiently, on time, and within budget. It is designed to ensure that software products meet business and technical requirements through a structured set of phases and deliverables.

Originally formalized in the **1960s** during a time of increasing software complexity, the SDLC started with the **Waterfall model**, a linear approach. Over time, it evolved into more **iterative and adaptive methodologies** to support changing customer needs.

#### Key Benefits

- **Structured Workflow:**
   Provides a consistent roadmap for development, helping teams avoid ad hoc or chaotic processes.
- **Clearly Defined Phases:**
   Each phase (planning, design, development, etc.) is well-documented, allowing teams to understand what to focus on at each stage.
- **Improved Communication:**
   Enhances collaboration among developers, stakeholders, and customers. Everyone understands their role and when their input is required.
- **Iterative Capability:**
   Supports revisiting previous stages to adapt to new requirements or feedback, increasing flexibility.
- **Early Problem Detection:**
   Identifies issues during early stages like planning or design, reducing costly fixes later in development.
- **Defined Roles:**
   Assigns clear responsibilities to each team member, minimizing conflict and improving productivity.

The SDLC offers a **disciplined approach** to software development. It reduces risk, improves efficiency, fosters clear communication, and supports adaptability. As projects grow more complex, the SDLC remains a vital tool for aligning business goals with technical execution.

#### The Six SDLC Phases

| **Phase**       | **Purpose**                         | **Key Activities**                                           | **Output**                                |
| :-------------- | ----------------------------------- | ------------------------------------------------------------ | ----------------------------------------- |
| **Planning**    | Define and document requirements    | Identify users, goals, inputs/outputs<br>Estimate resources, costs, schedule<br>Build prototypes if needed | Software Requirements Specification (SRS) |
| **Design**      | Architect the software solution     | Design system structure<br>Create design document<br>Review with stakeholders | Design Document                           |
| **Development** | Build the software based on design  | Assign coding tasks<br>Write code using appropriate tools<br>Follow organizational coding standards | Working Code                              |
| **Testing**     | Verify functionality and quality    | Conduct unit, integration, system, and acceptance tests<br>Fix bugs<br>Retest for stability and compliance | Tested and Stable Code                    |
| **Deployment**  | Release software to users           | Release to UAT environment<br>Gain stakeholder sign-off<br>Deploy to production via web, app store, or internal tool | Live Software in Production               |
| **Maintenance** | Support and improve post-deployment | Monitor for bugs<br>Identify UI issues and enhancements<br>Feed updates into future development cycles | Updated Requirements / Next Iteration     |

The SDLC offers a **repeatable framework** for managing software development through distinct, manageable phases. From requirement gathering to ongoing support, each phase contributes to building robust and adaptable software solutions. By incorporating stakeholder feedback and iterative design, teams can continuously improve their products throughout the software lifecycle.



### Key Processes in Building Quality Software

| **Process**                | **Purpose**                                                 | **Key Practices / Elements**                                 |
| -------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| **Requirements Gathering** | Define what the software must do                            | - Create Software Requirements Specification (SRS)<br>- Include use cases<br>- Identify functional, UI, system, and non-functional requirements |
| **Design**                 | Translate requirements into technical architecture          | - Break down requirements into components<br>- Define system structure, APIs, UI, and database<br>- Ensure performance and security planning |
| **Coding for Quality**     | Write clean, maintainable, and error-resistant code         | - Follow coding standards and styles<br>- Use linters to detect issues<br>- Write comments and documentation in code |
| **Testing**                | Verify software meets requirements and is free of bugs      | - Perform unit, integration, system, and UAT(User Acceptance Testing) testing<br>- Use functional, non-functional, and regression test types |
| **Releases**               | Distribute software in controlled phases                    | - Alpha: early internal version<br>- Beta: external limited testing<br>- GA: general availability to all users |
| **Documentation**          | Provide guidance for both technical and non-technical users | - System docs: README, architecture, maintenance guides<br>- User docs: manuals, videos, help tools |



### Requirements Gathering

- The **requirements process** is iterative and critical to aligning software with business and user needs.
- **SRS**: Focuses on software functionality and performance.
- **URS**: Captures user goals in use-case format.
- **SysRS**: Covers system-wide constraints, including hardware and policy requirements.

| **Topic**                                    | **Purpose / Description**                                 | **Key Details**                                              |
| -------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| **Requirement Gathering Steps**              | Define the problem and document a solution plan           | 1. Identify stakeholders<br>2. Establish goals and objectives<br>3. Elicit requirements<br>4. Document requirements<br>5. Analyze and confirm<br>6. Prioritize |
| **Stakeholders**                             | Identify individuals/groups affected by the software      | Includes decision-makers, end-users, system admins, engineering, sales, marketing, and support |
| **Goals vs. Objectives**                     | Goals = broad outcomes<br>Objectives = measurable actions | Goals guide long-term vision<br>Objectives help achieve those goals |
| **Elicitation Methods**                      | Gather raw requirements from stakeholders                 | Surveys<br>Interviews<br>Questionnaires                      |
| **Requirement Confirmation**                 | Ensure requirements are accurate and agreed upon          | Analyze for clarity, consistency, and completeness<br>Reviewed and approved by stakeholders |
| **Prioritization Labels**                    | Rank requirements to manage delivery focus                | “Must-have”, “Highly desired”, “Nice to have”                |
| **SRS (Software Requirement Specification)** | Captures all technical/software needs                     | Includes:<br>- Purpose, scope<br>- Constraints, assumptions, dependencies<br>- Functional<br>- External Interface<br>- System Features<br>- Non-functional |
| **URS (User Requirement Specification)**     | Describes end-user needs using stories or use cases       | Answers:<br>Who is the user?<br>What function is needed?<br>Why is it needed?<br>Validated via User Acceptance Testing (UAT) |
| **SysRS (System Requirement Specification)** | Broadest doc outlining the full system requirements       | Includes:<br>- Capabilities<br>- Interfaces<br>- Policy, regulatory, performance, personnel, and security needs<br>- Hardware/software expectations and acceptance criteria |



### Software Development Methodologies

| **Methodology** | **Structure**                                                | **Pros**                                                     | **Cons**                                                     |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Waterfall**   | - Sequential<br>- Each phase completed before the next begins<br>- No overlap between stages | - Simple and easy to understand<br>- Clearly defined stages<br>- Easier budget estimation | - Inflexible to changes<br>- Late customer feedback<br>- Long development cycles |
| **V-Model**     | - Extension of Waterfall<br>- “V” shape: Left = Verification, Right = Validation<br>- Test plans created early | - Clear mapping of testing to development<br>- Saves time during validation<br>- Structured | - Very rigid<br>- Changes are hard to accommodate after testing begins |
| **Agile**       | - Iterative and cyclical<br>- Work in short sprints (1–4 weeks)<br>- Continuous feedback loop | - Adapts easily to changing requirements<br>- Early and frequent delivery of working software | - Hard to estimate total cost/scope early<br>- Requires high stakeholder involvement |



### Software Testing

| **Category / Level**       | **Purpose**                                                  | **Key Characteristics**                                      |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Functional Testing**     | Verify that software meets functional requirements           | - Based on inputs/outputs (black box)<br>- Tests usability and accessibility<br>- Can be manual or automated |
| **Non-Functional Testing** | Evaluate software’s quality attributes                       | - Tests performance, scalability, security, recovery, documentation consistency, cross-platform behavior |
| **Regression Testing**     | Ensure recent changes haven't broken existing functionality  | - Triggered by bug fixes or requirement changes<br>- Prioritize frequently failing, complex, or recently modified test cases |
| **Unit Testing**           | Validate individual components (functions/modules)           | - Done by developers<br>- Detects construction errors early<br>- Increases development efficiency |
| **Integration Testing**    | Detect errors between combined modules                       | - Black-box testing<br>- Checks interaction between modules, databases, external systems<br>- Finds logic or exception mismatches |
| **System Testing**         | Verify the complete integrated software against all requirements | - Conducted in a staging environment<br>- Includes both functional and non-functional tests |
| **Acceptance Testing**     | Confirm the software meets user/business needs               | - Final validation by users or stakeholders<br>- Done during maintenance or before production rollout |



### Software Documentation

| **Category**                             | **Purpose**                                                  | **Target Audience**                       | **Examples / Notes**                                         |
| ---------------------------------------- | ------------------------------------------------------------ | ----------------------------------------- | ------------------------------------------------------------ |
| **Documentation Formats**                | Methods to deliver information about software                | All users                                 | Written<br>Video<br>Graphical                                |
| **Product Documentation**                | Describes what the software is and how it functions          | Developers, QA, End Users, Stakeholders   | Includes: Requirements, Design, Technical, QA, and User documentation |
| **Process Documentation**                | Describes how to perform a task or follow a workflow         | Developers, Admins, QA                    | Includes process overviews, often paired with SOPs           |
| **Requirements Docs**                    | Define expected functionality of software                    | Developers, Architects, QA                | SRS, URS, SysRS                                              |
| **Design Docs**                          | Explain how the software will be built                       | Architects, Developers                    | Conceptual and technical designs                             |
| **Technical Docs**                       | Help understand and maintain the codebase                    | Developers                                | Code comments, working papers, engineering notes             |
| **QA Documentation**                     | Outline testing strategy, execution, and metrics             | QA Engineers                              | Test plans, test cases, strategies, traceability matrices    |
| **User Documentation**                   | Guide end users on software use and troubleshooting          | End Users                                 | FAQs, tutorials, manuals, help guides                        |
| **SOPs (Standard Operating Procedures)** | Detailed step-by-step guide for org-specific tasks           | Internal teams (e.g., engineers, testers) | Flowcharts, outlines, or written steps<br>e.g., code merge procedures |
| **Maintenance Note**                     | Documentation must stay up-to-date, especially after UI changes | All stakeholders                          | Updated during the **maintenance phase** of the SDLC         |



### Software Versions

| **Topic**                | **Description / Purpose**                                    |
| ------------------------ | ------------------------------------------------------------ |
| **Definition**           | A system for tracking changes, updates, and patches to programs and applications |
| **Common Formats**       | - Typically use 2, 3, or 4 numbers (e.g., 1.2.0.5)<br>- Numbers are separated by periods |
| **Semantic Versioning**  | A common structure with 4 parts:<br>1. Major (new release)<br>2. Minor (small updates)<br>3. Patch (bug fixes)<br>4. Build (less significant/internal) |
| **Alternate Formats**    | Some developers use **date-based** versions (e.g., Ubuntu 18.04.2 = Year 2018, April, update 2) |
| **Finding Version Info** | Typically found under **Help > About** in applications (e.g., in Chrome, via menu > Help > About) |
| **Beta/Test Versions**   | Versions under 1.0 (e.g., 0.9) indicate the software is in testing/beta stage |
| **Compatibility Issues** | - Common between old and new versions<br>- Can be resolved by updating or using **backward-compatible** software |



### Roles in Software Engineering

| **Role**                            | **Description**                                          | **Key Responsibilities**                                     |
| ----------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| **Project Manager (Waterfall)**     | Oversees the entire project in traditional SDLC          | Planning, scheduling, budgeting<br>Allocating resources<br>Executing plans<br>Facilitating communication |
| **Scrum Master (Agile)**            | Ensures team success and communication in Agile projects | Facilitates Agile processes<br>Prioritizes people over process<br>Supports team collaboration |
| **Stakeholder**                     | End-users, clients, admins, and decision-makers          | Define requirements<br>Provide feedback<br>Participate in beta and acceptance testing |
| **System / Software Architect**     | Designs the technical foundation of the software         | Define software architecture<br>Guide technical decisions<br>Support development phases |
| **UX Designer**                     | Focuses on user experience and interaction               | Design intuitive interfaces<br>Define user interactions<br>Ensure usability and accessibility |
| **Software Developer**              | Writes and maintains the codebase                        | Implement architecture and requirements<br>Collaborate with UX design<br>Build functional features |
| **Tester / QA Engineer**            | Ensures software quality and correctness                 | Write and run test cases<br>Identify bugs<br>Verify software meets requirements |
| **Site Reliability Engineer (SRE)** | Bridges development and operations                       | Monitor systems<br>Automate infrastructure<br>Troubleshoot and ensure system reliability |
| **Product Manager / Owner**         | Owns the product vision and aligns with user needs       | Understand client/user needs<br>Lead development goals<br>Ensure product delivers stakeholder value |
| **Technical Writer**                | Produces documentation for non-technical users           | Write manuals, guides, reports<br>Communicate complex ideas clearly<br>Support user onboarding and feedback |

### Summary & Highlights

- Software engineering is the application of scientific principles to the design and creation of software. 
- Responsibilities of a software engineer include designing, building, and maintaining software systems. 
- Using the SDLC can improve efficiency and reduce risks by: 
  - letting team members know what they should be working on and when 
  - facilitating communication between the customer, other stakeholders, and the development team 
  - letting stakeholders know where they fit into that process and 
  - letting cross-domain teams know when they have completed their tasks so development can move to the next phase.   
- Common software engineering processes are requirements gathering, design, coding, testing, releasing, and documenting. 
- The requirement gathering process entails identifying stakeholders, establishing goals and objectives, eliciting requirements from the stakeholders, documenting the requirements, analyzing, prioritizing, and confirming the requirements. 
- An SRS is a document that captures the functionalities that the software should perform and also establishes benchmarks or service levels for its performance. 
- A URS is a subset of the SRS that details user specification requirements. 
- The SysRS contains the same information as an SRS, but can also additionally include system capabilities, interfaces, and user characteristics, policy requirements, regulation requirements, personnel requirements, performance requirements, security requirements, and system acceptance criteria. 
- Waterfall, V-shape model, and agile are all different methodologies for implementing the software development life cycle. 
- Functional testing is concerned with inputs and corresponding outputs of the system under test, non-functional testing tests for attributes such as performance, security, scalability, and availability. Whereas regression testing confirms that a recent change to the application, such as a bug fix, does not adversely affect already existing functionality. 
- Types of documentation include requirements, design, technical, quality assurance, and user. 
- There are many different roles involved in a software engineering project. Some of them include project manager or scrum master, stakeholder, system or software architect, UX designer, software developer, tester or QA engineer, site reliability or Ops engineer, product manager or owner, and technical writer or information developer. 

## Application Development Concepts

### Squads

A **Squad** in Agile is a small, cross-functional, self-organizing team responsible for a specific feature, product, or service. Each squad typically includes developers, testers, designers, and a product owner. Squads work autonomously, follow Agile principles (e.g., Scrum or Kanban), and collaborate closely to deliver end-to-end value.

**Key points:**

- 6–12 members
- Owns one product or feature area
- Works like a mini startup
- Inspired by Spotify’s Agile model
- Encourages autonomy and accountability



### Pair Programming

| **Aspect**      | **Details**                                                  |
| --------------- | ------------------------------------------------------------ |
| **Definition**  | Agile development technique where two developers work side-by-side on the same code (physically or virtually). |
| **Main Styles** | - **Driver/Navigator**: One types (driver), one guides (navigator); roles are swapped regularly<br>- **Ping-Pong**: Based on test-driven development (TDD); one writes failing test, other writes code to pass it<br>- **Strong Style**: Experienced dev navigates, junior dev drives—idea must go through another’s hands before being implemented |
| **Benefits**    | - Promotes knowledge sharing and onboarding<br>- Enhances communication and problem-solving skills<br>- Reduces typos, bugs, and logic errors<br>- Encourages early code review<br>- Leads to higher code quality despite potentially slower development pace |
| **Challenges**  | - Requires high concentration and can be mentally draining<br>- Scheduling conflicts can occur<br>- Risk of role imbalance (e.g., one dominates)<br>- Personality mismatches<br>- Noise issues in multi-pair settings |



### Application Development Tools 

| **Tool / Concept**   | **Purpose**                                                  | **Key Features**                                             | **Examples**                                     |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ |
| **Version Control**  | Track changes in source code; manage collaboration           | - Records edits by time and author<br>- Enables branching, merging, and reverts | Git, GitHub                                      |
| **Libraries**        | Reusable code for solving specific problems or adding features | - Developer controls when functions are called<br>- Speeds up development | jQuery, Email-validator, Apache Commons          |
| **Frameworks**       | Provide a structured workflow and architecture for apps      | - Inversion of control: framework calls your code<br>- Standardizes structure and reduces config time | AngularJS, Vue.js, Django                        |
| **CI/CD**            | Automate integration, testing, and deployment of code        | - CI: Integrate changes frequently and test<br>- CD: Deliver changes to staging or production reliably | Jenkins, GitHub Actions, GitLab CI/CD            |
| **Build Tools**      | Compile, package, and test code automatically                | - Automates tasks: compiling, bundling, testing<br>- Useful in multi-developer environments | Webpack, Babel, Gradle, Maven                    |
| **Packages**         | Bundled archive of app files and metadata for distribution   | - Contains install scripts, versioning, dependencies<br>- Ensures easy installation for end users | `.deb`, `.rpm`, `.pkg` files                     |
| **Package Managers** | Manage finding, installing, updating, and removing packages  | - Automates dependency management<br>- Ensures integrity (via checksums, signatures)<br>- Connects to online repositories | npm (JS), Pip/Conda (Python), RubyGems, Homebrew |



### Software Design and Modeling

| **Concept**                         | **Purpose / Description**                                    | **Key Elements / Examples**                                  |
| ----------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Structured Design**               | Breaks down software into smaller modules to improve organization and scalability | - Modules should be **cohesive** (group related functions)<br>- Should be **loosely coupled** (minimal dependencies) |
| **Behavioral Models**               | Describe **what** the system does without specifying **how** it is done | - Focus on interactions and states<br>- Often represented through **UML behavioral diagrams** |
| **UML (Unified Modeling Language)** | A standardized visual language to represent software architecture and behavior | - Language-agnostic<br>- Divided into **structural** and **behavioral** diagrams |
| **Advantages of UML**               | Enhances communication, planning, and onboarding             | - Saves time/cost by planning before coding<br>- Aids collaboration across technical and non-technical teams |
| **State Transition Diagram**        | Behavioral UML diagram that shows system states and transitions based on events | - States (e.g., "waiting", "testing")<br>- Events trigger transitions between states |
| **Interaction Diagram**             | Shows how objects interact over time in a dynamic context    | - Often visualized using **sequence diagrams**<br>- Example: online appointment booking workflow |



### Object-Oriented Analysis and Design (OOAD) 

| **Concept**             | **Purpose / Description**                                    | **Key Details / Examples**                                   |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **OOAD**                | A method for designing software systems using object-oriented principles | - Used with languages like Java, Python, C++<br>- Emphasizes modularity and interaction of objects |
| **Object**              | An instance of a class that holds data and behaviors         | - E.g., `Naya Patel` as a patient object<br>- Can perform actions like `cancelAppointment()` |
| **Class**               | A blueprint or template for creating objects                 | - Defines properties (e.g., `LastName`) and methods<br>- Instantiation assigns real values to these attributes |
| **Class Diagram (UML)** | A structural UML diagram showing relationships and attributes of classes | - Boxes = Classes<br>- Shows properties and methods<br>- Shows inheritance relationships |
| **Inheritance**         | Mechanism where a subclass inherits attributes from its parent class | - E.g., `Doctor` inherits from `MedicalPersonnel`<br>`Specialist` inherits from `Doctor` |



### Application Architecture

| **Concept**                             | **Purpose / Description**                                    | **Key Features / Examples**                                  |
| --------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Component**                           | Encapsulated unit of functionality used within applications  | - Characteristics: Reusable, Replaceable, Independent, Extensible, Encapsulated, Non-context specific |
| **Examples of Components**              | Functional units reusable across systems                     | - API connectors<br>- Data Access Objects<br>- Controllers   |
| **Component-Based Architecture**        | System design composed of loosely coupled components         | - Higher abstraction than object-oriented design<br>- Promotes modular, scalable applications |
| **Service**                             | A component that is **deployed independently** and reused across systems | - Always-running instance<br>- Handles business tasks like credit checks or loan processing |
| **Service vs Component**                | Services are built from components and run independently     | - Services = network-accessible, single instances<br>- Components = internal reusable blocks |
| **Service-Oriented Architecture (SOA)** | Network-based communication between services                 | - Services interact via protocols (e.g., HTTP)<br>- Loosely coupled<br>- Enables distributed system design |
| **Distributed System**                  | System with multiple services running on different machines, appearing as one to the user | - Properties: Fault-tolerant, Concurrent, Scalable, Heterogeneous (hardware/OS)<br>- Examples: Client-server, Microservices |
| **Node**                                | Any device that processes and transmits data on the network  | - Hosts one or more services within the distributed architecture |



### Software Architectural Patterns

- **Architectural Pattern** = Reusable solution to a recurring structural problem in system design
- Patterns can often be **combined** (e.g., microservices within a 3-tier architecture)
- Some are **mutually exclusive** (e.g., P2P cannot be 2-tier because of role separation)

| **Pattern**                | **Description**                                              | **Key Characteristics**                                      | **Example**                          |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------ |
| **2-Tier (Client-Server)** | Client interfaces with a dedicated server                    | - Centralized server<br>- Clients send requests, server responds<br>- Simple architecture | Text messaging app, DB client-server |
| **3-Tier**                 | Application divided into Presentation, Logic, and Data layers | - Layers interact only with adjacent ones<br>- Promotes separation of concerns | Most web apps (UI ↔ App ↔ DB)        |
| **Peer-to-Peer (P2P)**     | Decentralized nodes act as both clients and servers          | - No central coordination<br>- Nodes share resources (e.g., storage, compute)<br>- Scalable, resilient | Bitcoin, Ethereum                    |
| **Event-Driven**           | Focuses on producers and consumers reacting to events        | - Loose coupling<br>- Event router distributes notifications<br>- Real-time interactions | Ride-sharing apps (e.g., Uber)       |
| **Microservices**          | System broken into independent, loosely coupled services     | - Each service handles one function<br>- Communication via APIs<br>- Highly scalable and maintainable | Social media platforms               |

### Microservices

**Microservices** is an architectural style where an application is built as a collection of **small, independent services**, each handling a **specific business function**.

#### Key Characteristics

- **Single Responsibility**: Each service does one thing well  
- **Independent Deployment**: Can be developed and deployed separately  
- **API Communication**: Communicates via REST, gRPC, or message queues  
- **Own Data Store**: Each service manages its own database  
- **Technology Agnostic**: Different services can use different tech stacks  

#### Comparison: Monolith vs Microservices

| Feature         | Monolith              | Microservices           |
| --------------- | --------------------- | ----------------------- |
| Structure       | All-in-one            | Modular and independent |
| Deployment      | As a single unit      | Per service             |
| Scalability     | Whole system          | Per service             |
| Fault Isolation | One crash affects all | Crashes are isolated    |

#### Common Stack

- **Backend**: FastAPI, Flask, Node.js, Spring Boot  
- **API Gateway**: Nginx, Kong, Zuul  
- **Containerization**: Docker  
- **Orchestration**: Kubernetes  
- **Communication**: REST, gRPC, RabbitMQ, Kafka  
