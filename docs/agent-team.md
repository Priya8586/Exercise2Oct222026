# Agent team

The team for building Mona's Project Pulse dashboard is coordinated through GitHub Copilot CLI in a Codespace.

| Agent | Target model | Responsibility | Definition |
| --- | --- | --- | --- |
| **Orchestrator** | Claude Opus 5.5 (copilot) | Coordinates the work, gets the implementation plan, assigns specialists scoped tasks, manages dependencies and phases, and integrates and verifies their results. It does not implement the dashboard itself. | `.github/agents/orchestrator.agent.md` |
| **Planner** | Claude Opus 5.5 (copilot) | Researches the repository, relevant documentation, dependencies, and edge cases, then provides an ordered implementation plan with file assignments, dependencies, risks, and validation expectations. It does not write code. | `.github/agents/planner.agent.md` |
| **Designer** | Gemini 3.7 Flash (copilot) | Shapes the dashboard's usability, accessibility, information hierarchy, interaction flow, visual clarity, and responsive behavior. For Project Pulse, it emphasizes project cards, status badges, priority, and polished responsive styling. | `.github/agents/designer.agent.md` |
| **Coder** | GPT-5.5 (copilot) | Implements assigned application code and support configuration, following repository patterns and validating changes. For Project Pulse, assigned runnable-app work can include a launch configuration that opens the dashboard. | `.github/agents/coder.agent.md` |

The Orchestrator delegates planning to the Planner, then assigns implementation and design work to the Coder and Designer with explicit file scopes. It runs independent work in parallel and sequences work when dependencies or overlapping files require it. Agents do not stage, commit, or push; those Git operations remain under the learner's control through Copilot CLI.
