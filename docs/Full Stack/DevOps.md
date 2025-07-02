## Overview of DevOps

### Intro to DevOps

| **Category**                              | **Key Points**                                               |
| ----------------------------------------- | ------------------------------------------------------------ |
| **🔧 What is DevOps?**                     | - DevOps is **not** a tool or a job title<br>- It’s a **collaborative practice** between development and operations<br>- Follows **Lean and Agile** principles<br>- Goal: **Rapid and continuous delivery** of software |
| **🌱 Why Culture Matters More Than Tools** | - **#1 reason DevOps fails**: Lack of organizational learning & cultural change<br>- **Gartner**: 75% of initiatives fail due to these issues<br>- **George Spafford**: “People-related factors… not technology”<br>- **DORA Report (2021)**: Team culture has a big impact on success |
| **🔄 How to Change the Culture**           | **1. Think Differently**<br>- Use social coding<br>- Emphasize reuse and sharing<br>- Lean ideas: small batches, MVPs for feedback<br><br>**2. Work Differently**<br>- Use **TDD** and **BDD**<br>- Ensure high-quality, repeatable processes<br>- Implement **CI/CD** for shippable changes<br><br>**3. Organize Differently**<br>- Team structure affects architecture<br>- Avoid “reward theater”; promote real collaboration<br><br>**4. Measure Differently**<br>- Change measurement systems<br>- Avoid **vanity metrics** (e.g., lines of code)<br>- Use **actionable metrics** that reflect customer/product value<br>- “You get what you measure” |
| **💡 Final Advice**                        | - Foster **teamwork**, **accountability**, and **trust**<br>- Be willing to **experiment and fail fast**<br>- Every failure is a **learning opportunity**<br>- Embrace change: *“We don’t do DevOps… we become DevOps.”* |



### Business Case for DevOps

| **Category**                        | **Key Points**                                               |
| ----------------------------------- | ------------------------------------------------------------ |
| **📉 Business Disruption & Urgency** | - Since 2000, **52% of Fortune 500 companies** are gone<br>- The primary threat: **Disruption**, not competition<br>- Disruption is inevitable: *“Not if, but when.”* |
| **📱 Disruption Examples**           | **Banks**:<br>- Slow to adopt tech like check-deposit apps<br>- Risk losing customers to faster-moving competitors<br><br>**Uber vs Taxi Industry**:<br>- Tech (GPS, payments, smartphones) already existed<br>- Innovation = **new business model**, not new tech<br>- Taxis sought regulation instead of adapting |
| **📦 Disrupted Industries**          | - **Travel agents** replaced by online booking<br>- **Point-and-shoot cameras** replaced by smartphones<br>- **Blockbuster** failed to see they were in the **entertainment** business<br>- **Netflix**: Pivoted from DVD rental to streaming and original content<br>- **Garmin**: Shifted from mapping to fitness and tracking wearables |
| **💡 Key Takeaways**                 | - **Technology ≠ Innovation**<br>- Tech is the **enabler**, not the **driver** of innovation<br>- Success depends on **business model innovation**, then leveraging tech<br>- Companies must **adapt or go extinct** |



### DevOps Adoption

| **Category**                          | **Key Points**                                               |
| ------------------------------------- | ------------------------------------------------------------ |
| **🧠 Cultural Shift Required**         | - DevOps requires **unlearning old habits**, especially in large enterprises<br>- Startups adapt faster due to less legacy culture<br>- Core idea: Embrace **failure**, **rollback quickly**, **limit blast radius**<br>- Test in production via **A/B testing**, not theoretical guesses |
| **📦 Microservices & Design**          | - Apps like **Spotify** use microservices for flexibility<br>- Components can be updated **independently** without full redeployment<br>- Allows rapid delivery and experimentation with minimal impact |
| **🚀 Historical DevOps Milestones**    | **Flickr (2009)**:<br>- John Allspaw & Paul Hammond: *“10+ Deploys per Day”*<br>- Dev & Ops collaboration enabled fast, partial deployments<br><br>**Etsy (2011)**:<br>- 517 deploys in 1 month by 76 devs<br>- Deployment every ~25 minutes<br>- Success due to **trust, transparency, communication, discipline** |
| **🏢 DevOps in the Enterprise (2016)** | - **DevOps Enterprise Summit** showed enterprise success stories:<br>• Ticketmaster: 98% ↓ in mean time to recovery<br>• Nordstrom: 20% shorter lead time<br>• Target: Full stack deploy from 3 months → minutes<br>• USAA: Release cycle from 28 → 7 days<br>• ING: 500 teams doing DevOps<br>• CSG: Incidents per release 200 → 18 |
| **💡 Key Takeaways**                   | - DevOps is **not a tool**, **not a box to buy**<br>- True DevOps success is driven by **culture change**<br>- Requires: **Trust, transparency, coordination, communication, and discipline**<br>- Enterprises can do it too—not just “unicorn” startups |



### Definition of DevOps

| **Category**                    | **Key Points**                                               |
| ------------------------------- | ------------------------------------------------------------ |
| **📖 Origin & Definition**       | - Term **“DevOps”** coined in 2009 by **Patrick Debois**<br>- Described as an extension of Agile into Operations<br>- “Agile for Ops” = Dev & Ops working together, not in silos<br>- Definition: DevOps is the **practice of Dev and Ops engineers working together** throughout the **entire software lifecycle**, applying **Lean and Agile** principles to deliver software **rapidly and continuously** |
| **🏗️ Characteristics of DevOps** | - **Culture of collaboration** with openness, trust, transparency<br>- Requires **new app design**: not monolithic, but **microservices**<br>- Needs **automation** to handle microservices deployment<br>- Requires a **dynamic, programmable platform** for fast, on-demand environments |
| **🚫 What DevOps is NOT**        | - ❌ Just Dev + Ops working together<br>- ❌ A **separate team** or a new “DevOps Team”<br>- ❌ A **tool** (though tools support DevOps)<br>- ❌ Just automation or hiring a “DevOps engineer”<br>- DevOps is not a **one-size-fits-all** approach—strategy depends on the type of product (e.g., SaaS, shrink-wrap, installables) |
| **💡 Key Takeaways**             | - DevOps is a **cultural change**, not a toolset<br>- Requires **one team**, **one mindset**, and **one set of measurements**<br>- Tools reinforce DevOps culture but **do not create it** |



### Essential Characteristics of DevOps

![image-20250701152521290](DevOps.assets/image-20250701152521290.png)

![image-20250701152638338](DevOps.assets/image-20250701152638338.png)

| **Category**                                   | **Key Points**                                               |
| ---------------------------------------------- | ------------------------------------------------------------ |
| **🎯 DevOps Goal**                              | - The ultimate goal: **Agility**<br>- Move with **maximum velocity** and **minimum risk**<br>- Enable **smart experimentation** and fast customer feedback |
| **🌩️ Three Pillars of Agility (Perfect Storm)** | 1. **DevOps**<br>• Culture change<br>• Automated pipelines<br>• Infrastructure as code<br>• Immutable infrastructure<br><br>2. **Microservices**<br>• Loosely coupled design with REST APIs<br>• Designed to fail fast and resist failure<br><br>3. **Containers**<br>• Developer-centric and fast startup<br>• Ephemeral, portable, disposable environments |
| **📈 Application Evolution**                    | - Waterfall → Agile → DevOps<br>- Monoliths → SOA → Microservices<br>- Physical servers → VMs → Containers<br>- DevOps built on **services + cloud + automation** |
| **📊 DevOps Dimensions**                        | 1. **Culture** (most important)<br>2. **Method**<br>3. **Tools** (what vendors mostly sell)<br><br>• Many fail by focusing only on tools, not culture |
| **🔁 Changing Culture**                         | - Change the way people **think**, **work**, **organize**, and **are measured**<br>- Embrace social coding, small batches, TDD, and BDD<br>- Culture must be led **top-down** and adopted **bottom-up**<br>- “You get what you measure” — redefine success metrics |
| **💡 Key Takeaways**                            | - DevOps includes: **cultural change, automation, infrastructure as code, microservices, containers, immutable infra**<br>- Culture is the **#1 success factor** (Atlassian)<br>- True DevOps transformation = thinking, working, organizing, and measuring differently |



### Leading Up to DevOps

| **Category**                                 | **Key Points**                                               |
| -------------------------------------------- | ------------------------------------------------------------ |
| **📜 The Waterfall Method**                   | - Development proceeded in strict **phases**: Requirements → Design → Code → Test → Deploy<br>- Each phase had **entrance/exit criteria**, preventing backward movement<br>- Designs took months; development and testing also isolated and lengthy |
| **⛔ Major Problems with Waterfall**          | - **No room for change** once a phase ended<br>- **No intermediate delivery** or feedback<br>- High risk: Problems only discovered **at the end**<br>- **Siloed teams**: Designers, Developers, Testers, and Ops worked separately<br>- **Operations team**, furthest from the code, had to deploy and maintain it |
| **💣 Consequences of the Waterfall Approach** | - Long lead times and delivery delays<br>- Mistakes discovered late were **very costly** to fix<br>- **Lost information** between handoffs across teams<br>- **Frustration**, **blockers**, and **inefficiency** were common |
| **💡 Key Takeaways**                          | - Waterfall fostered silos between Dev and Ops<br>- DevOps emerged as a response to these pain points, promoting collaboration and iterative delivery |



### XP, Agile, and Beyond

| **Category**                    | **Key Points**                                               |
| ------------------------------- | ------------------------------------------------------------ |
| **🧪 Extreme Programming (XP)**  | - Introduced by **Kent Beck** in 1996<br>- Emphasized **tight feedback loops**: from months (release plans) to seconds (coding)<br>- Focused on **software quality**, fast feedback, and iteration<br>- Promoted **pair programming** for knowledge sharing and code quality |
| **⚡ Agile Manifesto (2001)**    | - Created by 17 developers at Snowbird, Utah<br>- Core values:<br>• Individuals & interactions > Processes & tools<br>• Working software > Comprehensive documentation<br>• Customer collaboration > Contract negotiation<br>• Responding to change > Following a plan |
| **📈 Agile Practices**           | - **Self-organizing**, cross-functional teams<br>- Work in **sprints** with adaptive planning<br>- Encourages **early delivery**, **continuous improvement**, and **rapid response to change** |
| **🚧 The Problem: Agile vs Ops** | - Agile Devs moved fast, but Ops processes were slow<br>- Example: Dev team ready in Feb, but VMs delivered in Sept<br>- Tickets, long wait times, and process bottlenecks slowed delivery |
| **🐢 Two-Speed IT & Shadow IT**  | - **Two-Speed IT**: Devs are fast, Ops are slow<br>- Devs bypass IT using the **cloud** to get resources<br>- Leads to **Shadow IT** (IT infrastructure unknown to official IT department) |
| **💡 Key Takeaways**             | - XP led to Agile; Agile improved Dev velocity<br>- **Agile alone is not enough** without making Ops agile too<br>- This gap led to the need for **DevOps**—to align Dev and Ops for speed and collaboration |



### Brief History of DevOps

| **Category**                             | **Key Points**                                               |
| ---------------------------------------- | ------------------------------------------------------------ |
| **📅 Timeline of Key Events (2007–2019)** | - **2007**: Patrick Debois notices Dev & Ops disconnect<br>- **2008**: Andrew Shafer hosts “Agile Infrastructure” BoF at Agile Conference (misses his own session, Debois shows up!)<br>- **2009**: John Allspaw’s “10+ Deploys per Day” talk at Velocity<br>- **2009**: First **DevOpsDays** held in Ghent, Belgium—term "DevOps" coined<br>- **2010**: Jez Humble & David Farley publish *Continuous Delivery* book<br>- **2013**: Gene Kim et al. publish *The Phoenix Project*<br>- **2015**: Nicole Forsgren, Gene Kim, Jez Humble found **DORA**<br>- **2016**: *The DevOps Handbook* published by Kim, Humble, Debois, Willis<br>- 40+ DevOpsDays events across 21 countries in 10 years |
| **📚 Influential Publications**           | - *Continuous Delivery* (2010) – defined principles for automation & rapid delivery<br>- *The Phoenix Project* (2013) – IT transformation through lean principles<br>- *The DevOps Handbook* (2016) – practical DevOps implementation guide |
| **👤 Key Influencers**                    | - **Patrick Debois** – “Father of DevOps”, founded DevOpsDays<br>- **Andrew Clay Shafer** – sparked Agile Infrastructure conversation<br>- **John Allspaw** – Velocity talk popularized DevOps practice<br>- **Jez Humble** – co-authored major books, DORA co-founder<br>- **Gene Kim** – Phoenix Project author, DORA<br>- **Nicole Forsgren** – DORA CEO, key research on performance metrics<br>- **John Willis** – DevOpsDays organizer, Docker/Chef, co-author<br>- **Bridget Kromhout** – DevOpsDays lead (2015–2020), *Arrested DevOps* podcast |
| **💡 Core Message**                       | - DevOps is a **grassroots movement**, **by practitioners**<br>- It is not a product or job title<br>- Focuses on **cultural transformation**, **collaboration**, and **measurement**<br>- A response to real-world roadblocks in Dev + Ops collaboration |



### Summary

- **Technology is the enabler of innovation**, rather than the driver of innovation. You must have an innovative business idea to leverage technology.
- In 2009, John Allspaw described an innovative approach to managing development and operations that enabled Flickr to complete over ten deploys per day, when many companies were completing fewer than one deploy every six months. This was a key moment in the growth of DevOps.
- DevOps is the practice of development and operation engineers working together during the entire development lifecycle, following Lean and Agile principles that allow them to deliver software in a rapid and continuous manner.
- DevOps is not it is not just Dev and Ops working together. It is a cultural change and a different way to work. DevOps has three dimensions: culture, methods, and tools. Of these, culture is the most important.
- The essential characteristics of DevOps include cultural change, automated pipelines, infrastructure as code, immutable infrastructure, cloud native application design, the ecosystem of containers, and how to deploy with immutable infrastructure.
- DevOps started in 2007 when Patrick Debois and Andrew Clay Shafer began to gather like-minded people together at conferences to talk about common experiences.
- In 2009, Allspaw delivered his now famous “10+ Deploys Per Day – Dev and Ops Cooperation at Flickr” presentation and the idea gained ground. Also in 2009, Patrick Debois started a conference called DevOpsDays that helped spread the DevOps message.
- Books such as Continuous Delivery in 2010, The Phoenix Project in 2013, and The DevOps Handbook in 2016, helped practitioners understand how DevOps worked.
- The major influential people of the early DevOps movement: Patrick Debois, Andrew Clay Shafer, John Allspaw, Jez Humble, Gene Kim, John Willis, Bridget Kromhout, and Nicole Forsgren, went out and made a difference, showing the results that could be achieved with DevOps.
- The message spread from practitioner to practitioner until they began to realize what was possible with DevOps and that it was a better way to work.



## Thinking DevOps

### Social Coding Principles

| **Category**                          | **Key Points**                                               |
| ------------------------------------- | ------------------------------------------------------------ |
| **🌐 What is Social Coding?**          | - Think: *“Open Source for Inner Source”*<br>- Code is developed **communally**, even in enterprises<br>- Everyone is encouraged to **fork, contribute, and reuse** internal code<br>- Reduces duplicate work and promotes **code sharing** and **collaboration** |
| **🔁 Problem Solved by Social Coding** | - In traditional closed repos: code is invisible, reused less<br>- Teams often **rebuild code** just to get minor changes<br>- Social coding enables forking + contributing instead of rewriting |
| **✅ How It Works**                    | - Discuss changes with repo owner → fork → create a branch → implement → submit **pull request**<br>- Owner reviews, requests changes/tests if needed, then merges<br>- Maintains **control** + encourages contributions = win-win |
| **👥 Pair Programming**                | - Originated from **Extreme Programming (XP)**<br>- Involves **two people** at one workstation:<br>• **Driver**: types code<br>• **Navigator**: reviews, plans, and strategizes<br>- Switch roles every ~20 minutes |
| **🔥 Benefits of Pair Programming**    | - **Higher code quality**<br>- Bugs are found earlier via **"programming out loud"**<br>- **Knowledge transfer** between junior and senior devs<br>- **Shared code ownership**: avoids single points of failure<br>- Better team alignment and reduced long-term maintenance costs |
| **💡 Key Takeaways**                   | - Social coding enables code **reuse**, contribution, and **collaboration**<br>- Pair programming improves code quality and **creates better programmers** by sharing insights and knowledge |



### Git Repository Guidelines

| **Category**                       | **Key Points**                                               |
| ---------------------------------- | ------------------------------------------------------------ |
| **📁 Repository Structure**         | - Create **one repository per component or microservice**<br>- Avoid **mono repos** (multiple microservices in one repo)<br>- Keeps checkouts lightweight and focused on relevant code |
| **🌿 Branching Strategy**           | - Use **feature branches**: create a new branch for each issue<br>- Avoid **long-lived branches** (e.g., old-style `development` branches)<br>- Git branches are **lightweight** and should be deleted after merge |
| **🔁 Git Feature Branch Workflow**  | 1. **Create or fork** a repo<br>2. **Clone** to local machine<br>3. **Create a feature branch** tied to a GitHub Issue<br>4. Make changes locally<br>5. **Push to remote** and open a **pull request (PR)**<br>6. **Another team member reviews and merges** the PR into `master` |
| **🧑‍🤝‍🧑 Code Review Best Practices** | - **Never merge your own pull request**<br>- Always have **someone else** review and merge<br>- Pull requests = **code review opportunities**<br>- Ensures **higher code quality** and team alignment |
| **💡 Key Takeaways**                | - One repo per component<br>- Use **Git Feature Branch Workflow**<br>- PRs should be reviewed and merged by peers<br>- Every PR is a chance to improve code through review |



### Working in Small Batches

| **Category**                      | **Key Points**                                               |
| --------------------------------- | ------------------------------------------------------------ |
| **📁 Repository Structure**        | - Create **one repository per component or microservice**<br>- Avoid **mono repos** that group multiple microservices together<br>- Keeps checkouts minimal and relevant |
| **🌿 Branching Strategy**          | - Use **feature branches** for every issue<br>- Avoid long-lived branches like `development`<br>- Branches are **lightweight** and should be deleted after merging |
| **🔁 Git Feature Branch Workflow** | 1. Create or fork a GitHub repo<br>2. Clone it locally<br>3. Create a feature branch linked to a GitHub Issue<br>4. Make and commit changes locally<br>5. Push to remote and open a **pull request (PR)**<br>6. Another teammate reviews and merges into `master` |
| **👀 Code Review Best Practices**  | - **Do not merge your own PR**<br>- Always have another team member do the review and merge<br>- Every PR is an opportunity for **peer review and feedback** |
| **💡 Key Takeaways**               | - Follow the **Git Feature Branch Workflow**<br>- Keep repos **modular**, branches **short-lived**, and **pull-reviewed**<br>- Promote **team visibility and collaboration** through PRs |



### Minimum Viable Product (MVP)

| **Category**            | **Key Points**                                               |
| ----------------------- | ------------------------------------------------------------ |
| **🧪 What is an MVP?**   | - MVP = **Minimum Viable Product**<br>- Not the same as Phase 1 or a beta release<br>- It’s the **cheapest, fastest experiment** to test a **value hypothesis** and gain **learning** |
| **🎯 Purpose of an MVP** | - Goal: **Learn** what the customer really wants—not just deliver<br>- Each MVP should help decide: **Pivot or Persevere?**<br>- Use MVPs to gather feedback and improve progressively |
| **🚫 Wrong Approach**    | - Iterative delivery without feedback is **not** MVP<br>- Example: Delivering car parts one by one without usability or learning (wheel → chassis → car) = wasted effort and no insights |
| **✅ Right Approach**    | - MVPs should be **usable**, **testable**, and focused on feedback<br>- Example: Start with skateboard → add steering → add pedals → evolve to motorcycle → convertible<br>- Customer journey shifts based on **real feedback**, not initial assumption |
| **📚 Key Mindset**       | - MVPs are **experiments**, and **failure is acceptable**<br>- The value comes from **what you learn**, not what you deliver<br>- Ask: “What did we learn? What should we try next?” |
| **💡 Key Takeaways**     | - An MVP is a **learning tool**, not just a product slice<br>- Use MVPs to **test, adapt**, and move toward what the **customer truly desires**<br>- In DevOps, MVPs reduce risk and improve customer alignment |



### Test Driven Development 

| **Category**                                 | **Key Points**                                               |
| -------------------------------------------- | ------------------------------------------------------------ |
| **🧪 What is Test-Driven Development (TDD)?** | - Write tests **before** writing code<br>- Test cases **drive the design** of the code<br>- You write tests for how the code **should behave**, then implement just enough code to pass them |
| **🔁 TDD Workflow – Red, Green, Refactor**    | 1. **Red** – Write a failing test<br>2. **Green** – Write code to pass the test<br>3. **Refactor** – Improve the code without changing its behavior<br>4. Repeat |
| **⚙️ Benefits of TDD**                        | - Forces **caller’s perspective**: you consider usability before writing code<br>- Produces **higher-quality code**<br>- **Defects found earlier**, saving debugging time<br>- Ensures that **future changes don’t break functionality** |
| **📉 Common Excuses (and Why They're Wrong)** | - “I already know my code works” → But others (including future you) won’t<br>- “I don’t write broken code” → Dependencies and environments change<br>- “I don’t have time” → TDD **saves time** in the long run |
| **🚀 Why TDD Matters for DevOps**             | - Automated tests are **critical for CI/CD pipelines**<br>- You **can’t safely deploy continuously** without automated testing<br>- TDD gives **confidence** to refactor, deploy, and scale safely |
| **💡 Key Takeaways**                          | - TDD = write test → write code → refactor<br>- Encourages better design and behavior-driven development<br>- Essential for maintaining **automated, high-quality DevOps pipelines** |



### Behavior Driven Development

| **Category**           | **Key Points**                                               |
| ---------------------- | ------------------------------------------------------------ |
| **🔍 What is BDD?**     | - **Behavior-Driven Development (BDD)** focuses on **system behavior** from the **outside in**<br>- Useful for **integration testing** and ensuring business outcomes are met<br>- Contrast with TDD, which focuses on **unit-level correctness** from the **inside out** |
| **🔁 BDD vs TDD**       | - **BDD:** Are we building the **right thing**?<br>- **TDD:** Are we building the thing **right**?<br>- BDD = behavior from consumer’s view; TDD = logic from developer’s view |
| **🧠 How BDD Works**    | 1. **Collaboration** between devs, testers, and customers<br>2. Define behaviors using **Gherkin syntax** (Given, When, Then)<br>3. Use tools like **Cucumber**, **Behave**, or **jBehave** to turn those into automated tests |
| **🗣️ Gherkin Syntax**   | - **Given**: Precondition or starting context<br>- **When**: Triggering action<br>- **Then**: Expected outcome<br>- **And**: Additions to Given/When/Then lines<br>- Written in **natural language** understandable by all stakeholders |
| **📄 Example Scenario** | **Feature**: Returns go to stock<br/>**As a** store owner<br/>**I need** to add items back to stock when they're returned<br/>So that I can keep track of my stock on hand<br/><br />**Scenario 1**: Refunded items should be returned to stock<br/>**Given** that a customer previously bought a black sweater from me<br/>**And** I have 3 black sweaters in stock<br/>**When** they return the black sweater for a refund<br/>**Then** I should have 4 black sweaters in stock |
| **✅ Benefits of BDD**  | - Improves **team communication**<br>- Aligns **developers and stakeholders** on expectations<br>- Enables **executable documentation** and **automated tests** from user stories<br>- Ensures clear definition of **“done”**<br>- Helps automate testing early, even **before development starts** |
| **💡 Key Takeaways**    | - BDD uses **plain language** + automated tests<br>- Ensures you build what the **user actually needs**<br>- Encourages shared understanding and lowers communication barriers |



### Cloud Native Microservices

![image-20250701235142209](DevOps.assets/image-20250701235142209.png)

![image-20250701235506751](DevOps.assets/image-20250701235506751.png)

| **Category**                                    | **Key Points**                                               |
| ----------------------------------------------- | ------------------------------------------------------------ |
| **☁️ What is Cloud Native Microservices?**       | - **Cloud native** = applications designed to run and scale in the cloud<br>- Built as a collection of **independent microservices**<br>- Each service is focused on a **single business domain**<br>- Services communicate via **REST APIs**, not shared databases |
| **🧱 Microservices vs Monolith**                 | - **Monolith**: tightly coupled; shared databases; hard to scale pieces independently<br>- **Microservices**: loosely coupled; each has its **own database**; independently deployable and scalable |
| **🔄 Stateless Microservices**                   | - “Stateless” = no **internal hidden state** stored in memory<br>- State is persisted externally (e.g., DB or object-store)<br>- Enables scalability, resilience, and fault tolerance |
| **🚀 Benefits of Microservices Architecture**    | - **Independent deployment**: Update one service without affecting others<br>- **Independent scalability**: Scale specific services (e.g., notifications) without scaling the whole system<br>- **Fault tolerance**: Failed instances are killed and respawned (“**cattle not pets**”) |
| **📚 Microservices Principles (Fowler & Lewis)** | - Each service runs in its own process<br>- Communicates using **lightweight mechanisms** like HTTP/REST<br>- Built around **business capabilities**<br>- Fully automatable deployment (CI/CD) is essential |
| **📐 12-Factor App Guidelines**                  | - Originated from **Heroku**<br>- Standard for building **cloud native, stateless services**<br>- Emphasizes configurability, portability, and scalability |
| **💡 Key Takeaways**                             | - Cloud-native = microservices + stateless + REST APIs + independent DBs<br>- Microservices allow **faster changes**, **team autonomy**, and **DevOps-driven deployment**<br>- Enables **true continuous delivery** by reducing system-wide coupling |

- Cloud native architecture is a collection of independently deployable microservices
- Stateless microservices each maintain their own state in a separate database or persistent object store
- Microservices are loosely coupled services, designed for scalability and communication with APIs



### Designing for Failure

| **Category**                  | **Key Points**                                               |
| ----------------------------- | ------------------------------------------------------------ |
| **⚠️ Embracing Failure**       | - In distributed systems, **failure is inevitable**<br>- Goal: **Recover quickly**, not avoid all failure<br>- Shift from “mean time to failure” → “mean time to recovery”<br>- Developers must **build resilience** into the application, not just rely on Ops |
| **🔁 Retry Pattern**           | - Handle **transient failures** (e.g., temporary outages)<br>- Retry failed operations with **exponential backoff** (1s → 2s → 4s...)<br>- Prevents overwhelming the service and gives time to recover<br>- Required for **cloud-native resilience**, e.g., DB startup delays or throttling (HTTP 429) |
| **⚡ Circuit Breaker Pattern** | - Prevents **cascading failures**<br>- When error rate exceeds threshold, **open the circuit** to stop further calls<br>- Automatically transitions to **half-open** state to test recovery<br>- Resets to **closed** if successful, else stays **open**<br>- Inspired by electrical circuit breakers |
| **🚪 Bulkhead Pattern**        | - Isolates components using **thread pools** or containers<br>- Failure in one service/thread pool **won’t affect others**<br>- Inspired by ship design: bulkheads keep compartments separate to prevent sinking |
| **🧪 Chaos Engineering**       | - Practice of **intentionally breaking things** to test system resilience<br>- Netflix’s **Chaos Monkey** kills random services to observe recovery<br>- Helps validate resilience patterns like retries, circuit breakers, etc. |
| **💡 Key Takeaways**           | - Failure is **expected**; resilience must be **designed in**<br>- Use patterns: **Retry**, **Circuit Breaker**, **Bulkhead**<br>- Use **chaos engineering** to test and prove system robustness under real failure conditions |



### Summary

- Social coding is coding as a community and public repositories and pair programming result in higher code quality. 
- Working in small batches reduces waste and means quickly delivering something useful to the customer. 
- Minimum viable product is as much about delivery as it is about building what the customer really desires. 
- Test-driven development is writing the test for the code you wish you had, then writing the code to make the test pass. It allows you to develop faster and with more confidence.
- Behavior-driven development focuses on the behavior of the system from the outside in. It looks at the system as a consumer of it. 
- Behavior-driven development improves communication by using an approachable syntax that developers and stakeholders can understand. 
- Microservices are built around business capabilities and are independently deployable by fully automated deployment machinery. 
- Cloud native architecture enables independently deployable microservices that take advantage of horizontal scaling and result in more resilient services. 
- Failure is inevitable, so we design for failure rather than trying to avoid failure. 
- It is important to embrace failure and quickly recover when failures happen. 



## Working DevOps

### Taylorism and Working in Silos

| **Category**                                      | **Key Points**                                               |
| ------------------------------------------------- | ------------------------------------------------------------ |
| **⚙️ What is Taylorism?**                          | - Named after **Frederick Winslow Taylor** (1911)<br>- Originated from factory work during the industrial revolution<br>- Promotes **command-and-control** management style<br>- Work is broken into **task-specific roles** (e.g., assembly lines)<br>- Managers plan, workers execute with little autonomy |
| **🏭 Impact of Taylorism on Modern IT**            | - Promotes **siloed teams**: project managers → architects → developers → testers → operations → security<br>- Each handoff is a **risk point**: loss of context, mistakes, delays<br>- Optimized for **repetition and mass production**, not for custom development |
| **👎 Why Taylorism Fails in Software Development** | - Software is **bespoke, knowledge-based craftwork**, not mass production<br>- You often build things that **don’t exist yet**, unlike standardized car parts<br>- Building one unique product ≠ justify assembly-line tooling<br>- Requires **creativity, iteration, and collaboration**, not rigid silos |
| **🚫 Problems with Silos**                         | - Causes **bottlenecks**, slow feedback loops, and high error rates<br>- Encourages blame and communication breakdown<br>- Each team works with different goals, reducing overall effectiveness |
| **✅ DevOps Culture vs Taylorism**                 | - DevOps promotes **teaming and collaboration**, not separation<br>- Automate relentlessly, minimize manual work<br>- Embrace **small, frequent releases** for rapid feedback and risk reduction<br>- Managers should empower, not micromanage ("Hire smart people so they can tell us what to do") |
| **💡 Key Takeaways**                               | - **Abandon Taylorism** and command-and-control for DevOps success<br>- Treat software like **craftwork**, not factory output<br>- Break down silos, empower teams, and enable continuous learning and delivery |

![image-20250702025411725](DevOps.assets/image-20250702025411725.png)



### Software Engineering vs. Civil Engineering

| **Category**                                               | **Key Points**                                               |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| **🏗️ Civil Engineering Approach**                           | - Follows a **waterfall-like model**:<br>• Architect → Blueprint → Construction → Maintenance<br>- Each role completes their task and then **moves on**<br>- Once built, structures are **stable** and rarely change<br>- Works well for physical systems where change is minimal |
| **💻 How Software Differs**                                 | - Software is **organic and always evolving**<br>- Even if the app doesn’t change, OS patches, package updates, and security fixes constantly affect it<br>- **New features** are continuously added — unlike buildings, you *do* add new “floors” to software |
| **🚧 The Problem with Treating Software Like Construction** | - Teams throw deliverables over the wall: Architect → Dev → QA → Ops<br>- Leads to **lack of ownership** and **context loss**<br>- Once the project is “done,” the team disbands and knowledge fades<br>- Operations must handle future changes alone |
| **📉 Flaws of the Project Model**                           | - The **“project complete → move on”** mindset fails in software<br>- It ignores the **constant change** and **need for iteration**<br>- Creates code without long-term stewardship or enhancement vision |
| **✅ DevOps/Product Thinking**                              | - Treat software like a **product**, not a project<br>- Maintain **long-lived teams** with **end-to-end ownership**<br>- Developers who build the system also **maintain and evolve it**<br>- This results in higher quality, better ideas, and sustained improvement |
| **💡 Key Takeaways**                                        | - Software is **never done**; it evolves<br>- Abandon civil engineering-style handoffs<br>- Embrace **stable teams**, **continuous enhancement**, and **product ownership** for long-term success in DevOps |



### Required DevOps Behaviors

| **Category**                           | **Key DevOps Behaviors**                                     |
| -------------------------------------- | ------------------------------------------------------------ |
| **🤝 Collaboration & Shared Ownership** | - Break down silos between Dev, QA, and Ops<br>- Encourage **cross-functional teams**<br>- Teams share responsibility for **quality, delivery, and reliability** |
| **🔁 Continuous Improvement**           | - Always look for ways to improve **processes and outcomes**<br>- Conduct **blameless postmortems**<br>- Implement feedback from incidents, deployments, and users |
| **🚀 Rapid, Frequent Delivery**         | - Deliver small, **incremental changes** often<br>- Reduce batch size and scope of releases<br>- Use **CI/CD pipelines** to automate deployment |
| **📈 Metrics-Driven Culture**           | - Use **measurable goals** to guide improvements (e.g., deployment frequency, lead time, MTTR)<br>- Make decisions based on **data, not opinions**<br>- Continuously monitor system health |
| **⚙️ Automation-First Mindset**         | - Automate repetitive tasks (testing, deployment, monitoring)<br>- Improve consistency, reduce human error<br>- Infrastructure as Code (IaC) for managing environments |
| **🔐 Security as Code (DevSecOps)**     | - Build security into the pipeline from the start<br>- Automate security tests<br>- Encourage collaboration between Dev, Ops, and Security teams |
| **🧪 Experimentation & Learning**       | - Promote a **safe-to-fail** environment<br>- Encourage **experimentation** and innovation<br>- Treat failures as learning opportunities |
| **👥 Empathy & Respect**                | - Practice **blameless culture**<br>- Respect different team roles and perspectives<br>- Prioritize **psychological safety** to foster open communication |



### Infrastructure as Code

| **Category**                                | **Key Points**                                               |
| ------------------------------------------- | ------------------------------------------------------------ |
| **💻 What is Infrastructure as Code (IaC)?** | - Describes **infrastructure using executable text/code**<br>- Not documentation — real **code** that can be executed by tools<br>- Tools: **Ansible**, **Puppet**, **Chef**, **Terraform**, **Docker**, **Kubernetes** |
| **⚙️ Benefits of IaC**                       | - **Repeatable** and **automated** setups<br>- **Version-controlled** infrastructure<br>- Prevents manual misconfiguration and **server drift**<br>- Enables consistent environments across dev, test, prod |
| **🌩️ Ephemeral Infrastructure**              | - Infrastructure is **transient** and created **on demand**<br>- No more hand-crafted long-living servers<br>- Example: spin up test environment → use it → destroy it<br>- Makes infrastructure **disposable and reproducible** |
| **🐄 "Cattle, Not Pets"**                    | - Don’t treat servers as unique or irreplaceable<br>- If a server (or container) fails, just replace it<br>- Avoid manual fixes; always **recreate from template/code** |
| **📦 Immutable Delivery via Containers**     | - Use **Docker** or similar tools to package apps + dependencies<br>- Changes are made to **images**, not running containers<br>- Enables **consistent deployment** from dev to prod<br>- If issues occur, **rollback is instant** by replacing containers |
| **🔄 Rolling Updates & Rollbacks**           | - Deploy new version as a **new container**<br>- If stable → promote it to production<br>- If failure → **stop and replace** with previous container<br>- Avoid patching live containers—**redeploy from updated image** |
| **💡 Key Takeaways**                         | - IaC = infrastructure as code, not scripts<br>- Enables **automation, reproducibility, and consistency**<br>- Treat infrastructure and containers as **ephemeral**, not permanent<br>- Use versioned templates and images for control and rollback |



### Continuous Integration

| **Category**                               | **Key Points**                                               |
| ------------------------------------------ | ------------------------------------------------------------ |
| **🔄 What is Continuous Integration (CI)?** | - CI = **Building, testing, and integrating every developer change** into the master/main branch<br>- Each commit triggers **automated tests and builds**<br>- Ensures the master branch is **always in a deployable state** |
| **🚀 What is Continuous Delivery (CD)?**    | - CD = Ensures code can be rapidly and safely **deployed to a production-like environment**<br>- Often confused with CI, but is a **separate practice**<br>- Real production deployment = **Continuous Deployment** |
| **⚒️ How CI Works**                         | - Developers use **short-lived branches**<br>- Changes are merged via **pull requests** after **tests pass**<br>- Pull requests trigger **automated builds and tests**<br>- Merge only after all tests succeed |
| **💥 Problems with Traditional Dev**        | - **Long-lived branches** cause merge conflicts<br>- Teams delay integration, leading to **broken builds** and **delays**<br>- Old VCS made branching expensive, but Git solves this |
| **📦 Why Small Batches Matter**             | - Frequent commits reduce **conflict risk**<br>- Smaller changes are easier to **review and test**<br>- Avoids large, risky merges that take days to resolve |
| **🧪 Automation in CI**                     | - CI tools (GitHub Actions, Jenkins, Travis CI, etc.) automate:<br>• Detecting code changes<br>• Running builds<br>• Running all tests<br>- Ensures the **build is self-testing** |
| **👁️ Code Review via Pull Requests**        | - Every pull request is an opportunity for **peer review**<br>- Improves code quality and team communication<br>- Pull requests should **never be merged** with failing tests |
| **✅ Benefits of CI**                       | - Faster reaction time and delivery<br>- Reduces integration risk<br>- Encourages **clean, tested, and deployable code**<br>- Boosts **collaboration and code ownership**<br>- Makes **automated testing a standard** |
| **💡 Key Takeaways**                        | - CI = integrate and test **every change**<br>- CD = deploy every change to a **prod-like environment**<br>- Use **automation**, **short branches**, **pull requests**, and **tests**<br>- The **master branch must always be deployable** |



### Continuous Delivery

| **Category**                                     | **Key Points**                                               |
| ------------------------------------------------ | ------------------------------------------------------------ |
| **🔁 What is Continuous Delivery (CD)?**          | - CD = Practice of ensuring software can be **released to production at any time**<br>- Builds on Continuous Integration (CI)<br>- The **master branch must always be deployable**<br>- Code is automatically built, tested, and deployed to **production-like environments** |
| **📦 CI/CD Pipeline Components**                  | - **Code Repository** (e.g., GitHub)<br>- **Build Server** (e.g., Travis CI, GitHub Actions)<br>- **Integration/Orchestration Server** for automation<br>- **Artifact Repository** (e.g., Docker registry, JAR repo)<br>- **Deployment Configuration Tools** (e.g., Ansible, Kubernetes) |
| **🔧 Five Key Principles of Continuous Delivery** | 1. **Built-in Quality** – All changes go through automated tests<br>2. **Work in Small Batches** – Reduces risk, improves testability<br>3. **Automate Repetitive Tasks** – Let people focus on solving problems<br>4. **Relentless Improvement** – Measure and iterate<br>5. **Everyone is Responsible** – Broken builds are a team problem |
| **🚀 Continuous Deployment (CDP)**                | - Code is deployed **directly to production** after passing CI/CD<br>- Also known as **“continuous release”**<br>- Feature flags can control which parts are active |
| **🛡️ How DevOps Manages Risk**                    | - Deploy **early and often** to gain confidence<br>- Use **feature flags** to control activation separately from deployment<br>- Implement **blue-green deploys**, **canary testing**, and **zero downtime** strategies<br>- Avoid manual deployments to prevent human error |
| **📊 CI vs CD vs CDP**                            | - **CI**: Build + test every change<br>- **CD**: Deliver to pre-prod/staging environments<br>- **CDP**: Auto-deploy to **production**<br>- All aim to **shorten feedback loops** and **reduce failure impact** |
| **💡 Key Takeaways**                              | - CI/CD pipelines ensure fast, safe, and repeatable deployments<br>- Continuous Delivery requires CI and focuses on release readiness<br>- Deployment must be **automated**, **measured**, and **decoupled from activation** for reliability |



### Summary

- Taylorism was designed for factory work and software development is bespoke, that is, more like craftwork, and that working in silos leads to mistakes and bottlenecks. 
- Team ownership and stable teams make software development more like product development rather than project management. 
- Developers want innovation, while Operations want stability. 
- Required DevOps behaviors include shared ownership, collaboration, embracing change, and data-driven responses. 
- Infrastructure as Code is describing infrastructure in a textual executable format. 
- Ephemeral infrastructure can be used and then discarded because servers are built on demand, via automation, using Infrastructure as Code techniques. 
- Continuous Integration is building, testing, and integrating every developer change into the master branch after tests have passed. 
- The benefits of Continuous Integration include faster reaction time, moving faster, and reducing the risk in integrating code. 
- Continuous Delivery ensures that code can be rapidly and safely deployed to production by delivering every change to a production-like environment. 
- The five principles of Continuous Delivery have to do with quality, working in small batches, automation, continuous improvement, and shared responsibility.