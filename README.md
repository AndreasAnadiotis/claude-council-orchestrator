# Multi-Agent Council Orchestrator for Claude Code

An advanced prompt-engineering and multi-agent framework built on top of the Claude Code CLI. This project configures a parallel evaluation protocol that stress-tests business models, operational strategies, and product ideas from three distinct, rigorous perspectives simultaneously.

## 🚀 How It Works
When triggered by the custom phrase `council discuss [idea]`, the framework spins up three independent sub-agents in parallel to evaluate the proposal before synthesizing a final executive dashboard.

### The Council Members:
1. **The Optimist Maximalist:** Evaluates best-case trajectories, market ceilings, and high-value flywheels.
2. **The Devil's Advocate:** Conducts pre-mortems, uncovers blind spots, and highlights structural vulnerabilities.
3. **The Neutral Analyst:** Grounded anchor focused on data verification, trade-offs, and empirical uncertainties.

## 📂 Architecture
- `CLAUDE.md` - The master orchestration layer and system rules.
- `agents/optimist-maximalist.md` - Persona configuration for uppercase potential.
- `agents/devils-advocate.md` - Persona configuration for risk mitigation.
- `agents/neutral-analyst.md` - Persona configuration for objective trade-off mapping.

## 📊 Sample Output: Council Consensus Dashboard
At the conclusion of every analysis, the orchestrator outputs a structured summary:
- **Agent Recommendations:** A 2-sentence distillation of each agent's independent stance.
- **The Convergence Point:** The core ground truth where all perspectives align.
- **Actionable Next Steps:** 4 immediate, sequential execution steps.
- **Alternative Pivot:** A lower-risk alternative path surfaced during the friction round.
