# 🏰 Week 2 – Data-Oriented Design & Agile Memory Palace

---
- ## 🏗️ Room 1: The CPU Temple —  *Data-Oriented Design Core Ideas*
  
  **Entrance Hall – What is Data-Oriented Design?**
- A temple built to **worship data flow and performance**.
- Think of it as **“database-like” techniques** applied to memory and CPU.
- The CPU is the deity:
	- What slows it down? Cache misses.
	- What speeds it up? Contiguous data and predictability.
	  
	  **Chamber of Application**
- Engraved on the walls: *Database engines*, *Games*, *Simulations*, *Solvers*.
- Any place with **lots of uniform data** but **no formal database**.
  
  ---
- ## ⚙️ Room 2: The Object Graveyard —  *Why OOP Hurts Performance*
  
  **Statues of Indirection**
- Every object points to another object — **too many references**!
- Each statue labeled:
	- Extra CPU work
	- Heap allocation
	- Hot + Cold data mixed
	- Read-only and read-write data tangled
	  
	  **Hot Data Altar**
- A small glowing core: “Hot data = frequently reused, small data set.”
  
  **Cache Pitfall Corridor**
- Signs read:
	- CPU can’t use RAM directly.
	- Data only lives in registers.
	- Instructions only run from nano-op cache.
	  
	  ---
- ## 🧠 Room 3: The Cache Cathedral
  
  **Two Altars of Eviction**
- *Least Recently Used* and *Least Frequently Used*.
- A neural oracle balances both → modern CPUs use **NN-based speculative prefetching**.
  
  **Patterns on the Floor**
- Sequential pattern = a long, predictable rug.
- Random pattern = scattered mosaic (slow access).
  
  **Shrine of Random Access (Java Example)**
  
  ```
  Integer[] array2 = new Integer[1*GB];
  for (var a: array2) { doStuff(a); }
  ```
- Each `Integer` = reference + data → heap explosion (48 GiB).
- Fixes: primitives, off-heap buffers, avoid per-element looping.
  
  ---
- ## 💾 Room 4: Heap and Memory Vault
  
  **Table of Local Variables**
- `ObjectX a;` → lives in **L1 cache** (inside CPU).
- `a = new ObjectX();` → lives in **heap** (main memory).
- The variable `a` = a **pointer** to that heap address.
  
  **Four Heap Lists in the Great Library**
- Tiny
- Small
- Medium
- Large
  
  Heap inscriptions:
- **Allocation:** first come, first serve.
- **Destruction:** random (garbage collection).
- **Layout:** fragmented, non-contiguous.
- **Bookkeeping:** uses extra space.
  
  ---
- ## 🧩 Room 5: Indirection and Eviction Hall
  
  **Twin Problems of Objects**
- Heap residence (random layout).
- Indirection (lookups, vtable, etc.).
  
  **Indirection Steps on a Spiral Staircase**
- Fetch instruction
- Fetch reference
- Find address in vtable
- Fetch function
- Cache hit/miss guessing game
  
  **Cache Eviction Plaque**
- CPUs fetch 32-byte blocks.
- Eviction happens even for 1-byte access — but it’s faster overall.
  
  ---
- ## 🔬 Room 6: The Design Laboratory —  *Steps of Data-Oriented Design*
  
  **Stations of Analysis**
- Split hot vs cold data.
	- Hot: in loops, frequent, object-heavy.
	- Cold: rare, unaffected by object count.
	- Unsure? → Use profilers/timers.
- Analyze data flow — merge shared data access.
- Group data mutated together.
  
  ---
- ## 🧮 Room 7: CPU Mechanics Chamber
  
  **Pipeline Columns**
- Fetch → Decode → Execute → Write
  
  **Speculation Garden**
- CPU guesses the future; if wrong → rollback and re-execute.
  
  **Superscalar Fountain**
- Water flows in parallel paths = out-of-order execution.
  
  **Stack Engine Pedestal**
- Simulates stack inside registers for speed.
  
  **Compiler vs CPU Overlook**
- Compiler: sees code statically.
- CPU: dynamic, uses neural nets for live optimization.
  
  ---
- ## 🛡️ Room 8: The Fortress of Defensive Programming
  
  **Five Towers:**
- **Const Correctness**
	- Prevents unwanted mutation.
	- 3 types: methods, objects, parameters.
- **Input Validation**
	- Bounds, object, capacity, SQL/HTML injection checks.
- **Assertions**
	- Dev only, pre/post conditions, no functions in assertions.
- **Error Handling**
	- *Exceptions:* no cost unless thrown, don’t expose to users.
	- *Error codes:* small, consistent overhead.
	- *Direct handling:* immediate fixes.
- **Resource Management**
	- Careful allocation/deallocation.
	  
	  ---
- ## 🔍 Room 9: Quality Assurance Quarters
  
  **Static Analysis Wing**
- Detects smells and bugs early.
  
  **Sanitizer Lab**
- Injects checking code (5 types):
	- Address, Memory, Undefined, Leak, Thread
	  
	  **Fuzzing Chamber**
- Feeds random inputs → checks for crashes or security flaws.
  
  **Unit Test Room**
- Isolated code testing (functions, classes).
  
  **Test-Driven Development Steps**
- Write empty code
- Write tests
- Implement until green
- Add tests
- Add code
- Comprehensive coverage
- Use **mocks/dummies** for missing dependencies.
  
  ---
- ## 🔗 Room 10: Testing Arena
  
  **Test Selection**
- Partition Testing → group categories.
- Guideline Testing → use known failure cases.
  
  **Integration Testing Tower**
- BigBang (all at once)
- Incremental (phases)
- Approaches: top-down, bottom-up, sandwich.
  
  **Regression Testing Garden**
- Re-run all old tests after change.
- 7 types: corrective, retest-all, selective, progressive, complete, partial, unit.
  
  **User Acceptance Chamber**
- Evaluate user needs, usability, functionality.
- Includes alpha (in-house) and beta (public).
  
  ---
- ## 🧱 Room 11: Agile Citadel
  
  **Main Hall – Agile Manifesto**
  
  > 
  
  Individuals & interactions > tools
  
  Working software > documentation
  
  Customer collaboration > contracts
  
  Responding to change > plans
  
  **Waterfall vs Agile Wall**
- Waterfall: clear, rigid, known problems.
- Agile: adaptive, fluid, unknown problems.
  
  **Security Corner**
- Plan security early (“shift left”).
- Hard to test; often at odds with usability.
  
  ---
- ## ⚡ Room 12: Agile Principles Gallery (12 Frescoes)
- Customer satisfaction
- Embrace change
- Frequent delivery
- Business + dev cooperation
- Trust the team
- Face-to-face
- Working software = progress
- Sustainable pace
- Excellence and good design
- Simplicity
- Self-organizing teams
- Reflect and improve
  
  ---
- ## 👥 Room 13: Team Empowerment Hall
- Teams own delivery.
- Outside interference reduces motivation.
- Together they: clarify, prioritize, agree, estimate.
- Shared ownership and accountability.
  
  ---
- ## 🎯 Room 14: Product Room — Requirements & Stories
  
  **Pareto’s Law Poster**
- 80% of results from 20% effort — but which 20%?
  
  **Requirement Scrolls**
- High-level, minimal, just-in-time.
- Capture collaboratively.
- Balance scope, cost, risk.
  
  **User Story Table**
- Format: *As a [who], I want [what], so that [why].*
- 3 parts: Name, Conversation, Acceptance criteria.
- Each ≤16 hours of work.
  
  ---
- ## 🌀 Room 15: Incremental Design Workshop
- Design evolves with the system.
- Contrast with traditional design (rigid, predictive).
- Agile assumes changing requirements.
  
  **Budget Mural**
- Time & budget fixed; scope flexible.
- Prioritize high-value deliverables.
- Shippable features = 100% complete.
  
  ---
- ## 🔁 Room 16: Agile Cycle Forge
  
  **Cycle Gears**
- Analyze → Develop → Test → Repeat
  
  **Benefits:** Reduced risk, flexibility, better cost control.
  
  **Prototype Bench**
- True prototypes → learn the problem.
- Skeleton → expand on it.
- Integrate changes continuously.
  
  **Nightly Builds Hatchery**
- Rebuild daily, run automated tests.
  
  ---
- ## 💻 Room 17: Collaboration Chamber — Pair Programming & Code Review
  
  **Pair Programming Table**
- Two developers, one keyboard.
- Benefits: shared knowledge, quality, motivation.
- Challenges: pace, skill gaps, communication.
  
  **Code Review Balcony**
- Every change reviewed.
- Risks: sloppiness, over-reliance, sunk cost, long feedback loops.
  
  ---
- ## 🏁 Room 18: Security Dungeon — OWASP Top 10
  
  | 
  | ID | 
  | Vulnerability | 
  | Fix | 
  |
  
  | ---- |
  
  | 
  | A01 | 
  | Broken access control | 
  | Deny by default | 
  |
  
  | 
  | A02 | 
  | Cryptographic failures | 
  | Encrypt in transit/at rest | 
  |
  
  | 
  | A03 | 
  | Injection | 
  | Safe APIs + whitelisting | 
  |
  
  | 
  | A04 | 
  | Insecure design | 
  | Shift left | 
  |
  
  | 
  | A05 | 
  | Misconfiguration | 
  | Secure install | 
  |
  
  | 
  | A06 | 
  | Outdated components | 
  | Patch + sign | 
  |
  
  | 
  | A07 | 
  | Auth failures | 
  | MFA, no backdoors | 
  |
  
  | 
  | A08 | 
  | Data integrity fail | 
  | Signed software | 
  |
  
  | 
  | A09 | 
  | Logging/monitoring fail | 
  | Log everything | 
  |
  
  | 
  | A10 | 
  | SSRF | 
  | Sanitize + whitelist | 
  |
  
  ---
- ## 🔄 Exit Hall: DevOps Shift Left Banner
- Move testing, security, and quality **earlier**.
- Test during design and coding.
- Integrate sanitary checks continuously.
  
  ---
- # 🧭 Summary Path
- CPU Temple → 2. OOP Graveyard → 3. Cache Cathedral →
- Memory Vault → 5. Indirection Hall → 6. Design Lab →
- CPU Mechanics → 8. Defensive Fortress → 9. QA Quarters →
- Testing Arena → 11. Agile Citadel → 12. Principles Gallery →
- Team Hall → 14. Product Room → 15. Design Workshop →
- Cycle Forge → 17. Collaboration Chamber → 18. Security Dungeon → Exit.