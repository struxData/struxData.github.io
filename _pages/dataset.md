---
layout: page
permalink: /dataset/
title: Dataset
description: 
nav: true
nav_order: 2
---

## Annotations

Manually annotated meeting segments and parsed 

### Full meeting transcript


### Statistical Analysis


## Data Splits

## Reproducibility


## Dataset

PodcastFillers dataset contains audio files and metadata. Tree structure of the PodcastFillers dataset:

### Metadata:
##### 1. Speech-to-text meeting video transcripts
Speech transcript in JSON format for each podcast episode. Generated using the [SpeechMatics STT](https://www.speechmatics.com/). Filename format: `{show name}_{episode name}.json`. 

Each word in the transcript is annotated as a dictionary:
```
{“confidence”:(float), “duration”:(int),  “offset”:(int),  “text”:(string)}
```
where “confidence” indicates the STT confidence in the prediction, “duration” (unit:microsecond or 1e-6 second) is the duration of the transcribed word, “offset” (unit:microsecond or 1e-6 second) is the start time of the transcribed word in the full-length recording.

##### 2. MeetingBank.csv
