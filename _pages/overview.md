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
Countless decisions shape our daily lives, and it is paramount to understand the how and why behind these choices. In this paper, we introduce a new LLM decision-making framework called STRUX, which enhances LLM decision-making by providing structured explanations. These include favorable and adverse facts related to the decision, along with their respective strengths. STRUX begins by distilling lengthy information into a concise table of key facts. It then employs a series of self-reflection steps to determine which of these facts are pivotal, categorizing them as either favorable or adverse in relation to a specific decision. Lastly, we fine-tune an LLM to identify and prioritize these key facts to optimize decision-making. STRUX has been evaluated on the challenging task of forecasting stock investment decisions based on earnings call transcripts and demonstrated superior performance against strong baselines. It enhances decision transparency by allowing users to understand the impact of different factors, representing a meaningful step towards practical decision-making with LLMs.


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
meetingbank = load_dataset("huuuyeah/meetingbank")

train_data = meetingbank['train']
test_data = meetingbank['test']
val_data = meetingbank['validation']

def generator(data_split):
  for instance in data_split:
    yiled instance['id'], instance['summary'], instance['transcript']
```

## Multi-media Resources

MeetingBank dataset will be hosted at Zenodo. The audio files of each meeting will be hosted individually on Huggingface. All resources will includes meeting audio, transcripts, meetingbank main JSON file, summaries from 6 systems and human annotations.

**Text & Audio**: [zenodo](https://zenodo.org/record/7989108), Huggingface([splits](https://huggingface.co/datasets/huuuyeah/meetingbank), [audio&transcripts](https://huggingface.co/datasets/huuuyeah/MeetingBank_Audio))

**Videos**: All meeting videos can be found in https://archive.org/

- [Alameda](https://archive.org/details/meetingbank-alameda), [Boston](https://archive.org/details/meetingbank-boston), [Denver](https://archive.org/details/meetingbank-denver), [Long Beach](https://archive.org/details/meetingbank-long-beach) ,[King County](https://archive.org/details/meetingbank-king-county), [Seattle](https://archive.org/details/meetingbank-seattle)

**Python Scripts**
Useful scripts and guidance can be found in github repo [MeetingBank_Utils](https://github.com/YebowenHu/MeetingBank-utils)
