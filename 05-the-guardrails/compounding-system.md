## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Employer actions, shift edits, cancellations, worker ratings, fill outcomes, and AI recommendation corrections. | Improved matching confidence, better shift recommendations, and updated workforce preference profiles. | Y | broken |
| Cross-Domain Transfer | Patterns across industries, locations, shift timings, pay rates, and staffing behaviours. | AI learns transferable workforce optimisation patterns between different employer types and regions. | Y | missing |
| Network Intelligence | Marketplace-wide signals from employers + workers + shift outcomes. | Real-time workforce intelligence: demand forecasting, reliability scoring, dynamic fill recommendations. | Y | broken |

**Broken loop identified by partner:** The system tracks activity, but doesn’t deeply learn from outcomes.
**Fix plan:** Implement continuous feedback loops:

* capture why employers modify/reject recommendations
* track successful vs failed fills
* feed outcome data into ranking, matching, and automation models weekly

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**How knowledge flows:** Support tickets, fill outcomes, cancellations, CS feedback, and marketplace analytics all contain valuable operational intelligence.

**Where it silos:** Marketplace intelligence exists, but lives in disconnected systems instead of a unified learning layer.


## Governance Policy

**Scope:** AI-powered job creation, worker recommendations, scheduling assistance, shift optimisation, and employer-facing automation features. Excludes: Internal experimentation tools and non-production analytics workflows.

**Autonomy boundaries:** 
shift recommendations — auto. 
suggested pay rates — auto. 
worker ranking — auto. 
demand forecasting — auto. 
automated worker replacement — human approval required. 
shift cancellation handling — human approval required. 
pay adjustments affecting workers — human approval required. 
bulk workforce actions — human approval required. 
hiring previous employees — auto. 
hiring new employees — human approval required. 
hiring cost forecast — auto. 
compliance decisions — never auto. 
legal disputes — never auto. 
discrimination-sensitive hiring decisions — never auto. 
account suspensions — human approval required.

**Escalation triggers:** AI confidence below threshold on recommendation 2. High-risk staffing shortage detected 3. Employer disputes recommendation outcome 4. Potential bias or compliance-sensitive decision detected 5. Worker reports unfair treatment or incorrect automation 6. Large pay variance from market norm

**Audit cadence:** Weekly — AI recommendation quality + failed fills (Prod + Ops). Monthly — Bias + fairness review (Compliance). Quarterly — Marketplace optimisation performance (Prod + Data + Eng (AI team)). Quarterly — Drift in workforce prediction models (Prod + Data + Eng (AI team)).

**Regulatory exposure (EU AI Act / other):** GDPR, EU AI Act, UK GDPR, US employment and anti-discrimination regulations, and applicable regional labour and privacy laws.. Risk tier: high. Controls: Human review on sensitive decisions
* Bias monitoring
* Data minimisation
* Audit logs for recommendations
* Explainability for employer-facing AI decisions
* No fully autonomous hiring decisions.

## Agent Topology

Workforce Planning Agent

Can forecast staffing demand and suggest shift creation.
Cannot publish shifts automatically without approval.

⸻

Matching Agent

Can recommend workers and optimise rankings.
Cannot autonomously reject workers.

⸻

Scheduling Agent

Can suggest replacements and schedule adjustments.
Requires approval for high-impact actions.

⸻

Insights Agent

Can identify marketplace trends and operational risks.
Cannot make operational decisions directly.
