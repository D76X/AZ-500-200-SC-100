# Modern Software Engineering

[Modern Software Engineering](https://www.youtube.com/@ModernSoftwareEngineeringYT)  

---

# AI Topics

[AI Briefings by Modern Software Engineering - Playlist](https://www.youtube.com/playlist?list=PLwLLcwQlnXBxEN_e5gfzfKmUS9XW2U8Jz)   

[I Stopped Coding and Started Architecting Agents (And You Should Too) Modern Software](https://www.youtube.com/watch?v=JaiJ5wxdmCA)   

[How to Stop AI from Ruining Your Codebase Modern Software Engineering](https://www.youtube.com/watch?v=6AgndHSkHFI&t=108s)   

[Why "Vibe Coding" is a Lie (And Startups are Paying the Price) Modern Software Engineering](https://www.youtube.com/watch?v=T539pbwTIZY)   

[The Real AI Threat ISN'T Sci-Fi (It’s So Much Worse) Modern Software Engineering](https://www.youtube.com/watch?v=mRF99to28sA)   

---

## Harness Engineering

[I Stopped Coding and Started Architecting Agents (And You Should Too) Modern Software](https://www.youtube.com/watch?v=JaiJ5wxdmCA)   

---

# What are guides in Harness Engineering?

In harness engineering, guides are feedforward control mechanisms that steer an AI agent's 
behavior and decisions before it takes action. [1] 

## Key Characteristics of Guides

* Proactive Steering: They act as guardrails, instructions, and contextual maps provided up front to prevent errors rather than just catching them later. [2, 3] 
* Pre-action Input: They define boundaries, operational rules, and project specifics before execution begins. [1, 3] 
* Complement to Sensors: While sensors provide feedback after an action (like automated tests or error logs), guides provide direction before the agent executes a task. [1, 3] 

## Common Examples

* Instruction Files: Markdown files like AGENTS.md or CLAUDE.md that outline project goals, rules, and constraints.
* Progressive Disclosure Maps: Short architectural maps or summaries that direct agents to relevant documents on demand.
* Code Modifiers and Linters: Static rules or pre-commit configurations that coach or restrict the model's output formatting and coding styles.
* Reusable Skills: Explicit capability definitions that tell the model how to safely interact with specific tools or APIs. [1, 3, 4, 5, 6, 7] 

· 1970 M01 1

[1] [https://martinfowler.com](https://martinfowler.com/articles/harness-engineering.html)
[2] [https://dev.to](https://dev.to/tacoda/sensors-and-guides-two-ways-your-harness-talks-to-your-agent-39oh)
[3] [https://www.youtube.com](https://www.youtube.com/shorts/-SORWXsNb6E)
[4] [https://www.youtube.com](https://www.youtube.com/watch?v=19v0011R-sI&t=592)
[5] [https://github.com](https://github.com/walkinglabs/learn-harness-engineering)
[6] [https://medium.com](https://medium.com/@gaurav.caprihan/harness-engineering-for-dummies-997af08e3264)
[7] [https://www.nxcode.io](https://www.nxcode.io/resources/news/harness-engineering-complete-guide-ai-agent-codex-2026)

---

# What are sensors in Harness Engineering?

In harness engineering, sensors are feedback control mechanisms that observe what an AI coding agent 
produces and provide data so the agent can self-correct before a human reviews the code. [1, 2] 
Harness engineering treats an AI system as Agent = Model + Harness, where sensors act as the automated 
evaluation loop. While "guides" steer an agent before it acts, sensors check its work after it acts. [3, 4, 5] 

## Types of Sensors

Sensors fall into two main execution categories based on how they process information: [1] 

* Computational Sensors: Fast, deterministic tools run by the CPU. They provide factual, objective observations in milliseconds or seconds.
* Examples: Automated test suites, linters, type checkers, and log monitoring. [1, 6] 
* Inferential Sensors: Semantic analysis or probabilistic evaluations typically run by a GPU or NPU. They are slower and more expensive, often relying on an "LLM as a judge" to evaluate another LLM's output.
* Examples: AI code reviews and semantic quality checks. [1, 6] 

## Why Sensors Matter

* Self-Correction: They give agents clear, actionable feedback signals (such as specific linter error messages) to fix bugs autonomously. [1, 6] 
* Reduced Oversight: They catch structural issues like style violations, duplicate code, or broken builds early, lowering the review burden on human developers. [1, 2] 
* Situational Awareness: A dashboard of passing or failing sensors gives developers quick health checks across the codebase path to production. [2, 6] 

· 1970 M01 1

[1] [https://martinfowler.com](https://martinfowler.com/articles/harness-engineering.html)
[2] [https://www.thoughtworks.com](https://www.thoughtworks.com/insights/blog/generative-ai/harness-engineering-agent-feedback-exploring-ai-coding-sensors)
[3] [https://www.softwareimprovementgroup.com](https://www.softwareimprovementgroup.com/blog/what-is-harness-engineering/)
[4] [https://nestr.io](https://nestr.io/blog/harness-engineering-ai-agents)
[5] [https://www.youtube.com](https://www.youtube.com/shorts/-SORWXsNb6E)
[6] [https://www.youtube.com](https://www.youtube.com/watch?v=uLWOLmeHOSE&t=4)

---