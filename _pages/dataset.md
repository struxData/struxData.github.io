---
layout: page
permalink: /dataset/
title: Dataset
description: 
nav: true
nav_order: 2
---

## Public Meetings
A collection of 11,950 quarterly earnings call transcripts from major NASDAQ 500 and S&P 500 companies (2017–2024), each averaging about 10,187 tokens. It spans 869 companies across 11 financial sectors, with a balanced training subset of 1,100 transcripts and a 2024 test set of 587. Ground‐truth investment labels (Strongly Buy, Buy, Hold, Sell, Strongly Sell) are assigned based on 30‐day post‐earnings stock performance. This text‐only dataset serves as a robust resource for investment decision making, planning, and broader NLP research.

## Dataset
```
record (single meeting transcript):
├── ticker              // Stock ticker as a string (e.g., "PPG")
├── date                // Meeting date as a string, typically in the "YYYY-MM-DD" format
├── participants        // List of participants, where each element is a dictionary containing:
│     ├── name          // Participant's name (string)
│     ├── description   // A brief description or role (string), e.g., "Vice President, Investor Relations"
│     └── position      // Position of the participant (string), e.g., "Executive" or "Analyst"
├── prepared_remarks    // List of pre-prepared remarks; each element is a string representing a segment of speech
└── questions_and_answers  // List of Q&A segments, where each element is a dictionary with:
      ├── name        // Name of the person asking the question or providing an answer (string)
      └── speech      // List of strings, with each string representing a sentence or segment of the spoken text
```
