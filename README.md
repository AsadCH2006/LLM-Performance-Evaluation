# 🔬 LLM Performance Evaluation & Architectural Benchmark

An empirical research study evaluating the synthesis capabilities, tokenization dynamics, context retention, and structural resiliency of modern Large Language Model (LLM) architectures.

---

## 📌 Project Overview

This repository moves beyond surface-level text generation to examine how large language models function under technical constraints. By benchmarking proprietary and open-weights models across identical operational baselines and adversarial stress tests, this project evaluates:

* **Tokenization Density:** Analyzing character-to-token compression across differing model vocabularies.
* **Context Window Boundaries:** Comparing retrieval performance and context limits across model families.
* **Instruction Resiliency:** Stress-testing model logic under adversarial and multi-step prompt constraints.

---

## 📁 Repository Structure

```text
LLM-Performance-Evaluation/
├── src/
│   ├── source_document.txt       # Control dataset (IPCC AR6 Section A.1 baseline text)
│   ├── basic_prompt.txt          # Phase 1: Operational summary prompt
│   └── adversarial_prompt.txt    # Phase 2: Multi-step logic & math stress-test prompt
└── README.md                     # Research overview and comparative evaluation report

🧪 Experimental Methodology
Phase 1: Operational Baseline

All target models were provided with a standardized control paragraph (sourced from IPCC climate report summaries) and instructed to extract three primary metrics:

    Primary cause and quantitative scale.

    Direct socioeconomic impacts.

    Systemic adaptation barriers.

Phase 2: Adversarial Stress Testing

To test instruction-following resilience, models were subjected to an adversarial prompt requiring reverse word processing, digit extraction, mathematical operations, and concept synthesis within a single execution cycle.
📊 Phase 1: Baseline Summarization Results
1. Claude 3.5 Sonnet

    Unequivocal human activities, primarily through greenhouse gas emissions, have driven global surface temperatures to 1.1°C above 1850–1900 baselines during the 2011–2020 decade.

    Vulnerable communities face disproportionate socioeconomic harm, enduring acute food and water insecurity, loss of livelihoods, and severe weather impacts despite contributing the least to historical emissions.

    Current adaptation strategies are severely hindered by systemic financial deficits, critical data gaps, and inadequate infrastructure deployment in high-risk regions.

2. Gemini 1.5 Pro

    Global warming is definitively caused by human greenhouse gas emissions, which successfully raised global surface temperatures by an average of 1.1°C over the last decade.

    Impacts are fundamentally unequal, creating severe socioeconomic strain, infrastructure damage, and resource scarcity for communities that historically contributed the lowest emissions.

    Adaptation progress faces massive obstacles, primarily driven by a lack of global climate finance, poor policy integration, and insufficient localized data to track risks.

3. Llama 3.3 Instruct

    Primary cause and scale of global warming: Human activities, primarily through emissions of greenhouse gases, have caused global warming, resulting in a global surface temperature increase of 1.1°C above 1850-1900 in 2011-2020.

    Socioeconomic impacts: Vulnerable communities, who have historically contributed the least to global emissions, are disproportionately affected by severe weather events, acute food and water insecurity, and loss of local livelihoods.

    Barriers to adaptation strategies: Current climate adaptation efforts face significant challenges due to a widening global climate finance deficit, critical regional data gaps, and a lack of integrated infrastructure planning.

🔬 Architectural Analysis
1. Token Distribution & Vocabulary Efficiency

Passing the 112-word IPCC source document through each model's native tokenizer yielded distinct processing characteristics:

{
  "tokenization_analysis": {
    "raw_character_count": 718,
    "word_count": 112,
    "efficiency_metrics": {
      "Claude_3.5_Sonnet": {
        "tokens_generated": 131,
        "characters_per_token": 5.48,
        "vocabulary_architecture": "~100,000+ custom BPE"
      },
      "Gemini_1.5_Pro": {
        "tokens_generated": 142,
        "characters_per_token": 5.05,
        "vocabulary_architecture": "~256,000 SentencePiece"
      },
      "Llama_3.3_Instruct": {
        "tokens_generated": 138,
        "characters_per_token": 5.20,
        "vocabulary_architecture": "128,256 tiktoken-variant"
      }
    }
  }
}

Claude 3.5 Sonnet demonstrated the highest character density (5.48 chars/token), compressing scientific terms efficiently.Llama 3.3 Instruct balanced character-level compression (5.20 chars/token) using its 128k vocabulary layout.Gemini 1.5 Pro traded token density (5.05 chars/token) for broad SentencePiece multi-lingual versatility.2. Comparative MatrixEvaluation MetricClaude 3.5 SonnetGemini 1.5 ProLlama 3.3 InstructSynthesis QualityExcellent (Structured)Excellent (Accessible)Moderate (Literal Phrases)Factual Preservation100% Accuracy100% Accuracy100% AccuracyToken DensityHigh (5.48 c/t)Medium (5.05 c/t)High-Medium (5.20 c/t)Context Limit200,000 Tokens2,000,000+ Tokens128,000 TokensReasoning StrengthsStep-by-Step LogicBroad Context RetrievalDirect Rule Execution🛠️ How to ReplicateClone this repository:Bashgit clone [https://github.com/AsadCH2006/LLM-Performance-Evaluation.git](https://github.com/AsadCH2006/LLM-Performance-Evaluation.git)
cd LLM-Performance-Evaluation
Inspect the raw text and evaluation prompts located in the src/ directory.Test prompts against target LLM provider APIs or playgrounds to evaluate model behaviors.