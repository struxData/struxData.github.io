---
layout: page
permalink: /dataset/
title: Dataset
description: 
nav: true
nav_order: 2
---

## Annotations

Manually annotated meeting segments and 

### Full meeting transcript
Each of the 85,803 manually annotated events is labeled as one of 5 filler classes or 8 non-filler classes (label: number of events).

Fillers
- Uh: 17,907

### Statistical Analysis


## Data Split for Machine Learning:

To facilitate  machine learning experiments, the audio data in this dataset (full-length recordings and preprocessed 1-sec clips) are pre-arranged into “train”, “validation”, and “test” folders. This split ensures that episodes from the same podcast show are always in the same subset (train, validation, or test), to prevent speaker leakage. We also ensured that each subset in this split remains gender balanced, same as the complete dataset.

We strongly recommend using this split in your experiments. It will ensure your results are not inflated due to overfitting, and that they are comparable to the results published in the [FillerNet paper](https://arxiv.org/abs/2203.15135)

## Reproducibility

The preprocessing utility functions and code repository for reproducing our experimental results: [PodcastFillersUtils](https://github.com/gzhu06/PodcastFillers_Utils)


## Dataset

PodcastFillers dataset contains audio files and metadata. Tree structure of the PodcastFillers dataset:

```
.
├── LICENSE_ANNOTATIONS_ADOBE_RESEARCH_LICENSE.txt
├── LICENSE_AUDIO.csv
├── README.txt
├── audio
│   ├── clip_wav
│   ├── episode_mp3
│   └── episode_wav
└── metadata
    ├── PodcastFillers.csv
    ├── episode_annotations
    ├── episode_sed_eval_paper
    ├── episode_transcripts
    └── episode_vad
```
### Metadata:
##### 1. Speech-to-text podcasts transcripts
Speech transcript in JSON format for each podcast episode. Generated using the [SpeechMatics STT](https://www.speechmatics.com/). Filename format: `{show name}_{episode name}.json`. 

Each word in the transcript is annotated as a dictionary:
```
{“confidence”:(float), “duration”:(int),  “offset”:(int),  “text”:(string)}
```
where “confidence” indicates the STT confidence in the prediction, “duration” (unit:microsecond or 1e-6 second) is the duration of the transcribed word, “offset” (unit:microsecond or 1e-6 second) is the start time of the transcribed word in the full-length recording.

##### 2. PodcastFillers.csv
This is the dataset’s main annotation file, and contains the annotations of all 85,803 manually annotated events. Each annotated event also corresponds to one pre-processed audio clip. For each annotated event / audio clip, we provide:

- **clip_name** (str): The filename of the audio clip containing this event: `{pfID}.wav`

- **pfID** (str): The PodcastFillers 5-digit ID of the clip/event, a unique identifier.

- **fullvoc_label** (str): The full-vocabulary label for this audio event, one of “Uh”, “Um”, “You know”, “Like”, “Other”, “Laughter”, “Breath”, “Agree”, “Words”, “Repetitions”, “Overlap”, “Music” and “Noise”. See [Annotations](/annotations/) for details.

- **consolidated_label** (str): Consolidated-vocabulary label used for training FillerNet, including “Uh”, “Um”, “Laughter”, “Breath”, “Words”, “Music” or “None”. “None” is assigned to events outside the consolidated vocabulary. See [Annotations](/annotations/) for details.

- **episode_split_subset** (str): The subset (train/validation/test) folder the episode this 1-second clip comes from belongs to. See Data Split for Machine Learning in [Annotations](/annotations/) for details.

- **clip_split_subset** (str): The subset (train/validation/test/extra) folder this 1-second clip belongs to. See Data Split for Machine Learning in [Annotations](/annotations/) for details. Note that while every episode belongs to one of train/validation/test, the clips are sorted into these subsets plus one additional folder “extra”, which contains clips that are excluded from the consolidated vocabulary. See [Annotations](/annotations/) for details.

- **podcast_filename** (str): The filename of the full-length podcast episode where this event occurs, it takes the format of `{show name}_{episode name}`

- **event_start_inepisode** (float): The start time of the event in the episode, unit: second.

- **event_end_inepisode** (float): The end time of the event in the episode, unit: second.

- **event_start_inclip** (float): The start time of the event in the 1-second clip, unit: second.

- **event_end_inclip** (float) : The end time of the event in the 1-second clip, unit: second.

- **clip_start_inepisode** (float): The start time of the 1-sec clip in the episode, unit: second.

- **clip_end_inspieosde** (float): The end time of the 1-sec clip in the episode, unit: second.

- **duration** (float): Duration of the event in the episode, unit: second. Note that it can be larger than 1.0 because some events are longer than 1 second.

- **confidence** (float): Confidence among crowd annotators, it indicates confidence in the range 0-1.

- **agreement** (int): Agreement among crowd annotators. It indicates the number of annotators.

##### 3. Per-episode csv files

These files have the exact same format as PodcastFillers.csv, but only contain the audio events for a specific podcast episode. There’s one file per episode. Filename format:  `{show name}_{episode name}.csv` 

##### 4. VAD activation csv files

Voice activity detection predictions using our pretained robust VAD model, the first column indicates time stamps (unit:second) and the second one indicates activations. Filename format:  `{show name}_{episode name}.csv`

##### 5. Ground truth and prediction sed_eval txt files

Ground truth and AVC-FillerNet predicted events using [sed_eval](https://tut-arg.github.io/sed_eval/) supported format: 
```
{start_time} {end_time} event_label
```
Filename format:  `{show name}_{episode name}.txt`
