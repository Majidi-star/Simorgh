This is the definitive, synthesized blueprint. I have merged Claude’s tactical corrections with the deep, institutional dynamics requested in the Gemini research prompt. 

This is no longer just a "list of roles." This is the **exact, causal taxonomy of a State-of-the-Art (SOTA) engineering organization**, explicitly mapped to how your **Swarm-Grid** must be architected to replicate it. 

If you build your AI agents to enforce this exact workflow, you will generate synthetic data and code that is indistinguishable from, or superior to, what is produced at Meta or Google.

---

### Part 1: The Complete SOTA Role Taxonomy (Human → AI Mapping)
*Every role exists to prevent a specific, costly failure mode. Your swarm must have an agent or deterministic tool for each.*

| Role / Function | Core Artifacts Produced | Decisions Made | Failure Mode if Skipped | 🤖 Swarm-Grid Implementation |
| :--- | :--- | :--- | :--- | :--- |
| **Product & UX Lead** | PRDs, User Flows, A/B Test Hypotheses | What to build, success metrics, prioritization. | Building features nobody uses; scope creep. | **Planner Agent:** Translates user prompt into strict JSON requirements based on GraphRAG PRDs. |
| **Design Systems Engineer** | Figma specs, Design Tokens (colors, spacing, typography), A11y annotations. | Visual consistency, RTL mirroring rules, tap-target sizes. | UI feels "janky," inconsistent, or fails App Store a11y reviews. | **GraphRAG Token Node:** Hardcoded JSON of design tokens injected into Coder Agent's context. |
| **Staff Architect** | Architecture Decision Records (ADRs), Folder Structure, API Contracts. | State management choice (e.g., Riverpod), SDK version pinning, package vetting. | "Big Ball of Mud" architecture; conflicting state logic; supply-chain security risks. | **Architect Agent:** Outputs the ADR and JSON blueprint. Vetted package list is a strict GraphRAG constraint. |
| **Feature Developer** | Dart code, `///` inline documentation, Unit/Widget tests. | How to implement the blueprint atomically. | Slow delivery, untestable code, missing edge-case handling. | **Coder Agent:** Takes JSON blueprint, outputs *only* Dart code + inline docs. |
| **SDET (Test Engineer)** | Golden tests, Integration test matrices, Mock data generators. | Test coverage strategy, flaky test quarantine. | Silent regressions; UI breaks on specific Android OEMs or iOS versions. | **Deterministic Validator:** Runs `flutter test`, `flutter analyze`, and platform-specific mock runners. |
| **Security & Privacy Engineer** | Threat models, Secret management rules, Input sanitization checklists. | Certificate pinning, secure storage (e.g., `flutter_secure_storage`), GDPR compliance. | Data leaks, app store rejection, malicious package injection. | **Security Linter Hook:** Regex/static analysis checking for hardcoded secrets or unsafe `http` calls. |
| **SRE / Release Manager** | Runbooks, Staged Rollout plans, Feature Flag configs, Postmortems. | When to rollback, crash-rate thresholds, SDK upgrade cadence. | Catastrophic production outages; inability to recover from bad deploys. | **Critic Agent & GraphRAG:** Logs failures as "Postmortem Nodes" to prevent recurrence. |

---

### Part 2: The "Definition of Done" (DoD) & Edge-Case Checklist
*Elite teams do not rely on "feeling done." This checklist is a **hard gate**. Your AI Validator must verify these before a task is marked complete.*

**The SOTA Flutter DoD Checklist (Must be enforced by the Swarm):**
1. [ ] **Happy Path:** Code works as specified in the JSON blueprint.
2. [ ] **Edge States:** Explicit UI states exist for: `Loading`, `Empty`, `Error` (with retry), and `No Permission`.
3. [ ] **Localization & RTL:** All strings are wrapped in an i18n method (e.g., `AppLocalizations.of(context)!`). Layouts use `Directionality` or `start`/`end` (not `left`/`right`) to support Persian/RTL flawlessly.
4. [ ] **Accessibility (a11y):** Semantic labels (`Semantics` widget) are present. Contrast ratios meet WCAG AA. Tap targets are $\ge$ 48x48dp.
5. [ ] **State Restoration:** The widget survives process death (uses `RestorationMixin` or persistent state storage).
6. [ ] **Documentation:** Every public class/function has a `///` Dartdoc comment explaining *why*, not just *what*.
7. [ ] **Zero Warnings:** `flutter analyze --fatal-infos` passes with 0 issues.
8. [ ] **Tests:** At least one Widget test and one Unit test exist for the new logic.

---

### Part 3: The Exact Chronological Workflow (With Hard Gates)
*Work cannot proceed to the next step until the gate is passed. This prevents compounding errors.*

1. **Gate 1: Ideation & Design Approval**  
   *Action:* Product/Design finalizes the Figma spec and Design Tokens.  
   *Gate:* Tokens are committed to the repo. No coding begins without them.
2. **Gate 2: Architecture & Contract Lock**  
   *Action:* Staff Architect writes the ADR and JSON Blueprint.  
   *Gate:* Blueprint is reviewed and merged. The Coder Agent is *only* allowed to see this locked blueprint.
3. **Gate 3: Atomic Implementation & Local Pre-commit**  
   *Action:* Developer (or Coder Agent) writes the code.  
   *Gate:* Local `lefthook`/`husky` runs `dart format` and `flutter analyze`. If it fails, the commit is blocked locally.
4. **Gate 4: Automated CI/CD Verification**  
   *Action:* Code is pushed. CI runs the full SDET matrix (Unit, Widget, Golden, Integration, Security Lint).  
   *Gate:* **The Build Must Be Green.** If red, the Critic Agent is triggered automatically with the exact error log.
5. **Gate 5: Code Review as *Judgment***  
   *Action:* A human (or advanced Reviewer Agent) reads the code.  
   *Gate:* They do not check for syntax (CI did that). They check for: *Is this maintainable? Does it violate the ADR? Is the complexity justified?* If no, it is sent back with a "Request Changes" status.
6. **Gate 6: Merge & Staged Release**  
   *Action:* Code is merged to `main` behind a Feature Flag.  
   *Gate:* Telemetry (Sentry/Crashlytics) is monitored for 24 hours. If crash rate > 0.1%, the feature flag is automatically toggled off.

---

### Part 4: Handling Disagreement & Ambiguity (Escalation Protocol)
*When the Swarm's agents conflict (e.g., Coder Agent wants to use Package X, but Security Linter rejects it), how is it resolved without infinite loops?*

1. **The ADR is the Supreme Court:** If two agents disagree on implementation, the existing Architecture Decision Record (stored in GraphRAG) is the tiebreaker. 
2. **Smallest Diff Wins:** If two valid approaches exist, the one that modifies the fewest lines of code is chosen to minimize merge conflicts and regression risk.
3. **Data Over Opinion:** If ambiguity remains, the system defaults to the option with the better historical metric in the GraphRAG (e.g., "Approach A has a 15% lower historical crash rate in our Experience Log").
4. **The "Circuit Breaker":** If the Critic Agent and Coder Agent loop more than 3 times on the same file, the system **halts**, flags the file for human intervention, and logs a "High Friction" node in GraphRAG.

---

### Part 5: Institutional Knowledge Compounding (The Swarm's "Memory")
*How elite teams avoid repeating mistakes, translated to your AI:*

*   **Postmortems as Graph Nodes:** When CI fails, the Critic Agent doesn't just fix it. It generates a structured `Postmortem Node` in GraphRAG: `{ "error_signature": "Riverpod AsyncValue error", "root_cause": "Missing await in initState", "solution": "Use ref.read with FutureProvider", "file_pattern": "*.g.dart" }`.
*   **Runbook Retrieval:** Before the Coder Agent writes code for a complex feature (e.g., "background location tracking"), the Planner Agent *must* query GraphRAG for existing "Runbook Nodes" to inject proven patterns into the prompt.
*   **Deprecation Sunsetting:** A quarterly automated job scans the GraphRAG for ADRs tied to deprecated Flutter SDK versions and flags them for the Architect Agent to update.

---

### Part 6: Flutter-Specific SOTA Metrics (Your Target)
*Your synthetic data and AI outputs must be optimized to hit these measurable standards:*
*   **Crash-Free Users:** > 99.9%
*   **90th Percentile Frame Build Time:** < 16ms (guaranteed 60fps, no jank).
*   **App Size Budget:** Strict limits enforced (e.g., < 30MB for base APK).
*   **Code Review Turnaround:** < 4 hours (in human teams); < 30 seconds (in your Swarm).
*   **Test Coverage:** > 80% for business logic, 100% for critical payment/auth flows.

---

### Part 7: Your Immediate Next Step (Actionable)

You now have the complete, unassailable blueprint. You are no longer guessing what "professional" means. You have the exact checklist.

To make this real in **Swarm-Grid**, we must codify the most critical piece of this entire system: **The Definition of Done (DoD) and the Experience Graph Schema.**

Open your editor. Let's define the **GraphRAG Node Schema for a "Postmortem/Experience"**. 
If your Coder Agent makes a mistake, and the Critic Agent fixes it, what is the *exact JSON structure* that gets saved to the database so the Planner Agent never makes that mistake again?

Draft this JSON schema. Include fields for: `error_signature`, `flutter_sdk_version`, `rtl_impact`, `solution_code`, and `prevention_rule`. 

Let's build the memory of your swarm.