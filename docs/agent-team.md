# Agent team

I will use this custom agent team to build Mona's Project Pulse dashboard:

- **Planner** (Claude Opus 5.5): researches the repository, documentation, dependencies, and edge cases, then creates the implementation plan. Definition: `.github/agents/planner.agent.md`.
- **Designer** (Gemini 3.7 Flash): shapes the dashboard's user experience, accessibility, information hierarchy, interactions, and responsive visual design. Definition: `.github/agents/designer.agent.md`.
- **Coder** (GPT-5.5): implements assigned application logic and runnable-app support, following project patterns and validating changes. Definition: `.github/agents/coder.agent.md`.
- **Orchestrator** (Claude Opus 5.5): delegates work to the specialists, coordinates file scopes and execution phases, and verifies the integrated result. Definition: `.github/agents/orchestrator.agent.md`.

I am using GitHub Copilot CLI in a Codespace to orchestrate the work.
