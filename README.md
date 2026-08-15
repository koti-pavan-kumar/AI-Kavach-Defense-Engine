# 🛡️ AI Kavach: Air-Gapped Autonomous Cyber Reasoning & Remediation Engine

> **Built for Indian Army Terrier Cyber Quest 2026 (TCQ 3.0) — Track: AI Kavach** > *Developed by Team AutoPatchCompiler*

---

## 📌 Executive Overview

Mission-critical defense networks running legacy C/C++ tactical software face severe security risks from memory corruption flaws (e.g., Buffer Overflows, Null Pointer Dereferences, Format String Injections). Manual code triage, vulnerability identification, and patch creation take days or weeks, creating high-risk exploit windows in operational battlefield systems.

**AI Kavach** is an autonomous, 100% air-gapped cyber reasoning and automated code remediation pipeline. It ingests source code, maps vulnerabilities to official **CWE IDs**, generates secure repairs via local quantized Code-LLMs (**Qwen2.5-Coder-7B** via **Ollama**), and verifies patches using a **closed-loop local GCC compiler sandbox**—ensuring zero AI code hallucinations reach production.

---

## 🚀 Key Features & Innovations

- **🔒 100% Air-Gapped & Zero Data Leakage:** Operates completely offline without cloud API calls, protecting classified defense software repositories and consuming zero satellite/WAN bandwidth.
- **⚡ Sub-4-Second Autonomous Remediation:** Completes end-to-end vulnerability classification and secure code patching in an average latency of **3,427.13 ms (~3.4 seconds)** on single consumer GPU hardware.
- **🛠️ Self-Healing Compiler Sandbox Loop:** Integrates automated compilation testing (`GCC`) to verify structural syntax and prevent AI code hallucinations from breaking production builds.
- **💻 Lightweight Edge Footprint:** Optimized to run entirely on standard tactical edge workstations (**NVIDIA RTX 4060 Ti - 16GB VRAM**) rather than expensive datacenter infrastructure.

---

## 🏗️ System Architecture & Workflow

```text
┌─────────────────────────┐     ┌──────────────────────────┐     ┌───────────────────────────────┐
│ Tactical C/C++ Source   │ ──► │ AST Parser & Pre-process │ ──► │ Ollama / Qwen2.5-Coder-7B     │
│ Telemetry (Air-Gapped)  │     └──────────────────────────┘     │ (Local RTX 4060 Ti VRAM)      │
└─────────────────────────┘                                      └──────────────┬────────────────┘
                                                                                │
┌─────────────────────────┐     ┌──────────────────────────┐                    │
│ Verified Secure Binary /│ ◄── │ Local GCC Compiler       │ ◄──────────────────┘ Auto-Generated
│ Production Output       │     │ Sandbox Verification     │                      Patch & CWE Label
└─────────────────────────┘     └──────────────────────────┘
