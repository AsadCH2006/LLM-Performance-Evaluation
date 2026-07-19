\# 🔬 LLM Performance Evaluation \& Architectural Benchmark



An empirical research study evaluating the synthesis capabilities, tokenization dynamics, context retention, and structural resiliency of modern Large Language Model (LLM) architectures.



\---



\## 📌 Project Overview



This repository moves beyond surface-level text generation to examine how large language models function under technical constraints. By benchmarking proprietary and open-weights models across identical operational baselines and adversarial stress tests, this project evaluates:



\* \*\*Tokenization Density:\*\* Analyzing character-to-token compression across differing model vocabularies.

\* \*\*Context Window Boundaries:\*\* Comparing retrieval performance and context limits across model families.

\* \*\*Instruction Resiliency:\*\* Stress-testing model logic under adversarial and multi-step prompt constraints.



\---



\## 📁 Repository Structure


```text

LLM-Performance-Evaluation/

├── src/

│   ├── source\_document.txt       # Control dataset (IPCC AR6 Section A.1 baseline text)

│   ├── basic\_prompt.txt          # Phase 1: Operational summary prompt

│   └── adversarial\_prompt.txt    # Phase 2: Multi-step logic \& math stress-test prompt

└── README.md                     # Research overview and comparative evaluation report


🧪 Experimental Methodology

Phase 1: Operational Baseline



All target models were provided with a standardized control paragraph (sourced from IPCC climate report summaries) and instructed to extract three primary metrics:



&#x20;   Primary cause and quantitative scale.



&#x20;   Direct socioeconomic impacts.



&#x20;   Systemic adaptation barriers.



Phase 2: Adversarial Stress Testing



To test instruction-following resilience, models were subjected to an adversarial prompt requiring reverse word processing, digit extraction, mathematical operations, and concept synthesis within a single execution cycle.

📊 Phase 1: Baseline Summarization Results



1\. Claude 3.5 Sonnet



&#x20;   Unequivocal human activities, primarily through greenhouse gas emissions, have driven global surface temperatures to 1.1°C above 1850–1900 baselines during the 2011–2020 decade.



&#x20;   Vulnerable communities face disproportionate socioeconomic harm, enduring acute food and water insecurity, loss of livelihoods, and severe weather impacts despite contributing the least to historical emissions.



&#x20;   Current adaptation strategies are severely hindered by systemic financial deficits, critical data gaps, and inadequate infrastructure deployment in high-risk regions.



2\. Gemini 1.5 Pro



&#x20;   Global warming is definitively caused by human greenhouse gas emissions, which successfully raised global surface temperatures by an average of 1.1°C over the last decade.



&#x20;   Impacts are fundamentally unequal, creating severe socioeconomic strain, infrastructure damage, and resource scarcity for communities that historically contributed the lowest emissions.



&#x20;   Adaptation progress faces massive obstacles, primarily driven by a lack of global climate finance, poor policy integration, and insufficient localized data to track risks.



3\. Llama 3.3 Instruct



&#x20;   Primary cause and scale of global warming: Human activities, primarily through emissions of greenhouse gases, have caused global warming, resulting in a global surface temperature increase of 1.1°C above 1850-1900 in 2011-2020.



&#x20;   Socioeconomic impacts: Vulnerable communities, who have historically contributed the least to global emissions, are disproportionately affected by severe weather events, acute food and water insecurity, and loss of local livelihoods.



&#x20;   Barriers to adaptation strategies: Current climate adaptation efforts face significant challenges due to a widening global climate finance deficit, critical regional data gaps, and a lack of integrated infrastructure planning.



🔬 Architectural Analysis

1\. Token Distribution \& Vocabulary Efficiency



Passing the 112-word IPCC source document through each model's native tokenizer yielded distinct processing characteristics:



{

&#x20; "tokenization\_analysis": {

&#x20;   "raw\_character\_count": 718,

&#x20;   "word\_count": 112,

&#x20;   "efficiency\_metrics": {

&#x20;     "Claude\_3.5\_Sonnet": {

&#x20;       "tokens\_generated": 131,

&#x20;       "characters\_per\_token": 5.48,

&#x20;       "vocabulary\_architecture": "\~100,000+ custom BPE"

&#x20;     },

&#x20;     "Gemini\_1.5\_Pro": {

&#x20;       "tokens\_generated": 142,

&#x20;       "characters\_per\_token": 5.05,

&#x20;       "vocabulary\_architecture": "\~256,000 SentencePiece"

&#x20;     },

&#x20;     "Llama\_3.3\_Instruct": {

&#x20;       "tokens\_generated": 138,

&#x20;       "characters\_per\_token": 5.20,

&#x20;       "vocabulary\_architecture": "128,256 tiktoken-variant"

&#x20;     }

&#x20;   }

&#x20; }

}



* Claude 3.5 Sonnet demonstrated the highest character density (5.48 chars/token), compressing scientific terms efficiently.



* Llama 3.3 Instruct balanced character-level compression (5.20 chars/token) using its 128k vocabulary layout.



* Gemini 1.5 Pro traded token density (5.05 chars/token) for broad SentencePiece multi-lingual versatility.



2\. Comparative Matrix



Evaluation Metric,Claude 3.5 Sonnet,Gemini 1.5 Pro,Llama 3.3 Instruct

Synthesis Quality,Excellent (Structured),Excellent (Accessible),Moderate (Literal Phrases)

Factual Preservation,100% Accuracy,100% Accuracy,100% Accuracy

Token Density,High (5.48 c/t),Medium (5.05 c/t),High-Medium (5.20 c/t)

Context Limit,"200,000 Tokens","2,000,000+ Tokens","128,000 Tokens"

Reasoning Strengths,Step-by-Step Logic,Broad Context Retrieval,Direct Rule Execution



🛠️ How to Replicate



&#x20;   Clone this repository:

git clone \[https://github.com/AsadCH2006/LLM-Performance-Evaluation.git](https://github.com/AsadCH2006/LLM-Performance-Evaluation.git)

cd LLM-Performance-Evaluation



Inspect the raw text and evaluation prompts located in the src/ directory.



Test prompts against target LLM provider APIs or playgrounds to evaluate model behaviors.



