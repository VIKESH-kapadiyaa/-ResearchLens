# 🔬 ResearchLens

> **An open-source AI research intelligence engine that helps researchers understand literature, identify research gaps, detect contradictions, and generate evidence-backed research directions.**

[![Status](https://img.shields.io/badge/status-in%20development-orange)]()
[![License](https://img.shields.io/badge/license-Apache2.0-yellow)]()
[![Python](https://img.shields.io/badge/Python-3.11+-blue)]()
[![Next.js](https://img.shields.io/badge/Next.js-TypeScript-black)]()

---

## 🚀 What is ResearchLens?

ResearchLens is an **open-source AI-powered research assistant** designed to help researchers move beyond simply reading and summarizing papers.

Researchers often spend hours reading dozens of papers to understand:

* What has already been discovered?
* Which findings agree with each other?
* Where do studies contradict one another?
* What limitations exist in current research?
* Which populations, methods, datasets, or conditions remain underexplored?
* What could be investigated next?

ResearchLens attempts to answer these questions by analyzing research literature and building connections between **papers, claims, methods, findings, limitations, and research gaps**.

### The core idea

```text
Research Papers
       ↓
Document Understanding
       ↓
Claims + Methods + Findings
       ↓
Research Knowledge Graph
       ↓
Gap & Contradiction Detection
       ↓
Evidence-backed Hypotheses
       ↓
Potential Research Directions
```

---

# 🎯 Why ResearchLens?

Traditional AI research tools are often focused on:

> **"Summarize this paper."**

ResearchLens aims to answer a more useful question:

> **"Given what these papers already tell us, what should researchers investigate next?"**

The system is designed to distinguish between:

🟢 **Supported** — directly supported by the literature

🟡 **Inferred** — derived from multiple pieces of evidence

🔴 **Speculative** — a possible hypothesis requiring validation

ResearchLens does **not** claim that AI can automatically prove that a research idea is completely novel worldwide.

Instead, it identifies **potential gaps and hypotheses based on the literature available to the system**.

---

# ✨ Features

## 📄 Research Paper Analysis

Upload one or multiple research papers and extract structured information including:

* Title
* Authors
* Abstract
* Sections
* Methods
* Results
* Conclusions
* Limitations
* References

---

## 💬 Ask Questions About Your Papers

Ask natural-language questions about uploaded literature.

Example:

> What limitations did the authors identify?

ResearchLens retrieves relevant evidence and generates an answer with source information.

```text
Answer
──────────────────────────────

The study identifies limited sample size as
one of its primary limitations.

Evidence:
Paper A — Page 8
```

---

## 🔎 Research Gap Detection

ResearchLens analyzes multiple papers to identify potentially underexplored areas.

Potential gaps include:

### Methodological gaps

A particular method may not have been tested under certain conditions.

### Population gaps

A population may be missing from existing studies.

### Dataset gaps

Existing research may rely heavily on a limited set of datasets.

### Context gaps

A finding may have been tested in one environment but not another.

### Temporal gaps

Research may not have been updated or compared against newer approaches.

---

# ⚡ Contradiction Detection

Different research papers sometimes produce conflicting findings.

ResearchLens attempts to identify potential contradictions.

Example:

```text
Paper A
──────────────
Treatment X improves outcome Y.


Paper B
──────────────
Treatment X produces no significant
improvement in outcome Y.

              ↓

Potential contradiction detected
```

The system presents the underlying evidence so researchers can investigate the disagreement themselves.

---

# 🧠 Hypothesis Generation

ResearchLens can transform identified gaps into potential research directions.

Example:

```text
Research Gap
     ↓
Existing Evidence
     ↓
Reasoning
     ↓
Hypothesis
     ↓
Suggested Experiment
```

Example output:

### Research Gap

Limited research has investigated Method X under Condition Y.

### Potential Hypothesis

Method X may produce different results under Condition Y compared with previously studied conditions.

### Suggested Experiment

```text
Control:
Existing Method

Experimental:
Existing Method + X

Dataset:
Dataset D

Evaluation:
Metric M
```

All generated hypotheses should be treated as **proposals for investigation, not established scientific facts**.

---

# 📚 Evidence & Citations

ResearchLens is designed around evidence.

Generated insights should be connected to their source material whenever possible.

Example:

```text
Claim:
Method X improves performance.

Evidence:
Paper A — Page 5
Paper C — Page 9

Evidence strength:
82%

Classification:
Supported
```

This helps researchers distinguish between information extracted from papers and AI-generated reasoning.

---

# 🏗️ Architecture

The initial architecture is:

```text
                         USER
                           │
                           ▼
                  ┌─────────────────┐
                  │    Next.js      │
                  │    Frontend     │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │     FastAPI     │
                  │     Backend     │
                  └────────┬────────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
       PDF Processing      LLM       Embeddings
             │             │             │
             └─────────────┼─────────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ PostgreSQL +    │
                  │ pgvector        │
                  └────────┬────────┘
                           │
                           ▼
                  Research Engine
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
          Claims        Gaps       Contradictions
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                   Hypothesis Engine
                           │
                           ▼
                    Research Report
```

---

# 🛠️ Technology Stack

## Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS

## Backend

* Python
* FastAPI
* Pydantic

## AI

ResearchLens is designed to support multiple AI providers.

Potential integrations include:

* OpenAI
* Anthropic
* Google
* Ollama
* Llama-based models
* Mistral-based models

The goal is to avoid locking the project to a single model provider.

## Document Processing

* PyMuPDF
* OCR support
* Structured document parsing

## Database

* PostgreSQL
* pgvector

## Infrastructure

* Docker
* Docker Compose
* GitHub Actions

---

# 📁 Project Structure

The project is currently organized around the following structure:

```text
researchlens/
│
├── apps/
│   ├── web/
│   └── api/
│
├── packages/
│   ├── document-parser/
│   ├── embeddings/
│   ├── research-engine/
│   ├── hypothesis-engine/
│   └── evaluation/
│
├── tests/
│
├── docs/
│   ├── architecture.md
│   ├── research-engine.md
│   ├── evaluation.md
│   └── contributing.md
│
├── examples/
│
├── docker-compose.yml
├── .env.example
├── .gitignore
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
└── README.md
```

> The repository structure may evolve as the project develops.

---

# 🚧 Project Status

ResearchLens is currently in **early development**.

### Current roadmap

```text
[ ] Project foundation
[ ] PDF ingestion
[ ] Document parsing
[ ] Embeddings
[ ] Vector search
[ ] RAG-based Q&A
[ ] Source citations
[ ] Claim extraction
[ ] Limitation extraction
[ ] Research gap detection
[ ] Contradiction detection
[ ] Hypothesis generation
[ ] Research graph
[ ] Web interface
[ ] Evaluation benchmark
[ ] Docker deployment
[ ] Public v0.1 release
```

---

# 🗺️ Roadmap

## v0.1 — Research Intelligence MVP

* PDF upload
* PDF parsing
* Semantic search
* Question answering
* Evidence citations
* Claim extraction
* Limitation extraction
* Basic research-gap detection
* Basic hypothesis generation

---

## v0.2 — Literature Comparison

* Multi-paper comparison
* Contradiction detection
* Research timeline
* Better evidence scoring
* Improved gap detection

---

## v0.3 — Research Knowledge Graph

```text
Paper
  ↓
Claim
  ↓
Entity
  ↓
Method
  ↓
Result
  ↓
Limitation
  ↓
Research Gap
  ↓
Hypothesis
```

Interactive visualization will allow users to explore these relationships.

---

## v0.4 — Local AI

ResearchLens will explore support for locally hosted models through tools such as Ollama.

The goal is to allow researchers to run ResearchLens without sending sensitive research documents to external AI providers.

---

## v0.5 — Literature Discovery

Potential integrations:

* arXiv
* PubMed
* Semantic Scholar
* Other academic literature sources

---

## v1.0 — Research Intelligence Platform

Long-term goals include:

* Large-scale literature analysis
* Citation graph analysis
* Research trend detection
* Automated literature reviews
* Research collaboration
* Advanced hypothesis generation
* Reproducible research workflows

---

# 🚀 Getting Started

## Prerequisites

Make sure you have:

```text
Python 3.11+
Node.js 20+
Git
Docker
Docker Compose
```

---

## Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/researchlens.git
cd researchlens
```

---

## Backend setup

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Activate it on macOS/Linux:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the API:

```bash
uvicorn main:app --reload
```

The API will be available at:

```text
http://localhost:8000
```

API documentation:

```text
http://localhost:8000/docs
```

---

## Frontend setup

```bash
cd frontend
npm install
npm run dev
```

The frontend will be available at:

```text
http://localhost:3000
```

---

# 🔐 Environment Variables

Create a `.env` file based on `.env.example`.

Example:

```env
DATABASE_URL=
OPENAI_API_KEY=
ANTHROPIC_API_KEY=
GOOGLE_API_KEY=
EMBEDDING_MODEL=
VECTOR_DATABASE_URL=
```

Never commit real API keys to GitHub.

---

# 🧪 Evaluation

ResearchLens will not only be evaluated by whether the generated text sounds good.

The project will measure:

### Retrieval quality

Did the system retrieve the correct evidence?

### Citation accuracy

Does the cited source actually support the generated statement?

### Hallucination rate

How often does the model generate unsupported information?

### Gap quality

Are detected research gaps actually supported by the literature?

### Hypothesis quality

Are generated hypotheses:

* Relevant?
* Testable?
* Evidence-backed?
* Clearly distinguished from established findings?

An evaluation dataset will be developed as the project matures.

---

# ⚠️ Scientific Disclaimer

ResearchLens is an AI-assisted research tool.

Generated:

* research gaps,
* hypotheses,
* explanations,
* summaries,
* experiments,
* and conclusions

must be independently verified by researchers.

A potential research gap identified by ResearchLens does **not** establish that the topic is globally unexplored.

Likewise, a generated hypothesis is **not a scientific discovery or established fact**.

Researchers should verify findings against the original literature and perform appropriate literature searches before making claims of novelty.

---

# 🤝 Contributing

ResearchLens is intended to be a community-driven open-source project.

Contributions are welcome.

You can contribute to:

```text
Document parsing
LLM integrations
Embedding models
Research-gap detection
Contradiction detection
Evaluation
Frontend
Backend
Research visualization
Documentation
Testing
```

Please read:

```text
CONTRIBUTING.md
```

before submitting a pull request.

---

# 💡 Contribution Ideas

Looking for something to work on?

Potential issues include:

```text
[good first issue]
Add a new document parser

[good first issue]
Improve README documentation

[feature]
Add Ollama support

[feature]
Add research graph visualization

[research]
Improve contradiction detection

[research]
Develop a research-gap evaluation benchmark
```

---

# 🌟 Vision

The long-term vision of ResearchLens is to build an open-source layer of **research intelligence**.

Instead of researchers manually navigating thousands of disconnected papers:

```text
        Literature
            │
            ▼
       Understanding
            │
            ▼
        Knowledge
            │
            ▼
      Relationships
            │
            ▼
       Research Gaps
            │
            ▼
       Hypotheses
            │
            ▼
       Experiments
```

ResearchLens aims to help researchers move from:

> **Reading what is known**

to:

> **Understanding what could be investigated next.**

---

# 📜 License

ResearchLens is released under the **MIT License**.

See [`LICENSE`](LICENSE) for details.

---

# ⭐ Support the Project

If you find ResearchLens useful:

⭐ Star the repository

🐛 Report bugs

💡 Suggest features

🔧 Submit pull requests

📢 Share the project with researchers and developers

Every contribution helps improve the project.

---

# 🔬 ResearchLens

**Understand the literature. Find the gaps. Explore what's next.**

> Built with ❤️ for researchers and the open-source community.
