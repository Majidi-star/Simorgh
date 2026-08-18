tags:

ai-swarm

local-llm

graph-rag

flutter

agentic-systems

date: 2024-05-19

status: reference

Swarm-Grid (Local Agentic Flutter Engine) — Product Foundations & Scope

Distilled from the core philosophy mapping out the mechanics behind replacing monolithic, expensive LLMs with a decentralized swarm of hyper-specialized Small Language Models (SLMs). This document dictates how this tool should and shouldn't operate to achieve world-class software engineering output on consumer hardware.

  

Why this note exists

The AI industry is trapped in a contradictory and exploitative paradigm — the "Monolithic LLM" crowd says "pay us $200/month for a 70B parameter god-model that hallucinates," while the "Local AI" crowd says "just run a dumb 7B model and accept mediocre output." It's not actually a binary choice. It's a failure of architecture. Once separated, the solution becomes obvious: build a highly opinionated, local-first agentic swarm that forces specialization, enforces deterministic guardrails, and stays entirely out of the "jack-of-all-trades" hallucination trap.

  

The Execution Stack

Layer 1 — The GraphRAG Codex (solid ground)

Pure structural knowledge and experiential memory. This consists of Flutter documentation, architectural decision records (ADRs), and a dynamic "Experience Graph" of past errors and fixes. Validated by the psychological need for a fixed "Source of Truth." This is the foundational bedrock of the swarm. Without the GraphRAG, the agents are just guessing.

  

Layer 2 — The SLM Swarm (proven methodology)

The strategic framework: replacing one massive, confused model with a team of hyper-specialized 1B to 7B models (e.g., Qwen2.5-Coder).

For it: Small models are fast, fit in consumer VRAM (8GB), and cost $0 to run. By restricting their context and scope, they achieve near-perfect accuracy in their specific domain.

Why it dictates the architecture: Swarm-Grid does not allow a single model to plan, code, and review simultaneously. Everything must be routed to the correct specialized agent. The architecture forces focus.

  

Layer 3 — Deterministic Guardrails (tactical reality)

The microscopic view: hardcoded linters, analyzers, and regex validators.

Mechanism: If the GraphRAG is the compass and the SLM Swarm is the engine, this layer is the physical road.

The failure point of most AI coders: Most AI tools rely on an LLM to check if the code is correct (probabilistic QA). Swarm-Grid makes deterministic validation a requirement for progression, keeping the agents honest about actual syntax and logic errors.

  

Layer 4 — The Agentic Orchestrator (the accelerator)

The context-aware integration of the routing loop.

What it is: An intelligence layer that inherently understands the user's prompt, queries the GraphRAG, routes tasks to the SLM Swarm, and intercepts the deterministic errors to feed back into the loop.

Why it's structured this way: AI is completely useless if it doesn't learn from its failures. By having persistent context of the "Experience Graph," the Orchestrator transitions from a one-shot generator to a self-improving engineering team.

  

Key Concepts Cheat-Sheet

| Concept | Origin / Philosophy | Product Implementation |

| --- | --- | --- |

| The Experience Graph | Compound Learning & Memory | A local Neo4j/GraphRAG database that stores (Error -> Fix) pairs. The team gets smarter with every failure. |

| Hyper-Specialized SLMs | Division of Labor | 1B-7B models (Qwen/DeepSeek) fine-tuned or heavily prompted for one specific task (Plan, Code, or Critique). |

| Deterministic QA | Truth over Probability | Hardcoded Python scripts running `flutter analyze` or regex checks. Zero LLM involvement in syntax checking. |

| Local-First Architecture | Data sovereignty & zero-cost | Ollama/vLLM running locally. The user owns the models, the data, and the infrastructure. No API keys required for core logic. |

| Context Starvation | Cognitive Load Management | Intentionally keeping the context window for each agent microscopic. The Coder only sees the JSON plan, not the whole conversation. |

  

What This Means for Product Scope

In scope (build on this)

Hyper-Specialized Agents (Layer 2) — The UI/CLI should clearly show which agent is working. The Planner outputs JSON, the Coder outputs Dart, the Critic outputs fixes.

Context-Aware Retrieval (Layer 1) — The Orchestrator must automatically inject relevant GraphRAG nodes into the agent's system prompt behind the scenes.

Hardcoded Validation Loops (Layer 3) — Frictionless integration with local Flutter SDK tools to instantly validate generated code.

Experience Logging (Layer 4) — When the Critic agent fixes an error, that exact interaction is parsed and saved as a new node in the GraphRAG.

  

Out of scope (don't build / avoid)

Monolithic LLM Routing. Swarm-Grid is an execution engine for small models, not a proxy for GPT-4 or Claude. Do not add fallback routing to paid cloud APIs.

Unstructured Code Generation. The Coder agent does not take vague prompts like "build me an app." It takes strict JSON widget trees from the Planner.

Gamification or "Chat" Interfaces. No endless chat windows. The interface should be a command center showing the agentic loop, the current agent, and the validation status.

  

The Elite Team Framework (useful for product UX / positioning)

Swarm-Grid does three distinct jobs by mimicking a world-class human engineering team. It's crucial to build the architecture around this distinction:

The Architect (Planner Agent) — "What are we building and what are the rules?" (Low interaction frequency, high importance. Outputs strict JSON).

The Builder (Coder Agent) — "Write the exact Dart code for this JSON tree." (High interaction frequency, tactical. Outputs pure code).

The QA / Tech Lead (Validator + Critic) — "Is this code valid, and if not, how do we fix it using our past experience?" (Medium frequency, reflective. Outputs fixes and logs to GraphRAG).

  

Product implication: The dashboard should prioritize Job #2 (The Builder's output) heavily. Job #1 should be easily accessible but not cluttering the daily view. Job #3 should be invoked automatically in the background, only surfacing to the user if the loop fails repeatedly.

  

Design / Compute Guardrails

Never market or refer to Swarm-Grid as a "coding assistant" or "copilot." Use terms like "autonomous engineering swarm," "agentic compiler," and "local execution engine."

Ensure the UI feels premium, dark, and focused. It should feel like a terminal command center, not a toy.

When the Orchestrator routes tasks, it should do so with zero latency. Keep the Python/Node backend highly optimized for local IPC.

Do not let the local model setup feel overwhelming. Provide sane defaults (e.g., auto-download Qwen2.5-1.5B via Ollama) but keep the complex VRAM management under the hood.

  

Open Questions to Revisit

How do we handle GraphRAG schema evolution? If the Experience Graph gets too large, how do we prune outdated "experiences" without losing critical context?

If the Critic agent fails to fix a deterministic error after 3 attempts, what is the exact escalation protocol? Do we pause and ask the human, or do we fallback to a larger local model (e.g., 7B)?

Do we want to introduce "Sprint Post-Mortems" where the swarm analyzes its own failure rate and automatically adjusts its system prompts?

  

Features

Scoped, grounded in the core philosophy — safe to build.

[x] Local Ollama/vLLM Integration — Backend setup to manage and route to local 1B-7B models.

[x] GraphRAG Knowledge Base — Local vector/graph database setup for storing Flutter docs and initial seed data.

[ ] The Planner Agent — Strict JSON-outputting agent that translates user prompts into widget trees.

[ ] The Coder Agent — Dart-outputting agent that takes the JSON plan and writes the Flutter code.

[ ] Deterministic Validator Hook — Python script integration to run `flutter analyze` on the Coder's output.

[ ] The Critic Agent & Experience Logger — Agent that reads validator errors, queries GraphRAG, rewrites code, and saves the (Error -> Fix) pair.

  

Feature Ideas

Not yet scoped or decided — park here, promote to Features once vetted against the framework above.

[ ] DeepSeek API Seed Generator — A one-time setup tool to use the DeepSeek API to generate the initial 5,000 "Golden" Flutter examples to fine-tune the local 1B models.

[ ] Multi-File State Management — Expanding the Planner Agent to output Riverpod/BLoC state logic alongside the UI widget tree.

[ ] Auto-Test Generation — Adding a "QA Agent" that writes `flutter_test` widget tests for the generated code.

[ ] Swarm Telemetry Dashboard — A visual graph showing the swarm's success rate, average loop iterations, and GraphRAG growth over time.

[ ] ⚠️ Guardrail: Any feature idea that leans toward "cloud API reliance" or "general-purpose chat" gets immediately flagged and checked against the Out of scope section above.