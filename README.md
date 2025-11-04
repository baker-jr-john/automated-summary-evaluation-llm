# Automated Summary Evaluation with Rubric-Based AI Feedback  
### A Proof-of-Concept Implementation Using Meta Llama 3.1 8B on Google Colab  

---

## 🧭 Overview
This repository contains the implementation, validation, and documentation for **_Automated Summary Evaluation with Rubric-Based AI Feedback_**, a proof-of-concept system demonstrating that an open-source large language model (LLM) can provide **immediate, rubric-aligned formative feedback** on middle-school informational summaries.  

The project was developed as part of a graduate-level research initiative exploring responsible applications of generative AI in K-12 education. It aims to validate the **technical feasibility** of rubric-based automated assessment while maintaining **human oversight, transparency, and educational value**.

---

## 🎯 Project Goals
- **Develop** a functional prototype using **Meta Llama 3.1 8B** capable of evaluating student summaries on four rubric dimensions.  
- **Validate** model agreement with a trained human rater, targeting  
  - Cohen’s κ ≥ 0.65  
  - Quadratic Weighted Kappa ≥ 0.60  
  - Adjacent agreement ≥ 85 %.  
- **Document** a transparent workflow for potential classroom pilot studies and teacher review dashboards.  
- **Demonstrate** a zero-cost, privacy-compliant implementation suitable for educational research and practice.  

---

## 🧩 Educational Context
The system targets **grades 6–8 informational text summaries** in English Language Arts (ELA).  
Teachers often face overwhelming grading workloads (e.g., 110–176 students daily), limiting timely feedback. This prototype illustrates how LLMs can support teachers by automating first-round formative feedback while preserving **teacher control over final grading**.

---

## ⚙️ Technical Architecture
| Component | Description |
|------------|-------------|
| **Model** | Meta Llama 3.1 8B (open-source, run locally on Colab GPU) |
| **Frameworks** | Python 3.10+, Hugging Face Transformers |
| **Retrieval (Grounding)** | Sentence Transformers (all-MiniLM-L6-v2) with cosine similarity search |
| **Interface** | Gradio (student input + feedback)  /  Streamlit (teacher dashboard) |
| **Storage** | SQLite (for scores, feedback, logs) |
| **Platform** | Google Colab (Pro Education tier) |
| **Version Control** | GitHub + comprehensive inline documentation |

---

## 🧠 Rubric Framework
The evaluation rubric adapts Common Core ELA standards for summarization. Each dimension is scored 1–5 and includes behavioral anchors.

| Dimension | Description |
|------------|-------------|
| **Completeness** | Coverage of main ideas and key supporting details |
| **Accuracy** | Faithfulness to the source text without distortion |
| **Coherence** | Logical organization and sentence-to-sentence flow |
| **Conciseness** | Appropriate length; avoids redundancy or irrelevant content |

The system produces JSON-structured outputs with per-dimension scores, reasoning, and actionable feedback.

---

## 🔬 Validation Design
**Dataset (n = 60)**  
- ~60 summaries (authentic + synthetic) across quality levels.  
- Authentic samples from the **ASAP** writing corpus; synthetic samples generated using **GPT-4o-Mini** to simulate learner-like error patterns.  

**Validation Process**  
1. Calibration and consistency checks by a trained human rater.  
2. Iterative development on 20 samples, final evaluation on 40 held-out samples.  
3. Performance metrics: Cohen’s κ, QWK, adjacent/exact agreement, RMSE.  
4. Error analysis of disagreements to identify rubric-dimension weaknesses.  

**Expected Outcome:**  
Substantial AI–human agreement demonstrating technical feasibility for formative feedback use.

---

## 🧰 Repository Contents
| File / Folder | Description |
|----------------|-------------|
| `automated_summary_evaluation_llama3_rubric_feedback_colab.ipynb` | Main Jupyter Notebook with full pipeline implementation |
| `data/` | Example source texts and student summaries (de-identified) |
| `rubrics/` | Four-dimension evaluation rubric and behavioral anchors |
| `docs/` | Project report, validation tables, and system diagrams |
| `LICENSE` | MIT License (for code) + CC BY 4.0 (for rubric & documentation) |

---

## 🧪 Reproducing the Study
1. **Open in Google Colab** → [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)  
2. **Run all cells** to load dependencies, initialize Llama 3.1 8B, and process sample summaries.  
3. Inspect JSON output for scores + feedback per dimension.  
4. (Optional) Launch the Gradio interface cell for interactive testing.  

---

## 🧩 Workflow Summary
1. Load source texts & summaries → embed with Sentence Transformers.  
2. Construct prompt (f-string template with rubric + few-shot examples).  
3. Run Llama 3.1 8B via Transformers for step-wise evaluation.  
4. Parse scores + feedback (JSON/regex).  
5. Visualize results in Streamlit dashboard.  

---

## 📈 Evaluation Metrics
| Metric | Target | Purpose |
|---------|---------|----------|
| **Cohen’s Kappa** | ≥ 0.65 | Substantial AI–human agreement |
| **Quadratic Weighted Kappa** | ≥ 0.60 | Degree-sensitive agreement |
| **Adjacent Agreement** | ≥ 85 % | Acceptable for formative feedback |
| **RMSE < 0.8** | — | Average scoring deviation |

---

## 🔒 Privacy & Ethical Compliance
- Student data are **de-identified** before inference (e.g., `STUDENT_001`).  
- No personally identifiable information leaves Colab; all processing occurs locally.  
- System is limited to **formative (low-stakes)** feedback only.  
- Teachers maintain final grading authority and can audit/override AI outputs.  
- Documentation aligns with **U.S. DOE (2023)** guidelines on responsible AI in education.

---

## 📚 References
Complete reference list available in [`docs/references.md`](docs/references.md).  
Key sources include:  
- Fleckenstein et al. (2023) meta-analysis of automated feedback efficacy.  
- Meyer et al. (2024) RCT showing LLM-generated feedback improves student revision.  
- Hashemi et al. (2024) LLM-Rubric framework for multi-dimensional evaluation.  
- Yancey et al. (2023) LLM agreement with human raters in educational contexts.  

---

## 🧑‍💻 Author
**John Baker**  
Graduate Student, Learning Analytics & AI – University of Pennsylvania   
📍 Hudson Valley, NY  |  📧 [jbaker!@upenn.edu]  

---

## 🪪 License
**Code:** [MIT License](LICENSE)  
**Rubrics & Documentation:** [Creative Commons Attribution 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)  

---

## 💡 Citation
If you reference this work in research or coursework, please cite as:

> Baker, J. (2025). *Automated Summary Evaluation with Rubric-Based AI Feedback: A Proof-of-Concept Implementation Using Meta Llama 3.1 8B.* University of Pennsylvania, Graduate School of Education. GitHub: https://github.com/johnbaker/automated-summary-evaluation-llm

---

## 🌱 Acknowledgments
Developed with support from the **University of Pennsylvania GSE Learning Analytics and AI Program**.  
Thanks to open-source contributors at **Meta**, **Hugging Face**, and the **Sentence Transformers** community for enabling accessible, transparent AI research.

---

*This repository demonstrates how open-source LLMs can augment, not replace, human judgment in education—balancing innovation with ethical responsibility.*

