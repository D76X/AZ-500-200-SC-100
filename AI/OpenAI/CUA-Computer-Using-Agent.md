# What is a computer-using agent (CUA)?

> Refs
[Fast Focus: Run Untrusted Code Safely with Azure Container Apps Dynamic Sessions Microsoft Azure Developers](https://www.youtube.com/watch?v=NtdxajLu9Ek&t=810s)

---

A `computer-using agent (CUA)` is an AI system that interacts with digital interfaces 
the way a human does—by viewing the screen, moving the cursor, clicking buttons, 
typing text, and scrolling through applications. 

[1] (https://www.thehackettgroup.com/glossary/computer-using-agent-model/), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

## How CUAs Work

Instead of relying solely on hidden code connections or Application Programming Interfaces (APIs), 
a CUA uses a continuous perceive-act loop: 

[1] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

1. Perceive: 
The agent captures a screenshot of the computer interface and sends it to a vision-language model (VLM) 
along with the user's task. 

[1] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

2. Reason: 
The model analyzes what is on the screen, grounds the target elements 
(such as finding the right button or form field), and decides the next step. 

[1] (https://cua.ai/docs/cua-driver/what-is-computer-use), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

3. Act: 
The agent executes the action—such as a mouse click at specific pixel coordinates or 
keyboard input—via the operating system. 

[1] (https://cua.ai/docs/cua-driver/what-is-computer-use), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

4. Verify: 
It takes a new screenshot to confirm whether the action succeeded before planning the next move. 

[1] (https://cua.ai/docs/cua-driver/what-is-computer-use), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

## Key Advantages

- No APIs Required: 
Because they operate at the graphical user interface (GUI) level, CUAs can 
automate legacy enterprise software, internal web portals, and desktop apps 
that lack public APIs or integrations. 

[1] (https://www.thehackettgroup.com/glossary/computer-using-agent-model/), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

- End-to-End Reasoning: 
Unlike rigid `Robotic Process Automation (RPA)` scripts that break if a button moves 
by a few pixels, a CUA dynamically adapts to interface changes by "seeing" the screen. 

[1] (https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/the-future-of-ai-computer-use-agents-have-arrived/4401025), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

- Cross-App Workflows: 
They can chain together actions across multiple distinct applications 
(like reading an invoice PDF and typing the data into a web form). 

[1] (https://www.youtube.com/watch?v=R0APWDVEm1g), 
[2] (https://medium.com/data-science-at-microsoft/where-ai-meets-gui-an-overview-of-computer-using-agents-3085d3bbe332)

## CUAs vs. Traditional Automation

- vs. API Function Calling: 
Direct API calls are much faster and more reliable. CUAs are reserved for software 
where an API does not exist. 

[1] (https://www.flozic.ai/agents/cua), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas)

- vs. Robotic Process Automation (RPA): 
RPA replays pre-recorded, hard-coded keystrokes and clicks. 
CUAs use visual reasoning to figure out how to complete a task on the fly. 

[1] (https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/the-future-of-ai-computer-use-agents-have-arrived/4401025), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas), 
[3] (https://www.flozic.ai/agents/cua)

## Examples and Frameworks

Several major models and platforms incorporate computer-use technology:

- Anthropic: Introduced computer use capabilities for Claude 3.5 Sonnet.
- OpenAI: Released its "Operator" research preview powered by its CUA model, integrated into ChatGPT.
- Google: Developed Gemini computer-use models.
- Microsoft: Uses computer use automation via tools like Microsoft Copilot Studio and Project Opal.
- Open-Source Infrastructure: Projects like Cua Docs provide drivers and sandboxed virtual environments (VMs) to let AI safely test and drive operating systems. 

[1] (https://learn.microsoft.com/en-us/microsoft-copilot-studio/computer-use), 
[2] (https://www.ultralytics.com/glossary/computer-use-agents-cuas), 
[3] (https://dev.to/goroman/cua-computer-using-agent-the-ai-that-operates-your-computer-1b4d), 
[4] (https://microsoft.github.io/ai-agents-for-beginners/15-browser-use/), 
[5] (https://www.youtube.com/watch?v=C4tu0FAECgg), 
[6] (https://cua.ai/docs/cua-driver/what-is-computer-use)

---

# CUA in Microsoft Foundry

[Use the computer use tool for agents (preview)](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/computer-use?pivots=python)  

---