## Abony Kamal

CSE undergraduate at BUET, working on agentic AI systems and human–computer interaction.

I build systems that retrieve, reason, and act — LLM agents, RAG pipelines, multi-agent
architectures — and I research how people actually relate to them. My undergraduate thesis
is in HCI, on human–AI companion relationships in conversational systems.

**Interested in:** agentic AI · LLM systems engineering · human–AI interaction · responsible AI in low-resource contexts

---

### Selected work

#### [patient-simulator](https://github.com/Abonykamal/patient-simulator) · Multi-agent clinical training simulation

Medical students practise history-taking by interviewing an AI-played patient, then receive
structured examiner-style feedback. Three character agents — patient, nurse, family member —
hold independent knowledge slices, with the patient disclosing sensitive facts only as rapport
develops; a routing controller decides who answers each turn. Cases are synthesised from a
clinical corpus through a retrieve–generate–validate pipeline rather than hand-authored.

Grading runs on a **separate, larger model on a different provider**, so the patient agent never
evaluates itself, with score aggregation computed deterministically in code. Provider-agnostic
LLM layer with cross-provider failover, event-sourced conversation turns, and 166 tests that
run against mocked providers.

`Python` · `FastAPI` · `Streamlit` · `ChromaDB` · `SQLite` · `NetworkX`

#### BUET Job Portal · AI-augmented recruitment platform — *private (university deployment)*

**Team lead.** A platform covering a university's full hiring lifecycle across five services and
four datastores, replacing a manual PDF- and spreadsheet-based process.

A backend-authoritative plugin architecture keeps every AI capability optional and independently
degradable — the core product runs correctly with all models switched off. The conversational
assistant is built on a LangGraph state machine with intent routing, RAG over institutional
documents, cross-plugin delegation with soft-fail, and a provider abstraction handling timeout,
retry-with-jitter, and circuit breaking. Candidate matching runs six weighted dimensions with
per-post score explanations behind a hard eligibility gate.

Auditability is built into the data model: every automated evaluation records the entity assessed,
the score, and the model version, so a ranking decision affecting someone's job can be explained
from the record rather than re-run.

`Java` · `Spring Boot` · `React/TypeScript` · `Python` · `FastAPI` · `PostgreSQL` · `Neo4j` · `Qdrant` · `Redis` · `Docker`

#### [BanglaDialToEn](https://github.com/fa88923/BanglaDialToEn) · Dialect-aware translation for five Bangladeshi regional dialects

Route-then-translate. A BanglaBERT classifier identifies the dialect (89.21% accuracy, 87.1%
macro-F1), then routes to a dialect-specific PEFT adapter over NLLB-200. The combined pipeline
reaches 43.37 SacreBLEU and 64.81 chrF++ across ~50.7K samples curated from seven sources with
deduplication and leakage prevention.

DoRA outperformed LoRA for only two of the five dialects — adapter gains turn out to be
dialect-dependent rather than universal.

`Python` · `PyTorch` · `Hugging Face PEFT`

#### [CSE322-ns3-project](https://github.com/Abonykamal/CSE322-ns3-project) · RTT fairness in BBR congestion control

Implemented and experimentally compared standard BBR, BBR with gamma correction, and two
modifications of my own on NS-3 dumbbell topologies. With competing 10 ms and 50 ms RTT flows
over a 30 Mbps bottleneck, Jain's Fairness Index moved from 0.674 to 0.963.

My two modifications *underperformed* the base algorithm, and the more useful result was working
out why: synchronised gain-reset timers drove both flows to identical behaviour simultaneously,
and EMA smoothing introduced asymmetric response lag between the fast and slow flows.

`C++` · `NS-3`

---

### Currently

- **HCI thesis** — human–AI companion relationships in conversational systems, at BUET.
- **Engineering-OS** — a reusable process kernel for AI-assisted development: lifecycle workflows, a stack-agnostic verify contract, quality gates calibrated to task size, and promotion-based memory. Private while in review.

---

### Toolkit

**Languages** Python · Java · TypeScript · C/C++ · SQL

**AI systems** LangGraph · RAG · multi-agent orchestration · PEFT/LoRA fine-tuning · LLM-as-judge evaluation · vector retrieval

**Infrastructure** FastAPI · Spring Boot · React · Docker · PostgreSQL · Neo4j · Qdrant · ChromaDB · Redis

---

📍 Dhaka, Bangladesh · [LinkedIn](www.linkedin.com/in/abony-kamal-716057206) · abonykamal@gmail.com
