## Abony Kamal

Final-year CSE undergraduate at BUET, building production-oriented AI systems and researching how people relate to them.

I build LLM agents, RAG pipelines and multi-agent applications, and I care most about making AI features reliable, optional and checkable rather than trusted by default. My undergraduate thesis is in HCI, on AI-initiated relational behaviours in conversational systems.

**Interested in:** agentic AI · LLM systems engineering · AI security · human–AI interaction

---

### Selected work

#### BUET Job Portal · AI-integrated recruitment platform (*private, university project*)

A recruitment platform covering a university's hiring cycle, from publishing job circulars to applications, screening, evaluation and ranking. **I lead the five-person team and designed the system architecture and the AI layer.**

- **AI is optional by design.** Every LLM feature runs as a separate plugin behind a vendor-neutral provider layer. When a plugin is switched off, its routes disappear and the UI hides its buttons, and the core recruitment workflow carries on unchanged.
- **Applicant chatbot.** A LangGraph assistant with intent routing, RAG and delegation to other plugins, with timeouts, retries and circuit breaking so a failing model provider doesn't take the conversation down with it.
- **Recruiter-assist: the model proposes, the recruiter decides.** Three tools for university staff, each giving the model only as much freedom as its mistakes can safely cost.
    - *Circular extraction* turns a job circular PDF into draft job posts. Output is validated against the same schema the post editor uses. Anything the model can't support from the document, like an ambiguous deadline date, is left blank for the recruiter rather than guessed, because a blank field gets noticed and a plausible wrong one doesn't.
    - *Template assistant* edits admit cards and notifications from plain-English instructions. The model can only pick from fields the backend supplies, and if it names even one unknown field the whole change is rejected, so the UI never claims an edit that didn't happen.
    - *Audit summary* writes a short narrative of the audit log. All the counts are computed in code and handed to the model as fixed facts, so it writes prose around the numbers but never produces them.
- **Engineering process.** I set up the CI pipelines, repository hooks and coding agent workflow the team builds with, and led cross-module integration and stabilisation.

`Java` · `Spring Boot` · `React/TypeScript` · `Python` · `FastAPI` · `LangGraph` · `PostgreSQL` · `Qdrant` · `Neo4j` · `Redis` · `Docker`

#### [patient-simulator](https://github.com/Abonykamal/patient-simulator) · Multi-agent clinical training simulation

Medical students practise history taking by interviewing an AI patient, starting from a single line like "58, presents with chest pain", then get examiner-style feedback on what they covered and missed.

- **Characters who know different things.** A patient, nurse and family member each have their own knowledge and context, and a router decides who answers. The patient holds back sensitive history until the student has built rapport, the way real patients do.
- **The grader grades the asking, not the answers.** A separate model from a different provider checks which important topics the student actually raised, so the patient model never grades itself. The score is computed in code, and the judge has no fallback model on purpose: if it fails, it fails loudly instead of quietly returning a weaker grade.
- **Patients are generated, not hand-written.** New cases are built from a clinical corpus through a retrieve, generate, validate and repair pipeline.
- **Built to survive flaky APIs.** Each agent's model is one line of config with cross-provider failover. Conversation turns are stored as events, so a failed call changes nothing and is always safe to retry. The full test suite runs against fake providers, with no real API calls.

`Python` · `FastAPI` · `Streamlit` · `ChromaDB` · `SQLite` · `NetworkX`

#### [InjectRAG](https://github.com/Abonykamal/CSE-406-InjectRAG) · Indirect prompt injection through RAG

Can an employee hijack a company's helpdesk chatbot just by filing a support ticket? We built a RAG helpdesk and attacked it with poisoned tickets whose hidden instructions redirect users to an attacker's link. **I designed the RAG pipeline and the attack.**

- **Retrieval was the easy part.** Poisoned tickets reached the model's context on 94% of target questions, for every model tested.
- **Bigger models were easier to hijack.** Attack success rose from 28% at 1.5B parameters to 61% at 7B and about 80% at 20B. In one case the 7B model correctly warned a user about a social engineering attempt, then pointed them to the attacker's link anyway.
- **The small model wasn't safer, just less obedient.** It also ignored a simple formatting rule in its own system prompt almost every time, and moving the attack to the top of its context barely changed anything.
- **The defense didn't hold.** Spotlighting, which tells the model to treat retrieved text as data, gave no reliable protection on any model, because it relies on the same instruction following the attack exploits.

`Python` · `FastAPI` · `Qdrant` · `Groq` · `Ollama`

#### [Engineering-OS](https://github.com/Abonykamal/Engineering-OS) · A development workflow for AI-assisted coding

AI-assisted development fails in predictable ways: context lost between sessions, "done" claimed without tests run, decisions made twice, docs that rot. Engineering-OS is a Claude Code plugin that closes each gap with the cheapest mechanism that works.

- **Scripts before prompts.** Each problem is solved by a script if possible, then a file convention, then a skill, and an agent only when a fresh context genuinely pays. Most of the system is deterministic.
- **One verification contract for every stack.** Each project exposes `verify quick`, `verify test` and `verify full`, and hooks, CI and workflows all call the same three commands. A hook blocks "done" until tests have actually run since the last edit.
- **One reviewer, read-only.** Review is the one job where sharing the author's context hurts, so it's the only core agent. It never edits code, and it may not report a problem without a concrete failure scenario.
- **Process scales with stakes.** A typo fix and a schema migration get different gates, and the plan file on disk, not the conversation, is the record of progress, so work survives a lost session.

`Claude Code` · `skills` · `agents` · `hooks`

#### [BanglaDialToEn](https://github.com/fa88923/BanglaDialToEn) · Translation for five Bangladeshi regional dialects

Route-then-translate. A BanglaBERT classifier identifies the dialect (89.2% accuracy), then routes to a dialect-specific PEFT adapter over NLLB-200, reaching 43.4 SacreBLEU across all five dialects. DoRA beat LoRA for only two dialects, so adapter gains turned out to depend on the dialect.

`Python` · `PyTorch` · `Hugging Face PEFT`

#### [CSE322-ns3-project](https://github.com/Abonykamal/CSE322-ns3-project) · RTT fairness in BBR congestion control

Compared standard BBR, BBR with gamma correction and two modifications of my own in NS-3. Gamma correction raised Jain's Fairness Index from 0.674 to 0.963. My own modifications underperformed, and the more useful result was working out why: synchronised gain-reset timers and asymmetric smoothing lag.

`C++` · `NS-3`

---

### Currently

- **HCI thesis** on AI-initiated relational behaviours in conversational systems, supervised by Dr. Novia Nurain at BUET.
- **BUET Job Portal**, continuing as team lead.

---

### Toolkit

**Languages** Python · TypeScript · Java · SQL · C/C++

**AI systems** LangGraph · RAG · multi-agent orchestration · LLM evaluation · PEFT/LoRA · vector search

**Infrastructure** FastAPI · Spring Boot · React · Docker · PostgreSQL · Qdrant · ChromaDB · Neo4j · Redis

---

📍 Dhaka, Bangladesh · [LinkedIn](https://www.linkedin.com/in/abony-kamal-716057206) · abonykamal@gmail.com
