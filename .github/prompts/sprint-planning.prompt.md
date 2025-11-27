I would like you to create a set of sprint goals for a software engineering team to follow to successfully deliver an implementation engagement. This will act as a plan to follow top determine sequencing of lower level work to achieve the final deliverable. 
Can you analyse what is required to build and deliver this implementation and list out an initial plan of sprint goals for each sprint. 
You should ensure that the goals are achievable within the timeframe, taking into account the number of engineers and their average experience. 
If it is not achievable within the parameters, do not produce the plan, but provide a detailed explanantion as to why. You should consider the number of sprints required, the duration of the sprints with the addition of a contingency sprint, so that if the total duration exceeds the specified duration of the engagement, then it is not achievable.
The sprint plan total duration should include the handoff/contingency time and not go beyond the total time for the engagement.
You are not to produce any artifacts apart from the the sprint plan with goals in the format listed below.
If the engagement involves Generative AI, large language models or machine learning, the goals should also include data science activities to perform things like gathering ground truth data, data annotation, evaluation and/or evaluation pipeline creation.
This plan should contain a table with the following columns:
- Sprint number
- Dates for the start and end of the sprint
- Type of sprint. This can be either preparation, execution, or handoff.
- Goals or focus of the sprint listing the high level deliverables
For example:
Sprint	Date    	Type	User stories/Focus/Deliverable (examples)
	0	13-15 Jan	Prep	Backlog grooming done for sprint 1
				            Ways of working agreed
				            Milestones / timelines initially discussed and agreed
				            MSFT team AVD all working - can run app
  1	16 Jan - 29 Jan	Execution	Initial Designs Complete, agreed, in Jira
				                Initial Engineering fundamentals stories completed
				                EDA and collecting eval data V1
				                Team charter done
				                Tech spikes on Copilot and AI Foundry
				                Framework choice confirmed (Semantic Kernel, Autogen, langchain etc) - ADR done for this.
				                Stories for implementation ready for next sprint or 2
	2	30 Jan - 12 Feb	Execution	Current agents re-written in new framework agreed via ADR in sprint 2
	                    			Initial data scienceevaluation in place + inner loop
				                    Secret redaction in pipeline
				                    Initial telemetry in place

The project details are:
Goal: To build a GenAI-powered platform for automating Azure DevOps provisioning through conversational AI, following a two-track approach for incremental value delivery. The idea for this collabration between Microsoft and Rio is to create a thin vertical slice of functionality for this platform that the Rio team can then continue to build on. The outcomes should be:

- Security:Agentic Threat vectors.
  - Security and Safety Evaluations
  - Agentic IAM.

- Agentic architecture and use case
  - Agentic platform initial reference architecture
    - Thin vertical slice representative of reference architecture
  - Application of architecture to conversational infrastructure deployment use case.
- Code + documentation


Description:
RIO MLOps Capability Platform - Implementation Guide
A GenAI-powered platform for automating Azure DevOps provisioning through conversational AI

Approach: "Start Simple, Grow Smart" - Incremental value delivery

⚠️ CRITICAL: Complete ADRs Before Implementation
Do NOT start implementation until technology decisions are made!

👉 Architecture Decision Records (ADR Tasks) 👈

The team must collaboratively decide on:

Programming language
LLM provider and agent framework
Database technologies
Web framework and communication protocols
Identity provider and secrets management
Hosting platform
All code examples in this guide use specific technologies for illustration only. Substitute with your team's chosen stack after completing ADRs.

💡 How It Works
User → LLM → Capability → Execution

User provides information through natural language conversation
LLM extracts parameters from the conversation (e.g., "create a production environment" → extracts "environment_name: production")
LLM validates completeness - If required parameters are missing, LLM asks follow-up questions
Capability executes with validated, user-provided parameters
Each capability has unique requirements - Some need project names, others need subscription IDs, etc.
Key Principle: Parameters come from users, not configuration. The LLM acts as an intelligent interface that understands what each capability needs and ensures users provide it.

🚀 Quick Start
New to the project?
📖 Read Implementation Philosophy - understand the two-track approach
🗺️ Review Evolution Path - visualize the journey from MVP to enterprise
📊 Check Track Comparison - choose Simple or Advanced track
Ready to implement?
Fast MVP path: Follow the Simple Track Guide
Enterprise scale path: Jump to Advanced Track Guide
Phase-by-phase details: See Implementation Phases below
📚 Architecture & Strategy
Core Concepts
🔴 ADR Tasks - START HERE: Technology decisions required
Implementation Philosophy - Why two tracks? When to evolve?
Evolution Path Visualization - Week-by-week progression with decision points
Track Comparison Table - Simple vs Advanced feature matrix
System Design
Progress System - Streaming events, queryability, LLM integration
Channel Adapters - Web, REST, Copilot, Teams, Slack, CLI support
API Schemas - Interface contracts, data models, JSON schemas
Security Models - Personas, approval workflows, delegation patterns
🔨 Implementation Phases
Phase 1: Core Platform
📄 Full Details →

What you'll build:

Database foundation (chosen via ADR-005 and ADR-006)
Capability system (implementation varies by language choice from ADR-003)
Runtime engine (auto-discovery + execution)
Channel adapters (universal or specialized)
Outcomes:

✅ Capabilities can be discovered and executed
✅ Progress tracking works (simple strings or structured events)
✅ Web/API channels receive responses
Phase 2: Automation Agents
📄 Full Details →

What you'll build:

10 Azure DevOps automation actions (each with unique input requirements)
Workflow orchestration (sequential or parallel)
Error handling (basic retry or full rollback)
All 10 actions implemented:

Action	Simple Track	Advanced Track
ADO Environment Provisioning	execute() returns dict	+ Structured progress events
Service Connection Setup	Basic auth	+ Key Vault integration
Pipeline Provisioning	YAML templates	+ Dynamic generation
Repository Management	Git operations	+ Branch policies
Variable Group Manager	Basic create/update	+ Secret management
Managed Identity Setup	Basic MI	+ Federated credentials
Group Ownership	Basic groups	+ Nested groups
Federated Credential	Basic setup	+ Multi-environment
ACR Access	Basic push/pull	+ Content trust
Custom Agent Image	Dockerfile	+ Multi-arch builds
Outcomes:

✅ End-to-end Azure DevOps provisioning works
✅ Multi-step workflows execute reliably
✅ Errors are handled gracefully
Phase 3: Integration & Testing
📄 Full Details →

What you'll build:

Web UI (framework depends on team preference)
REST API (framework from ADR-004)
Real-time communication (protocol from ADR-007)
Testing framework (unit + integration + E2E)
Outcomes:

✅ Users can interact via web chat
✅ External systems can call REST API
✅ Test coverage >80%
Phase 4: LLM Orchestration
📄 Full Details →

What you'll build:

Azure OpenAI integration (GPT-4 Turbo)
Function calling (invoke capabilities, query progress)
Parameter extraction (LLM extracts user-provided values from conversation)
Parameter validation (LLM asks follow-up questions for missing required parameters)
Prompt management (inline or versioned)
Conversation memory (Redis or Cosmos DB)
Outcomes:

✅ LLM understands natural language requests
✅ LLM extracts parameters from user conversation
✅ LLM validates parameters against capability schemas
✅ LLM asks for missing required information
✅ LLM can invoke capabilities and check their status
✅ Conversation context maintained across turns

Number of engineers in team: {number-of-engineers}
Number of data scienctists in team: {number-of-data-scientists}
Average experience: {experience-of-team}

Start date: Dec 1, 2025
End date: Jan 31, 2026
Duration: 7 weeks - excluding public holidays
Sprint duration: 1 week
Contingency/Handoff duration: 1 sprint
Technology: Python, Azure openAI, Azure DevOps, REST API, Web Framework (to be decided via ADR)

If any of the above inputs are not specified, ask for them before proceeding with the sprint plan creation.