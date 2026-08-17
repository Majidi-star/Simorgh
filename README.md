# 🦅 Simorgh: The Zero-Cost Agentic IDE
### **Thirty Birds. One Mind.**
**Run a frontier-class coding swarm locally. Zero API costs. Zero vendor lock-in. 100% legally pristine.**

Welcome to **Simorgh**, an open-source, local-first agentic coding framework designed to replace cloud-dependent tools like Cursor, Cline, and Z Code. 

In Persian legend, thirty birds journey to find the Simorgh, only to realize that together, *they are the Simorgh*. We applied this exact philosophy to AI. Instead of forcing your entire codebase through a slow, expensive, privacy-invading 500B-parameter cloud API, Simorgh uses a **Nano-Swarm** of hyper-specialized 1B–2B parameter models. 

They collaborate to architect, route, and write code entirely on your machine. The swarm *is* the giant.

---

## 🧠 The "Thirty Birds" Architecture
Most AI coding tools rely on a single, massive brain. Simorgh breaks the software engineering process down into atomic tasks and assigns them to a swarm of specialized, locally-running nano-agents. 

*   **The Visionary (1.5B Planner):** Reads the repository state, absorbs RAG context, and generates the Chain-of-Thought reasoning path.
*   **The Navigator (1.5B Router):** Takes the plan and translates it into mathematically perfect, strict JSON tool calls (AST parsing, file reading, dependency checking).
*   **The Artisan (1.5B Syntax Engine):** Takes the tool context and outputs flawless, unified code diffs without hallucinating external libraries.

Because these agents operate on a shared, highly-curated trajectory, they outperform monolithic 7B models at coding tasks while using **90% less VRAM** and costing **$0 in API fees**.

---

## 🛡️ The "Clean Room" Training Pipeline
The AI industry is plagued by legal gray areas, proprietary data traps, and restrictive API Terms of Service. Simorgh was built differently. Our student models were trained using a **100% legally pristine, offline synthetic data pipeline**.

### 1. No Proprietary API Distillation
We did not scrape OpenAI, Anthropic, or Google. We did not use free-tier web interfaces. Our synthetic trajectories were generated entirely by **local, open-weight Teacher Models** (Qwen 2.5 Coder 32B and DeepSeek Coder V2 Lite) running offline via Ollama.

### 2. Apache 2.0 & MIT Provenance
Every piece of training data, every RAG documentation snippet, and every base model used in our refinement loops is governed strictly by **Apache 2.0, MIT, or the NVIDIA Open Model License**. 
*   *No Cross-Architecture Traps:* We avoided restrictive community licenses (like Llama 3) that forbid training non-family models.
*   *No Data Harvesting:* Your prompts never leave your device to train a competitor's next model.

### 3. Execution-Based Refinement
Our datasets weren't just generated; they were verified. We used local agentic loops to generate code, apply it to sandboxed Git repositories, and run unit tests. **Only code that compiled and passed tests made it into our training sets.**

---

## ⚡ Core Features

*   **🔌 Zero-Config Local Inference:** Natively integrates with **Ollama** and **LM Studio**. Just point Simorgh to `localhost:11434` and start coding.
*   **🐍 AST-Aware Tool Routing:** The Navigator agent doesn't guess; it parses your repository's Abstract Syntax Tree to ensure it only edits files and functions that actually exist.
*   **📚 Clean-Room RAG Memory:** Bring your own permissively licensed documentation. The swarm reads local Markdown files of your internal APIs and libraries to write perfectly formatted code.
*   **⚡ Blazing Fast Autocomplete:** Because the Artisan engine is only 1.5B parameters, code diffs are generated at **60+ tokens/second** on consumer hardware (RTX 3060 / M-Series Macs).
*   **🔒 Enterprise-Grade Privacy:** Air-gap ready. Perfect for closed-source enterprise environments where pasting code into a cloud API is a fireable offense.

---

## 🛠️ Getting Started

### Prerequisites
You need a local inference server running the Simorgh Nano-Swarm models. We recommend **Ollama**.

**1. Install Ollama**
Download from [ollama.com](https://ollama.com).

**2. Pull the Swarm Models**
```bash
ollama pull simorgh/planner:1.5b
ollama pull simorgh/navigator:1.5b
ollama pull simorgh/artisan:1.5b
```

**3. Install the Simorgh CLI / IDE Extension**
```bash
npm install -g simorgh-cli
# OR install the VS Code extension from the marketplace
```

**4. Initialize your Workspace & Begin the Journey**
```bash
simorgh init
simorgh fly "Build a FastAPI REST endpoint for user authentication using JWT"
```
*Watch the swarm work: The Planner thinks, the Navigator opens the files, and the Artisan writes the diffs in real-time.*

---

## 🏗️ For Developers: Build Your Own Swarm
Want to fine-tune the agents on your own company's codebase? We have open-sourced our entire **Agentic Refinement Pipeline**.

Check out the `/training` directory in this repository to see how we use `distilabel` and `Unsloth` to turn raw GitHub diffs into perfectly formatted, multi-agent trajectories for 1B models.

---

## 📜 License & Legal Provenance

**Simorgh Framework Code:** Licensed under the **Apache 2.0 License**.
**Simorgh Nano-Swarm Weights:** Licensed under the **Apache 2.0 License**.

**Legal Provenance Manifest:**
We believe in radical transparency. You can view the exact lineage of our training data, including the HuggingFace dataset hashes, the specific open-weight Teacher Models used, and the permissive licenses of our RAG sources in our [PROVENANCE.md](./PROVENANCE.md) file. 

***"The thirty birds sought the king, only to find the king was the swarm all along."*** 
Build the future of software engineering. Locally. Legally. For Free.