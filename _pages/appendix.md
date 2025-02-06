---
layout: page
permalink: /appendix/
title: Appendix
description:
nav: true
nav_order: 4
---

## Dataset Usage
## 1. Dataset Selection & Filtering
- **Source & Scale:**  
  - Contains 11,950 quarterly earnings call transcripts (2017–2024) for 869 companies (NASDAQ 500 & S&P 500).  
  - Each transcript averages ~10,187 tokens.
- **Balanced Sampling:**  
  - Training set: 100 transcripts from each of 11 financial sectors (totaling 1,100 samples).  
  - Test set: 587 transcripts from 2024, ensuring they are outside the LLM’s pretraining data.
- **Text-Only Focus:**  
  - Retains only textual content by removing any acoustic features.

## 2. Structural Transformation into Fact Tables
- **Conversion Process:**  
  - Each transcript is distilled into a structured fact table summarizing key financial details.
- **Segmented Summarization:**  
  - **Prepared Remarks:** Summarized into 3–5 key facts per segment.  
  - **Q&A Sessions:** Summarized into 1–3 key facts per segment.  
  - Result: Approximately 40 facts are generated per transcript.

## 3. Integration with the STRUX Framework
- **Supporting Fact Selection:**  
  - From the fact table, around 9 key supporting facts are automatically selected.  
  - Facts are categorized as positive or negative with strength labels (e.g., “+” or “–”).
- **Self-Reflection Mechanism:**  
  - An iterative reflection process refines fact selection and strength assignments without human annotations.
- **Decision-Making Outcome:**  
  - The refined fact table informs investment decisions (e.g., Strongly Buy, Buy, Hold, Sell, Strongly Sell), enhancing both prediction accuracy and transparency.
