# 🔬 Empirical Evaluation of LLM Architectures: Document Summarization Benchmark

This repository contains a performance evaluation benchmarking three Large Language Models (**Claude 3.5 Sonnet**, **Gemini 1.5 Pro**, and **Llama 3.3 Instruct**) on document summarization and complex prompt execution tasks.

---

## 📂 Project Structure

* `src/source_document.txt`: Section A.1 of the IPCC Sixth Assessment Report (AR6).
* `src/basic_prompt.txt`: Standard baseline evaluation prompt.
* `src/adversarial_prompt.txt`: Complex logic and structural stress-test prompt.
* `README.md`: Master evaluation report and architectural comparison.

---

## 1. Summarization Results (Standard Prompt)

### Claude 3.5 Sonnet
* **Unequivocal human activities**, primarily through greenhouse gas emissions, have driven global surface temperatures to 1.1°C above 1850–1900 baselines during the 2011–2020 decade.
* **Vulnerable communities face disproportionate socioeconomic harm**, enduring acute food and water insecurity, loss of livelihoods, and severe weather impacts despite contributing the least to historical emissions.
* **Current adaptation strategies are severely hindered** by systemic financial deficits, critical data gaps, and inadequate infrastructure deployment in high-risk regions.

### Gemini 1.5 Pro
* **Global warming is definitively caused by human greenhouse gas emissions**, which successfully raised global surface temperatures by an average of 1.1°C over the last decade.
* **Impacts are fundamentally unequal**, creating severe socioeconomic strain, infrastructure damage, and resource scarcity for communities that historically contributed the lowest emissions.
* **Adaptation progress faces massive obstacles**, primarily driven by a lack of global climate finance, poor policy integration, and insufficient localized data to track risks.

### Llama 3.3 Instruct
* **Primary cause and scale of global warming:** Human activities, primarily through emissions of greenhouse gases, have caused global warming, resulting in a global surface temperature increase of 1.1°C above 1850-1900 in 2011-2020.
* **Socioeconomic impacts:** Vulnerable communities, who have historically contributed the least to global emissions, are disproportionately affected by severe weather events, acute food and water insecurity, and loss of local livelihoods.
* **Barriers to adaptation strategies:** Current climate adaptation efforts face significant challenges due to a widening global climate finance deficit, critical regional data gaps, and a lack of integrated infrastructure planning.

---

## 2. Token Efficiency & Quantitative Metrics

| Metric | Source Document | Claude 3.5 Sonnet Output | Gemini 1.5 Pro Output | Llama 3.3 Output |
| :--- | :--- | :--- | :--- | :--- |
| **Word Count** | 112 words | 74 words | 72 words | 82 words |
| **Estimated Input Tokens** | ~145 tokens | ~145 tokens | ~145 tokens | ~145 tokens |
| **Estimated Output Tokens** | N/A | ~98 tokens | ~94 tokens | ~110 tokens |
| **Compression Ratio** | 100% | 66% of source length | 64% of source length | 73% of source length |

---

## 3. Adversarial / Stress-Test Evaluation (`adversarial_prompt.txt`)

To test architectural limits, each model was tasked with a multi-step constraint prompt requiring backward reading, arithmetic extraction, and baseline contextual reasoning.

### Model Behavior Analysis:
* **Claude 3.5 Sonnet:** Exhibited superior chain-of-thought isolation. It identified and extracted the numerical values (`1.1`, `1850`, `1900`, `2011`, `2020`) before executing the arithmetic and answering the baseline question cleanly.
* **Gemini 1.5 Pro:** Prioritized the conceptual question (historical baselines) and generalized the string-reversal step, demonstrating strong semantic focus but slightly looser rule adherence under structural constraints.
* **Llama 3.3 Instruct:** Attempted verbatim text-reversal, leading to high token usage and formatting friction before correctly answering the baseline question.

---

## 4. Performance Comparison Matrix

| Model | Summary Quality | Accuracy | Conciseness | Hallucinations | Overall Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Claude 3.5 Sonnet** | **Outstanding:** Flawless structure and academic syntax. | **Flawless:** Preserved exact baseline metrics (1850–1900). | **Excellent:** High factual density with zero filler. | **None:** Kept strictly within source boundaries. | **4.9 / 5.0** |
| **Gemini 1.5 Pro** | **Good:** Highly accessible and easy to read. | **High:** Retained key facts, though generalized some baselines. | **Good:** Slightly more conversational phrasing. | **None:** Zero extrapolation. | **4.3 / 5.0** |
| **Llama 3.3 Instruct** | **Very Good:** Very direct and punchy structure. | **High:** Accurately captured stats and dates. | **Excellent:** Brief, direct points. | **None:** Followed instructions strictly. | **4.6 / 5.0** |

---

## 5. Final Conclusion & Winner

### Winner: **Claude 3.5 Sonnet**
1. **Technical Precision:** Retained exact scientific baseline windows (`1850–1900`) essential for policy reporting.
2. **Optimal Compression:** Highest ratio of hard facts per output token generated.
3. **Constraint Adherence:** Handled multi-step adversarial rules without degrading output formatting.
