# 🏰 Week 1 – Project Management & Process Design Memory Palace

---
- ## 🏛️ Entrance Hall — *Projects vs Processes*
  
  **Two Doors at the Entrance:**
  
  * 🚪 **Left Door – Process**
  
  * Routine, continuous, well-documented, efficient.
  * Controlled by **fixed measurements**.
  * Measured by **efficiency & cost**.
  * Success rate: **>99%**.
  
  * 🚪 **Right Door – Project**
  
  * Ad hoc, fixed start & end.
  * Unknown inputs/outputs.
  * Created from scratch.
  * Controlled by **desired outcomes**.
  * Measured by **meeting requirements**.
  * Success rate: **~50%**.
  
  ---
- ## ⏳ Hall of the Triple Pillars — *Project Success Metrics*
  
  Three marble pillars stand tall:
  
  1. ⏰ **Time**
  2. 💰 **Budget**
  3. ✅ **Quality** *(on requirements)*
  
  ---
- ## ⚙️ Room of Project Considerations
  
  **Murals of System Development:**
  
  * Dependencies on other software.
  * Specific skillsets at milestones.
  * Activities follow strict sequences.
  
  **Three Carvings of Brooks’ Problems:**
  
  * 🧩 **Essential Problems** – requirements, scope.
  * 🧰 **Accidental Problems** – tools, people, process.
  * ⚡ **Inefficiency** – mismatched complexity (too simple or too complex).
  
  ---
- ## 🧠 Chamber of Complexity (Dijkstra’s Workshop)
  
  **Two Scrolls:**
  
  * Minimize *essential complexity*:
  
  * Decompose problems.
  * Loose coupling.
  * Clean interfaces.
  * Prevent *accidental complexity*:
  
  * Use solid tools and frameworks.
  
  A plaque reads: “All other goals are secondary to managing complexity.”
  
  ---
- ## 🧩 Gallery of Good Design
  
  Paintings labeled:
  
  * Minimal complexity
  * Maintainable
  * Loose coupling
  * Extendable
  * Reusable
  * High **fan-in**, low **fan-out**
  * Lean and stratified
  * Standardized
  
  > “Make everything as simple as possible — but not simpler.”
  
  ---
- ## 🏗️ Design Pyramid — *Five Levels of Design*
  
  You ascend five floors of the pyramid:
- ### 🏛️ Level 1: Project Design
  
  * **Requirements**, **Scope**, **Feasibility**, **Architecture**.
  * Fulfills: functions, features, data I/O, performance, reliability.
  * Scope via **narratives** and **use cases**.
  * Goals from **stakeholder needs and priorities**.
  * Feasibility from **people, tools, and resources**.
  * Explicit requirements reduce risk and cost.
  
  **Four Requirement Checklists (Four Tablets):**
  
  1. ⚙️ *Functional* – inputs, outputs, interfaces, tasks, UI.
  2. 🧾 *Quality* – performance, security, reliability, maintainability.
  3. 📚 *Completeness* – feasible, fulfills needs, documents changes.
  4. ✅ *Correctness* – syntax, conflicts, testability, clarity.
  
  **Architecture Components:**
  
  * Language, subsystems, classes, data, business rules, UI, performance, scalability, I/O, errors, frameworks, security.
  
  ---
- ### 🧱 Level 2: Subsystems
  
  * Self-contained units, assigned to different people.
  * Manage frameworks and interactions.
  * Aim for **low fan-out**.
- ### 📦 Level 3: Classes / Packages
  
  * OOP = methods; DOD = data.
  * Design by considering object actions, interactions, and interfaces.
- ### ⚙️ Level 4: Methods / Data
  
  * Public interfaces, clarity, and interactions between components.
- ### 💻 Level 5: Source Code
  
  * Requirements, naming conventions, documentation, design patterns, parameters, pre/post conditions.
  
  ---
- ## 🎯 SMART Goals Chamber
  
  Five glowing stones spell **SMART**:
  
  * Specific
  * Measurable
  * Agreed upon
  * Realistic
  * Time-bound
  
  Nearby stands the **Deliverable Altar:**
  
  * Must be verifiable, specific, time-bound, quality-checked, and stakeholder-approved.
  
  ---
- ## 📅 Scheduling Observatory
  
  **Three Dials of Scheduling:**
  
  * Effort (time)
  * Resources
  * Deliverables
  
  If unrealistic → delay, add resources, or reduce scope.
  
  **Mythical Man Statue:**
  
  > “Adding more people makes you later.”
  
  ---
- ## 📚 The Planning Library — *Supporting Plans*
  
  Three scrolls rest on a desk:
  
  1. 🧍 **Human Resource Plan** – key staff, skillsets, numbers.
  2. 📢 **Communication Plan** – who to update, how, how often.
  3. ⚠️ **Risk Management Plan** – Accept, Reduce, Transfer, Avoid.
  
  ---
- ## 🖐️ The 5 P Hall — *Core Project Activities*
  
  Five banners hang from the ceiling:
  
  * People
  * Price
  * Product
  * Process
  * Project
  
  Each representing one pillar of project management.
  
  ---
- ## 👥 The Team Roundtable — *Roles and Success*
  
  Seats labeled:
  
  * Project Manager
  * Systems Analyst
  * UI Designer
  * Architect
  * Specialists
  * Documentation
  
  **Success Banners:**
  
  * *Individual*: interest, experience.
  * *Team*: communication, collaboration, management skills.
  
  ---
- ## 🧭 The Metrics Observatory
  
  **Three Spheres of Success:**
  
  * Activity (duration, due date, precursor)
  * Milestone (measurable end-product)
  * Deliverable (tangible outcome)
  
  **Deliverable vs Milestone:**
  
  * Deliverable = tangible result
  * Milestone = marker of completion
  
  ---
- ## 📊 The Metrics Vault
  
  **Why metrics?**
  Estimate resources; measure project (cost/duration) & application (size/complexity).
  
  **SMART Metrics Examples:**
  
  * Counts
  * Percentages
  * Sums
  * Averages
  * Ratios
  
  **Four Metric Types:**
  
  * Process
  * Product
  * Result / Control
  * Predictor
  
  **OOP Metrics:**
  
  * Change absorption (concreteness).
  * Application size (use cases, domain classes).
  * Class size (attributes, operations, method size).
  
  ---
- ## 🗓️ Project Scheduling Chamber
  
  Steps inscribed on the walls:
  
  1. Split work into tasks (minimize dependencies)
  2. Assign team members
  3. Estimate time
  4. Estimate effort
  
  **Non-Agile Scheduling Scroll:**
  
  * Identify activities, dependencies, resources, people, charts.
  
  **Kanban Board (Five Lanes):**
  
  * Stories/backlog → To Do → In Progress → Testing → Done
  
  ---
- ## 🕸️ The Network Analysis Web
  
  **Purpose:** find the critical path, estimate time, and calculate slack.
  
  **Six Steps of CPM:**
  
  1. Label tasks, dependencies, time
  2. Forward pass (earliest times)
  3. Backward pass (latest times)
  4. Total float = LS - ES
  5. Free float = independent slack
  6. Identify critical path
  
  **Limitations:** ignores uncertainty, human factors (task switching, Parkinson’s law).
  
  ---
- ## 🧩 CCPM Chamber — *Critical Chain Project Management*
  
  **Additions to CPM:**
  
  * Resource dependencies
  * Uncertain time
  * Buffers
  
  **Three Buffers:**
  
  * Project buffer (end of project)
  * Feeding buffer (non-critical paths)
  * Resource buffer (alert for resource need)
  
  **Planning Steps:**
  
  1. Identify tasks
  2. Create estimates
  3. Create buffers
  4. Assign resources
  5. Find critical chain
  6. Execute (track critical path)
  7. Monitor buffers
  
  ---
- ## ⚠️ Risk Management Tower
  
  **Why Manage Risk?**
  
  * Uncertainty & anticipation.
  
  **How:** Identify → Analyze → Rank.
  
  **Two Dimensions:** Probability × Cost.
  
  **Top 10 Risks:**
  
  * Personnel shortfall, unrealistic schedules, wrong features/interfaces, gold plating, changing requirements, external dependencies, performance, infeasible goals, competition, interruptions.
  
  **Consequences:** timeline, cost, feasibility, quality.
  **Cycle:** Perception → Analysis → Strategy → Monitor → Manage.
  
  ---
- ## 🔺 Software Triangle Hall
  
  An iron triangle labeled:
  
  * Cheap
  * Good
  * Fast
  
  > “You can only pick two.”
  
  **Feature Adding Corner:**
  
  * Avoid gold plating.
  * ROI drops as features increase.
  
  ---
- ## 🧍 Human Factors Room
  
  Graffiti on the wall:
  
  * Bad communication
  * Crunch
  * Procrastination
  * Gold plating
  * Task switching
  
  ---
- ## ⚖️ Methodology Chamber — *Agile vs Waterfall*
  
  **Waterfall:**
  
  * Requires perfect planning.
  * Unsuitable for changeable software.
  
  **Agile:**
  
  * Sometimes too little prep.
  * Must still pause to plan.
  
  **Wicked Problem Altar:**
  
  * “Unknown unknowns.”
  
  ---
- ## 🔄 Iteration Dome — *Modern Processes*
  
  **Benefits:** lightweight, parallel, adaptive.
  **Cycles engraved on rotating wheels:**
  
  **Prototyping:** Requirements → Prototype → Test
  **RAD:** Requirements → Design → Develop → Deploy → Learn
  **Iterative:** Plan → Develop → Prototype → Feedback → Develop
  
  **Differences from Waterfall:**
  
  * Frequent versions
  * Close collaboration
  * Client proximity
  * Hands-on development
  * Team expertise
  * Direct testing
  * Reduced risk
  * Faster value delivery
  
  ---
- # 🧭 Summary Path
  
  1. Entrance Hall → 2. Triple Pillars → 3. Considerations → 4. Complexity →
  2. Design Gallery → 6. Design Pyramid → 7. SMART Chamber →
  3. Scheduling Observatory → 9. Planning Library → 10. 5Ps Hall →
  4. Team Roundtable → 12. Metrics Observatory → 13. Metrics Vault →
  5. Scheduling Chamber → 15. Network Analysis Web → 16. CCPM Chamber →
  6. Risk Tower → 18. Software Triangle → 19. Human Factors →
  7. Methodology Chamber → 21. Iteration Dome → Exit.