<div align="center">

<h1>Mithil S</h1>

<p>
  <a href="https://mithil.systems"><img src="https://img.shields.io/badge/mithil.systems-000000?style=flat-square&logo=safari&logoColor=white"/></a>&nbsp;&nbsp;
  <a href="https://linkedin.com/in/mithil27360"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>&nbsp;&nbsp;
  <a href="mailto:mithil27360@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white"/></a>&nbsp;&nbsp;

</p>

</div>


```yaml
name    : Mithil S
bio     : I train models. More fascinated by the ones inside your skull.
domain  : AI · ML · NLP · Retrieval Systems · Neuroscience · BCI · MedTech
building: RAG systems that hold up under real traffic, not just in demos
research: ML systems · intelligent agents · signal processing · neuro-AI
school  : Manipal Institute of Technology · Data Science · 2028
```

<br>

> **Keras · [PR #21816](https://github.com/keras-team/keras/pull/21816)** &nbsp; Fixed a hardware-level MPS tensor broadcast failure sitting 29 frames deep in Metal GPU internals, restoring 5–15× GPU training speed for all Apple Silicon users. Merged by François Chollet. Ships in a codebase with 62K stars and 200M+ downloads.

<br>

---

## Projects

<br>

### [Aurora RAG Chatbot](https://github.com/mithil27360/AURORA_RAG) &nbsp;&nbsp; `Technical Lead`

*An AI assistant that answered live questions for 400+ college fest attendees — schedules, venues, registrations — with no human operator.*

<table>
  <tr>
    <td align="center"><b>400+</b><br><sub>attendees served</sub></td>
    <td align="center"><b>3,690+</b><br><sub>questions answered</sub></td>
    <td align="center"><b>100%</b><br><sub>uptime · 15 days</sub></td>
    <td align="center"><b>4.2s → 18ms</b><br><sub>p50 cached latency</sub></td>
    <td align="center"><b>36.5%</b><br><sub>LLM calls eliminated</sub></td>
  </tr>
</table>

The hard constraint was real: a free-tier LLM service under live event traffic. Too many simultaneous questions would have taken the whole thing down. The solution was a three-layer caching system where repeated questions were answered from memory in milliseconds, with the actual AI only invoked for genuinely new queries. An async FastAPI pipeline on two workers held up through peak traffic without dropping requests. Cross-encoder reranking over the top 50 retrieved candidates kept answers precise. A security layer caught and blocked 16+ prompt injection attempts during live stress testing.

80+ event coordinators updated content throughout the fest via a live Google Sheet that synced to the system every five minutes, with zero downtime on content refreshes.

<kbd>Python</kbd> <kbd>FastAPI</kbd> <kbd>Redis</kbd> <kbd>ChromaDB</kbd> <kbd>Groq LLaMA 3 70B</kbd> <kbd>Docker</kbd> <kbd>Prometheus</kbd> <kbd>Nginx</kbd>

<br>

---

### [EEG2GAN](https://github.com/mithil27360/EEG2GAN) &nbsp;&nbsp; `Research`

*Can a model reconstruct what someone is seeing from their raw brainwaves?*

EEG signals captured while subjects viewed ImageNet images were fed into a Transformer encoder paired with a Conditional GAN to reconstruct the original visual stimulus. The core challenge is that EEG data is extremely noisy and the brain-to-image mapping is poorly understood. Evaluated on MindBigData across 569 ImageNet classes, comparing a 2-layer, 4-head Transformer against an LSTM baseline.

| Method | Inception Score ↑ | EEG-Image Similarity ↑ | FID ↓ |
|:---|:---:|:---:|:---:|
| ThoughtViz (2017) | 4.12 | 0.211 | 312.4 |
| LSTM Baseline | 6.15 | 0.419 | 141.4 |
| **EEG2GAN** | **7.10** | **0.478** | **128.9** |

Higher Inception Score means more realistic and diverse generations. Higher EEG-Image Similarity means the output is semantically closer to what the subject actually saw. Lower FID means the output distribution is closer to real photographs. EEG2GAN beats both baselines on all three metrics.

<kbd>PyTorch</kbd> <kbd>Transformer</kbd> <kbd>Conditional GAN</kbd> <kbd>DiffAugment</kbd> <kbd>EEG Signal Processing</kbd>

<br>

---

### [AI Cloud Drive](https://github.com/mithil27360/Cloud-drive) &nbsp;&nbsp; `System Design`

*Cloud storage with a built-in AI assistant. Upload documents from anywhere, access them from anywhere, and ask questions in plain English instead of searching manually.*

It works like Google Drive with a brain attached. You store PDFs, reports, and documents in the cloud, and the AI reads through all of them so you do not have to. Ask something like "what does this contract say about termination clauses?" and the system finds the relevant sections, generates a grounded answer, and shows exactly where the information came from. Crucially, it refuses to answer when the retrieved context is not sufficient rather than guessing — which matters more than it sounds in practice.

The retrieval pipeline was built specifically to study where standard RAG systems break. Dense vector search is combined with BM25 keyword search via Reciprocal Rank Fusion so the system does not go blind on exact technical terms or identifiers. A context sufficiency gate blocks generation when retrieval confidence falls below threshold. A post-generation validator discards answers that violate domain rules before they reach the user. An ablation engine measured the reranker's isolated contribution at +15% Precision@K.

<kbd>Python</kbd> <kbd>FastAPI</kbd> <kbd>ChromaDB</kbd> <kbd>PostgreSQL</kbd> <kbd>MinIO</kbd> <kbd>Redis</kbd> <kbd>Celery</kbd> <kbd>Groq</kbd> <kbd>Docker</kbd>

<br>

---

## Experience

**Analytics Intern · RAG and Data Analytics** &nbsp; Star Health and Allied Insurance &nbsp; *Dec 2025*

Built an AI system that lets analysts query years of insurance market data in plain English, without writing a single SQL query. Before this, extracting insights meant manually digging through spreadsheets across multiple insurers and product segments covering 15M+ tokens of unstructured policy documents. The RAG pipeline made it conversational — an analyst could ask something like "which insurer had the highest claim ratio in Q3?" and get a sourced answer in under a second.

<table>
  <tr>
    <td align="center"><b>+28%</b><br><sub>Recall@5</sub></td>
    <td align="center"><b>+22%</b><br><sub>context precision</sub></td>
    <td align="center"><b>2.4s → 650ms</b><br><sub>end-to-end latency</sub></td>
    <td align="center"><b>−42%</b><br><sub>token usage</sub></td>
    <td align="center"><b>84%</b><br><sub>faithfulness · RAGAS</sub></td>
  </tr>
</table>

Hybrid retrieval combining BM25 and dense vector search with cross-encoder reranking kept results accurate on domain-specific insurance terminology. Query routing and prompt compression brought latency down and cut token costs significantly. Evaluated using the RAGAS framework: 84% faithfulness and 81% answer relevance.

<br>

---

<div align="center">
<sub><kbd>Python</kbd> <kbd>SQL</kbd> <kbd>FastAPI</kbd> <kbd>Flask</kbd> <kbd>PyTorch</kbd> <kbd>Keras</kbd> <kbd>Sentence-Transformers</kbd> <kbd>ChromaDB</kbd> <kbd>Redis</kbd> <kbd>PostgreSQL</kbd> <kbd>Docker</kbd> <kbd>RAGAS</kbd> <kbd>BM25</kbd> <kbd>FAISS</kbd></sub>
</div>
