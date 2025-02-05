---
layout: about
title: Home
permalink: /
subtitle:

news: false # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: false  # includes social icons at the bottom of the page
---

## Overview
Our dataset consists of 11,950 quarterly earnings call transcripts from major companies listed on the NASDAQ 500 and S&P 500, sourced from the [Motley Fool](https://www.fool.com/) website between 2017 and 2024. Each transcript contains an average of 10,187 tokens, making it a valuable testbed for investment decision prediction and market sentiment analysis. The dataset includes transcripts from 869 companies across 11 financial sectors. For training, we constructed a balanced subset of 1,100 transcripts (100 from each sector), while our test set comprises 587 transcripts from 2024, specifically selected to avoid overlap with LLM pretraining data (cutoff: December 2023). The dataset is annotated with ground-truth investment labels (Strongly Buy, Buy, Hold, Sell, or Strongly Sell) based on 30-day post-earnings stock performance, focusing solely on textual content without acoustic features.

## Acknowledgement

Please cite the following paper in work that makes use of this dataset:

[STRUX: An LLM for Decision-Making with Structured Explanations](https://arxiv.org/abs/2410.12583)\
Yiming Lu, Yebowen Hu, Hassan Foroosh, Wei Jin, Fei Liu\
In main conference of the Nations of the Americas Chapter of the Association for Computational Linguistics (NAACL'25), Albuquerque, US.

## Bibtex
```
@article{lu2024strux,
  title={STRUX: An LLM for Decision-Making with Structured Explanations},
  author={Lu, Yiming and Hu, Yebowen and Foroosh, Hassan and Jin, Wei and Liu, Fei},
  journal={arXiv preprint arXiv:2410.12583},
  year={2024}
}
```

## Usage
```python
from datasets import load_dataset
transcripts = load_dataset("BUILDERlym/STRUX-Transcripts")

train_data = transcripts['train']
test_data = transcripts['test']

def generator(data_split):
  for instance in data_split:
    yiled instance['ticker'], instance['date'], instance['participants'], instance['prepared_remarks'], instance['questions_and_answers']
```

**Python Scripts**
Useful scripts and guidance can be found in github repo [MeetingBank_Utils](https://github.com/YebowenHu/MeetingBank-utils)
