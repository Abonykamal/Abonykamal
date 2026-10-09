## Abony Kamal

Final-year CSE undergraduate at BUET, building production-oriented AI systems and researching how people relate to them.

I build LLM agents, RAG pipelines and multi-agent applications, with a focus on making AI features reliable, optional and checkable rather than trusted by default. My undergraduate thesis is in HCI, on AI-initiated relational behaviours in conversational systems.

**Interested in:** agentic AI · LLM systems engineering · AI security · human–AI interaction

---

### Selected work

#### BUET Job Portal · AI-integrated recruitment platform (*private, university project*)

**Team lead and system architect** for a five-person team building a platform that covers a university's hiring cycle, from circular publication to applications, screening, evaluation and ranking.

I designed the AI integration architecture. Every LLM feature lives in an optional plugin behind a vendor-neutral provider layer, so the core platform runs unchanged when AI is switched off.

- **Applicant chatbot.** A LangGraph assistant with intent routing, RAG and cross-plugin delegation, plus timeouts, retries and circuit breaking for provider failures.
- **Recruiter-assist.** AI tools that turn circular PDFs into draft job posts, edit admit card and notification templates from plain-English instructions, and summarise audit logs. The model proposes and the recruiter decides. Every output is validated in code before a recruiter sees it, and anything the model gets wrong is left blank rather than guessed.

I also designed the Recruitment Management architecture and set up the team's CI pipelines, repository hooks and coding agent workflow.

`Java` · `Spring Boot` · `React/TypeScript` · `Python` · `FastAPI` · `LangGraph` · `PostgreSQL` · `Qdrant` · `Neo4j` · `Redis` · `Docker`

#### [patient-simulator](https://github.com/Abonykamal/patient-simulator) · Multi-agent clinical training simulation

Medical students practise history taking by interviewing AI-played patients, nurses and family members, then receive examiner-style feedback. Each character has its own knowledge and context, and the patient reveals sensitive history only as the student builds rapport. New patient cases are generated from a clinical corpus through a retrieve, generate and validate pipeline.

Grading runs on a **separate model from a different provider**, so the patient agent never grades itself, and the final score is computed in code. The LLM layer is provider-agnostic with cross-provider failover, and conversation turns are stored as events so a failed call is always safe to retry.

`Python` · `FastAPI` · `Streamlit` · `ChromaDB` · `SQLite` · `NetworkX`

#### [InjectRAG](https://github.com/Abonykamal/CSE-406-InjectRAG) · Indirect prompt injection through RAG

A corpus poisoning attack on a simulated IT helpdesk chatbot, where malicious support tickets carry instructions that hijack the chatbot's answers once retrieved. I designed the RAG pipeline and the attack.

Poisoned tickets reached the model's context on 94% of target questions. Attack success **rose with model size**, from 28% at 1.5B to 61% at 7B and about 80% at 20B parameters. Spotlighting gave no reliable protection on any model, and controlled experiments showed the smaller model resisted only because it follows instructions poorly, not because it is safer.

`Python` · `FastAPI` · `Qdrant` · `Groq` · `Ollama`

#### [Engineering-OS](https://github.com/Abonykamal/Engineering-OS) · A development workflow for AI-assisted coding

A reusable Claude Code plugin that gives any repository a spec, plan, implement, review and release workflow, with human approval gates scaled to task size. A stack-independent verification contract, called by hooks and CI, blocks "done" claims until tests have actually run.

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
